Alert processing rule object containing target scopes, conditions and scheduling logic.
API Version: 2021-08-08.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a rule that adds an action group to all alerts in a subscription
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var alertProcessingRuleByName = new AzureNative.AlertsManagement.AlertProcessingRuleByName("alertProcessingRuleByName", new()
    {
        AlertProcessingRuleName = "AddActionGroupToSubscription",
        Location = "Global",
        Properties = new AzureNative.AlertsManagement.Inputs.AlertProcessingRulePropertiesArgs
        {
            Actions = new[]
            {
                new AzureNative.AlertsManagement.Inputs.AddActionGroupsArgs
                {
                    ActionGroupIds = new[]
                    {
                        "/subscriptions/subId1/resourcegroups/RGId1/providers/microsoft.insights/actiongroups/ActionGroup1",
                    },
                    ActionType = "AddActionGroups",
                },
            },
            Description = "Add ActionGroup1 to all alerts in the subscription",
            Enabled = true,
            Scopes = new[]
            {
                "/subscriptions/subId1",
            },
        },
        ResourceGroupName = "alertscorrelationrg",
        Tags = null,
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
		_, err := alertsmanagement.NewAlertProcessingRuleByName(ctx, "alertProcessingRuleByName", &alertsmanagement.AlertProcessingRuleByNameArgs{
			AlertProcessingRuleName: pulumi.String("AddActionGroupToSubscription"),
			Location:                pulumi.String("Global"),
			Properties: alertsmanagement.AlertProcessingRulePropertiesResponse{
				Actions: pulumi.AnyArray{
					alertsmanagement.AddActionGroups{
						ActionGroupIds: []string{
							"/subscriptions/subId1/resourcegroups/RGId1/providers/microsoft.insights/actiongroups/ActionGroup1",
						},
						ActionType: "AddActionGroups",
					},
				},
				Description: pulumi.String("Add ActionGroup1 to all alerts in the subscription"),
				Enabled:     pulumi.Bool(true),
				Scopes: pulumi.StringArray{
					pulumi.String("/subscriptions/subId1"),
				},
			},
			ResourceGroupName: pulumi.String("alertscorrelationrg"),
			Tags:              nil,
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
import com.pulumi.azurenative.alertsmanagement.AlertProcessingRuleByName;
import com.pulumi.azurenative.alertsmanagement.AlertProcessingRuleByNameArgs;
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
        var alertProcessingRuleByName = new AlertProcessingRuleByName("alertProcessingRuleByName", AlertProcessingRuleByNameArgs.builder()        
            .alertProcessingRuleName("AddActionGroupToSubscription")
            .location("Global")
            .properties(Map.ofEntries(
                Map.entry("actions", Map.ofEntries(
                    Map.entry("actionGroupIds", "/subscriptions/subId1/resourcegroups/RGId1/providers/microsoft.insights/actiongroups/ActionGroup1"),
                    Map.entry("actionType", "AddActionGroups")
                )),
                Map.entry("description", "Add ActionGroup1 to all alerts in the subscription"),
                Map.entry("enabled", true),
                Map.entry("scopes", "/subscriptions/subId1")
            ))
            .resourceGroupName("alertscorrelationrg")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const alertProcessingRuleByName = new azure_native.alertsmanagement.AlertProcessingRuleByName("alertProcessingRuleByName", {
    alertProcessingRuleName: "AddActionGroupToSubscription",
    location: "Global",
    properties: {
        actions: [{
            actionGroupIds: ["/subscriptions/subId1/resourcegroups/RGId1/providers/microsoft.insights/actiongroups/ActionGroup1"],
            actionType: "AddActionGroups",
        }],
        description: "Add ActionGroup1 to all alerts in the subscription",
        enabled: true,
        scopes: ["/subscriptions/subId1"],
    },
    resourceGroupName: "alertscorrelationrg",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

alert_processing_rule_by_name = azure_native.alertsmanagement.AlertProcessingRuleByName("alertProcessingRuleByName",
    alert_processing_rule_name="AddActionGroupToSubscription",
    location="Global",
    properties=azure_native.alertsmanagement.AlertProcessingRulePropertiesResponseArgs(
        actions=[azure_native.alertsmanagement.AddActionGroupsArgs(
            action_group_ids=["/subscriptions/subId1/resourcegroups/RGId1/providers/microsoft.insights/actiongroups/ActionGroup1"],
            action_type="AddActionGroups",
        )],
        description="Add ActionGroup1 to all alerts in the subscription",
        enabled=True,
        scopes=["/subscriptions/subId1"],
    ),
    resource_group_name="alertscorrelationrg",
    tags={})

```

```yaml
resources:
  alertProcessingRuleByName:
    type: azure-native:alertsmanagement:AlertProcessingRuleByName
    properties:
      alertProcessingRuleName: AddActionGroupToSubscription
      location: Global
      properties:
        actions:
          - actionGroupIds:
              - /subscriptions/subId1/resourcegroups/RGId1/providers/microsoft.insights/actiongroups/ActionGroup1
            actionType: AddActionGroups
        description: Add ActionGroup1 to all alerts in the subscription
        enabled: true
        scopes:
          - /subscriptions/subId1
      resourceGroupName: alertscorrelationrg
      tags: {}

```

{{% /example %}}
{{% example %}}
### Create or update a rule that adds two action groups to all Sev0 and Sev1 alerts in two resource groups
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var alertProcessingRuleByName = new AzureNative.AlertsManagement.AlertProcessingRuleByName("alertProcessingRuleByName", new()
    {
        AlertProcessingRuleName = "AddActionGroupsBySeverity",
        Location = "Global",
        Properties = new AzureNative.AlertsManagement.Inputs.AlertProcessingRulePropertiesArgs
        {
            Actions = new[]
            {
                new AzureNative.AlertsManagement.Inputs.AddActionGroupsArgs
                {
                    ActionGroupIds = new[]
                    {
                        "/subscriptions/subId1/resourcegroups/RGId1/providers/microsoft.insights/actiongroups/AGId1",
                        "/subscriptions/subId1/resourcegroups/RGId1/providers/microsoft.insights/actiongroups/AGId2",
                    },
                    ActionType = "AddActionGroups",
                },
            },
            Conditions = new[]
            {
                new AzureNative.AlertsManagement.Inputs.ConditionArgs
                {
                    Field = "Severity",
                    Operator = "Equals",
                    Values = new[]
                    {
                        "sev0",
                        "sev1",
                    },
                },
            },
            Description = "Add AGId1 and AGId2 to all Sev0 and Sev1 alerts in these resourceGroups",
            Enabled = true,
            Scopes = new[]
            {
                "/subscriptions/subId1/resourceGroups/RGId1",
                "/subscriptions/subId1/resourceGroups/RGId2",
            },
        },
        ResourceGroupName = "alertscorrelationrg",
        Tags = null,
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
		_, err := alertsmanagement.NewAlertProcessingRuleByName(ctx, "alertProcessingRuleByName", &alertsmanagement.AlertProcessingRuleByNameArgs{
			AlertProcessingRuleName: pulumi.String("AddActionGroupsBySeverity"),
			Location:                pulumi.String("Global"),
			Properties: alertsmanagement.AlertProcessingRulePropertiesResponse{
				Actions: pulumi.AnyArray{
					alertsmanagement.AddActionGroups{
						ActionGroupIds: []string{
							"/subscriptions/subId1/resourcegroups/RGId1/providers/microsoft.insights/actiongroups/AGId1",
							"/subscriptions/subId1/resourcegroups/RGId1/providers/microsoft.insights/actiongroups/AGId2",
						},
						ActionType: "AddActionGroups",
					},
				},
				Conditions: alertsmanagement.ConditionArray{
					&alertsmanagement.ConditionArgs{
						Field:    pulumi.String("Severity"),
						Operator: pulumi.String("Equals"),
						Values: pulumi.StringArray{
							pulumi.String("sev0"),
							pulumi.String("sev1"),
						},
					},
				},
				Description: pulumi.String("Add AGId1 and AGId2 to all Sev0 and Sev1 alerts in these resourceGroups"),
				Enabled:     pulumi.Bool(true),
				Scopes: pulumi.StringArray{
					pulumi.String("/subscriptions/subId1/resourceGroups/RGId1"),
					pulumi.String("/subscriptions/subId1/resourceGroups/RGId2"),
				},
			},
			ResourceGroupName: pulumi.String("alertscorrelationrg"),
			Tags:              nil,
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
import com.pulumi.azurenative.alertsmanagement.AlertProcessingRuleByName;
import com.pulumi.azurenative.alertsmanagement.AlertProcessingRuleByNameArgs;
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
        var alertProcessingRuleByName = new AlertProcessingRuleByName("alertProcessingRuleByName", AlertProcessingRuleByNameArgs.builder()        
            .alertProcessingRuleName("AddActionGroupsBySeverity")
            .location("Global")
            .properties(Map.ofEntries(
                Map.entry("actions", Map.ofEntries(
                    Map.entry("actionGroupIds",                     
                        "/subscriptions/subId1/resourcegroups/RGId1/providers/microsoft.insights/actiongroups/AGId1",
                        "/subscriptions/subId1/resourcegroups/RGId1/providers/microsoft.insights/actiongroups/AGId2"),
                    Map.entry("actionType", "AddActionGroups")
                )),
                Map.entry("conditions", Map.ofEntries(
                    Map.entry("field", "Severity"),
                    Map.entry("operator", "Equals"),
                    Map.entry("values",                     
                        "sev0",
                        "sev1")
                )),
                Map.entry("description", "Add AGId1 and AGId2 to all Sev0 and Sev1 alerts in these resourceGroups"),
                Map.entry("enabled", true),
                Map.entry("scopes",                 
                    "/subscriptions/subId1/resourceGroups/RGId1",
                    "/subscriptions/subId1/resourceGroups/RGId2")
            ))
            .resourceGroupName("alertscorrelationrg")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const alertProcessingRuleByName = new azure_native.alertsmanagement.AlertProcessingRuleByName("alertProcessingRuleByName", {
    alertProcessingRuleName: "AddActionGroupsBySeverity",
    location: "Global",
    properties: {
        actions: [{
            actionGroupIds: [
                "/subscriptions/subId1/resourcegroups/RGId1/providers/microsoft.insights/actiongroups/AGId1",
                "/subscriptions/subId1/resourcegroups/RGId1/providers/microsoft.insights/actiongroups/AGId2",
            ],
            actionType: "AddActionGroups",
        }],
        conditions: [{
            field: "Severity",
            operator: "Equals",
            values: [
                "sev0",
                "sev1",
            ],
        }],
        description: "Add AGId1 and AGId2 to all Sev0 and Sev1 alerts in these resourceGroups",
        enabled: true,
        scopes: [
            "/subscriptions/subId1/resourceGroups/RGId1",
            "/subscriptions/subId1/resourceGroups/RGId2",
        ],
    },
    resourceGroupName: "alertscorrelationrg",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

alert_processing_rule_by_name = azure_native.alertsmanagement.AlertProcessingRuleByName("alertProcessingRuleByName",
    alert_processing_rule_name="AddActionGroupsBySeverity",
    location="Global",
    properties=azure_native.alertsmanagement.AlertProcessingRulePropertiesResponseArgs(
        actions=[azure_native.alertsmanagement.AddActionGroupsArgs(
            action_group_ids=[
                "/subscriptions/subId1/resourcegroups/RGId1/providers/microsoft.insights/actiongroups/AGId1",
                "/subscriptions/subId1/resourcegroups/RGId1/providers/microsoft.insights/actiongroups/AGId2",
            ],
            action_type="AddActionGroups",
        )],
        conditions=[azure_native.alertsmanagement.ConditionArgs(
            field="Severity",
            operator="Equals",
            values=[
                "sev0",
                "sev1",
            ],
        )],
        description="Add AGId1 and AGId2 to all Sev0 and Sev1 alerts in these resourceGroups",
        enabled=True,
        scopes=[
            "/subscriptions/subId1/resourceGroups/RGId1",
            "/subscriptions/subId1/resourceGroups/RGId2",
        ],
    ),
    resource_group_name="alertscorrelationrg",
    tags={})

```

```yaml
resources:
  alertProcessingRuleByName:
    type: azure-native:alertsmanagement:AlertProcessingRuleByName
    properties:
      alertProcessingRuleName: AddActionGroupsBySeverity
      location: Global
      properties:
        actions:
          - actionGroupIds:
              - /subscriptions/subId1/resourcegroups/RGId1/providers/microsoft.insights/actiongroups/AGId1
              - /subscriptions/subId1/resourcegroups/RGId1/providers/microsoft.insights/actiongroups/AGId2
            actionType: AddActionGroups
        conditions:
          - field: Severity
            operator: Equals
            values:
              - sev0
              - sev1
        description: Add AGId1 and AGId2 to all Sev0 and Sev1 alerts in these resourceGroups
        enabled: true
        scopes:
          - /subscriptions/subId1/resourceGroups/RGId1
          - /subscriptions/subId1/resourceGroups/RGId2
      resourceGroupName: alertscorrelationrg
      tags: {}

```

{{% /example %}}
{{% example %}}
### Create or update a rule that removes all action groups from alerts on a specific VM during a one-off maintenance window (1800-2000 at a specific date, Pacific Standard Time)
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var alertProcessingRuleByName = new AzureNative.AlertsManagement.AlertProcessingRuleByName("alertProcessingRuleByName", new()
    {
        AlertProcessingRuleName = "RemoveActionGroupsMaintenanceWindow",
        Location = "Global",
        Properties = new AzureNative.AlertsManagement.Inputs.AlertProcessingRulePropertiesArgs
        {
            Actions = new[]
            {
                new AzureNative.AlertsManagement.Inputs.RemoveAllActionGroupsArgs
                {
                    ActionType = "RemoveAllActionGroups",
                },
            },
            Description = "Removes all ActionGroups from all Alerts on VMName during the maintenance window",
            Enabled = true,
            Schedule = new AzureNative.AlertsManagement.Inputs.ScheduleArgs
            {
                EffectiveFrom = "2021-04-15T18:00:00",
                EffectiveUntil = "2021-04-15T20:00:00",
                TimeZone = "Pacific Standard Time",
            },
            Scopes = new[]
            {
                "/subscriptions/subId1/resourceGroups/RGId1/providers/Microsoft.Compute/virtualMachines/VMName",
            },
        },
        ResourceGroupName = "alertscorrelationrg",
        Tags = null,
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
		_, err := alertsmanagement.NewAlertProcessingRuleByName(ctx, "alertProcessingRuleByName", &alertsmanagement.AlertProcessingRuleByNameArgs{
			AlertProcessingRuleName: pulumi.String("RemoveActionGroupsMaintenanceWindow"),
			Location:                pulumi.String("Global"),
			Properties: alertsmanagement.AlertProcessingRulePropertiesResponse{
				Actions: pulumi.AnyArray{
					alertsmanagement.RemoveAllActionGroups{
						ActionType: "RemoveAllActionGroups",
					},
				},
				Description: pulumi.String("Removes all ActionGroups from all Alerts on VMName during the maintenance window"),
				Enabled:     pulumi.Bool(true),
				Schedule: &alertsmanagement.ScheduleArgs{
					EffectiveFrom:  pulumi.String("2021-04-15T18:00:00"),
					EffectiveUntil: pulumi.String("2021-04-15T20:00:00"),
					TimeZone:       pulumi.String("Pacific Standard Time"),
				},
				Scopes: pulumi.StringArray{
					pulumi.String("/subscriptions/subId1/resourceGroups/RGId1/providers/Microsoft.Compute/virtualMachines/VMName"),
				},
			},
			ResourceGroupName: pulumi.String("alertscorrelationrg"),
			Tags:              nil,
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
import com.pulumi.azurenative.alertsmanagement.AlertProcessingRuleByName;
import com.pulumi.azurenative.alertsmanagement.AlertProcessingRuleByNameArgs;
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
        var alertProcessingRuleByName = new AlertProcessingRuleByName("alertProcessingRuleByName", AlertProcessingRuleByNameArgs.builder()        
            .alertProcessingRuleName("RemoveActionGroupsMaintenanceWindow")
            .location("Global")
            .properties(Map.ofEntries(
                Map.entry("actions", Map.of("actionType", "RemoveAllActionGroups")),
                Map.entry("description", "Removes all ActionGroups from all Alerts on VMName during the maintenance window"),
                Map.entry("enabled", true),
                Map.entry("schedule", Map.ofEntries(
                    Map.entry("effectiveFrom", "2021-04-15T18:00:00"),
                    Map.entry("effectiveUntil", "2021-04-15T20:00:00"),
                    Map.entry("timeZone", "Pacific Standard Time")
                )),
                Map.entry("scopes", "/subscriptions/subId1/resourceGroups/RGId1/providers/Microsoft.Compute/virtualMachines/VMName")
            ))
            .resourceGroupName("alertscorrelationrg")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const alertProcessingRuleByName = new azure_native.alertsmanagement.AlertProcessingRuleByName("alertProcessingRuleByName", {
    alertProcessingRuleName: "RemoveActionGroupsMaintenanceWindow",
    location: "Global",
    properties: {
        actions: [{
            actionType: "RemoveAllActionGroups",
        }],
        description: "Removes all ActionGroups from all Alerts on VMName during the maintenance window",
        enabled: true,
        schedule: {
            effectiveFrom: "2021-04-15T18:00:00",
            effectiveUntil: "2021-04-15T20:00:00",
            timeZone: "Pacific Standard Time",
        },
        scopes: ["/subscriptions/subId1/resourceGroups/RGId1/providers/Microsoft.Compute/virtualMachines/VMName"],
    },
    resourceGroupName: "alertscorrelationrg",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

alert_processing_rule_by_name = azure_native.alertsmanagement.AlertProcessingRuleByName("alertProcessingRuleByName",
    alert_processing_rule_name="RemoveActionGroupsMaintenanceWindow",
    location="Global",
    properties=azure_native.alertsmanagement.AlertProcessingRulePropertiesResponseArgs(
        actions=[azure_native.alertsmanagement.RemoveAllActionGroupsArgs(
            action_type="RemoveAllActionGroups",
        )],
        description="Removes all ActionGroups from all Alerts on VMName during the maintenance window",
        enabled=True,
        schedule=azure_native.alertsmanagement.ScheduleArgs(
            effective_from="2021-04-15T18:00:00",
            effective_until="2021-04-15T20:00:00",
            time_zone="Pacific Standard Time",
        ),
        scopes=["/subscriptions/subId1/resourceGroups/RGId1/providers/Microsoft.Compute/virtualMachines/VMName"],
    ),
    resource_group_name="alertscorrelationrg",
    tags={})

```

```yaml
resources:
  alertProcessingRuleByName:
    type: azure-native:alertsmanagement:AlertProcessingRuleByName
    properties:
      alertProcessingRuleName: RemoveActionGroupsMaintenanceWindow
      location: Global
      properties:
        actions:
          - actionType: RemoveAllActionGroups
        description: Removes all ActionGroups from all Alerts on VMName during the maintenance window
        enabled: true
        schedule:
          effectiveFrom: 2021-04-15T18:00:00
          effectiveUntil: 2021-04-15T20:00:00
          timeZone: Pacific Standard Time
        scopes:
          - /subscriptions/subId1/resourceGroups/RGId1/providers/Microsoft.Compute/virtualMachines/VMName
      resourceGroupName: alertscorrelationrg
      tags: {}

```

{{% /example %}}
{{% example %}}
### Create or update a rule that removes all action groups from all alerts in a subscription coming from a specific alert rule
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var alertProcessingRuleByName = new AzureNative.AlertsManagement.AlertProcessingRuleByName("alertProcessingRuleByName", new()
    {
        AlertProcessingRuleName = "RemoveActionGroupsSpecificAlertRule",
        Location = "Global",
        Properties = new AzureNative.AlertsManagement.Inputs.AlertProcessingRulePropertiesArgs
        {
            Actions = new[]
            {
                new AzureNative.AlertsManagement.Inputs.RemoveAllActionGroupsArgs
                {
                    ActionType = "RemoveAllActionGroups",
                },
            },
            Conditions = new[]
            {
                new AzureNative.AlertsManagement.Inputs.ConditionArgs
                {
                    Field = "AlertRuleId",
                    Operator = "Equals",
                    Values = new[]
                    {
                        "/subscriptions/suubId1/resourceGroups/Rgid2/providers/microsoft.insights/activityLogAlerts/RuleName",
                    },
                },
            },
            Description = "Removes all ActionGroups from all Alerts that fire on above AlertRule",
            Enabled = true,
            Scopes = new[]
            {
                "/subscriptions/subId1",
            },
        },
        ResourceGroupName = "alertscorrelationrg",
        Tags = null,
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
		_, err := alertsmanagement.NewAlertProcessingRuleByName(ctx, "alertProcessingRuleByName", &alertsmanagement.AlertProcessingRuleByNameArgs{
			AlertProcessingRuleName: pulumi.String("RemoveActionGroupsSpecificAlertRule"),
			Location:                pulumi.String("Global"),
			Properties: alertsmanagement.AlertProcessingRulePropertiesResponse{
				Actions: pulumi.AnyArray{
					alertsmanagement.RemoveAllActionGroups{
						ActionType: "RemoveAllActionGroups",
					},
				},
				Conditions: alertsmanagement.ConditionArray{
					&alertsmanagement.ConditionArgs{
						Field:    pulumi.String("AlertRuleId"),
						Operator: pulumi.String("Equals"),
						Values: pulumi.StringArray{
							pulumi.String("/subscriptions/suubId1/resourceGroups/Rgid2/providers/microsoft.insights/activityLogAlerts/RuleName"),
						},
					},
				},
				Description: pulumi.String("Removes all ActionGroups from all Alerts that fire on above AlertRule"),
				Enabled:     pulumi.Bool(true),
				Scopes: pulumi.StringArray{
					pulumi.String("/subscriptions/subId1"),
				},
			},
			ResourceGroupName: pulumi.String("alertscorrelationrg"),
			Tags:              nil,
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
import com.pulumi.azurenative.alertsmanagement.AlertProcessingRuleByName;
import com.pulumi.azurenative.alertsmanagement.AlertProcessingRuleByNameArgs;
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
        var alertProcessingRuleByName = new AlertProcessingRuleByName("alertProcessingRuleByName", AlertProcessingRuleByNameArgs.builder()        
            .alertProcessingRuleName("RemoveActionGroupsSpecificAlertRule")
            .location("Global")
            .properties(Map.ofEntries(
                Map.entry("actions", Map.of("actionType", "RemoveAllActionGroups")),
                Map.entry("conditions", Map.ofEntries(
                    Map.entry("field", "AlertRuleId"),
                    Map.entry("operator", "Equals"),
                    Map.entry("values", "/subscriptions/suubId1/resourceGroups/Rgid2/providers/microsoft.insights/activityLogAlerts/RuleName")
                )),
                Map.entry("description", "Removes all ActionGroups from all Alerts that fire on above AlertRule"),
                Map.entry("enabled", true),
                Map.entry("scopes", "/subscriptions/subId1")
            ))
            .resourceGroupName("alertscorrelationrg")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const alertProcessingRuleByName = new azure_native.alertsmanagement.AlertProcessingRuleByName("alertProcessingRuleByName", {
    alertProcessingRuleName: "RemoveActionGroupsSpecificAlertRule",
    location: "Global",
    properties: {
        actions: [{
            actionType: "RemoveAllActionGroups",
        }],
        conditions: [{
            field: "AlertRuleId",
            operator: "Equals",
            values: ["/subscriptions/suubId1/resourceGroups/Rgid2/providers/microsoft.insights/activityLogAlerts/RuleName"],
        }],
        description: "Removes all ActionGroups from all Alerts that fire on above AlertRule",
        enabled: true,
        scopes: ["/subscriptions/subId1"],
    },
    resourceGroupName: "alertscorrelationrg",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

alert_processing_rule_by_name = azure_native.alertsmanagement.AlertProcessingRuleByName("alertProcessingRuleByName",
    alert_processing_rule_name="RemoveActionGroupsSpecificAlertRule",
    location="Global",
    properties=azure_native.alertsmanagement.AlertProcessingRulePropertiesResponseArgs(
        actions=[azure_native.alertsmanagement.RemoveAllActionGroupsArgs(
            action_type="RemoveAllActionGroups",
        )],
        conditions=[azure_native.alertsmanagement.ConditionArgs(
            field="AlertRuleId",
            operator="Equals",
            values=["/subscriptions/suubId1/resourceGroups/Rgid2/providers/microsoft.insights/activityLogAlerts/RuleName"],
        )],
        description="Removes all ActionGroups from all Alerts that fire on above AlertRule",
        enabled=True,
        scopes=["/subscriptions/subId1"],
    ),
    resource_group_name="alertscorrelationrg",
    tags={})

```

```yaml
resources:
  alertProcessingRuleByName:
    type: azure-native:alertsmanagement:AlertProcessingRuleByName
    properties:
      alertProcessingRuleName: RemoveActionGroupsSpecificAlertRule
      location: Global
      properties:
        actions:
          - actionType: RemoveAllActionGroups
        conditions:
          - field: AlertRuleId
            operator: Equals
            values:
              - /subscriptions/suubId1/resourceGroups/Rgid2/providers/microsoft.insights/activityLogAlerts/RuleName
        description: Removes all ActionGroups from all Alerts that fire on above AlertRule
        enabled: true
        scopes:
          - /subscriptions/subId1
      resourceGroupName: alertscorrelationrg
      tags: {}

```

{{% /example %}}
{{% example %}}
### Create or update a rule that removes all action groups from all alerts on any VM in two resource groups during a recurring maintenance window (2200-0400 every Sat and Sun, India Standard Time)
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var alertProcessingRuleByName = new AzureNative.AlertsManagement.AlertProcessingRuleByName("alertProcessingRuleByName", new()
    {
        AlertProcessingRuleName = "RemoveActionGroupsRecurringMaintenance",
        Location = "Global",
        Properties = new AzureNative.AlertsManagement.Inputs.AlertProcessingRulePropertiesArgs
        {
            Actions = new[]
            {
                new AzureNative.AlertsManagement.Inputs.RemoveAllActionGroupsArgs
                {
                    ActionType = "RemoveAllActionGroups",
                },
            },
            Conditions = new[]
            {
                new AzureNative.AlertsManagement.Inputs.ConditionArgs
                {
                    Field = "TargetResourceType",
                    Operator = "Equals",
                    Values = new[]
                    {
                        "microsoft.compute/virtualmachines",
                    },
                },
            },
            Description = "Remove all ActionGroups from all Vitual machine Alerts during the recurring maintenance",
            Enabled = true,
            Schedule = new AzureNative.AlertsManagement.Inputs.ScheduleArgs
            {
                Recurrences = new[]
                {
                    new AzureNative.AlertsManagement.Inputs.WeeklyRecurrenceArgs
                    {
                        DaysOfWeek = new[]
                        {
                            "Saturday",
                            "Sunday",
                        },
                        EndTime = "04:00:00",
                        RecurrenceType = "Weekly",
                        StartTime = "22:00:00",
                    },
                },
                TimeZone = "India Standard Time",
            },
            Scopes = new[]
            {
                "/subscriptions/subId1/resourceGroups/RGId1",
                "/subscriptions/subId1/resourceGroups/RGId2",
            },
        },
        ResourceGroupName = "alertscorrelationrg",
        Tags = null,
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.alertsmanagement.AlertProcessingRuleByName;
import com.pulumi.azurenative.alertsmanagement.AlertProcessingRuleByNameArgs;
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
        var alertProcessingRuleByName = new AlertProcessingRuleByName("alertProcessingRuleByName", AlertProcessingRuleByNameArgs.builder()        
            .alertProcessingRuleName("RemoveActionGroupsRecurringMaintenance")
            .location("Global")
            .properties(Map.ofEntries(
                Map.entry("actions", Map.of("actionType", "RemoveAllActionGroups")),
                Map.entry("conditions", Map.ofEntries(
                    Map.entry("field", "TargetResourceType"),
                    Map.entry("operator", "Equals"),
                    Map.entry("values", "microsoft.compute/virtualmachines")
                )),
                Map.entry("description", "Remove all ActionGroups from all Vitual machine Alerts during the recurring maintenance"),
                Map.entry("enabled", true),
                Map.entry("schedule", Map.ofEntries(
                    Map.entry("recurrences", Map.ofEntries(
                        Map.entry("daysOfWeek",                         
                            "Saturday",
                            "Sunday"),
                        Map.entry("endTime", "04:00:00"),
                        Map.entry("recurrenceType", "Weekly"),
                        Map.entry("startTime", "22:00:00")
                    )),
                    Map.entry("timeZone", "India Standard Time")
                )),
                Map.entry("scopes",                 
                    "/subscriptions/subId1/resourceGroups/RGId1",
                    "/subscriptions/subId1/resourceGroups/RGId2")
            ))
            .resourceGroupName("alertscorrelationrg")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const alertProcessingRuleByName = new azure_native.alertsmanagement.AlertProcessingRuleByName("alertProcessingRuleByName", {
    alertProcessingRuleName: "RemoveActionGroupsRecurringMaintenance",
    location: "Global",
    properties: {
        actions: [{
            actionType: "RemoveAllActionGroups",
        }],
        conditions: [{
            field: "TargetResourceType",
            operator: "Equals",
            values: ["microsoft.compute/virtualmachines"],
        }],
        description: "Remove all ActionGroups from all Vitual machine Alerts during the recurring maintenance",
        enabled: true,
        schedule: {
            recurrences: [{
                daysOfWeek: [
                    "Saturday",
                    "Sunday",
                ],
                endTime: "04:00:00",
                recurrenceType: "Weekly",
                startTime: "22:00:00",
            }],
            timeZone: "India Standard Time",
        },
        scopes: [
            "/subscriptions/subId1/resourceGroups/RGId1",
            "/subscriptions/subId1/resourceGroups/RGId2",
        ],
    },
    resourceGroupName: "alertscorrelationrg",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

alert_processing_rule_by_name = azure_native.alertsmanagement.AlertProcessingRuleByName("alertProcessingRuleByName",
    alert_processing_rule_name="RemoveActionGroupsRecurringMaintenance",
    location="Global",
    properties=azure_native.alertsmanagement.AlertProcessingRulePropertiesResponseArgs(
        actions=[azure_native.alertsmanagement.RemoveAllActionGroupsArgs(
            action_type="RemoveAllActionGroups",
        )],
        conditions=[azure_native.alertsmanagement.ConditionArgs(
            field="TargetResourceType",
            operator="Equals",
            values=["microsoft.compute/virtualmachines"],
        )],
        description="Remove all ActionGroups from all Vitual machine Alerts during the recurring maintenance",
        enabled=True,
        schedule={
            "recurrences": [azure_native.alertsmanagement.WeeklyRecurrenceArgs(
                days_of_week=[
                    "Saturday",
                    "Sunday",
                ],
                end_time="04:00:00",
                recurrence_type="Weekly",
                start_time="22:00:00",
            )],
            "timeZone": "India Standard Time",
        },
        scopes=[
            "/subscriptions/subId1/resourceGroups/RGId1",
            "/subscriptions/subId1/resourceGroups/RGId2",
        ],
    ),
    resource_group_name="alertscorrelationrg",
    tags={})

```

```yaml
resources:
  alertProcessingRuleByName:
    type: azure-native:alertsmanagement:AlertProcessingRuleByName
    properties:
      alertProcessingRuleName: RemoveActionGroupsRecurringMaintenance
      location: Global
      properties:
        actions:
          - actionType: RemoveAllActionGroups
        conditions:
          - field: TargetResourceType
            operator: Equals
            values:
              - microsoft.compute/virtualmachines
        description: Remove all ActionGroups from all Vitual machine Alerts during the recurring maintenance
        enabled: true
        schedule:
          recurrences:
            - daysOfWeek:
                - Saturday
                - Sunday
              endTime: 04:00:00
              recurrenceType: Weekly
              startTime: 22:00:00
          timeZone: India Standard Time
        scopes:
          - /subscriptions/subId1/resourceGroups/RGId1
          - /subscriptions/subId1/resourceGroups/RGId2
      resourceGroupName: alertscorrelationrg
      tags: {}

```

{{% /example %}}
{{% example %}}
### Create or update a rule that removes all action groups outside business hours (Mon-Fri 09:00-17:00, Eastern Standard Time)
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var alertProcessingRuleByName = new AzureNative.AlertsManagement.AlertProcessingRuleByName("alertProcessingRuleByName", new()
    {
        AlertProcessingRuleName = "RemoveActionGroupsOutsideBusinessHours",
        Location = "Global",
        Properties = new AzureNative.AlertsManagement.Inputs.AlertProcessingRulePropertiesArgs
        {
            Actions = new[]
            {
                new AzureNative.AlertsManagement.Inputs.RemoveAllActionGroupsArgs
                {
                    ActionType = "RemoveAllActionGroups",
                },
            },
            Description = "Remove all ActionGroups outside business hours",
            Enabled = true,
            Schedule = new AzureNative.AlertsManagement.Inputs.ScheduleArgs
            {
                Recurrences = 
                {
                    new AzureNative.AlertsManagement.Inputs.DailyRecurrenceArgs
                    {
                        EndTime = "09:00:00",
                        RecurrenceType = "Daily",
                        StartTime = "17:00:00",
                    },
                    new AzureNative.AlertsManagement.Inputs.WeeklyRecurrenceArgs
                    {
                        DaysOfWeek = new[]
                        {
                            "Saturday",
                            "Sunday",
                        },
                        RecurrenceType = "Weekly",
                    },
                },
                TimeZone = "Eastern Standard Time",
            },
            Scopes = new[]
            {
                "/subscriptions/subId1",
            },
        },
        ResourceGroupName = "alertscorrelationrg",
        Tags = null,
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.alertsmanagement.AlertProcessingRuleByName;
import com.pulumi.azurenative.alertsmanagement.AlertProcessingRuleByNameArgs;
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
        var alertProcessingRuleByName = new AlertProcessingRuleByName("alertProcessingRuleByName", AlertProcessingRuleByNameArgs.builder()        
            .alertProcessingRuleName("RemoveActionGroupsOutsideBusinessHours")
            .location("Global")
            .properties(Map.ofEntries(
                Map.entry("actions", Map.of("actionType", "RemoveAllActionGroups")),
                Map.entry("description", "Remove all ActionGroups outside business hours"),
                Map.entry("enabled", true),
                Map.entry("schedule", Map.ofEntries(
                    Map.entry("recurrences",                     
                        Map.ofEntries(
                            Map.entry("endTime", "09:00:00"),
                            Map.entry("recurrenceType", "Daily"),
                            Map.entry("startTime", "17:00:00")
                        ),
                        Map.ofEntries(
                            Map.entry("daysOfWeek",                             
                                "Saturday",
                                "Sunday"),
                            Map.entry("recurrenceType", "Weekly")
                        )),
                    Map.entry("timeZone", "Eastern Standard Time")
                )),
                Map.entry("scopes", "/subscriptions/subId1")
            ))
            .resourceGroupName("alertscorrelationrg")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const alertProcessingRuleByName = new azure_native.alertsmanagement.AlertProcessingRuleByName("alertProcessingRuleByName", {
    alertProcessingRuleName: "RemoveActionGroupsOutsideBusinessHours",
    location: "Global",
    properties: {
        actions: [{
            actionType: "RemoveAllActionGroups",
        }],
        description: "Remove all ActionGroups outside business hours",
        enabled: true,
        schedule: {
            recurrences: [
                {
                    endTime: "09:00:00",
                    recurrenceType: "Daily",
                    startTime: "17:00:00",
                },
                {
                    daysOfWeek: [
                        "Saturday",
                        "Sunday",
                    ],
                    recurrenceType: "Weekly",
                },
            ],
            timeZone: "Eastern Standard Time",
        },
        scopes: ["/subscriptions/subId1"],
    },
    resourceGroupName: "alertscorrelationrg",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

alert_processing_rule_by_name = azure_native.alertsmanagement.AlertProcessingRuleByName("alertProcessingRuleByName",
    alert_processing_rule_name="RemoveActionGroupsOutsideBusinessHours",
    location="Global",
    properties=azure_native.alertsmanagement.AlertProcessingRulePropertiesResponseArgs(
        actions=[azure_native.alertsmanagement.RemoveAllActionGroupsArgs(
            action_type="RemoveAllActionGroups",
        )],
        description="Remove all ActionGroups outside business hours",
        enabled=True,
        schedule={
            "recurrences": [
                azure_native.alertsmanagement.DailyRecurrenceArgs(
                    end_time="09:00:00",
                    recurrence_type="Daily",
                    start_time="17:00:00",
                ),
                azure_native.alertsmanagement.WeeklyRecurrenceArgs(
                    days_of_week=[
                        "Saturday",
                        "Sunday",
                    ],
                    recurrence_type="Weekly",
                ),
            ],
            "timeZone": "Eastern Standard Time",
        },
        scopes=["/subscriptions/subId1"],
    ),
    resource_group_name="alertscorrelationrg",
    tags={})

```

```yaml
resources:
  alertProcessingRuleByName:
    type: azure-native:alertsmanagement:AlertProcessingRuleByName
    properties:
      alertProcessingRuleName: RemoveActionGroupsOutsideBusinessHours
      location: Global
      properties:
        actions:
          - actionType: RemoveAllActionGroups
        description: Remove all ActionGroups outside business hours
        enabled: true
        schedule:
          recurrences:
            - endTime: 09:00:00
              recurrenceType: Daily
              startTime: 17:00:00
            - daysOfWeek:
                - Saturday
                - Sunday
              recurrenceType: Weekly
          timeZone: Eastern Standard Time
        scopes:
          - /subscriptions/subId1
      resourceGroupName: alertscorrelationrg
      tags: {}

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:alertsmanagement:AlertProcessingRuleByName RemoveActionGroupsOutsideBusinessHours /subscriptions/subId1/resourceGroups/alertscorrelationrg/providers/Microsoft.AlertsManagement/actionRules/RemoveActionGroupsOutsideBusinessHours 
```
