Azure Resource Manager resource envelope.
API Version: 2022-10-01.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateOrUpdate datastore (Azure Data Lake Gen1 w/ ServicePrincipal).
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var datastore = new AzureNative.MachineLearningServices.Datastore("datastore", new()
    {
        DatastoreProperties = new AzureNative.MachineLearningServices.Inputs.AzureDataLakeGen1DatastoreArgs
        {
            Credentials = new AzureNative.MachineLearningServices.Inputs.ServicePrincipalDatastoreCredentialsArgs
            {
                AuthorityUrl = "string",
                ClientId = "00000000-1111-2222-3333-444444444444",
                CredentialsType = "ServicePrincipal",
                ResourceUrl = "string",
                Secrets = new AzureNative.MachineLearningServices.Inputs.ServicePrincipalDatastoreSecretsArgs
                {
                    ClientSecret = "string",
                    SecretsType = "ServicePrincipal",
                },
                TenantId = "00000000-1111-2222-3333-444444444444",
            },
            DatastoreType = "AzureDataLakeGen1",
            Description = "string",
            StoreName = "string",
            Tags = 
            {
                { "string", "string" },
            },
        },
        Name = "string",
        ResourceGroupName = "test-rg",
        SkipValidation = false,
        WorkspaceName = "my-aml-workspace",
    });

});


```

```go
package main

