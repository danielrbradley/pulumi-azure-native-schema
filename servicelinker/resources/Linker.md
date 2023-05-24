Linker of source and target resource
API Version: 2022-05-01.
Previous API Version: 2021-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### PutLink
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var linker = new AzureNative.ServiceLinker.Linker("linker", new()
    {
        AuthInfo = new AzureNative.ServiceLinker.Inputs.SecretAuthInfoArgs
        {
            AuthType = "secret",
            Name = "name",
            SecretInfo = new AzureNative.ServiceLinker.Inputs.ValueSecretInfoArgs
            {
                SecretType = "rawValue",
                Value = "secret",
            },
        },
        LinkerName = "linkName",
        ResourceUri = "subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.Web/sites/test-app",
        TargetService = new AzureNative.ServiceLinker.Inputs.AzureResourceArgs
        {
            Id = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.DBforPostgreSQL/servers/test-pg/databases/test-db",
            Type = "AzureResource",
        },
    });

});


```

```go
package main

import (
	servicelinker "github.com/pulumi/pulumi-azure-native-sdk/servicelinker"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := servicelinker.NewLinker(ctx, "linker", &servicelinker.LinkerArgs{
			AuthInfo: servicelinker.SecretAuthInfo{
				AuthType: "secret",
				Name:     "name",
				SecretInfo: servicelinker.ValueSecretInfo{
					SecretType: "rawValue",
					Value:      "secret",
				},
			},
			LinkerName:  pulumi.String("linkName"),
			ResourceUri: pulumi.String("subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.Web/sites/test-app"),
			TargetService: servicelinker.AzureResource{
				Id:   "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.DBforPostgreSQL/servers/test-pg/databases/test-db",
				Type: "AzureResource",
			},
		})
		if err != nil {
			return err
		}
		return nil
	})
}

```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.servicelinker.Linker;
import com.pulumi.azurenative.servicelinker.LinkerArgs;
import java.util.List;
import java.util.ArrayList;
import java.util.Map;
import java.io.File;
import java.nio.file.Files;
import java.nio.file.Paths;

public class App {
    public static void main(String[] args) {
        Pulumi.run(App::stack);
    }

    public static void stack(Context ctx) {
        var linker = new Linker("linker", LinkerArgs.builder()        
            .authInfo(Map.ofEntries(
                Map.entry("authType", "secret"),
                Map.entry("name", "name"),
                Map.entry("secretInfo", Map.ofEntries(
                    Map.entry("secretType", "rawValue"),
                    Map.entry("value", "secret")
                ))
            ))
            .linkerName("linkName")
            .resourceUri("subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.Web/sites/test-app")
            .targetService(Map.ofEntries(
                Map.entry("id", "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.DBforPostgreSQL/servers/test-pg/databases/test-db"),
                Map.entry("type", "AzureResource")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const linker = new azure_native.servicelinker.Linker("linker", {
    authInfo: {
        authType: "secret",
        name: "name",
        secretInfo: {
            secretType: "rawValue",
            value: "secret",
        },
    },
    linkerName: "linkName",
    resourceUri: "subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.Web/sites/test-app",
    targetService: {
        id: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.DBforPostgreSQL/servers/test-pg/databases/test-db",
        type: "AzureResource",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

linker = azure_native.servicelinker.Linker("linker",
    auth_info=azure_native.servicelinker.SecretAuthInfoArgs(
        auth_type="secret",
        name="name",
        secret_info=azure_native.servicelinker.ValueSecretInfoArgs(
            secret_type="rawValue",
            value="secret",
        ),
    ),
    linker_name="linkName",
    resource_uri="subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.Web/sites/test-app",
    target_service=azure_native.servicelinker.AzureResourceArgs(
        id="/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.DBforPostgreSQL/servers/test-pg/databases/test-db",
        type="AzureResource",
    ))

```

```yaml
resources:
  linker:
    type: azure-native:servicelinker:Linker
    properties:
      authInfo:
        authType: secret
        name: name
        secretInfo:
          secretType: rawValue
          value: secret
      linkerName: linkName
      resourceUri: subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.Web/sites/test-app
      targetService:
        id: /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.DBforPostgreSQL/servers/test-pg/databases/test-db
        type: AzureResource

```

