Describes a Shared Private Link Resource managed by the Azure Cognitive Search service.
API Version: 2022-09-01.
Previous API Version: 2020-08-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### SharedPrivateLinkResourceCreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sharedPrivateLinkResource = new AzureNative.Search.SharedPrivateLinkResource("sharedPrivateLinkResource", new()
    {
        Properties = new AzureNative.Search.Inputs.SharedPrivateLinkResourcePropertiesArgs
        {
            GroupId = "blob",
            PrivateLinkResourceId = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Storage/storageAccounts/storageAccountName",
            RequestMessage = "please approve",
        },
        ResourceGroupName = "rg1",
        SearchServiceName = "mysearchservice",
        SharedPrivateLinkResourceName = "testResource",
    });

});


```

```go
package main

import (
	search "github.com/pulumi/pulumi-azure-native-sdk/search"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := search.NewSharedPrivateLinkResource(ctx, "sharedPrivateLinkResource", &search.SharedPrivateLinkResourceArgs{
			Properties: &search.SharedPrivateLinkResourcePropertiesArgs{
				GroupId:               pulumi.String("blob"),
				PrivateLinkResourceId: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Storage/storageAccounts/storageAccountName"),
				RequestMessage:        pulumi.String("please approve"),
			},
			ResourceGroupName:             pulumi.String("rg1"),
			SearchServiceName:             pulumi.String("mysearchservice"),
			SharedPrivateLinkResourceName: pulumi.String("testResource"),
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
import com.pulumi.azurenative.search.SharedPrivateLinkResource;
import com.pulumi.azurenative.search.SharedPrivateLinkResourceArgs;
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
        var sharedPrivateLinkResource = new SharedPrivateLinkResource("sharedPrivateLinkResource", SharedPrivateLinkResourceArgs.builder()        
            .properties(Map.ofEntries(
                Map.entry("groupId", "blob"),
                Map.entry("privateLinkResourceId", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Storage/storageAccounts/storageAccountName"),
                Map.entry("requestMessage", "please approve")
            ))
            .resourceGroupName("rg1")
            .searchServiceName("mysearchservice")
            .sharedPrivateLinkResourceName("testResource")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sharedPrivateLinkResource = new azure_native.search.SharedPrivateLinkResource("sharedPrivateLinkResource", {
    properties: {
        groupId: "blob",
        privateLinkResourceId: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Storage/storageAccounts/storageAccountName",
        requestMessage: "please approve",
    },
    resourceGroupName: "rg1",
    searchServiceName: "mysearchservice",
    sharedPrivateLinkResourceName: "testResource",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

shared_private_link_resource = azure_native.search.SharedPrivateLinkResource("sharedPrivateLinkResource",
    properties=azure_native.search.SharedPrivateLinkResourcePropertiesArgs(
        group_id="blob",
        private_link_resource_id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Storage/storageAccounts/storageAccountName",
        request_message="please approve",
    ),
    resource_group_name="rg1",
    search_service_name="mysearchservice",
    shared_private_link_resource_name="testResource")

```

```yaml
resources:
  sharedPrivateLinkResource:
    type: azure-native:search:SharedPrivateLinkResource
    properties:
      properties:
        groupId: blob
        privateLinkResourceId: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Storage/storageAccounts/storageAccountName
        requestMessage: please approve
      resourceGroupName: rg1
      searchServiceName: mysearchservice
      sharedPrivateLinkResourceName: testResource

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:search:SharedPrivateLinkResource testResource /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Search/searchServices/mysearchservice/sharedPrivateLinkResources/testResource 
```
