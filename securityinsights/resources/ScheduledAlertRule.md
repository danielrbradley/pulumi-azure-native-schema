Represents scheduled alert rule.
API Version: 2023-02-01.
Previous API Version: 2020-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Creates or updates a Fusion alert rule.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var scheduledAlertRule = new AzureNative.SecurityInsights.ScheduledAlertRule("scheduledAlertRule", new()
    {
        ResourceGroupName = "myRg",
        RuleId = "myFirstFusionRule",
        WorkspaceName = "myWorkspace",
    });

});


```

```go
package main

import (
	securityinsights "github.com/pulumi/pulumi-azure-native-sdk/securityinsights"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := securityinsights.NewScheduledAlertRule(ctx, "scheduledAlertRule", &securityinsights.ScheduledAlertRuleArgs{
			ResourceGroupName: pulumi.String("myRg"),
			RuleId:            pulumi.String("myFirstFusionRule"),
			WorkspaceName:     pulumi.String("myWorkspace"),
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
import com.pulumi.azurenative.securityinsights.ScheduledAlertRule;
import com.pulumi.azurenative.securityinsights.ScheduledAlertRuleArgs;
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
        var scheduledAlertRule = new ScheduledAlertRule("scheduledAlertRule", ScheduledAlertRuleArgs.builder()        
            .resourceGroupName("myRg")
            .ruleId("myFirstFusionRule")
            .workspaceName("myWorkspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const scheduledAlertRule = new azure_native.securityinsights.ScheduledAlertRule("scheduledAlertRule", {
    resourceGroupName: "myRg",
    ruleId: "myFirstFusionRule",
    workspaceName: "myWorkspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

scheduled_alert_rule = azure_native.securityinsights.ScheduledAlertRule("scheduledAlertRule",
    resource_group_name="myRg",
    rule_id="myFirstFusionRule",
    workspace_name="myWorkspace")

```

```yaml
resources:
  scheduledAlertRule:
    type: azure-native:securityinsights:ScheduledAlertRule
    properties:
      resourceGroupName: myRg
      ruleId: myFirstFusionRule
      workspaceName: myWorkspace

```

{{% /example %}}
{{% example %}}
### Creates or updates a MicrosoftSecurityIncidentCreation rule.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var scheduledAlertRule = new AzureNative.SecurityInsights.ScheduledAlertRule("scheduledAlertRule", new()
    {
        ResourceGroupName = "myRg",
        RuleId = "microsoftSecurityIncidentCreationRuleExample",
        WorkspaceName = "myWorkspace",
    });

});


```

```go
package main

import (
	securityinsights "github.com/pulumi/pulumi-azure-native-sdk/securityinsights"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := securityinsights.NewScheduledAlertRule(ctx, "scheduledAlertRule", &securityinsights.ScheduledAlertRuleArgs{
			ResourceGroupName: pulumi.String("myRg"),
			RuleId:            pulumi.String("microsoftSecurityIncidentCreationRuleExample"),
			WorkspaceName:     pulumi.String("myWorkspace"),
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
import com.pulumi.azurenative.securityinsights.ScheduledAlertRule;
import com.pulumi.azurenative.securityinsights.ScheduledAlertRuleArgs;
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
        var scheduledAlertRule = new ScheduledAlertRule("scheduledAlertRule", ScheduledAlertRuleArgs.builder()        
            .resourceGroupName("myRg")
            .ruleId("microsoftSecurityIncidentCreationRuleExample")
            .workspaceName("myWorkspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const scheduledAlertRule = new azure_native.securityinsights.ScheduledAlertRule("scheduledAlertRule", {
    resourceGroupName: "myRg",
    ruleId: "microsoftSecurityIncidentCreationRuleExample",
    workspaceName: "myWorkspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

scheduled_alert_rule = azure_native.securityinsights.ScheduledAlertRule("scheduledAlertRule",
    resource_group_name="myRg",
    rule_id="microsoftSecurityIncidentCreationRuleExample",
    workspace_name="myWorkspace")

```

```yaml
resources:
  scheduledAlertRule:
    type: azure-native:securityinsights:ScheduledAlertRule
    properties:
      resourceGroupName: myRg
      ruleId: microsoftSecurityIncidentCreationRuleExample
      workspaceName: myWorkspace

```

{{% /example %}}
{{% example %}}
### Creates or updates a Scheduled alert rule.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var scheduledAlertRule = new AzureNative.SecurityInsights.ScheduledAlertRule("scheduledAlertRule", new()
    {
        AlertDetailsOverride = new AzureNative.SecurityInsights.Inputs.AlertDetailsOverrideArgs
        {
            AlertDescriptionFormat = "Suspicious activity was made by {{ComputerIP}}",
            AlertDisplayNameFormat = "Alert from {{Computer}}",
            AlertDynamicProperties = new[]
            {
                new AzureNative.SecurityInsights.Inputs.AlertPropertyMappingArgs
                {
                    AlertProperty = "ProductComponentName",
                    Value = "ProductComponentNameCustomColumn",
                },
                new AzureNative.SecurityInsights.Inputs.AlertPropertyMappingArgs
                {
                    AlertProperty = "ProductName",
                    Value = "ProductNameCustomColumn",
                },
                new AzureNative.SecurityInsights.Inputs.AlertPropertyMappingArgs
                {
                    AlertProperty = "AlertLink",
                    Value = "Link",
                },
            },
        },
        CustomDetails = 
        {
            { "OperatingSystemName", "OSName" },
            { "OperatingSystemType", "OSType" },
        },
        Description = "An example for a scheduled rule",
        DisplayName = "My scheduled rule",
        Enabled = true,
        EntityMappings = new[]
        {
            new AzureNative.SecurityInsights.Inputs.EntityMappingArgs
            {
                EntityType = "Host",
                FieldMappings = new[]
                {
                    new AzureNative.SecurityInsights.Inputs.FieldMappingArgs
                    {
                        ColumnName = "Computer",
                        Identifier = "FullName",
                    },
                },
            },
            new AzureNative.SecurityInsights.Inputs.EntityMappingArgs
            {
                EntityType = "IP",
                FieldMappings = new[]
                {
                    new AzureNative.SecurityInsights.Inputs.FieldMappingArgs
                    {
                        ColumnName = "ComputerIP",
                        Identifier = "Address",
                    },
                },
            },
        },
        EventGroupingSettings = new AzureNative.SecurityInsights.Inputs.EventGroupingSettingsArgs
        {
            AggregationKind = "AlertPerResult",
        },
        IncidentConfiguration = new AzureNative.SecurityInsights.Inputs.IncidentConfigurationArgs
        {
            CreateIncident = true,
            GroupingConfiguration = new AzureNative.SecurityInsights.Inputs.GroupingConfigurationArgs
            {
                Enabled = true,
                GroupByAlertDetails = new[]
                {
                    "DisplayName",
                },
                GroupByCustomDetails = new[]
                {
                    "OperatingSystemType",
                    "OperatingSystemName",
                },
                GroupByEntities = new[]
                {
                    "Host",
                },
                LookbackDuration = "PT5H",
                MatchingMethod = "Selected",
                ReopenClosedIncident = false,
            },
        },
        Kind = "Scheduled",
        Query = "Heartbeat",
        QueryFrequency = "PT1H",
        QueryPeriod = "P2DT1H30M",
        ResourceGroupName = "myRg",
        RuleId = "73e01a99-5cd7-4139-a149-9f2736ff2ab5",
        Severity = "High",
        SuppressionDuration = "PT1H",
        SuppressionEnabled = false,
        Tactics = new[]
        {
            "Persistence",
            "LateralMovement",
        },
        TriggerOperator = AzureNative.SecurityInsights.TriggerOperator.GreaterThan,
        TriggerThreshold = 0,
        WorkspaceName = "myWorkspace",
    });

});


```

```go
package main

import (
	securityinsights "github.com/pulumi/pulumi-azure-native-sdk/securityinsights"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := securityinsights.NewScheduledAlertRule(ctx, "scheduledAlertRule", &securityinsights.ScheduledAlertRuleArgs{
			AlertDetailsOverride: securityinsights.AlertDetailsOverrideResponse{
				AlertDescriptionFormat: pulumi.String("Suspicious activity was made by {{ComputerIP}}"),
				AlertDisplayNameFormat: pulumi.String("Alert from {{Computer}}"),
				AlertDynamicProperties: securityinsights.AlertPropertyMappingArray{
					&securityinsights.AlertPropertyMappingArgs{
						AlertProperty: pulumi.String("ProductComponentName"),
						Value:         pulumi.String("ProductComponentNameCustomColumn"),
					},
					&securityinsights.AlertPropertyMappingArgs{
						AlertProperty: pulumi.String("ProductName"),
						Value:         pulumi.String("ProductNameCustomColumn"),
					},
					&securityinsights.AlertPropertyMappingArgs{
						AlertProperty: pulumi.String("AlertLink"),
						Value:         pulumi.String("Link"),
					},
				},
			},
			CustomDetails: pulumi.StringMap{
				"OperatingSystemName": pulumi.String("OSName"),
				"OperatingSystemType": pulumi.String("OSType"),
			},
			Description: pulumi.String("An example for a scheduled rule"),
			DisplayName: pulumi.String("My scheduled rule"),
			Enabled:     pulumi.Bool(true),
			EntityMappings: []securityinsights.EntityMappingArgs{
				{
					EntityType: pulumi.String("Host"),
					FieldMappings: securityinsights.FieldMappingArray{
						{
							ColumnName: pulumi.String("Computer"),
							Identifier: pulumi.String("FullName"),
						},
					},
				},
				{
					EntityType: pulumi.String("IP"),
					FieldMappings: securityinsights.FieldMappingArray{
						{
							ColumnName: pulumi.String("ComputerIP"),
							Identifier: pulumi.String("Address"),
						},
					},
				},
			},
			EventGroupingSettings: &securityinsights.EventGroupingSettingsArgs{
				AggregationKind: pulumi.String("AlertPerResult"),
			},
			IncidentConfiguration: securityinsights.IncidentConfigurationResponse{
				CreateIncident: pulumi.Bool(true),
				GroupingConfiguration: &securityinsights.GroupingConfigurationArgs{
					Enabled: pulumi.Bool(true),
					GroupByAlertDetails: pulumi.StringArray{
						pulumi.String("DisplayName"),
					},
					GroupByCustomDetails: pulumi.StringArray{
						pulumi.String("OperatingSystemType"),
						pulumi.String("OperatingSystemName"),
					},
					GroupByEntities: pulumi.StringArray{
						pulumi.String("Host"),
					},
					LookbackDuration:     pulumi.String("PT5H"),
					MatchingMethod:       pulumi.String("Selected"),
					ReopenClosedIncident: pulumi.Bool(false),
				},
			},
			Kind:                pulumi.String("Scheduled"),
			Query:               pulumi.String("Heartbeat"),
			QueryFrequency:      pulumi.String("PT1H"),
			QueryPeriod:         pulumi.String("P2DT1H30M"),
			ResourceGroupName:   pulumi.String("myRg"),
			RuleId:              pulumi.String("73e01a99-5cd7-4139-a149-9f2736ff2ab5"),
			Severity:            pulumi.String("High"),
			SuppressionDuration: pulumi.String("PT1H"),
			SuppressionEnabled:  pulumi.Bool(false),
			Tactics: pulumi.StringArray{
				pulumi.String("Persistence"),
				pulumi.String("LateralMovement"),
			},
			TriggerOperator:  securityinsights.TriggerOperatorGreaterThan,
			TriggerThreshold: pulumi.Int(0),
			WorkspaceName:    pulumi.String("myWorkspace"),
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
import com.pulumi.azurenative.securityinsights.ScheduledAlertRule;
import com.pulumi.azurenative.securityinsights.ScheduledAlertRuleArgs;
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
        var scheduledAlertRule = new ScheduledAlertRule("scheduledAlertRule", ScheduledAlertRuleArgs.builder()        
            .alertDetailsOverride(Map.ofEntries(
                Map.entry("alertDescriptionFormat", "Suspicious activity was made by {{ComputerIP}}"),
                Map.entry("alertDisplayNameFormat", "Alert from {{Computer}}"),
                Map.entry("alertDynamicProperties",                 
                    Map.ofEntries(
                        Map.entry("alertProperty", "ProductComponentName"),
                        Map.entry("value", "ProductComponentNameCustomColumn")
                    ),
                    Map.ofEntries(
                        Map.entry("alertProperty", "ProductName"),
                        Map.entry("value", "ProductNameCustomColumn")
                    ),
                    Map.ofEntries(
                        Map.entry("alertProperty", "AlertLink"),
                        Map.entry("value", "Link")
                    ))
            ))
            .customDetails(Map.ofEntries(
                Map.entry("OperatingSystemName", "OSName"),
                Map.entry("OperatingSystemType", "OSType")
            ))
            .description("An example for a scheduled rule")
            .displayName("My scheduled rule")
            .enabled(true)
            .entityMappings(            
                Map.ofEntries(
                    Map.entry("entityType", "Host"),
                    Map.entry("fieldMappings", Map.ofEntries(
                        Map.entry("columnName", "Computer"),
                        Map.entry("identifier", "FullName")
                    ))
                ),
                Map.ofEntries(
                    Map.entry("entityType", "IP"),
                    Map.entry("fieldMappings", Map.ofEntries(
                        Map.entry("columnName", "ComputerIP"),
                        Map.entry("identifier", "Address")
                    ))
                ))
            .eventGroupingSettings(Map.of("aggregationKind", "AlertPerResult"))
            .incidentConfiguration(Map.ofEntries(
                Map.entry("createIncident", true),
                Map.entry("groupingConfiguration", Map.ofEntries(
                    Map.entry("enabled", true),
                    Map.entry("groupByAlertDetails", "DisplayName"),
                    Map.entry("groupByCustomDetails",                     
                        "OperatingSystemType",
                        "OperatingSystemName"),
                    Map.entry("groupByEntities", "Host"),
                    Map.entry("lookbackDuration", "PT5H"),
                    Map.entry("matchingMethod", "Selected"),
                    Map.entry("reopenClosedIncident", false)
                ))
            ))
            .kind("Scheduled")
            .query("Heartbeat")
            .queryFrequency("PT1H")
            .queryPeriod("P2DT1H30M")
            .resourceGroupName("myRg")
            .ruleId("73e01a99-5cd7-4139-a149-9f2736ff2ab5")
            .severity("High")
            .suppressionDuration("PT1H")
            .suppressionEnabled(false)
            .tactics(            
                "Persistence",
                "LateralMovement")
            .triggerOperator("GreaterThan")
            .triggerThreshold(0)
            .workspaceName("myWorkspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const scheduledAlertRule = new azure_native.securityinsights.ScheduledAlertRule("scheduledAlertRule", {
    alertDetailsOverride: {
        alertDescriptionFormat: "Suspicious activity was made by {{ComputerIP}}",
        alertDisplayNameFormat: "Alert from {{Computer}}",
        alertDynamicProperties: [
            {
                alertProperty: "ProductComponentName",
                value: "ProductComponentNameCustomColumn",
            },
            {
                alertProperty: "ProductName",
                value: "ProductNameCustomColumn",
            },
            {
                alertProperty: "AlertLink",
                value: "Link",
            },
        ],
    },
    customDetails: {
        OperatingSystemName: "OSName",
        OperatingSystemType: "OSType",
    },
    description: "An example for a scheduled rule",
    displayName: "My scheduled rule",
    enabled: true,
    entityMappings: [
        {
            entityType: "Host",
            fieldMappings: [{
                columnName: "Computer",
                identifier: "FullName",
            }],
        },
        {
            entityType: "IP",
            fieldMappings: [{
                columnName: "ComputerIP",
                identifier: "Address",
            }],
        },
    ],
    eventGroupingSettings: {
        aggregationKind: "AlertPerResult",
    },
    incidentConfiguration: {
        createIncident: true,
        groupingConfiguration: {
            enabled: true,
            groupByAlertDetails: ["DisplayName"],
            groupByCustomDetails: [
                "OperatingSystemType",
                "OperatingSystemName",
            ],
            groupByEntities: ["Host"],
            lookbackDuration: "PT5H",
            matchingMethod: "Selected",
            reopenClosedIncident: false,
        },
    },
    kind: "Scheduled",
    query: "Heartbeat",
    queryFrequency: "PT1H",
    queryPeriod: "P2DT1H30M",
    resourceGroupName: "myRg",
    ruleId: "73e01a99-5cd7-4139-a149-9f2736ff2ab5",
    severity: "High",
    suppressionDuration: "PT1H",
    suppressionEnabled: false,
    tactics: [
        "Persistence",
        "LateralMovement",
    ],
    triggerOperator: azure_native.securityinsights.TriggerOperator.GreaterThan,
    triggerThreshold: 0,
    workspaceName: "myWorkspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

scheduled_alert_rule = azure_native.securityinsights.ScheduledAlertRule("scheduledAlertRule",
    alert_details_override=azure_native.securityinsights.AlertDetailsOverrideResponseArgs(
        alert_description_format="Suspicious activity was made by {{ComputerIP}}",
        alert_display_name_format="Alert from {{Computer}}",
        alert_dynamic_properties=[
            azure_native.securityinsights.AlertPropertyMappingArgs(
                alert_property="ProductComponentName",
                value="ProductComponentNameCustomColumn",
            ),
            azure_native.securityinsights.AlertPropertyMappingArgs(
                alert_property="ProductName",
                value="ProductNameCustomColumn",
            ),
            azure_native.securityinsights.AlertPropertyMappingArgs(
                alert_property="AlertLink",
                value="Link",
            ),
        ],
    ),
    custom_details={
        "OperatingSystemName": "OSName",
        "OperatingSystemType": "OSType",
    },
    description="An example for a scheduled rule",
    display_name="My scheduled rule",
    enabled=True,
    entity_mappings=[
        {
            "entityType": "Host",
            "fieldMappings": [azure_native.securityinsights.FieldMappingArgs(
                column_name="Computer",
                identifier="FullName",
            )],
        },
        {
            "entityType": "IP",
            "fieldMappings": [azure_native.securityinsights.FieldMappingArgs(
                column_name="ComputerIP",
                identifier="Address",
            )],
        },
    ],
    event_grouping_settings=azure_native.securityinsights.EventGroupingSettingsArgs(
        aggregation_kind="AlertPerResult",
    ),
    incident_configuration=azure_native.securityinsights.IncidentConfigurationResponseArgs(
        create_incident=True,
        grouping_configuration=azure_native.securityinsights.GroupingConfigurationArgs(
            enabled=True,
            group_by_alert_details=["DisplayName"],
            group_by_custom_details=[
                "OperatingSystemType",
                "OperatingSystemName",
            ],
            group_by_entities=["Host"],
            lookback_duration="PT5H",
            matching_method="Selected",
            reopen_closed_incident=False,
        ),
    ),
    kind="Scheduled",
    query="Heartbeat",
    query_frequency="PT1H",
    query_period="P2DT1H30M",
    resource_group_name="myRg",
    rule_id="73e01a99-5cd7-4139-a149-9f2736ff2ab5",
    severity="High",
    suppression_duration="PT1H",
    suppression_enabled=False,
    tactics=[
        "Persistence",
        "LateralMovement",
    ],
    trigger_operator=azure_native.securityinsights.TriggerOperator.GREATER_THAN,
    trigger_threshold=0,
    workspace_name="myWorkspace")

```

```yaml
resources:
  scheduledAlertRule:
    type: azure-native:securityinsights:ScheduledAlertRule
    properties:
      alertDetailsOverride:
        alertDescriptionFormat: Suspicious activity was made by {{ComputerIP}}
        alertDisplayNameFormat: Alert from {{Computer}}
        alertDynamicProperties:
          - alertProperty: ProductComponentName
            value: ProductComponentNameCustomColumn
          - alertProperty: ProductName
            value: ProductNameCustomColumn
          - alertProperty: AlertLink
            value: Link
      customDetails:
        OperatingSystemName: OSName
        OperatingSystemType: OSType
      description: An example for a scheduled rule
      displayName: My scheduled rule
      enabled: true
      entityMappings:
        - entityType: Host
          fieldMappings:
            - columnName: Computer
              identifier: FullName
        - entityType: IP
          fieldMappings:
            - columnName: ComputerIP
              identifier: Address
      eventGroupingSettings:
        aggregationKind: AlertPerResult
      incidentConfiguration:
        createIncident: true
        groupingConfiguration:
          enabled: true
          groupByAlertDetails:
            - DisplayName
          groupByCustomDetails:
            - OperatingSystemType
            - OperatingSystemName
          groupByEntities:
            - Host
          lookbackDuration: PT5H
          matchingMethod: Selected
          reopenClosedIncident: false
      kind: Scheduled
      query: Heartbeat
      queryFrequency: PT1H
      queryPeriod: P2DT1H30M
      resourceGroupName: myRg
      ruleId: 73e01a99-5cd7-4139-a149-9f2736ff2ab5
      severity: High
      suppressionDuration: PT1H
      suppressionEnabled: false
      tactics:
        - Persistence
        - LateralMovement
      triggerOperator: GreaterThan
      triggerThreshold: 0
      workspaceName: myWorkspace

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:securityinsights:ScheduledAlertRule 73e01a99-5cd7-4139-a149-9f2736ff2ab5 /subscriptions/d0cfe6b2-9ac0-4464-9919-dccaee2e48c0/resourceGroups/myRg/providers/Microsoft.OperationalInsights/workspaces/myWorkspace/providers/Microsoft.SecurityInsights/alertRules/73e01a99-5cd7-4139-a149-9f2736ff2ab5 
```
