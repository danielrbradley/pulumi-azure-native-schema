The alert rule information
API Version: 2021-04-01.
Previous API Version: 2019-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a Smart Detector alert rule
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var smartDetectorAlertRule = new AzureNative.AlertsManagement.SmartDetectorAlertRule("smartDetectorAlertRule", new()
    {
        ActionGroups = new AzureNative.AlertsManagement.Inputs.ActionGroupsInformationArgs
        {
            CustomEmailSubject = "My custom email subject",
            CustomWebhookPayload = "{\"AlertRuleName\":\"#alertrulename\"}",
            GroupIds = new[]
            {
                "/subscriptions/b368ca2f-e298-46b7-b0ab-012281956afa/resourcegroups/actionGroups/providers/microsoft.insights/actiongroups/MyActionGroup",
            },
        },
        AlertRuleName = "MyAlertRule",
        Description = "Sample smart detector alert rule description",
        Detector = new AzureNative.AlertsManagement.Inputs.DetectorArgs
        {
            Id = "VMMemoryLeak",
        },
        Frequency = "PT5M",
        ResourceGroupName = "MyAlertRules",
        Scope = new[]
        {
            "/subscriptions/b368ca2f-e298-46b7-b0ab-012281956afa/resourceGroups/MyVms/providers/Microsoft.Compute/virtualMachines/vm1",
        },
        Severity = "Sev3",
        State = "Enabled",
        Throttling = new AzureNative.AlertsManagement.Inputs.ThrottlingInformationArgs
        {
            Duration = "PT20M",
        },
    });

});


```

```go
package main