import (
	machinelearningservices "github.com/pulumi/pulumi-azure-native-sdk/machinelearningservices"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := machinelearningservices.NewDatastore(ctx, "datastore", &machinelearningservices.DatastoreArgs{
			DatastoreProperties: machinelearningservices.AzureDataLakeGen1Datastore{
				Credentials: machinelearningservices.ServicePrincipalDatastoreCredentials{
					AuthorityUrl:    "string",
					ClientId:        "00000000-1111-2222-3333-444444444444",
					CredentialsType: "ServicePrincipal",
					ResourceUrl:     "string",
					Secrets: machinelearningservices.ServicePrincipalDatastoreSecrets{
						ClientSecret: "string",
						SecretsType:  "ServicePrincipal",
					},
					TenantId: "00000000-1111-2222-3333-444444444444",
				},
				DatastoreType: "AzureDataLakeGen1",
				Description:   "string",
				StoreName:     "string",
				Tags: map[string]interface{}{
					"string": "string",
				},
			},
			Name:              pulumi.String("string"),
			ResourceGroupName: pulumi.String("test-rg"),
			SkipValidation:    pulumi.Bool(false),
			WorkspaceName:     pulumi.String("my-aml-workspace"),
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
import com.pulumi.azurenative.machinelearningservices.Datastore;
import com.pulumi.azurenative.machinelearningservices.DatastoreArgs;
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
        var datastore = new Datastore("datastore", DatastoreArgs.builder()        
            .datastoreProperties(Map.ofEntries(
                Map.entry("credentials", Map.ofEntries(
                    Map.entry("authorityUrl", "string"),
                    Map.entry("clientId", "00000000-1111-2222-3333-444444444444"),
                    Map.entry("credentialsType", "ServicePrincipal"),
                    Map.entry("resourceUrl", "string"),
                    Map.entry("secrets", Map.ofEntries(
                        Map.entry("clientSecret", "string"),
                        Map.entry("secretsType", "ServicePrincipal")
                    )),
                    Map.entry("tenantId", "00000000-1111-2222-3333-444444444444")
                )),
                Map.entry("datastoreType", "AzureDataLakeGen1"),
                Map.entry("description", "string"),
                Map.entry("storeName", "string"),
                Map.entry("tags", AzureBlobDatastoreArgs.builder()
                    .string("string")
                    .build())
            ))
            .name("string")
            .resourceGroupName("test-rg")
            .skipValidation(false)
            .workspaceName("my-aml-workspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const datastore = new azure_native.machinelearningservices.Datastore("datastore", {
    datastoreProperties: {
        credentials: {
            authorityUrl: "string",
            clientId: "00000000-1111-2222-3333-444444444444",
            credentialsType: "ServicePrincipal",
            resourceUrl: "string",
            secrets: {
                clientSecret: "string",
                secretsType: "ServicePrincipal",
            },
            tenantId: "00000000-1111-2222-3333-444444444444",
        },
        datastoreType: "AzureDataLakeGen1",
        description: "string",
        storeName: "string",
        tags: {
            string: "string",
        },
    },
    name: "string",
    resourceGroupName: "test-rg",
    skipValidation: false,
    workspaceName: "my-aml-workspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

datastore = azure_native.machinelearningservices.Datastore("datastore",
    datastore_properties=azure_native.machinelearningservices.AzureDataLakeGen1DatastoreArgs(
        credentials=azure_native.machinelearningservices.ServicePrincipalDatastoreCredentialsArgs(
            authority_url="string",
            client_id="00000000-1111-2222-3333-444444444444",
            credentials_type="ServicePrincipal",
            resource_url="string",
            secrets=azure_native.machinelearningservices.ServicePrincipalDatastoreSecretsArgs(
                client_secret="string",
                secrets_type="ServicePrincipal",
            ),
            tenant_id="00000000-1111-2222-3333-444444444444",
        ),
        datastore_type="AzureDataLakeGen1",
        description="string",
        store_name="string",
        tags={
            "string": "string",
        },
    ),
    name="string",
    resource_group_name="test-rg",
    skip_validation=False,
    workspace_name="my-aml-workspace")

```

```yaml
resources:
  datastore:
    type: azure-native:machinelearningservices:Datastore
    properties:
      datastoreProperties:
        credentials:
          authorityUrl: string
          clientId: 00000000-1111-2222-3333-444444444444
          credentialsType: ServicePrincipal
          resourceUrl: string
          secrets:
            clientSecret: string
            secretsType: ServicePrincipal
          tenantId: 00000000-1111-2222-3333-444444444444
        datastoreType: AzureDataLakeGen1
        description: string
        storeName: string
        tags:
          string: string
      name: string
      resourceGroupName: test-rg
      skipValidation: false
      workspaceName: my-aml-workspace

```

{{% /example %}}
{{% example %}}
### CreateOrUpdate datastore (Azure Data Lake Gen2 w/ Service Principal).
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var datastore = new AzureNative.MachineLearningServices.Datastore("datastore", new()
    {
        DatastoreProperties = new AzureNative.MachineLearningServices.Inputs.AzureDataLakeGen2DatastoreArgs
        {
            AccountName = "string",
            Credentials = new AzureNative.MachineLearningServices.Inputs.ServicePrincipalDatastoreCredentialsArgs
            {
                AuthorityUrl = "string",
                ClientId = "00000000-1111-2222-3333-444444444444",
                CredentialsType = "ServicePrincipal",
                ResourceUrl = "string",
                Secrets = new AzureNative.MachineLearningServices.Inputs.ServicePrincipalDatastoreSecretsArgs
                {
                    ClientSecret = "string",
                    SecretsType = "ServicePrincipal",
                },
                TenantId = "00000000-1111-2222-3333-444444444444",
            },
            DatastoreType = "AzureDataLakeGen2",
            Description = "string",
            Endpoint = "string",
            Filesystem = "string",
            Protocol = "string",
            Tags = 
            {
                { "string", "string" },
            },
        },
        Name = "string",
        ResourceGroupName = "test-rg",
        SkipValidation = false,
        WorkspaceName = "my-aml-workspace",
    });

});


```

```go
package main

import (
	machinelearningservices "github.com/pulumi/pulumi-azure-native-sdk/machinelearningservices"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := machinelearningservices.NewDatastore(ctx, "datastore", &machinelearningservices.DatastoreArgs{
			DatastoreProperties: machinelearningservices.AzureDataLakeGen2Datastore{
				AccountName: "string",
				Credentials: machinelearningservices.ServicePrincipalDatastoreCredentials{
					AuthorityUrl:    "string",
					ClientId:        "00000000-1111-2222-3333-444444444444",
					CredentialsType: "ServicePrincipal",
					ResourceUrl:     "string",
					Secrets: machinelearningservices.ServicePrincipalDatastoreSecrets{
						ClientSecret: "string",
						SecretsType:  "ServicePrincipal",
					},
					TenantId: "00000000-1111-2222-3333-444444444444",
				},
				DatastoreType: "AzureDataLakeGen2",
				Description:   "string",
				Endpoint:      "string",
				Filesystem:    "string",
				Protocol:      "string",
				Tags: map[string]interface{}{
					"string": "string",
				},
			},
			Name:              pulumi.String("string"),
			ResourceGroupName: pulumi.String("test-rg"),
			SkipValidation:    pulumi.Bool(false),
			WorkspaceName:     pulumi.String("my-aml-workspace"),
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
import com.pulumi.azurenative.machinelearningservices.Datastore;
import com.pulumi.azurenative.machinelearningservices.DatastoreArgs;
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
        var datastore = new Datastore("datastore", DatastoreArgs.builder()        
            .datastoreProperties(Map.ofEntries(
                Map.entry("accountName", "string"),
                Map.entry("credentials", Map.ofEntries(
                    Map.entry("authorityUrl", "string"),
                    Map.entry("clientId", "00000000-1111-2222-3333-444444444444"),
                    Map.entry("credentialsType", "ServicePrincipal"),
                    Map.entry("resourceUrl", "string"),
                    Map.entry("secrets", Map.ofEntries(
                        Map.entry("clientSecret", "string"),
                        Map.entry("secretsType", "ServicePrincipal")
                    )),
                    Map.entry("tenantId", "00000000-1111-2222-3333-444444444444")
                )),
                Map.entry("datastoreType", "AzureDataLakeGen2"),
                Map.entry("description", "string"),
                Map.entry("endpoint", "string"),
                Map.entry("filesystem", "string"),
                Map.entry("protocol", "string"),
                Map.entry("tags", AzureBlobDatastoreArgs.builder()
                    .string("string")
                    .build())
            ))
            .name("string")
            .resourceGroupName("test-rg")
            .skipValidation(false)
            .workspaceName("my-aml-workspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const datastore = new azure_native.machinelearningservices.Datastore("datastore", {
    datastoreProperties: {
        accountName: "string",
        credentials: {
            authorityUrl: "string",
            clientId: "00000000-1111-2222-3333-444444444444",
            credentialsType: "ServicePrincipal",
            resourceUrl: "string",
            secrets: {
                clientSecret: "string",
                secretsType: "ServicePrincipal",
            },
            tenantId: "00000000-1111-2222-3333-444444444444",
        },
        datastoreType: "AzureDataLakeGen2",
        description: "string",
        endpoint: "string",
        filesystem: "string",
        protocol: "string",
        tags: {
            string: "string",
        },
    },
    name: "string",
    resourceGroupName: "test-rg",
    skipValidation: false,
    workspaceName: "my-aml-workspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

datastore = azure_native.machinelearningservices.Datastore("datastore",
    datastore_properties=azure_native.machinelearningservices.AzureDataLakeGen2DatastoreArgs(
        account_name="string",
        credentials=azure_native.machinelearningservices.ServicePrincipalDatastoreCredentialsArgs(
            authority_url="string",
            client_id="00000000-1111-2222-3333-444444444444",
            credentials_type="ServicePrincipal",
            resource_url="string",
            secrets=azure_native.machinelearningservices.ServicePrincipalDatastoreSecretsArgs(
                client_secret="string",
                secrets_type="ServicePrincipal",
            ),
            tenant_id="00000000-1111-2222-3333-444444444444",
        ),
        datastore_type="AzureDataLakeGen2",
        description="string",
        endpoint="string",
        filesystem="string",
        protocol="string",
        tags={
            "string": "string",
        },
    ),
    name="string",
    resource_group_name="test-rg",
    skip_validation=False,
    workspace_name="my-aml-workspace")

```

```yaml
resources:
  datastore:
    type: azure-native:machinelearningservices:Datastore
    properties:
      datastoreProperties:
        accountName: string
        credentials:
          authorityUrl: string
          clientId: 00000000-1111-2222-3333-444444444444
          credentialsType: ServicePrincipal
          resourceUrl: string
          secrets:
            clientSecret: string
            secretsType: ServicePrincipal
          tenantId: 00000000-1111-2222-3333-444444444444
        datastoreType: AzureDataLakeGen2
        description: string
        endpoint: string
        filesystem: string
        protocol: string
        tags:
          string: string
      name: string
      resourceGroupName: test-rg
      skipValidation: false
      workspaceName: my-aml-workspace

```

{{% /example %}}
{{% example %}}
### CreateOrUpdate datastore (Azure File store w/ AccountKey).
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var datastore = new AzureNative.MachineLearningServices.Datastore("datastore", new()
    {
        DatastoreProperties = new AzureNative.MachineLearningServices.Inputs.AzureFileDatastoreArgs
        {
            AccountName = "string",
            Credentials = new AzureNative.MachineLearningServices.Inputs.AccountKeyDatastoreCredentialsArgs
            {
                CredentialsType = "AccountKey",
                Secrets = new AzureNative.MachineLearningServices.Inputs.AccountKeyDatastoreSecretsArgs
                {
                    Key = "string",
                    SecretsType = "AccountKey",
                },
            },
            DatastoreType = "AzureFile",
            Description = "string",
            Endpoint = "string",
            FileShareName = "string",
            Protocol = "string",
            Tags = 
            {
                { "string", "string" },
            },
        },
        Name = "string",
        ResourceGroupName = "test-rg",
        SkipValidation = false,
        WorkspaceName = "my-aml-workspace",
    });

});


```

```go
package main

import (
	machinelearningservices "github.com/pulumi/pulumi-azure-native-sdk/machinelearningservices"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := machinelearningservices.NewDatastore(ctx, "datastore", &machinelearningservices.DatastoreArgs{
			DatastoreProperties: machinelearningservices.AzureFileDatastore{
				AccountName: "string",
				Credentials: machinelearningservices.AccountKeyDatastoreCredentials{
					CredentialsType: "AccountKey",
					Secrets: machinelearningservices.AccountKeyDatastoreSecrets{
						Key:         "string",
						SecretsType: "AccountKey",
					},
				},
				DatastoreType: "AzureFile",
				Description:   "string",
				Endpoint:      "string",
				FileShareName: "string",
				Protocol:      "string",
				Tags: map[string]interface{}{
					"string": "string",
				},
			},
			Name:              pulumi.String("string"),
			ResourceGroupName: pulumi.String("test-rg"),
			SkipValidation:    pulumi.Bool(false),
			WorkspaceName:     pulumi.String("my-aml-workspace"),
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
import com.pulumi.azurenative.machinelearningservices.Datastore;
import com.pulumi.azurenative.machinelearningservices.DatastoreArgs;
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
        var datastore = new Datastore("datastore", DatastoreArgs.builder()        
            .datastoreProperties(Map.ofEntries(
                Map.entry("accountName", "string"),
                Map.entry("credentials", Map.ofEntries(
                    Map.entry("credentialsType", "AccountKey"),
                    Map.entry("secrets", Map.ofEntries(
                        Map.entry("key", "string"),
                        Map.entry("secretsType", "AccountKey")
                    ))
                )),
                Map.entry("datastoreType", "AzureFile"),
                Map.entry("description", "string"),
                Map.entry("endpoint", "string"),
                Map.entry("fileShareName", "string"),
                Map.entry("protocol", "string"),
                Map.entry("tags", AzureBlobDatastoreArgs.builder()
                    .string("string")
                    .build())
            ))
            .name("string")
            .resourceGroupName("test-rg")
            .skipValidation(false)
            .workspaceName("my-aml-workspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const datastore = new azure_native.machinelearningservices.Datastore("datastore", {
    datastoreProperties: {
        accountName: "string",
        credentials: {
            credentialsType: "AccountKey",
            secrets: {
                key: "string",
                secretsType: "AccountKey",
            },
        },
        datastoreType: "AzureFile",
        description: "string",
        endpoint: "string",
        fileShareName: "string",
        protocol: "string",
        tags: {
            string: "string",
        },
    },
    name: "string",
    resourceGroupName: "test-rg",
    skipValidation: false,
    workspaceName: "my-aml-workspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

datastore = azure_native.machinelearningservices.Datastore("datastore",
    datastore_properties=azure_native.machinelearningservices.AzureFileDatastoreArgs(
        account_name="string",
        credentials=azure_native.machinelearningservices.AccountKeyDatastoreCredentialsArgs(
            credentials_type="AccountKey",
            secrets=azure_native.machinelearningservices.AccountKeyDatastoreSecretsArgs(
                key="string",
                secrets_type="AccountKey",
            ),
        ),
        datastore_type="AzureFile",
        description="string",
        endpoint="string",
        file_share_name="string",
        protocol="string",
        tags={
            "string": "string",
        },
    ),
    name="string",
    resource_group_name="test-rg",
    skip_validation=False,
    workspace_name="my-aml-workspace")

```

```yaml
resources:
  datastore:
    type: azure-native:machinelearningservices:Datastore
    properties:
      datastoreProperties:
        accountName: string
        credentials:
          credentialsType: AccountKey
          secrets:
            key: string
            secretsType: AccountKey
        datastoreType: AzureFile
        description: string
        endpoint: string
        fileShareName: string
        protocol: string
        tags:
          string: string
      name: string
      resourceGroupName: test-rg
      skipValidation: false
      workspaceName: my-aml-workspace

```

{{% /example %}}
{{% example %}}
### CreateOrUpdate datastore (AzureBlob w/ AccountKey).
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var datastore = new AzureNative.MachineLearningServices.Datastore("datastore", new()
    {
        DatastoreProperties = new AzureNative.MachineLearningServices.Inputs.AzureBlobDatastoreArgs
        {
            AccountName = "string",
            ContainerName = "string",
            Credentials = new AzureNative.MachineLearningServices.Inputs.AccountKeyDatastoreCredentialsArgs
            {
                CredentialsType = "AccountKey",
                Secrets = new AzureNative.MachineLearningServices.Inputs.AccountKeyDatastoreSecretsArgs
                {
                    Key = "string",
                    SecretsType = "AccountKey",
                },
            },
            DatastoreType = "AzureBlob",
            Description = "string",
            Endpoint = "core.windows.net",
            Protocol = "https",
            Tags = 
            {
                { "string", "string" },
            },
        },
        Name = "string",
        ResourceGroupName = "test-rg",
        SkipValidation = false,
        WorkspaceName = "my-aml-workspace",
    });

});


```

```go
package main

import (
	machinelearningservices "github.com/pulumi/pulumi-azure-native-sdk/machinelearningservices"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := machinelearningservices.NewDatastore(ctx, "datastore", &machinelearningservices.DatastoreArgs{
			DatastoreProperties: machinelearningservices.AzureBlobDatastore{
				AccountName:   "string",
				ContainerName: "string",
				Credentials: machinelearningservices.AccountKeyDatastoreCredentials{
					CredentialsType: "AccountKey",
					Secrets: machinelearningservices.AccountKeyDatastoreSecrets{
						Key:         "string",
						SecretsType: "AccountKey",
					},
				},
				DatastoreType: "AzureBlob",
				Description:   "string",
				Endpoint:      "core.windows.net",
				Protocol:      "https",
				Tags: map[string]interface{}{
					"string": "string",
				},
			},
			Name:              pulumi.String("string"),
			ResourceGroupName: pulumi.String("test-rg"),
			SkipValidation:    pulumi.Bool(false),
			WorkspaceName:     pulumi.String("my-aml-workspace"),
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
import com.pulumi.azurenative.machinelearningservices.Datastore;
import com.pulumi.azurenative.machinelearningservices.DatastoreArgs;
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
        var datastore = new Datastore("datastore", DatastoreArgs.builder()        
            .datastoreProperties(Map.ofEntries(
                Map.entry("accountName", "string"),
                Map.entry("containerName", "string"),
                Map.entry("credentials", Map.ofEntries(
                    Map.entry("credentialsType", "AccountKey"),
                    Map.entry("secrets", Map.ofEntries(
                        Map.entry("key", "string"),
                        Map.entry("secretsType", "AccountKey")
                    ))
                )),
                Map.entry("datastoreType", "AzureBlob"),
                Map.entry("description", "string"),
                Map.entry("endpoint", "core.windows.net"),
                Map.entry("protocol", "https"),
                Map.entry("tags", AzureBlobDatastoreArgs.builder()
                    .string("string")
                    .build())
            ))
            .name("string")
            .resourceGroupName("test-rg")
            .skipValidation(false)
            .workspaceName("my-aml-workspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const datastore = new azure_native.machinelearningservices.Datastore("datastore", {
    datastoreProperties: {
        accountName: "string",
        containerName: "string",
        credentials: {
            credentialsType: "AccountKey",
            secrets: {
                key: "string",
                secretsType: "AccountKey",
            },
        },
        datastoreType: "AzureBlob",
        description: "string",
        endpoint: "core.windows.net",
        protocol: "https",
        tags: {
            string: "string",
        },
    },
    name: "string",
    resourceGroupName: "test-rg",
    skipValidation: false,
    workspaceName: "my-aml-workspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

datastore = azure_native.machinelearningservices.Datastore("datastore",
    datastore_properties=azure_native.machinelearningservices.AzureBlobDatastoreArgs(
        account_name="string",
        container_name="string",
        credentials=azure_native.machinelearningservices.AccountKeyDatastoreCredentialsArgs(
            credentials_type="AccountKey",
            secrets=azure_native.machinelearningservices.AccountKeyDatastoreSecretsArgs(
                key="string",
                secrets_type="AccountKey",
            ),
        ),
        datastore_type="AzureBlob",
        description="string",
        endpoint="core.windows.net",
        protocol="https",
        tags={
            "string": "string",
        },
    ),
    name="string",
    resource_group_name="test-rg",
    skip_validation=False,
    workspace_name="my-aml-workspace")

```

```yaml
resources:
  datastore:
    type: azure-native:machinelearningservices:Datastore
    properties:
      datastoreProperties:
        accountName: string
        containerName: string
        credentials:
          credentialsType: AccountKey
          secrets:
            key: string
            secretsType: AccountKey
        datastoreType: AzureBlob
        description: string
        endpoint: core.windows.net
        protocol: https
        tags:
          string: string
      name: string
      resourceGroupName: test-rg
      skipValidation: false
      workspaceName: my-aml-workspace

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:machinelearningservices:Datastore string string 
```
