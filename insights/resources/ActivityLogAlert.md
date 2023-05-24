An Activity Log Alert rule resource.
API Version: 2020-10-01.
Previous API Version: 2020-10-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update an Activity Log Alert rule
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var activityLogAlert = new AzureNative.Insights.ActivityLogAlert("activityLogAlert", new()
    {
        Actions = new AzureNative.Insights.Inputs.ActionListArgs
        {
            ActionGroups = new[]
            {
                new AzureNative.Insights.Inputs.ActionGroupArgs
                {
                    ActionGroupId = "/subscriptions/187f412d-1758-44d9-b052-169e2564721d/resourceGroups/MyResourceGroup/providers/Microsoft.Insights/actionGroups/SampleActionGroup",
                    WebhookProperties = 
                    {
                        { "sampleWebhookProperty", "SamplePropertyValue" },
                    },
                },
            },
        },
        ActivityLogAlertName = "SampleActivityLogAlertRule",
        Condition = new AzureNative.Insights.Inputs.AlertRuleAllOfConditionArgs
        {
            AllOf = new[]
            {
                new AzureNative.Insights.Inputs.AlertRuleAnyOfOrLeafConditionArgs
                {
                    Equals = "Administrative",
                    Field = "category",
                },
                new AzureNative.Insights.Inputs.AlertRuleAnyOfOrLeafConditionArgs
                {
                    Equals = "Error",
                    Field = "level",
                },
            },
        },
        Description = "Description of sample Activity Log Alert rule.",
        Enabled = true,
        Location = "Global",
        ResourceGroupName = "MyResourceGroup",
        Scopes = new[]
        {
            "/subscriptions/187f412d-1758-44d9-b052-169e2564721d",
        },
        Tags = null,
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
		_, err := insights.NewActivityLogAlert(ctx, "activityLogAlert", &insights.ActivityLogAlertArgs{
			Actions: insights.ActionListResponse{
				ActionGroups: insights.ActionGroupTypeArray{
					&insights.ActionGroupTypeArgs{
						ActionGroupId: pulumi.String("/subscriptions/187f412d-1758-44d9-b052-169e2564721d/resourceGroups/MyResourceGroup/providers/Microsoft.Insights/actionGroups/SampleActionGroup"),
						WebhookProperties: pulumi.StringMap{
							"sampleWebhookProperty": pulumi.String("SamplePropertyValue"),
						},
					},
				},
			},
			ActivityLogAlertName: pulumi.String("SampleActivityLogAlertRule"),
			Condition: insights.AlertRuleAllOfConditionResponse{
				AllOf: insights.AlertRuleAnyOfOrLeafConditionArray{
					&insights.AlertRuleAnyOfOrLeafConditionArgs{
						Equals: pulumi.String("Administrative"),
						Field:  pulumi.String("category"),
					},
					&insights.AlertRuleAnyOfOrLeafConditionArgs{
						Equals: pulumi.String("Error"),
						Field:  pulumi.String("level"),
					},
				},
			},
			Description:       pulumi.String("Description of sample Activity Log Alert rule."),
			Enabled:           pulumi.Bool(true),
			Location:          pulumi.String("Global"),
			ResourceGroupName: pulumi.String("MyResourceGroup"),
			Scopes: pulumi.StringArray{
				pulumi.String("/subscriptions/187f412d-1758-44d9-b052-169e2564721d"),
			},
			Tags: nil,
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
import com.pulumi.azurenative.insights.ActivityLogAlert;
import com.pulumi.azurenative.insights.ActivityLogAlertArgs;
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
        var activityLogAlert = new ActivityLogAlert("activityLogAlert", ActivityLogAlertArgs.builder()        
            .actions(Map.of("actionGroups", Map.ofEntries(
                Map.entry("actionGroupId", "/subscriptions/187f412d-1758-44d9-b052-169e2564721d/resourceGroups/MyResourceGroup/providers/Microsoft.Insights/actionGroups/SampleActionGroup"),
                Map.entry("webhookProperties", Map.of("sampleWebhookProperty", "SamplePropertyValue"))
            )))
            .activityLogAlertName("SampleActivityLogAlertRule")
            .condition(Map.of("allOf",             
                Map.ofEntries(
                    Map.entry("equals", "Administrative"),
                    Map.entry("field", "category")
                ),
                Map.ofEntries(
                    Map.entry("equals", "Error"),
                    Map.entry("field", "level")
                )))
            .description("Description of sample Activity Log Alert rule.")
            .enabled(true)
            .location("Global")
            .resourceGroupName("MyResourceGroup")
            .scopes("/subscriptions/187f412d-1758-44d9-b052-169e2564721d")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const activityLogAlert = new azure_native.insights.ActivityLogAlert("activityLogAlert", {
    actions: {
        actionGroups: [{
            actionGroupId: "/subscriptions/187f412d-1758-44d9-b052-169e2564721d/resourceGroups/MyResourceGroup/providers/Microsoft.Insights/actionGroups/SampleActionGroup",
            webhookProperties: {
                sampleWebhookProperty: "SamplePropertyValue",
            },
        }],
    },
    activityLogAlertName: "SampleActivityLogAlertRule",
    condition: {
        allOf: [
            {
                equals: "Administrative",
                field: "category",
            },
            {
                equals: "Error",
                field: "level",
            },
        ],
    },
    description: "Description of sample Activity Log Alert rule.",
    enabled: true,
    location: "Global",
    resourceGroupName: "MyResourceGroup",
    scopes: ["/subscriptions/187f412d-1758-44d9-b052-169e2564721d"],
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

activity_log_alert = azure_native.insights.ActivityLogAlert("activityLogAlert",
    actions=azure_native.insights.ActionListResponseArgs(
        action_groups=[azure_native.insights.ActionGroupArgs(
            action_group_id="/subscriptions/187f412d-1758-44d9-b052-169e2564721d/resourceGroups/MyResourceGroup/providers/Microsoft.Insights/actionGroups/SampleActionGroup",
            webhook_properties={
                "sampleWebhookProperty": "SamplePropertyValue",
            },
        )],
    ),
    activity_log_alert_name="SampleActivityLogAlertRule",
    condition=azure_native.insights.AlertRuleAllOfConditionResponseArgs(
        all_of=[
            azure_native.insights.AlertRuleAnyOfOrLeafConditionArgs(
                equals="Administrative",
                field="category",
            ),
            azure_native.insights.AlertRuleAnyOfOrLeafConditionArgs(
                equals="Error",
                field="level",
            ),
        ],
    ),
    description="Description of sample Activity Log Alert rule.",
    enabled=True,
    location="Global",
    resource_group_name="MyResourceGroup",
    scopes=["/subscriptions/187f412d-1758-44d9-b052-169e2564721d"],
    tags={})

```

```yaml
resources:
  activityLogAlert:
    type: azure-native:insights:ActivityLogAlert
    properties:
      actions:
        actionGroups:
          - actionGroupId: /subscriptions/187f412d-1758-44d9-b052-169e2564721d/resourceGroups/MyResourceGroup/providers/Microsoft.Insights/actionGroups/SampleActionGroup
            webhookProperties:
              sampleWebhookProperty: SamplePropertyValue
      activityLogAlertName: SampleActivityLogAlertRule
      condition:
        allOf:
          - equals: Administrative
            field: category
          - equals: Error
            field: level
      description: Description of sample Activity Log Alert rule.
      enabled: true
      location: Global
      resourceGroupName: MyResourceGroup
      scopes:
        - /subscriptions/187f412d-1758-44d9-b052-169e2564721d
      tags: {}

```

{{% /example %}}
{{% example %}}
### Create or update an Activity Log Alert rule with 'anyOf' condition
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var activityLogAlert = new AzureNative.Insights.ActivityLogAlert("activityLogAlert", new()
    {
        Actions = new AzureNative.Insights.Inputs.ActionListArgs
        {
            ActionGroups = new[]
            {
                new AzureNative.Insights.Inputs.ActionGroupArgs
                {
                    ActionGroupId = "/subscriptions/187f412d-1758-44d9-b052-169e2564721d/resourceGroups/MyResourceGroup/providers/Microsoft.Insights/actionGroups/SampleActionGroup",
                    WebhookProperties = 
                    {
                        { "sampleWebhookProperty", "SamplePropertyValue" },
                    },
                },
            },
        },
        ActivityLogAlertName = "SampleActivityLogAlertRuleWithAnyOfCondition",
        Condition = new AzureNative.Insights.Inputs.AlertRuleAllOfConditionArgs
        {
            AllOf = new[]
            {
                new AzureNative.Insights.Inputs.AlertRuleAnyOfOrLeafConditionArgs
                {
                    Equals = "ServiceHealth",
                    Field = "category",
                },
                new AzureNative.Insights.Inputs.AlertRuleAnyOfOrLeafConditionArgs
                {
                    AnyOf = new[]
                    {
                        new AzureNative.Insights.Inputs.AlertRuleLeafConditionArgs
                        {
                            Equals = "Incident",
                            Field = "properties.incidentType",
                        },
                        new AzureNative.Insights.Inputs.AlertRuleLeafConditionArgs
                        {
                            Equals = "Maintenance",
                            Field = "properties.incidentType",
                        },
                    },
                },
            },
        },
        Description = "Description of sample Activity Log Alert rule with 'anyOf' condition.",
        Enabled = true,
        Location = "Global",
        ResourceGroupName = "MyResourceGroup",
        Scopes = new[]
        {
            "subscriptions/187f412d-1758-44d9-b052-169e2564721d",
        },
        Tags = null,
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.insights.ActivityLogAlert;
import com.pulumi.azurenative.insights.ActivityLogAlertArgs;
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
        var activityLogAlert = new ActivityLogAlert("activityLogAlert", ActivityLogAlertArgs.builder()        
            .actions(Map.of("actionGroups", Map.ofEntries(
                Map.entry("actionGroupId", "/subscriptions/187f412d-1758-44d9-b052-169e2564721d/resourceGroups/MyResourceGroup/providers/Microsoft.Insights/actionGroups/SampleActionGroup"),
                Map.entry("webhookProperties", Map.of("sampleWebhookProperty", "SamplePropertyValue"))
            )))
            .activityLogAlertName("SampleActivityLogAlertRuleWithAnyOfCondition")
            .condition(Map.of("allOf",             
                Map.ofEntries(
                    Map.entry("equals", "ServiceHealth"),
                    Map.entry("field", "category")
                ),
                Map.of("anyOf",                 
                    Map.ofEntries(
                        Map.entry("equals", "Incident"),
                        Map.entry("field", "properties.incidentType")
                    ),
                    Map.ofEntries(
                        Map.entry("equals", "Maintenance"),
                        Map.entry("field", "properties.incidentType")
                    ))))
            .description("Description of sample Activity Log Alert rule with 'anyOf' condition.")
            .enabled(true)
            .location("Global")
            .resourceGroupName("MyResourceGroup")
            .scopes("subscriptions/187f412d-1758-44d9-b052-169e2564721d")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const activityLogAlert = new azure_native.insights.ActivityLogAlert("activityLogAlert", {
    actions: {
        actionGroups: [{
            actionGroupId: "/subscriptions/187f412d-1758-44d9-b052-169e2564721d/resourceGroups/MyResourceGroup/providers/Microsoft.Insights/actionGroups/SampleActionGroup",
            webhookProperties: {
                sampleWebhookProperty: "SamplePropertyValue",
            },
        }],
    },
    activityLogAlertName: "SampleActivityLogAlertRuleWithAnyOfCondition",
    condition: {
        allOf: [
            {
                equals: "ServiceHealth",
                field: "category",
            },
            {
                anyOf: [
                    {
                        equals: "Incident",
                        field: "properties.incidentType",
                    },
                    {
                        equals: "Maintenance",
                        field: "properties.incidentType",
                    },
                ],
            },
        ],
    },
    description: "Description of sample Activity Log Alert rule with 'anyOf' condition.",
    enabled: true,
    location: "Global",
    resourceGroupName: "MyResourceGroup",
    scopes: ["subscriptions/187f412d-1758-44d9-b052-169e2564721d"],
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

activity_log_alert = azure_native.insights.ActivityLogAlert("activityLogAlert",
    actions=azure_native.insights.ActionListResponseArgs(
        action_groups=[azure_native.insights.ActionGroupArgs(
            action_group_id="/subscriptions/187f412d-1758-44d9-b052-169e2564721d/resourceGroups/MyResourceGroup/providers/Microsoft.Insights/actionGroups/SampleActionGroup",
            webhook_properties={
                "sampleWebhookProperty": "SamplePropertyValue",
            },
        )],
    ),
    activity_log_alert_name="SampleActivityLogAlertRuleWithAnyOfCondition",
    condition=azure_native.insights.AlertRuleAllOfConditionResponseArgs(
        all_of=[
            azure_native.insights.AlertRuleAnyOfOrLeafConditionArgs(
                equals="ServiceHealth",
                field="category",
            ),
            {
                "anyOf": [
                    azure_native.insights.AlertRuleLeafConditionArgs(
                        equals="Incident",
                        field="properties.incidentType",
                    ),
                    azure_native.insights.AlertRuleLeafConditionArgs(
                        equals="Maintenance",
                        field="properties.incidentType",
                    ),
                ],
            },
        ],
    ),
    description="Description of sample Activity Log Alert rule with 'anyOf' condition.",
    enabled=True,
    location="Global",
    resource_group_name="MyResourceGroup",
    scopes=["subscriptions/187f412d-1758-44d9-b052-169e2564721d"],
    tags={})

```

```yaml
resources:
  activityLogAlert:
    type: azure-native:insights:ActivityLogAlert
    properties:
      actions:
        actionGroups:
          - actionGroupId: /subscriptions/187f412d-1758-44d9-b052-169e2564721d/resourceGroups/MyResourceGroup/providers/Microsoft.Insights/actionGroups/SampleActionGroup
            webhookProperties:
              sampleWebhookProperty: SamplePropertyValue
      activityLogAlertName: SampleActivityLogAlertRuleWithAnyOfCondition
      condition:
        allOf:
          - equals: ServiceHealth
            field: category
          - anyOf:
              - equals: Incident
                field: properties.incidentType
              - equals: Maintenance
                field: properties.incidentType
      description: Description of sample Activity Log Alert rule with 'anyOf' condition.
      enabled: true
      location: Global
      resourceGroupName: MyResourceGroup
      scopes:
        - subscriptions/187f412d-1758-44d9-b052-169e2564721d
      tags: {}

```

{{% /example %}}
{{% example %}}
### Create or update an Activity Log Alert rule with 'containsAny'
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var activityLogAlert = new AzureNative.Insights.ActivityLogAlert("activityLogAlert", new()
    {
        Actions = new AzureNative.Insights.Inputs.ActionListArgs
        {
            ActionGroups = new[]
            {
                new AzureNative.Insights.Inputs.ActionGroupArgs
                {
                    ActionGroupId = "/subscriptions/187f412d-1758-44d9-b052-169e2564721d/resourceGroups/MyResourceGroup/providers/Microsoft.Insights/actionGroups/SampleActionGroup",
                    WebhookProperties = 
                    {
                        { "sampleWebhookProperty", "SamplePropertyValue" },
                    },
                },
            },
        },
        ActivityLogAlertName = "SampleActivityLogAlertRuleWithContainsAny",
        Condition = new AzureNative.Insights.Inputs.AlertRuleAllOfConditionArgs
        {
            AllOf = new[]
            {
                new AzureNative.Insights.Inputs.AlertRuleAnyOfOrLeafConditionArgs
                {
                    Equals = "ServiceHealth",
                    Field = "category",
                },
                new AzureNative.Insights.Inputs.AlertRuleAnyOfOrLeafConditionArgs
                {
                    ContainsAny = new[]
                    {
                        "North Europe",
                        "West Europe",
                    },
                    Field = "properties.impactedServices[*].ImpactedRegions[*].RegionName",
                },
            },
        },
        Description = "Description of sample Activity Log Alert rule with 'containsAny'.",
        Enabled = true,
        Location = "Global",
        ResourceGroupName = "MyResourceGroup",
        Scopes = new[]
        {
            "subscriptions/187f412d-1758-44d9-b052-169e2564721d",
        },
        Tags = null,
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
		_, err := insights.NewActivityLogAlert(ctx, "activityLogAlert", &insights.ActivityLogAlertArgs{
			Actions: insights.ActionListResponse{
				ActionGroups: insights.ActionGroupTypeArray{
					&insights.ActionGroupTypeArgs{
						ActionGroupId: pulumi.String("/subscriptions/187f412d-1758-44d9-b052-169e2564721d/resourceGroups/MyResourceGroup/providers/Microsoft.Insights/actionGroups/SampleActionGroup"),
						WebhookProperties: pulumi.StringMap{
							"sampleWebhookProperty": pulumi.String("SamplePropertyValue"),
						},
					},
				},
			},
			ActivityLogAlertName: pulumi.String("SampleActivityLogAlertRuleWithContainsAny"),
			Condition: insights.AlertRuleAllOfConditionResponse{
				AllOf: insights.AlertRuleAnyOfOrLeafConditionArray{
					&insights.AlertRuleAnyOfOrLeafConditionArgs{
						Equals: pulumi.String("ServiceHealth"),
						Field:  pulumi.String("category"),
					},
					&insights.AlertRuleAnyOfOrLeafConditionArgs{
						ContainsAny: pulumi.StringArray{
							pulumi.String("North Europe"),
							pulumi.String("West Europe"),
						},
						Field: pulumi.String("properties.impactedServices[*].ImpactedRegions[*].RegionName"),
					},
				},
			},
			Description:       pulumi.String("Description of sample Activity Log Alert rule with 'containsAny'."),
			Enabled:           pulumi.Bool(true),
			Location:          pulumi.String("Global"),
			ResourceGroupName: pulumi.String("MyResourceGroup"),
			Scopes: pulumi.StringArray{
				pulumi.String("subscriptions/187f412d-1758-44d9-b052-169e2564721d"),
			},
			Tags: nil,
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
import com.pulumi.azurenative.insights.ActivityLogAlert;
import com.pulumi.azurenative.insights.ActivityLogAlertArgs;
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
        var activityLogAlert = new ActivityLogAlert("activityLogAlert", ActivityLogAlertArgs.builder()        
            .actions(Map.of("actionGroups", Map.ofEntries(
                Map.entry("actionGroupId", "/subscriptions/187f412d-1758-44d9-b052-169e2564721d/resourceGroups/MyResourceGroup/providers/Microsoft.Insights/actionGroups/SampleActionGroup"),
                Map.entry("webhookProperties", Map.of("sampleWebhookProperty", "SamplePropertyValue"))
            )))
            .activityLogAlertName("SampleActivityLogAlertRuleWithContainsAny")
            .condition(Map.of("allOf",             
                Map.ofEntries(
                    Map.entry("equals", "ServiceHealth"),
                    Map.entry("field", "category")
                ),
                Map.ofEntries(
                    Map.entry("containsAny",                     
                        "North Europe",
                        "West Europe"),
                    Map.entry("field", "properties.impactedServices[*].ImpactedRegions[*].RegionName")
                )))
            .description("Description of sample Activity Log Alert rule with 'containsAny'.")
            .enabled(true)
            .location("Global")
            .resourceGroupName("MyResourceGroup")
            .scopes("subscriptions/187f412d-1758-44d9-b052-169e2564721d")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const activityLogAlert = new azure_native.insights.ActivityLogAlert("activityLogAlert", {
    actions: {
        actionGroups: [{
            actionGroupId: "/subscriptions/187f412d-1758-44d9-b052-169e2564721d/resourceGroups/MyResourceGroup/providers/Microsoft.Insights/actionGroups/SampleActionGroup",
            webhookProperties: {
                sampleWebhookProperty: "SamplePropertyValue",
            },
        }],
    },
    activityLogAlertName: "SampleActivityLogAlertRuleWithContainsAny",
    condition: {
        allOf: [
            {
                equals: "ServiceHealth",
                field: "category",
            },
            {
                containsAny: [
                    "North Europe",
                    "West Europe",
                ],
                field: "properties.impactedServices[*].ImpactedRegions[*].RegionName",
            },
        ],
    },
    description: "Description of sample Activity Log Alert rule with 'containsAny'.",
    enabled: true,
    location: "Global",
    resourceGroupName: "MyResourceGroup",
    scopes: ["subscriptions/187f412d-1758-44d9-b052-169e2564721d"],
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

activity_log_alert = azure_native.insights.ActivityLogAlert("activityLogAlert",
    actions=azure_native.insights.ActionListResponseArgs(
        action_groups=[azure_native.insights.ActionGroupArgs(
            action_group_id="/subscriptions/187f412d-1758-44d9-b052-169e2564721d/resourceGroups/MyResourceGroup/providers/Microsoft.Insights/actionGroups/SampleActionGroup",
            webhook_properties={
                "sampleWebhookProperty": "SamplePropertyValue",
            },
        )],
    ),
    activity_log_alert_name="SampleActivityLogAlertRuleWithContainsAny",
    condition=azure_native.insights.AlertRuleAllOfConditionResponseArgs(
        all_of=[
            azure_native.insights.AlertRuleAnyOfOrLeafConditionArgs(
                equals="ServiceHealth",
                field="category",
            ),
            azure_native.insights.AlertRuleAnyOfOrLeafConditionArgs(
                contains_any=[
                    "North Europe",
                    "West Europe",
                ],
                field="properties.impactedServices[*].ImpactedRegions[*].RegionName",
            ),
        ],
    ),
    description="Description of sample Activity Log Alert rule with 'containsAny'.",
    enabled=True,
    location="Global",
    resource_group_name="MyResourceGroup",
    scopes=["subscriptions/187f412d-1758-44d9-b052-169e2564721d"],
    tags={})

```

```yaml
resources:
  activityLogAlert:
    type: azure-native:insights:ActivityLogAlert
    properties:
      actions:
        actionGroups:
          - actionGroupId: /subscriptions/187f412d-1758-44d9-b052-169e2564721d/resourceGroups/MyResourceGroup/providers/Microsoft.Insights/actionGroups/SampleActionGroup
            webhookProperties:
              sampleWebhookProperty: SamplePropertyValue
      activityLogAlertName: SampleActivityLogAlertRuleWithContainsAny
      condition:
        allOf:
          - equals: ServiceHealth
            field: category
          - containsAny:
              - North Europe
              - West Europe
            field: properties.impactedServices[*].ImpactedRegions[*].RegionName
      description: Description of sample Activity Log Alert rule with 'containsAny'.
      enabled: true
      location: Global
      resourceGroupName: MyResourceGroup
      scopes:
        - subscriptions/187f412d-1758-44d9-b052-169e2564721d
      tags: {}

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:insights:ActivityLogAlert SampleActivityLogAlertRuleWithContainsAny /subscriptions/187f412d-1758-44d9-b052-169e2564721d/resourceGroups/MyResourceGroup/providers/microsoft.insights/activityLogAlerts/SampleActivityLogAlertRuleWithContainsAny 
```