{{% /example %}}
{{% example %}}
### PutLinkWithSecretStore
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var linker = new AzureNative.ServiceLinker.Linker("linker", new()
    {
        AuthInfo = new AzureNative.ServiceLinker.Inputs.SecretAuthInfoArgs
        {
            AuthType = "secret",
        },
        LinkerName = "linkName",
        ResourceUri = "subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.Web/sites/test-app",
        SecretStore = new AzureNative.ServiceLinker.Inputs.SecretStoreArgs
        {
            KeyVaultId = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.KeyVault/vaults/test-kv",
        },
        TargetService = new AzureNative.ServiceLinker.Inputs.AzureResourceArgs
        {
            Id = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.DocumentDb/databaseAccounts/test-acc/mongodbDatabases/test-db",
            Type = "AzureResource",
        },
    });

});


```

```go
package main

import (
	servicelinker "github.com/pulumi/pulumi-azure-native-sdk/servicelinker"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := servicelinker.NewLinker(ctx, "linker", &servicelinker.LinkerArgs{
			AuthInfo: servicelinker.SecretAuthInfo{
				AuthType: "secret",
			},
			LinkerName:  pulumi.String("linkName"),
			ResourceUri: pulumi.String("subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.Web/sites/test-app"),
			SecretStore: &servicelinker.SecretStoreArgs{
				KeyVaultId: pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.KeyVault/vaults/test-kv"),
			},
			TargetService: servicelinker.AzureResource{
				Id:   "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.DocumentDb/databaseAccounts/test-acc/mongodbDatabases/test-db",
				Type: "AzureResource",
			},
		})
		if err != nil {
			return err
		}
		return nil
	})
}

```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.servicelinker.Linker;
import com.pulumi.azurenative.servicelinker.LinkerArgs;
import java.util.List;
import java.util.ArrayList;
import java.util.Map;
import java.io.File;
import java.nio.file.Files;
import java.nio.file.Paths;

public class App {
    public static void main(String[] args) {
        Pulumi.run(App::stack);
    }

    public static void stack(Context ctx) {
        var linker = new Linker("linker", LinkerArgs.builder()        
            .authInfo(Map.of("authType", "secret"))
            .linkerName("linkName")
            .resourceUri("subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.Web/sites/test-app")
            .secretStore(Map.of("keyVaultId", "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.KeyVault/vaults/test-kv"))
            .targetService(Map.ofEntries(
                Map.entry("id", "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.DocumentDb/databaseAccounts/test-acc/mongodbDatabases/test-db"),
                Map.entry("type", "AzureResource")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const linker = new azure_native.servicelinker.Linker("linker", {
    authInfo: {
        authType: "secret",
    },
    linkerName: "linkName",
    resourceUri: "subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.Web/sites/test-app",
    secretStore: {
        keyVaultId: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.KeyVault/vaults/test-kv",
    },
    targetService: {
        id: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.DocumentDb/databaseAccounts/test-acc/mongodbDatabases/test-db",
        type: "AzureResource",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

linker = azure_native.servicelinker.Linker("linker",
    auth_info=azure_native.servicelinker.SecretAuthInfoArgs(
        auth_type="secret",
    ),
    linker_name="linkName",
    resource_uri="subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.Web/sites/test-app",
    secret_store=azure_native.servicelinker.SecretStoreArgs(
        key_vault_id="/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.KeyVault/vaults/test-kv",
    ),
    target_service=azure_native.servicelinker.AzureResourceArgs(
        id="/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.DocumentDb/databaseAccounts/test-acc/mongodbDatabases/test-db",
        type="AzureResource",
    ))

```

```yaml
resources:
  linker:
    type: azure-native:servicelinker:Linker
    properties:
      authInfo:
        authType: secret
      linkerName: linkName
      resourceUri: subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.Web/sites/test-app
      secretStore:
        keyVaultId: /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.KeyVault/vaults/test-kv
      targetService:
        id: /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.DocumentDb/databaseAccounts/test-acc/mongodbDatabases/test-db
        type: AzureResource

```

{{% /example %}}
{{% example %}}
### PutLinkWithServiceEndpoint
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var linker = new AzureNative.ServiceLinker.Linker("linker", new()
    {
        AuthInfo = new AzureNative.ServiceLinker.Inputs.SecretAuthInfoArgs
        {
            AuthType = "secret",
            Name = "name",
            SecretInfo = new AzureNative.ServiceLinker.Inputs.KeyVaultSecretUriSecretInfoArgs
            {
                SecretType = "keyVaultSecretUri",
                Value = "https://vault-name.vault.azure.net/secrets/secret-name/00000000000000000000000000000000",
            },
        },
        LinkerName = "linkName",
        ResourceUri = "subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.Web/sites/test-app",
        TargetService = new AzureNative.ServiceLinker.Inputs.AzureResourceArgs
        {
            Id = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.DBforPostgreSQL/servers/test-pg/databases/test-db",
            Type = "AzureResource",
        },
        VNetSolution = new AzureNative.ServiceLinker.Inputs.VNetSolutionArgs
        {
            Type = "serviceEndpoint",
        },
    });

});


