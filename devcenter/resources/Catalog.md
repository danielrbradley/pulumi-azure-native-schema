Represents a catalog.
API Version: 2022-11-11-preview.
Previous API Version: 2022-09-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Catalogs_CreateOrUpdateAdo
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var catalog = new AzureNative.DevCenter.Catalog("catalog", new()
    {
        AdoGit = new AzureNative.DevCenter.Inputs.GitCatalogArgs
        {
            Branch = "main",
            Path = "/templates",
            SecretIdentifier = "https://contosokv.vault.azure.net/secrets/CentralRepoPat",
            Uri = "https://contoso@dev.azure.com/contoso/contosoOrg/_git/centralrepo-fakecontoso",
        },
        CatalogName = "CentralCatalog",
        DevCenterName = "Contoso",
        ResourceGroupName = "rg1",
    });

});


```

```go
package main

import (
	devcenter "github.com/pulumi/pulumi-azure-native-sdk/devcenter"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := devcenter.NewCatalog(ctx, "catalog", &devcenter.CatalogArgs{
			AdoGit: &devcenter.GitCatalogArgs{
				Branch:           pulumi.String("main"),
				Path:             pulumi.String("/templates"),
				SecretIdentifier: pulumi.String("https://contosokv.vault.azure.net/secrets/CentralRepoPat"),
				Uri:              pulumi.String("https://contoso@dev.azure.com/contoso/contosoOrg/_git/centralrepo-fakecontoso"),
			},
			CatalogName:       pulumi.String("CentralCatalog"),
			DevCenterName:     pulumi.String("Contoso"),
			ResourceGroupName: pulumi.String("rg1"),
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
import com.pulumi.azurenative.devcenter.Catalog;
import com.pulumi.azurenative.devcenter.CatalogArgs;
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
        var catalog = new Catalog("catalog", CatalogArgs.builder()        
            .adoGit(Map.ofEntries(
                Map.entry("branch", "main"),
                Map.entry("path", "/templates"),
                Map.entry("secretIdentifier", "https://contosokv.vault.azure.net/secrets/CentralRepoPat"),
                Map.entry("uri", "https://contoso@dev.azure.com/contoso/contosoOrg/_git/centralrepo-fakecontoso")
            ))
            .catalogName("CentralCatalog")
            .devCenterName("Contoso")
            .resourceGroupName("rg1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const catalog = new azure_native.devcenter.Catalog("catalog", {
    adoGit: {
        branch: "main",
        path: "/templates",
        secretIdentifier: "https://contosokv.vault.azure.net/secrets/CentralRepoPat",
        uri: "https://contoso@dev.azure.com/contoso/contosoOrg/_git/centralrepo-fakecontoso",
    },
    catalogName: "CentralCatalog",
    devCenterName: "Contoso",
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

catalog = azure_native.devcenter.Catalog("catalog",
    ado_git=azure_native.devcenter.GitCatalogArgs(
        branch="main",
        path="/templates",
        secret_identifier="https://contosokv.vault.azure.net/secrets/CentralRepoPat",
        uri="https://contoso@dev.azure.com/contoso/contosoOrg/_git/centralrepo-fakecontoso",
    ),
    catalog_name="CentralCatalog",
    dev_center_name="Contoso",
    resource_group_name="rg1")

```

```yaml
resources:
  catalog:
    type: azure-native:devcenter:Catalog
    properties:
      adoGit:
        branch: main
        path: /templates
        secretIdentifier: https://contosokv.vault.azure.net/secrets/CentralRepoPat
        uri: https://contoso@dev.azure.com/contoso/contosoOrg/_git/centralrepo-fakecontoso
      catalogName: CentralCatalog
      devCenterName: Contoso
      resourceGroupName: rg1

```

{{% /example %}}
{{% example %}}
### Catalogs_CreateOrUpdateGitHub
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var catalog = new AzureNative.DevCenter.Catalog("catalog", new()
    {
        CatalogName = "CentralCatalog",
        DevCenterName = "Contoso",
        GitHub = new AzureNative.DevCenter.Inputs.GitCatalogArgs
        {
            Branch = "main",
            Path = "/templates",
            SecretIdentifier = "https://contosokv.vault.azure.net/secrets/CentralRepoPat",
            Uri = "https://github.com/Contoso/centralrepo-fake.git",
        },
        ResourceGroupName = "rg1",
    });

});


```

```go
package main

import (
	devcenter "github.com/pulumi/pulumi-azure-native-sdk/devcenter"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := devcenter.NewCatalog(ctx, "catalog", &devcenter.CatalogArgs{
			CatalogName:   pulumi.String("CentralCatalog"),
			DevCenterName: pulumi.String("Contoso"),
			GitHub: &devcenter.GitCatalogArgs{
				Branch:           pulumi.String("main"),
				Path:             pulumi.String("/templates"),
				SecretIdentifier: pulumi.String("https://contosokv.vault.azure.net/secrets/CentralRepoPat"),
				Uri:              pulumi.String("https://github.com/Contoso/centralrepo-fake.git"),
			},
			ResourceGroupName: pulumi.String("rg1"),
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
import com.pulumi.azurenative.devcenter.Catalog;
import com.pulumi.azurenative.devcenter.CatalogArgs;
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
        var catalog = new Catalog("catalog", CatalogArgs.builder()        
            .catalogName("CentralCatalog")
            .devCenterName("Contoso")
            .gitHub(Map.ofEntries(
                Map.entry("branch", "main"),
                Map.entry("path", "/templates"),
                Map.entry("secretIdentifier", "https://contosokv.vault.azure.net/secrets/CentralRepoPat"),
                Map.entry("uri", "https://github.com/Contoso/centralrepo-fake.git")
            ))
            .resourceGroupName("rg1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const catalog = new azure_native.devcenter.Catalog("catalog", {
    catalogName: "CentralCatalog",
    devCenterName: "Contoso",
    gitHub: {
        branch: "main",
        path: "/templates",
        secretIdentifier: "https://contosokv.vault.azure.net/secrets/CentralRepoPat",
        uri: "https://github.com/Contoso/centralrepo-fake.git",
    },
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

catalog = azure_native.devcenter.Catalog("catalog",
    catalog_name="CentralCatalog",
    dev_center_name="Contoso",
    git_hub=azure_native.devcenter.GitCatalogArgs(
        branch="main",
        path="/templates",
        secret_identifier="https://contosokv.vault.azure.net/secrets/CentralRepoPat",
        uri="https://github.com/Contoso/centralrepo-fake.git",
    ),
    resource_group_name="rg1")

```

```yaml
resources:
  catalog:
    type: azure-native:devcenter:Catalog
    properties:
      catalogName: CentralCatalog
      devCenterName: Contoso
      gitHub:
        branch: main
        path: /templates
        secretIdentifier: https://contosokv.vault.azure.net/secrets/CentralRepoPat
        uri: https://github.com/Contoso/centralrepo-fake.git
      resourceGroupName: rg1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:devcenter:Catalog CentralCatalog /subscriptions/0ac520ee-14c0-480f-b6c9-0a90c58ffff/resourceGroups/rg1/providers/Microsoft.DevCenter/devcenters/Contoso/catalogs/CentralCatalog 
```
