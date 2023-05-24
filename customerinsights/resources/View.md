The view resource format.
API Version: 2017-04-26.
Previous API Version: 2017-04-26. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Views_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var view = new AzureNative.CustomerInsights.View("view", new()
    {
        Definition = "{\\\"isProfileType\\\":false,\\\"profileTypes\\\":[],\\\"widgets\\\":[],\\\"style\\\":[]}",
        DisplayName = 
        {
            { "en", "some name" },
        },
        HubName = "sdkTestHub",
        ResourceGroupName = "TestHubRG",
        UserId = "testUser",
        ViewName = "testView",
    });

});


```

```go
package main

import (
	customerinsights "github.com/pulumi/pulumi-azure-native-sdk/customerinsights"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := customerinsights.NewView(ctx, "view", &customerinsights.ViewArgs{
			Definition: pulumi.String("{\\\"isProfileType\\\":false,\\\"profileTypes\\\":[],\\\"widgets\\\":[],\\\"style\\\":[]}"),
			DisplayName: pulumi.StringMap{
				"en": pulumi.String("some name"),
			},
			HubName:           pulumi.String("sdkTestHub"),
			ResourceGroupName: pulumi.String("TestHubRG"),
			UserId:            pulumi.String("testUser"),
			ViewName:          pulumi.String("testView"),
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
import com.pulumi.azurenative.customerinsights.View;
import com.pulumi.azurenative.customerinsights.ViewArgs;
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
        var view = new View("view", ViewArgs.builder()        
            .definition("{\\\"isProfileType\\\":false,\\\"profileTypes\\\":[],\\\"widgets\\\":[],\\\"style\\\":[]}")
            .displayName(Map.of("en", "some name"))
            .hubName("sdkTestHub")
            .resourceGroupName("TestHubRG")
            .userId("testUser")
            .viewName("testView")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const view = new azure_native.customerinsights.View("view", {
    definition: "{\\\"isProfileType\\\":false,\\\"profileTypes\\\":[],\\\"widgets\\\":[],\\\"style\\\":[]}",
    displayName: {
        en: "some name",
    },
    hubName: "sdkTestHub",
    resourceGroupName: "TestHubRG",
    userId: "testUser",
    viewName: "testView",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

view = azure_native.customerinsights.View("view",
    definition="{\\\"isProfileType\\\":false,\\\"profileTypes\\\":[],\\\"widgets\\\":[],\\\"style\\\":[]}",
    display_name={
        "en": "some name",
    },
    hub_name="sdkTestHub",
    resource_group_name="TestHubRG",
    user_id="testUser",
    view_name="testView")

```

```yaml
resources:
  view:
    type: azure-native:customerinsights:View
    properties:
      definition: '{\"isProfileType\":false,\"profileTypes\":[],\"widgets\":[],\"style\":[]}'
      displayName:
        en: some name
      hubName: sdkTestHub
      resourceGroupName: TestHubRG
      userId: testUser
      viewName: testView

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:customerinsights:View sdkTestHub/testView /subscriptions/c909e979-ef71-4def-a970-bc7c154db8c5/resourceGroups/TestHubRG/providers/Microsoft.CustomerInsights/hubs/sdkTestHub/views/testView 
```
