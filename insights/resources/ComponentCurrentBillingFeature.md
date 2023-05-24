An Application Insights component billing features
API Version: 2015-05-01.
Previous API Version: 2015-05-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ComponentCurrentBillingFeaturesUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var componentCurrentBillingFeature = new AzureNative.Insights.ComponentCurrentBillingFeature("componentCurrentBillingFeature", new()
    {
        CurrentBillingFeatures = new[]
        {
            "Basic",
            "Application Insights Enterprise",
        },
        DataVolumeCap = new AzureNative.Insights.Inputs.ApplicationInsightsComponentDataVolumeCapArgs
        {
            Cap = 100,
            StopSendNotificationWhenHitCap = true,
        },
        ResourceGroupName = "my-resource-group",
        ResourceName = "my-component",
    });

});


```

```go
package main

import (
	insights "github.com/pulumi/pulumi-azure-native-sdk/insights"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := insights.NewComponentCurrentBillingFeature(ctx, "componentCurrentBillingFeature", &insights.ComponentCurrentBillingFeatureArgs{
			CurrentBillingFeatures: pulumi.StringArray{
				pulumi.String("Basic"),
				pulumi.String("Application Insights Enterprise"),
			},
			DataVolumeCap: &insights.ApplicationInsightsComponentDataVolumeCapArgs{
				Cap:                            pulumi.Float64(100),
				StopSendNotificationWhenHitCap: pulumi.Bool(true),
			},
			ResourceGroupName: pulumi.String("my-resource-group"),
			ResourceName:      pulumi.String("my-component"),
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
import com.pulumi.azurenative.insights.ComponentCurrentBillingFeature;
import com.pulumi.azurenative.insights.ComponentCurrentBillingFeatureArgs;
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
        var componentCurrentBillingFeature = new ComponentCurrentBillingFeature("componentCurrentBillingFeature", ComponentCurrentBillingFeatureArgs.builder()        
            .currentBillingFeatures(            
                "Basic",
                "Application Insights Enterprise")
            .dataVolumeCap(Map.ofEntries(
                Map.entry("cap", 100),
                Map.entry("stopSendNotificationWhenHitCap", true)
            ))
            .resourceGroupName("my-resource-group")
            .resourceName("my-component")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const componentCurrentBillingFeature = new azure_native.insights.ComponentCurrentBillingFeature("componentCurrentBillingFeature", {
    currentBillingFeatures: [
        "Basic",
        "Application Insights Enterprise",
    ],
    dataVolumeCap: {
        cap: 100,
        stopSendNotificationWhenHitCap: true,
    },
    resourceGroupName: "my-resource-group",
    resourceName: "my-component",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

component_current_billing_feature = azure_native.insights.ComponentCurrentBillingFeature("componentCurrentBillingFeature",
    current_billing_features=[
        "Basic",
        "Application Insights Enterprise",
    ],
    data_volume_cap=azure_native.insights.ApplicationInsightsComponentDataVolumeCapArgs(
        cap=100,
        stop_send_notification_when_hit_cap=True,
    ),
    resource_group_name="my-resource-group",
    resource_name_="my-component")

```

```yaml
resources:
  componentCurrentBillingFeature:
    type: azure-native:insights:ComponentCurrentBillingFeature
    properties:
      currentBillingFeatures:
        - Basic
        - Application Insights Enterprise
      dataVolumeCap:
        cap: 100
        stopSendNotificationWhenHitCap: true
      resourceGroupName: my-resource-group
      resourceName: my-component

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:insights:ComponentCurrentBillingFeature myresource1 /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Insights/components/{resourceName}/currentbillingfeatures 
```
