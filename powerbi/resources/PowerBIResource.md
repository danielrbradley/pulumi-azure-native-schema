
API Version: 2020-06-01.
Previous API Version: 2020-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Creates or updates private link service resource
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var powerBIResource = new AzureNative.PowerBI.PowerBIResource("powerBIResource", new()
    {
        AzureResourceName = "azureResourceName",
        Location = "global",
        ResourceGroupName = "resourceGroup",
        Tags = 
        {
            { "tag1", "value1" },
            { "tag2", "value2" },
        },
        TenantId = "ac2bc297-8a3e-46f3-972d-87c2b4ae6e2f",
    });

});


```

```go
package main

import (
	powerbi "github.com/pulumi/pulumi-azure-native-sdk/powerbi"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := powerbi.NewPowerBIResource(ctx, "powerBIResource", &powerbi.PowerBIResourceArgs{
			AzureResourceName: pulumi.String("azureResourceName"),
			Location:          pulumi.String("global"),
			ResourceGroupName: pulumi.String("resourceGroup"),
			Tags: pulumi.StringMap{
				"tag1": pulumi.String("value1"),
				"tag2": pulumi.String("value2"),
			},
			TenantId: pulumi.String("ac2bc297-8a3e-46f3-972d-87c2b4ae6e2f"),
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
import com.pulumi.azurenative.powerbi.PowerBIResource;
import com.pulumi.azurenative.powerbi.PowerBIResourceArgs;
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
        var powerBIResource = new PowerBIResource("powerBIResource", PowerBIResourceArgs.builder()        
            .azureResourceName("azureResourceName")
            .location("global")
            .resourceGroupName("resourceGroup")
            .tags(Map.ofEntries(
                Map.entry("tag1", "value1"),
                Map.entry("tag2", "value2")
            ))
            .tenantId("ac2bc297-8a3e-46f3-972d-87c2b4ae6e2f")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const powerBIResource = new azure_native.powerbi.PowerBIResource("powerBIResource", {
    azureResourceName: "azureResourceName",
    location: "global",
    resourceGroupName: "resourceGroup",
    tags: {
        tag1: "value1",
        tag2: "value2",
    },
    tenantId: "ac2bc297-8a3e-46f3-972d-87c2b4ae6e2f",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

power_bi_resource = azure_native.powerbi.PowerBIResource("powerBIResource",
    azure_resource_name="azureResourceName",
    location="global",
    resource_group_name="resourceGroup",
    tags={
        "tag1": "value1",
        "tag2": "value2",
    },
    tenant_id="ac2bc297-8a3e-46f3-972d-87c2b4ae6e2f")

```

```yaml
resources:
  powerBIResource:
    type: azure-native:powerbi:PowerBIResource
    properties:
      azureResourceName: azureResourceName
      location: global
      resourceGroupName: resourceGroup
      tags:
        tag1: value1
        tag2: value2
      tenantId: ac2bc297-8a3e-46f3-972d-87c2b4ae6e2f

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:powerbi:PowerBIResource myPrivateLinkServiceResource /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.PowerBI/privateLinkServicesForPowerBI/{azureResourceName} 
```