import (
	alertsmanagement "github.com/pulumi/pulumi-azure-native-sdk/alertsmanagement"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := alertsmanagement.NewSmartDetectorAlertRule(ctx, "smartDetectorAlertRule", &alertsmanagement.SmartDetectorAlertRuleArgs{
			ActionGroups: &alertsmanagement.ActionGroupsInformationArgs{
				CustomEmailSubject:   pulumi.String("My custom email subject"),
				CustomWebhookPayload: pulumi.String("{\"AlertRuleName\":\"#alertrulename\"}"),
				GroupIds: pulumi.StringArray{
					pulumi.String("/subscriptions/b368ca2f-e298-46b7-b0ab-012281956afa/resourcegroups/actionGroups/providers/microsoft.insights/actiongroups/MyActionGroup"),
				},
			},
			AlertRuleName: pulumi.String("MyAlertRule"),
			Description:   pulumi.String("Sample smart detector alert rule description"),
			Detector: &alertsmanagement.DetectorArgs{
				Id: pulumi.String("VMMemoryLeak"),
			},
			Frequency:         pulumi.String("PT5M"),
			ResourceGroupName: pulumi.String("MyAlertRules"),
			Scope: pulumi.StringArray{
				pulumi.String("/subscriptions/b368ca2f-e298-46b7-b0ab-012281956afa/resourceGroups/MyVms/providers/Microsoft.Compute/virtualMachines/vm1"),
			},
			Severity: pulumi.String("Sev3"),
			State:    pulumi.String("Enabled"),
			Throttling: &alertsmanagement.ThrottlingInformationArgs{
				Duration: pulumi.String("PT20M"),
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
import com.pulumi.azurenative.alertsmanagement.SmartDetectorAlertRule;
import com.pulumi.azurenative.alertsmanagement.SmartDetectorAlertRuleArgs;
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
        var smartDetectorAlertRule = new SmartDetectorAlertRule("smartDetectorAlertRule", SmartDetectorAlertRuleArgs.builder()        
            .actionGroups(Map.ofEntries(
                Map.entry("customEmailSubject", "My custom email subject"),
                Map.entry("customWebhookPayload", "{\"AlertRuleName\":\"#alertrulename\"}"),
                Map.entry("groupIds", "/subscriptions/b368ca2f-e298-46b7-b0ab-012281956afa/resourcegroups/actionGroups/providers/microsoft.insights/actiongroups/MyActionGroup")
            ))
            .alertRuleName("MyAlertRule")
            .description("Sample smart detector alert rule description")
            .detector(Map.of("id", "VMMemoryLeak"))
            .frequency("PT5M")
            .resourceGroupName("MyAlertRules")
            .scope("/subscriptions/b368ca2f-e298-46b7-b0ab-012281956afa/resourceGroups/MyVms/providers/Microsoft.Compute/virtualMachines/vm1")
            .severity("Sev3")
            .state("Enabled")
            .throttling(Map.of("duration", "PT20M"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const smartDetectorAlertRule = new azure_native.alertsmanagement.SmartDetectorAlertRule("smartDetectorAlertRule", {
    actionGroups: {
        customEmailSubject: "My custom email subject",
        customWebhookPayload: "{\"AlertRuleName\":\"#alertrulename\"}",
        groupIds: ["/subscriptions/b368ca2f-e298-46b7-b0ab-012281956afa/resourcegroups/actionGroups/providers/microsoft.insights/actiongroups/MyActionGroup"],
    },
    alertRuleName: "MyAlertRule",
    description: "Sample smart detector alert rule description",
    detector: {
        id: "VMMemoryLeak",
    },
    frequency: "PT5M",
    resourceGroupName: "MyAlertRules",
    scope: ["/subscriptions/b368ca2f-e298-46b7-b0ab-012281956afa/resourceGroups/MyVms/providers/Microsoft.Compute/virtualMachines/vm1"],
    severity: "Sev3",
    state: "Enabled",
    throttling: {
        duration: "PT20M",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

smart_detector_alert_rule = azure_native.alertsmanagement.SmartDetectorAlertRule("smartDetectorAlertRule",
    action_groups=azure_native.alertsmanagement.ActionGroupsInformationArgs(
        custom_email_subject="My custom email subject",
        custom_webhook_payload="{\"AlertRuleName\":\"#alertrulename\"}",
        group_ids=["/subscriptions/b368ca2f-e298-46b7-b0ab-012281956afa/resourcegroups/actionGroups/providers/microsoft.insights/actiongroups/MyActionGroup"],
    ),
    alert_rule_name="MyAlertRule",
    description="Sample smart detector alert rule description",
    detector=azure_native.alertsmanagement.DetectorArgs(
        id="VMMemoryLeak",
    ),
    frequency="PT5M",
    resource_group_name="MyAlertRules",
    scope=["/subscriptions/b368ca2f-e298-46b7-b0ab-012281956afa/resourceGroups/MyVms/providers/Microsoft.Compute/virtualMachines/vm1"],
    severity="Sev3",
    state="Enabled",
    throttling=azure_native.alertsmanagement.ThrottlingInformationArgs(
        duration="PT20M",
    ))

```

```yaml
resources:
  smartDetectorAlertRule:
    type: azure-native:alertsmanagement:SmartDetectorAlertRule
    properties:
      actionGroups:
        customEmailSubject: My custom email subject
        customWebhookPayload: '{"AlertRuleName":"#alertrulename"}'
        groupIds:
          - /subscriptions/b368ca2f-e298-46b7-b0ab-012281956afa/resourcegroups/actionGroups/providers/microsoft.insights/actiongroups/MyActionGroup
      alertRuleName: MyAlertRule
      description: Sample smart detector alert rule description
      detector:
        id: VMMemoryLeak
      frequency: PT5M
      resourceGroupName: MyAlertRules
      scope:
        - /subscriptions/b368ca2f-e298-46b7-b0ab-012281956afa/resourceGroups/MyVms/providers/Microsoft.Compute/virtualMachines/vm1
      severity: Sev3
      state: Enabled
      throttling:
        duration: PT20M

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:alertsmanagement:SmartDetectorAlertRule MyAlertRule /subscriptions/b368ca2f-e298-46b7-b0ab-012281956afa/resourceGroups/MyAlertRules/providers/microsoft.alertsManagement/smartDetectorAlertRules/MyAlertRule 
```
