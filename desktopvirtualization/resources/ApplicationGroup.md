Represents a ApplicationGroup definition.
API Version: 2022-09-09.
Previous API Version: 2021-02-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ApplicationGroup_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var applicationGroup = new AzureNative.DesktopVirtualization.ApplicationGroup("applicationGroup", new()
    {
        ApplicationGroupName = "applicationGroup1",
        ApplicationGroupType = "RemoteApp",
        Description = "des1",
        FriendlyName = "friendly",
        HostPoolArmPath = "/subscriptions/daefabc0-95b4-48b3-b645-8a753a63c4fa/resourceGroups/resourceGroup1/providers/Microsoft.DesktopVirtualization/hostPools/hostPool1",
        Location = "centralus",
        ResourceGroupName = "resourceGroup1",
        Tags = 
        {
            { "tag1", "value1" },
            { "tag2", "value2" },
        },
    });

});


```

```go
package main

import (
	desktopvirtualization "github.com/pulumi/pulumi-azure-native-sdk/desktopvirtualization"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := desktopvirtualization.NewApplicationGroup(ctx, "applicationGroup", &desktopvirtualization.ApplicationGroupArgs{
			ApplicationGroupName: pulumi.String("applicationGroup1"),
			ApplicationGroupType: pulumi.String("RemoteApp"),
			Description:          pulumi.String("des1"),
			FriendlyName:         pulumi.String("friendly"),
			HostPoolArmPath:      pulumi.String("/subscriptions/daefabc0-95b4-48b3-b645-8a753a63c4fa/resourceGroups/resourceGroup1/providers/Microsoft.DesktopVirtualization/hostPools/hostPool1"),
			Location:             pulumi.String("centralus"),
			ResourceGroupName:    pulumi.String("resourceGroup1"),
			Tags: pulumi.StringMap{
				"tag1": pulumi.String("value1"),
				"tag2": pulumi.String("value2"),
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
import com.pulumi.azurenative.desktopvirtualization.ApplicationGroup;
import com.pulumi.azurenative.desktopvirtualization.ApplicationGroupArgs;
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
        var applicationGroup = new ApplicationGroup("applicationGroup", ApplicationGroupArgs.builder()        
            .applicationGroupName("applicationGroup1")
            .applicationGroupType("RemoteApp")
            .description("des1")
            .friendlyName("friendly")
            .hostPoolArmPath("/subscriptions/daefabc0-95b4-48b3-b645-8a753a63c4fa/resourceGroups/resourceGroup1/providers/Microsoft.DesktopVirtualization/hostPools/hostPool1")
            .location("centralus")
            .resourceGroupName("resourceGroup1")
            .tags(Map.ofEntries(
                Map.entry("tag1", "value1"),
                Map.entry("tag2", "value2")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const applicationGroup = new azure_native.desktopvirtualization.ApplicationGroup("applicationGroup", {
    applicationGroupName: "applicationGroup1",
    applicationGroupType: "RemoteApp",
    description: "des1",
    friendlyName: "friendly",
    hostPoolArmPath: "/subscriptions/daefabc0-95b4-48b3-b645-8a753a63c4fa/resourceGroups/resourceGroup1/providers/Microsoft.DesktopVirtualization/hostPools/hostPool1",
    location: "centralus",
    resourceGroupName: "resourceGroup1",
    tags: {
        tag1: "value1",
        tag2: "value2",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

application_group = azure_native.desktopvirtualization.ApplicationGroup("applicationGroup",
    application_group_name="applicationGroup1",
    application_group_type="RemoteApp",
    description="des1",
    friendly_name="friendly",
    host_pool_arm_path="/subscriptions/daefabc0-95b4-48b3-b645-8a753a63c4fa/resourceGroups/resourceGroup1/providers/Microsoft.DesktopVirtualization/hostPools/hostPool1",
    location="centralus",
    resource_group_name="resourceGroup1",
    tags={
        "tag1": "value1",
        "tag2": "value2",
    })

```

```yaml
resources:
  applicationGroup:
    type: azure-native:desktopvirtualization:ApplicationGroup
    properties:
      applicationGroupName: applicationGroup1
      applicationGroupType: RemoteApp
      description: des1
      friendlyName: friendly
      hostPoolArmPath: /subscriptions/daefabc0-95b4-48b3-b645-8a753a63c4fa/resourceGroups/resourceGroup1/providers/Microsoft.DesktopVirtualization/hostPools/hostPool1
      location: centralus
      resourceGroupName: resourceGroup1
      tags:
        tag1: value1
        tag2: value2

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:desktopvirtualization:ApplicationGroup applicationGroup1 /subscriptions/daefabc0-95b4-48b3-b645-8a753a63c4fa/resourceGroups/resourceGroup1/providers/Microsoft.DesktopVirtualization/applicationGroups/applicationGroup1 
```
