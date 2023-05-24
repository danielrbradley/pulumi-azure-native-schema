The scheduled query rule resource.
API Version: 2022-06-15.
Previous API Version: 2018-04-16. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a scheduled query rule for Single Resource
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var scheduledQueryRule = new AzureNative.Insights.ScheduledQueryRule("scheduledQueryRule", new()
    {
        Actions = new AzureNative.Insights.Inputs.ActionsArgs
        {
            ActionGroups = new[]
            {
                "/subscriptions/1cf177ed-1330-4692-80ea-fd3d7783b147/resourcegroups/sqrapi/providers/microsoft.insights/actiongroups/myactiongroup",
            },
            CustomProperties = 
            {
                { "key11", "value11" },
                { "key12", "value12" },
            },
        },
        AutoMitigate = true,
        CheckWorkspaceAlertsStorageConfigured = true,
        Criteria = new AzureNative.Insights.Inputs.ScheduledQueryRuleCriteriaArgs
        {
            AllOf = new[]
            {
                new AzureNative.Insights.Inputs.ConditionArgs
                {
                    Dimensions = new[]
                    {
                        new AzureNative.Insights.Inputs.DimensionArgs
                        {
                            Name = "ComputerIp",
                            Operator = "Exclude",
                            Values = new[]
                            {
                                "192.168.1.1",
                            },
                        },
                        new AzureNative.Insights.Inputs.DimensionArgs
                        {
                            Name = "OSType",
                            Operator = "Include",
                            Values = new[]
                            {
                                "*",
                            },
                        },
                    },
                    FailingPeriods = new AzureNative.Insights.Inputs.ConditionFailingPeriodsArgs
                    {
                        MinFailingPeriodsToAlert = 1,
                        NumberOfEvaluationPeriods = 1,
                    },
                    MetricMeasureColumn = "% Processor Time",
                    Operator = "GreaterThan",
                    Query = "Perf | where ObjectName == \"Processor\"",
                    ResourceIdColumn = "resourceId",
                    Threshold = 70,
                    TimeAggregation = "Average",
                },
            },
        },
        Description = "Performance rule",
        Enabled = true,
        EvaluationFrequency = "PT5M",
        Location = "eastus",
        MuteActionsDuration = "PT30M",
        ResourceGroupName = "QueryResourceGroupName",
        RuleName = "perf",
        Scopes = new[]
        {
            "/subscriptions/aaf177ed-1330-a9f2-80ea-fd3d7783b147/resourceGroups/scopeResourceGroup1/providers/Microsoft.Compute/virtualMachines/vm1",
        },
        Severity = 4,
        SkipQueryValidation = true,
        WindowSize = "PT10M",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.insights.ScheduledQueryRule;
import com.pulumi.azurenative.insights.ScheduledQueryRuleArgs;
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
        var scheduledQueryRule = new ScheduledQueryRule("scheduledQueryRule", ScheduledQueryRuleArgs.builder()        
            .actions(Map.ofEntries(
                Map.entry("actionGroups", "/subscriptions/1cf177ed-1330-4692-80ea-fd3d7783b147/resourcegroups/sqrapi/providers/microsoft.insights/actiongroups/myactiongroup"),
                Map.entry("customProperties", Map.ofEntries(
                    Map.entry("key11", "value11"),
                    Map.entry("key12", "value12")
                ))
            ))
            .autoMitigate(true)
            .checkWorkspaceAlertsStorageConfigured(true)
            .criteria(Map.of("allOf", Map.ofEntries(
                Map.entry("dimensions",                 
                    Map.ofEntries(
                        Map.entry("name", "ComputerIp"),
                        Map.entry("operator", "Exclude"),
                        Map.entry("values", "192.168.1.1")
                    ),
                    Map.ofEntries(
                        Map.entry("name", "OSType"),
                        Map.entry("operator", "Include"),
                        Map.entry("values", "*")
                    )),
                Map.entry("failingPeriods", Map.ofEntries(
                    Map.entry("minFailingPeriodsToAlert", 1),
                    Map.entry("numberOfEvaluationPeriods", 1)
                )),
                Map.entry("metricMeasureColumn", "% Processor Time"),
                Map.entry("operator", "GreaterThan"),
                Map.entry("query", "Perf | where ObjectName == \"Processor\""),
                Map.entry("resourceIdColumn", "resourceId"),
                Map.entry("threshold", 70),
                Map.entry("timeAggregation", "Average")
            )))
            .description("Performance rule")
            .enabled(true)
            .evaluationFrequency("PT5M")
            .location("eastus")
            .muteActionsDuration("PT30M")
            .resourceGroupName("QueryResourceGroupName")
            .ruleName("perf")
            .scopes("/subscriptions/aaf177ed-1330-a9f2-80ea-fd3d7783b147/resourceGroups/scopeResourceGroup1/providers/Microsoft.Compute/virtualMachines/vm1")
            .severity(4)
            .skipQueryValidation(true)
            .windowSize("PT10M")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const scheduledQueryRule = new azure_native.insights.ScheduledQueryRule("scheduledQueryRule", {
    actions: {
        actionGroups: ["/subscriptions/1cf177ed-1330-4692-80ea-fd3d7783b147/resourcegroups/sqrapi/providers/microsoft.insights/actiongroups/myactiongroup"],
        customProperties: {
            key11: "value11",
            key12: "value12",
        },
    },
    autoMitigate: true,
    checkWorkspaceAlertsStorageConfigured: true,
    criteria: {
        allOf: [{
            dimensions: [
                {
                    name: "ComputerIp",
                    operator: "Exclude",
                    values: ["192.168.1.1"],
                },
                {
                    name: "OSType",
                    operator: "Include",
                    values: ["*"],
                },
            ],
            failingPeriods: {
                minFailingPeriodsToAlert: 1,
                numberOfEvaluationPeriods: 1,
            },
            metricMeasureColumn: "% Processor Time",
            operator: "GreaterThan",
            query: "Perf | where ObjectName == \"Processor\"",
            resourceIdColumn: "resourceId",
            threshold: 70,
            timeAggregation: "Average",
        }],
    },
    description: "Performance rule",
    enabled: true,
    evaluationFrequency: "PT5M",
    location: "eastus",
    muteActionsDuration: "PT30M",
    resourceGroupName: "QueryResourceGroupName",
    ruleName: "perf",
    scopes: ["/subscriptions/aaf177ed-1330-a9f2-80ea-fd3d7783b147/resourceGroups/scopeResourceGroup1/providers/Microsoft.Compute/virtualMachines/vm1"],
    severity: 4,
    skipQueryValidation: true,
    windowSize: "PT10M",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

scheduled_query_rule = azure_native.insights.ScheduledQueryRule("scheduledQueryRule",
    actions=azure_native.insights.ActionsArgs(
        action_groups=["/subscriptions/1cf177ed-1330-4692-80ea-fd3d7783b147/resourcegroups/sqrapi/providers/microsoft.insights/actiongroups/myactiongroup"],
        custom_properties={
            "key11": "value11",
            "key12": "value12",
        },
    ),
    auto_mitigate=True,
    check_workspace_alerts_storage_configured=True,
    criteria=azure_native.insights.ScheduledQueryRuleCriteriaResponseArgs(
        all_of=[{
            "dimensions": [
                azure_native.insights.DimensionArgs(
                    name="ComputerIp",
                    operator="Exclude",
                    values=["192.168.1.1"],
                ),
                azure_native.insights.DimensionArgs(
                    name="OSType",
                    operator="Include",
                    values=["*"],
                ),
            ],
            "failingPeriods": azure_native.insights.ConditionFailingPeriodsArgs(
                min_failing_periods_to_alert=1,
                number_of_evaluation_periods=1,
            ),
            "metricMeasureColumn": "% Processor Time",
            "operator": "GreaterThan",
            "query": "Perf | where ObjectName == \"Processor\"",
            "resourceIdColumn": "resourceId",
            "threshold": 70,
            "timeAggregation": "Average",
        }],
    ),
    description="Performance rule",
    enabled=True,
    evaluation_frequency="PT5M",
    location="eastus",
    mute_actions_duration="PT30M",
    resource_group_name="QueryResourceGroupName",
    rule_name="perf",
    scopes=["/subscriptions/aaf177ed-1330-a9f2-80ea-fd3d7783b147/resourceGroups/scopeResourceGroup1/providers/Microsoft.Compute/virtualMachines/vm1"],
    severity=4,
    skip_query_validation=True,
    window_size="PT10M")

```

```yaml
resources:
  scheduledQueryRule:
    type: azure-native:insights:ScheduledQueryRule
    properties:
      actions:
        actionGroups:
          - /subscriptions/1cf177ed-1330-4692-80ea-fd3d7783b147/resourcegroups/sqrapi/providers/microsoft.insights/actiongroups/myactiongroup
        customProperties:
          key11: value11
          key12: value12
      autoMitigate: true
      checkWorkspaceAlertsStorageConfigured: true
      criteria:
        allOf:
          - dimensions:
              - name: ComputerIp
                operator: Exclude
                values:
                  - 192.168.1.1
              - name: OSType
                operator: Include
                values:
                  - '*'
            failingPeriods:
              minFailingPeriodsToAlert: 1
              numberOfEvaluationPeriods: 1
            metricMeasureColumn: '% Processor Time'
            operator: GreaterThan
            query: Perf | where ObjectName == "Processor"
            resourceIdColumn: resourceId
            threshold: 70
            timeAggregation: Average
      description: Performance rule
      enabled: true
      evaluationFrequency: PT5M
      location: eastus
      muteActionsDuration: PT30M
      resourceGroupName: QueryResourceGroupName
      ruleName: perf
      scopes:
        - /subscriptions/aaf177ed-1330-a9f2-80ea-fd3d7783b147/resourceGroups/scopeResourceGroup1/providers/Microsoft.Compute/virtualMachines/vm1
      severity: 4
      skipQueryValidation: true
      windowSize: PT10M

```

{{% /example %}}
{{% example %}}
### Create or update a scheduled query rule on Resource group(s)
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var scheduledQueryRule = new AzureNative.Insights.ScheduledQueryRule("scheduledQueryRule", new()
    {
        Actions = new AzureNative.Insights.Inputs.ActionsArgs
        {
            ActionGroups = new[]
            {
                "/subscriptions/1cf177ed-1330-4692-80ea-fd3d7783b147/resourcegroups/sqrapi/providers/microsoft.insights/actiongroups/myactiongroup",
            },
            CustomProperties = 
            {
                { "key11", "value11" },
                { "key12", "value12" },
            },
        },
        AutoMitigate = true,
        CheckWorkspaceAlertsStorageConfigured = true,
        Criteria = new AzureNative.Insights.Inputs.ScheduledQueryRuleCriteriaArgs
        {
            AllOf = new[]
            {
                new AzureNative.Insights.Inputs.ConditionArgs
                {
                    Dimensions = new[] {},
                    FailingPeriods = new AzureNative.Insights.Inputs.ConditionFailingPeriodsArgs
                    {
                        MinFailingPeriodsToAlert = 1,
                        NumberOfEvaluationPeriods = 1,
                    },
                    Operator = "GreaterThan",
                    Query = "Heartbeat",
                    Threshold = 360,
                    TimeAggregation = "Count",
                },
            },
        },
        Description = "Health check rule",
        Enabled = true,
        EvaluationFrequency = "PT5M",
        Location = "eastus",
        MuteActionsDuration = "PT30M",
        ResourceGroupName = "QueryResourceGroupName",
        RuleName = "heartbeat",
        Scopes = new[]
        {
            "/subscriptions/aaf177ed-1330-a9f2-80ea-fd3d7783b147/resourceGroups/scopeResourceGroup1",
        },
        Severity = 4,
        SkipQueryValidation = true,
        TargetResourceTypes = new[]
        {
            "Microsoft.Compute/virtualMachines",
        },
        WindowSize = "PT10M",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.insights.ScheduledQueryRule;
import com.pulumi.azurenative.insights.ScheduledQueryRuleArgs;
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
        var scheduledQueryRule = new ScheduledQueryRule("scheduledQueryRule", ScheduledQueryRuleArgs.builder()        
            .actions(Map.ofEntries(
                Map.entry("actionGroups", "/subscriptions/1cf177ed-1330-4692-80ea-fd3d7783b147/resourcegroups/sqrapi/providers/microsoft.insights/actiongroups/myactiongroup"),
                Map.entry("customProperties", Map.ofEntries(
                    Map.entry("key11", "value11"),
                    Map.entry("key12", "value12")
                ))
            ))
            .autoMitigate(true)
            .checkWorkspaceAlertsStorageConfigured(true)
            .criteria(Map.of("allOf", Map.ofEntries(
                Map.entry("dimensions", ),
                Map.entry("failingPeriods", Map.ofEntries(
                    Map.entry("minFailingPeriodsToAlert", 1),
                    Map.entry("numberOfEvaluationPeriods", 1)
                )),
                Map.entry("operator", "GreaterThan"),
                Map.entry("query", "Heartbeat"),
                Map.entry("threshold", 360),
                Map.entry("timeAggregation", "Count")
            )))
            .description("Health check rule")
            .enabled(true)
            .evaluationFrequency("PT5M")
            .location("eastus")
            .muteActionsDuration("PT30M")
            .resourceGroupName("QueryResourceGroupName")
            .ruleName("heartbeat")
            .scopes("/subscriptions/aaf177ed-1330-a9f2-80ea-fd3d7783b147/resourceGroups/scopeResourceGroup1")
            .severity(4)
            .skipQueryValidation(true)
            .targetResourceTypes("Microsoft.Compute/virtualMachines")
            .windowSize("PT10M")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const scheduledQueryRule = new azure_native.insights.ScheduledQueryRule("scheduledQueryRule", {
    actions: {
        actionGroups: ["/subscriptions/1cf177ed-1330-4692-80ea-fd3d7783b147/resourcegroups/sqrapi/providers/microsoft.insights/actiongroups/myactiongroup"],
        customProperties: {
            key11: "value11",
            key12: "value12",
        },
    },
    autoMitigate: true,
    checkWorkspaceAlertsStorageConfigured: true,
    criteria: {
        allOf: [{
            dimensions: [],
            failingPeriods: {
                minFailingPeriodsToAlert: 1,
                numberOfEvaluationPeriods: 1,
            },
            operator: "GreaterThan",
            query: "Heartbeat",
            threshold: 360,
            timeAggregation: "Count",
        }],
    },
    description: "Health check rule",
    enabled: true,
    evaluationFrequency: "PT5M",
    location: "eastus",
    muteActionsDuration: "PT30M",
    resourceGroupName: "QueryResourceGroupName",
    ruleName: "heartbeat",
    scopes: ["/subscriptions/aaf177ed-1330-a9f2-80ea-fd3d7783b147/resourceGroups/scopeResourceGroup1"],
    severity: 4,
    skipQueryValidation: true,
    targetResourceTypes: ["Microsoft.Compute/virtualMachines"],
    windowSize: "PT10M",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

scheduled_query_rule = azure_native.insights.ScheduledQueryRule("scheduledQueryRule",
    actions=azure_native.insights.ActionsArgs(
        action_groups=["/subscriptions/1cf177ed-1330-4692-80ea-fd3d7783b147/resourcegroups/sqrapi/providers/microsoft.insights/actiongroups/myactiongroup"],
        custom_properties={
            "key11": "value11",
            "key12": "value12",
        },
    ),
    auto_mitigate=True,
    check_workspace_alerts_storage_configured=True,
    criteria=azure_native.insights.ScheduledQueryRuleCriteriaResponseArgs(
        all_of=[{
            "dimensions": [],
            "failingPeriods": azure_native.insights.ConditionFailingPeriodsArgs(
                min_failing_periods_to_alert=1,
                number_of_evaluation_periods=1,
            ),
            "operator": "GreaterThan",
            "query": "Heartbeat",
            "threshold": 360,
            "timeAggregation": "Count",
        }],
    ),
    description="Health check rule",
    enabled=True,
    evaluation_frequency="PT5M",
    location="eastus",
    mute_actions_duration="PT30M",
    resource_group_name="QueryResourceGroupName",
    rule_name="heartbeat",
    scopes=["/subscriptions/aaf177ed-1330-a9f2-80ea-fd3d7783b147/resourceGroups/scopeResourceGroup1"],
    severity=4,
    skip_query_validation=True,
    target_resource_types=["Microsoft.Compute/virtualMachines"],
    window_size="PT10M")

```

```yaml
resources:
  scheduledQueryRule:
    type: azure-native:insights:ScheduledQueryRule
    properties:
      actions:
        actionGroups:
          - /subscriptions/1cf177ed-1330-4692-80ea-fd3d7783b147/resourcegroups/sqrapi/providers/microsoft.insights/actiongroups/myactiongroup
        customProperties:
          key11: value11
          key12: value12
      autoMitigate: true
      checkWorkspaceAlertsStorageConfigured: true
      criteria:
        allOf:
          - dimensions: []
            failingPeriods:
              minFailingPeriodsToAlert: 1
              numberOfEvaluationPeriods: 1
            operator: GreaterThan
            query: Heartbeat
            threshold: 360
            timeAggregation: Count
      description: Health check rule
      enabled: true
      evaluationFrequency: PT5M
      location: eastus
      muteActionsDuration: PT30M
      resourceGroupName: QueryResourceGroupName
      ruleName: heartbeat
      scopes:
        - /subscriptions/aaf177ed-1330-a9f2-80ea-fd3d7783b147/resourceGroups/scopeResourceGroup1
      severity: 4
      skipQueryValidation: true
      targetResourceTypes:
        - Microsoft.Compute/virtualMachines
      windowSize: PT10M

```

{{% /example %}}
{{% example %}}
### Create or update a scheduled query rule on Subscription 
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var scheduledQueryRule = new AzureNative.Insights.ScheduledQueryRule("scheduledQueryRule", new()
    {
        Actions = new AzureNative.Insights.Inputs.ActionsArgs
        {
            ActionGroups = new[]
            {
                "/subscriptions/1cf177ed-1330-4692-80ea-fd3d7783b147/resourcegroups/sqrapi/providers/microsoft.insights/actiongroups/myactiongroup",
            },
            CustomProperties = 
            {
                { "key11", "value11" },
                { "key12", "value12" },
            },
        },
        AutoMitigate = true,
        CheckWorkspaceAlertsStorageConfigured = true,
        Criteria = new AzureNative.Insights.Inputs.ScheduledQueryRuleCriteriaArgs
        {
            AllOf = new[]
            {
                new AzureNative.Insights.Inputs.ConditionArgs
                {
                    Dimensions = new[]
                    {
                        new AzureNative.Insights.Inputs.DimensionArgs
                        {
                            Name = "ComputerIp",
                            Operator = "Exclude",
                            Values = new[]
                            {
                                "192.168.1.1",
                            },
                        },
                        new AzureNative.Insights.Inputs.DimensionArgs
                        {
                            Name = "OSType",
                            Operator = "Include",
                            Values = new[]
                            {
                                "*",
                            },
                        },
                    },
                    FailingPeriods = new AzureNative.Insights.Inputs.ConditionFailingPeriodsArgs
                    {
                        MinFailingPeriodsToAlert = 1,
                        NumberOfEvaluationPeriods = 1,
                    },
                    MetricMeasureColumn = "% Processor Time",
                    Operator = "GreaterThan",
                    Query = "Perf | where ObjectName == \"Processor\"",
                    ResourceIdColumn = "resourceId",
                    Threshold = 70,
                    TimeAggregation = "Average",
                },
            },
        },
        Description = "Performance rule",
        Enabled = true,
        EvaluationFrequency = "PT5M",
        Location = "eastus",
        MuteActionsDuration = "PT30M",
        ResourceGroupName = "QueryResourceGroupName",
        RuleName = "perf",
        Scopes = new[]
        {
            "/subscriptions/aaf177ed-1330-a9f2-80ea-fd3d7783b147",
        },
        Severity = 4,
        SkipQueryValidation = true,
        TargetResourceTypes = new[]
        {
            "Microsoft.Compute/virtualMachines",
        },
        WindowSize = "PT10M",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.insights.ScheduledQueryRule;
import com.pulumi.azurenative.insights.ScheduledQueryRuleArgs;
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
        var scheduledQueryRule = new ScheduledQueryRule("scheduledQueryRule", ScheduledQueryRuleArgs.builder()        
            .actions(Map.ofEntries(
                Map.entry("actionGroups", "/subscriptions/1cf177ed-1330-4692-80ea-fd3d7783b147/resourcegroups/sqrapi/providers/microsoft.insights/actiongroups/myactiongroup"),
                Map.entry("customProperties", Map.ofEntries(
                    Map.entry("key11", "value11"),
                    Map.entry("key12", "value12")
                ))
            ))
            .autoMitigate(true)
            .checkWorkspaceAlertsStorageConfigured(true)
            .criteria(Map.of("allOf", Map.ofEntries(
                Map.entry("dimensions",                 
                    Map.ofEntries(
                        Map.entry("name", "ComputerIp"),
                        Map.entry("operator", "Exclude"),
                        Map.entry("values", "192.168.1.1")
                    ),
                    Map.ofEntries(
                        Map.entry("name", "OSType"),
                        Map.entry("operator", "Include"),
                        Map.entry("values", "*")
                    )),
                Map.entry("failingPeriods", Map.ofEntries(
                    Map.entry("minFailingPeriodsToAlert", 1),
                    Map.entry("numberOfEvaluationPeriods", 1)
                )),
                Map.entry("metricMeasureColumn", "% Processor Time"),
                Map.entry("operator", "GreaterThan"),
                Map.entry("query", "Perf | where ObjectName == \"Processor\""),
                Map.entry("resourceIdColumn", "resourceId"),
                Map.entry("threshold", 70),
                Map.entry("timeAggregation", "Average")
            )))
            .description("Performance rule")
            .enabled(true)
            .evaluationFrequency("PT5M")
            .location("eastus")
            .muteActionsDuration("PT30M")
            .resourceGroupName("QueryResourceGroupName")
            .ruleName("perf")
            .scopes("/subscriptions/aaf177ed-1330-a9f2-80ea-fd3d7783b147")
            .severity(4)
            .skipQueryValidation(true)
            .targetResourceTypes("Microsoft.Compute/virtualMachines")
            .windowSize("PT10M")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const scheduledQueryRule = new azure_native.insights.ScheduledQueryRule("scheduledQueryRule", {
    actions: {
        actionGroups: ["/subscriptions/1cf177ed-1330-4692-80ea-fd3d7783b147/resourcegroups/sqrapi/providers/microsoft.insights/actiongroups/myactiongroup"],
        customProperties: {
            key11: "value11",
            key12: "value12",
        },
    },
    autoMitigate: true,
    checkWorkspaceAlertsStorageConfigured: true,
    criteria: {
        allOf: [{
            dimensions: [
                {
                    name: "ComputerIp",
                    operator: "Exclude",
                    values: ["192.168.1.1"],
                },
                {
                    name: "OSType",
                    operator: "Include",
                    values: ["*"],
                },
            ],
            failingPeriods: {
                minFailingPeriodsToAlert: 1,
                numberOfEvaluationPeriods: 1,
            },
            metricMeasureColumn: "% Processor Time",
            operator: "GreaterThan",
            query: "Perf | where ObjectName == \"Processor\"",
            resourceIdColumn: "resourceId",
            threshold: 70,
            timeAggregation: "Average",
        }],
    },
    description: "Performance rule",
    enabled: true,
    evaluationFrequency: "PT5M",
    location: "eastus",
    muteActionsDuration: "PT30M",
    resourceGroupName: "QueryResourceGroupName",
    ruleName: "perf",
    scopes: ["/subscriptions/aaf177ed-1330-a9f2-80ea-fd3d7783b147"],
    severity: 4,
    skipQueryValidation: true,
    targetResourceTypes: ["Microsoft.Compute/virtualMachines"],
    windowSize: "PT10M",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

scheduled_query_rule = azure_native.insights.ScheduledQueryRule("scheduledQueryRule",
    actions=azure_native.insights.ActionsArgs(
        action_groups=["/subscriptions/1cf177ed-1330-4692-80ea-fd3d7783b147/resourcegroups/sqrapi/providers/microsoft.insights/actiongroups/myactiongroup"],
        custom_properties={
            "key11": "value11",
            "key12": "value12",
        },
    ),
    auto_mitigate=True,
    check_workspace_alerts_storage_configured=True,
    criteria=azure_native.insights.ScheduledQueryRuleCriteriaResponseArgs(
        all_of=[{
            "dimensions": [
                azure_native.insights.DimensionArgs(
                    name="ComputerIp",
                    operator="Exclude",
                    values=["192.168.1.1"],
                ),
                azure_native.insights.DimensionArgs(
                    name="OSType",
                    operator="Include",
                    values=["*"],
                ),
            ],
            "failingPeriods": azure_native.insights.ConditionFailingPeriodsArgs(
                min_failing_periods_to_alert=1,
                number_of_evaluation_periods=1,
            ),
            "metricMeasureColumn": "% Processor Time",
            "operator": "GreaterThan",
            "query": "Perf | where ObjectName == \"Processor\"",
            "resourceIdColumn": "resourceId",
            "threshold": 70,
            "timeAggregation": "Average",
        }],
    ),
    description="Performance rule",
    enabled=True,
    evaluation_frequency="PT5M",
    location="eastus",
    mute_actions_duration="PT30M",
    resource_group_name="QueryResourceGroupName",
    rule_name="perf",
    scopes=["/subscriptions/aaf177ed-1330-a9f2-80ea-fd3d7783b147"],
    severity=4,
    skip_query_validation=True,
    target_resource_types=["Microsoft.Compute/virtualMachines"],
    window_size="PT10M")

```

```yaml
resources:
  scheduledQueryRule:
    type: azure-native:insights:ScheduledQueryRule
    properties:
      actions:
        actionGroups:
          - /subscriptions/1cf177ed-1330-4692-80ea-fd3d7783b147/resourcegroups/sqrapi/providers/microsoft.insights/actiongroups/myactiongroup
        customProperties:
          key11: value11
          key12: value12
      autoMitigate: true
      checkWorkspaceAlertsStorageConfigured: true
      criteria:
        allOf:
          - dimensions:
              - name: ComputerIp
                operator: Exclude
                values:
                  - 192.168.1.1
              - name: OSType
                operator: Include
                values:
                  - '*'
            failingPeriods:
              minFailingPeriodsToAlert: 1
              numberOfEvaluationPeriods: 1
            metricMeasureColumn: '% Processor Time'
            operator: GreaterThan
            query: Perf | where ObjectName == "Processor"
            resourceIdColumn: resourceId
            threshold: 70
            timeAggregation: Average
      description: Performance rule
      enabled: true
      evaluationFrequency: PT5M
      location: eastus
      muteActionsDuration: PT30M
      resourceGroupName: QueryResourceGroupName
      ruleName: perf
      scopes:
        - /subscriptions/aaf177ed-1330-a9f2-80ea-fd3d7783b147
      severity: 4
      skipQueryValidation: true
      targetResourceTypes:
        - Microsoft.Compute/virtualMachines
      windowSize: PT10M

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:insights:ScheduledQueryRule perf /subscriptions/dd4bfc94-a096-412b-9c43-4bd13e35afbc/resourcegroups/QueryResourceGroupName/providers/microsoft.insights/scheduledqueryrules/perf 
```