```

```go
package main

import (
	servicelinker "github.com/pulumi/pulumi-azure-native-sdk/servicelinker"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := servicelinker.NewLinker(ctx, "linker", &servicelinker.LinkerArgs{
			AuthInfo: servicelinker.SecretAuthInfo{
				AuthType: "secret",
				Name:     "name",
				SecretInfo: servicelinker.KeyVaultSecretUriSecretInfo{
					SecretType: "keyVaultSecretUri",
					Value:      "https://vault-name.vault.azure.net/secrets/secret-name/00000000000000000000000000000000",
				},
			},
			LinkerName:  pulumi.String("linkName"),
			ResourceUri: pulumi.String("subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.Web/sites/test-app"),
			TargetService: servicelinker.AzureResource{
				Id:   "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.DBforPostgreSQL/servers/test-pg/databases/test-db",
				Type: "AzureResource",
			},
			VNetSolution: &servicelinker.VNetSolutionArgs{
				Type: pulumi.String("serviceEndpoint"),
			},
		})
		if err != nil {
			return err
		}
		return nil
	})
}

```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.servicelinker.Linker;
import com.pulumi.azurenative.servicelinker.LinkerArgs;
import java.util.List;
import java.util.ArrayList;
import java.util.Map;
import java.io.File;
import java.nio.file.Files;
import java.nio.file.Paths;

public class App {
    public static void main(String[] args) {
        Pulumi.run(App::stack);
    }

    public static void stack(Context ctx) {
        var linker = new Linker("linker", LinkerArgs.builder()        
            .authInfo(Map.ofEntries(
                Map.entry("authType", "secret"),
                Map.entry("name", "name"),
                Map.entry("secretInfo", Map.ofEntries(
                    Map.entry("secretType", "keyVaultSecretUri"),
                    Map.entry("value", "https://vault-name.vault.azure.net/secrets/secret-name/00000000000000000000000000000000")
                ))
            ))
            .linkerName("linkName")
            .resourceUri("subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.Web/sites/test-app")
            .targetService(Map.ofEntries(
                Map.entry("id", "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.DBforPostgreSQL/servers/test-pg/databases/test-db"),
                Map.entry("type", "AzureResource")
            ))
            .vNetSolution(Map.of("type", "serviceEndpoint"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const linker = new azure_native.servicelinker.Linker("linker", {
    authInfo: {
        authType: "secret",
        name: "name",
        secretInfo: {
            secretType: "keyVaultSecretUri",
            value: "https://vault-name.vault.azure.net/secrets/secret-name/00000000000000000000000000000000",
        },
    },
    linkerName: "linkName",
    resourceUri: "subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.Web/sites/test-app",
    targetService: {
        id: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.DBforPostgreSQL/servers/test-pg/databases/test-db",
        type: "AzureResource",
    },
    vNetSolution: {
        type: "serviceEndpoint",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

linker = azure_native.servicelinker.Linker("linker",
    auth_info=azure_native.servicelinker.SecretAuthInfoArgs(
        auth_type="secret",
        name="name",
        secret_info=azure_native.servicelinker.KeyVaultSecretUriSecretInfoArgs(
            secret_type="keyVaultSecretUri",
            value="https://vault-name.vault.azure.net/secrets/secret-name/00000000000000000000000000000000",
        ),
    ),
    linker_name="linkName",
    resource_uri="subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.Web/sites/test-app",
    target_service=azure_native.servicelinker.AzureResourceArgs(
        id="/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.DBforPostgreSQL/servers/test-pg/databases/test-db",
        type="AzureResource",
    ),
    v_net_solution=azure_native.servicelinker.VNetSolutionArgs(
        type="serviceEndpoint",
    ))

```

```yaml
resources:
  linker:
    type: azure-native:servicelinker:Linker
    properties:
      authInfo:
        authType: secret
        name: name
        secretInfo:
          secretType: keyVaultSecretUri
          value: https://vault-name.vault.azure.net/secrets/secret-name/00000000000000000000000000000000
      linkerName: linkName
      resourceUri: subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.Web/sites/test-app
      targetService:
        id: /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.DBforPostgreSQL/servers/test-pg/databases/test-db
        type: AzureResource
      vNetSolution:
        type: serviceEndpoint

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:servicelinker:Linker linkName /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.Web/sites/test-app/providers/Microsoft.ServiceLinker/links/linkName 
```
