Capture metrics of Azure resources based on ARM tags.
API Version: 2022-01-01-preview.
Previous API Version: 2022-01-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### MetricsSourceTagRules_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var metricsSourceTagRule = new AzureNative.Logz.MetricsSourceTagRule("metricsSourceTagRule", new()
    {
        MetricsSourceName = "MetricsSource1",
        MonitorName = "myMonitor",
        ResourceGroupName = "myResourceGroup",
        RuleSetName = "default",
    });

});


```

```go
package main

import (
	logz "github.com/pulumi/pulumi-azure-native-sdk/logz"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := logz.NewMetricsSourceTagRule(ctx, "metricsSourceTagRule", &logz.MetricsSourceTagRuleArgs{
			MetricsSourceName: pulumi.String("MetricsSource1"),
			MonitorName:       pulumi.String("myMonitor"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
			RuleSetName:       pulumi.String("default"),
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
import com.pulumi.azurenative.logz.MetricsSourceTagRule;
import com.pulumi.azurenative.logz.MetricsSourceTagRuleArgs;
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
        var metricsSourceTagRule = new MetricsSourceTagRule("metricsSourceTagRule", MetricsSourceTagRuleArgs.builder()        
            .metricsSourceName("MetricsSource1")
            .monitorName("myMonitor")
            .resourceGroupName("myResourceGroup")
            .ruleSetName("default")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const metricsSourceTagRule = new azure_native.logz.MetricsSourceTagRule("metricsSourceTagRule", {
    metricsSourceName: "MetricsSource1",
    monitorName: "myMonitor",
    resourceGroupName: "myResourceGroup",
    ruleSetName: "default",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

metrics_source_tag_rule = azure_native.logz.MetricsSourceTagRule("metricsSourceTagRule",
    metrics_source_name="MetricsSource1",
    monitor_name="myMonitor",
    resource_group_name="myResourceGroup",
    rule_set_name="default")

```

```yaml
resources:
  metricsSourceTagRule:
    type: azure-native:logz:MetricsSourceTagRule
    properties:
      metricsSourceName: MetricsSource1
      monitorName: myMonitor
      resourceGroupName: myResourceGroup
      ruleSetName: default

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:logz:MetricsSourceTagRule default /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Logz/monitors/myMonitor/metricsSource/MetricsSource1/tagRules/default 
```
