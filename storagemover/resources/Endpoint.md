The Endpoint resource, which contains information about file sources and targets.
API Version: 2023-03-01.
Previous API Version: 2022-07-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Endpoints_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var endpoint = new AzureNative.StorageMover.Endpoint("endpoint", new()
    {
        EndpointName = "examples-endpointName",
        Properties = new AzureNative.StorageMover.Inputs.AzureStorageBlobContainerEndpointPropertiesArgs
        {
            BlobContainerName = "examples-blobContainerName",
            Description = "Example Storage Container Endpoint Description",
            EndpointType = "AzureStorageBlobContainer",
            StorageAccountResourceId = "/subscriptions/11111111-2222-3333-4444-555555555555/resourceGroups/examples-rg/providers/Microsoft.Storage/storageAccounts/examples-storageAccountName/",
        },
        ResourceGroupName = "examples-rg",
        StorageMoverName = "examples-storageMoverName",
    });

});


```

```go
package main

import (
	storagemover "github.com/pulumi/pulumi-azure-native-sdk/storagemover"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := storagemover.NewEndpoint(ctx, "endpoint", &storagemover.EndpointArgs{
			EndpointName: pulumi.String("examples-endpointName"),
			Properties: storagemover.AzureStorageBlobContainerEndpointProperties{
				BlobContainerName:        "examples-blobContainerName",
				Description:              "Example Storage Container Endpoint Description",
				EndpointType:             "AzureStorageBlobContainer",
				StorageAccountResourceId: "/subscriptions/11111111-2222-3333-4444-555555555555/resourceGroups/examples-rg/providers/Microsoft.Storage/storageAccounts/examples-storageAccountName/",
			},
			ResourceGroupName: pulumi.String("examples-rg"),
			StorageMoverName:  pulumi.String("examples-storageMoverName"),
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
import com.pulumi.azurenative.storagemover.Endpoint;
import com.pulumi.azurenative.storagemover.EndpointArgs;
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
        var endpoint = new Endpoint("endpoint", EndpointArgs.builder()        
            .endpointName("examples-endpointName")
            .properties(Map.ofEntries(
                Map.entry("blobContainerName", "examples-blobContainerName"),
                Map.entry("description", "Example Storage Container Endpoint Description"),
                Map.entry("endpointType", "AzureStorageBlobContainer"),
                Map.entry("storageAccountResourceId", "/subscriptions/11111111-2222-3333-4444-555555555555/resourceGroups/examples-rg/providers/Microsoft.Storage/storageAccounts/examples-storageAccountName/")
            ))
            .resourceGroupName("examples-rg")
            .storageMoverName("examples-storageMoverName")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const endpoint = new azure_native.storagemover.Endpoint("endpoint", {
    endpointName: "examples-endpointName",
    properties: {
        blobContainerName: "examples-blobContainerName",
        description: "Example Storage Container Endpoint Description",
        endpointType: "AzureStorageBlobContainer",
        storageAccountResourceId: "/subscriptions/11111111-2222-3333-4444-555555555555/resourceGroups/examples-rg/providers/Microsoft.Storage/storageAccounts/examples-storageAccountName/",
    },
    resourceGroupName: "examples-rg",
    storageMoverName: "examples-storageMoverName",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

endpoint = azure_native.storagemover.Endpoint("endpoint",
    endpoint_name="examples-endpointName",
    properties=azure_native.storagemover.AzureStorageBlobContainerEndpointPropertiesArgs(
        blob_container_name="examples-blobContainerName",
        description="Example Storage Container Endpoint Description",
        endpoint_type="AzureStorageBlobContainer",
        storage_account_resource_id="/subscriptions/11111111-2222-3333-4444-555555555555/resourceGroups/examples-rg/providers/Microsoft.Storage/storageAccounts/examples-storageAccountName/",
    ),
    resource_group_name="examples-rg",
    storage_mover_name="examples-storageMoverName")

```

```yaml
resources:
  endpoint:
    type: azure-native:storagemover:Endpoint
    properties:
      endpointName: examples-endpointName
      properties:
        blobContainerName: examples-blobContainerName
        description: Example Storage Container Endpoint Description
        endpointType: AzureStorageBlobContainer
        storageAccountResourceId: /subscriptions/11111111-2222-3333-4444-555555555555/resourceGroups/examples-rg/providers/Microsoft.Storage/storageAccounts/examples-storageAccountName/
      resourceGroupName: examples-rg
      storageMoverName: examples-storageMoverName

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:storagemover:Endpoint examples-endpointName /subscriptions/11111111-2222-3333-4444-555555555555/resourceGroups/examples-rg/providers/Microsoft.StorageMover/storageMovers/examples-storageMoverName/endpoints/examples-endpointName 
```
