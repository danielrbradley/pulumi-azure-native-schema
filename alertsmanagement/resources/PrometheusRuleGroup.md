The Prometheus rule group resource.
API Version: 2023-03-01.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or Update a PrometheusRuleGroup
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var prometheusRuleGroup = new AzureNative.AlertsManagement.PrometheusRuleGroup("prometheusRuleGroup", new()
    {
        ClusterName = "myClusterName",
        Description = "This is the description of the following rule group",
        Enabled = true,
        Interval = "PT10M",
        Location = "East US",
        ResourceGroupName = "promResourceGroup",
        RuleGroupName = "myPrometheusRuleGroup",
        Rules = new[]
        {
            new AzureNative.AlertsManagement.Inputs.PrometheusRuleArgs
            {
                Expression = "histogram_quantile(0.99, sum(rate(jobs_duration_seconds_bucket{service=\"billing-processing\"}[5m])) by (job_type))",
                Labels = 
                {
                    { "team", "prod" },
                },
                Record = "job_type:billing_jobs_duration_seconds:99p5m",
            },
            new AzureNative.AlertsManagement.Inputs.PrometheusRuleArgs
            {
                Actions = new[]
                {
                    new AzureNative.AlertsManagement.Inputs.PrometheusRuleGroupActionArgs
                    {
                        ActionGroupId = "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourcegroups/myrg/providers/microsoft.insights/actiongroups/myactiongroup",
                        ActionProperties = 
                        {
                            { "key11", "value11" },
                            { "key12", "value12" },
                        },
                    },
                    new AzureNative.AlertsManagement.Inputs.PrometheusRuleGroupActionArgs
                    {
                        ActionGroupId = "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourcegroups/myrg/providers/microsoft.insights/actiongroups/myotheractiongroup",
                        ActionProperties = 
                        {
                            { "key21", "value21" },
                            { "key22", "value22" },
                        },
                    },
                },
                Alert = "Billing_Processing_Very_Slow",
                Annotations = 
                {
                    { "annotationName1", "annotationValue1" },
                },
                Enabled = true,
                Expression = "job_type:billing_jobs_duration_seconds:99p5m > 30",
                For = "PT5M",
                Labels = 
                {
                    { "team", "prod" },
                },
                ResolveConfiguration = new AzureNative.AlertsManagement.Inputs.PrometheusRuleResolveConfigurationArgs
                {
                    AutoResolved = true,
                    TimeToResolve = "PT10M",
                },
                Severity = 2,
            },
        },
        Scopes = new[]
        {
            "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/myResourceGroup/providers/microsoft.monitor/accounts/myAzureMonitorWorkspace",
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
		_, err := alertsmanagement.NewPrometheusRuleGroup(ctx, "prometheusRuleGroup", &alertsmanagement.PrometheusRuleGroupArgs{
			ClusterName:       pulumi.String("myClusterName"),
			Description:       pulumi.String("This is the description of the following rule group"),
			Enabled:           pulumi.Bool(true),
			Interval:          pulumi.String("PT10M"),
			Location:          pulumi.String("East US"),
			ResourceGroupName: pulumi.String("promResourceGroup"),
			RuleGroupName:     pulumi.String("myPrometheusRuleGroup"),
			Rules: []alertsmanagement.PrometheusRuleArgs{
				{
					Expression: pulumi.String("histogram_quantile(0.99, sum(rate(jobs_duration_seconds_bucket{service=\"billing-processing\"}[5m])) by (job_type))"),
					Labels: {
						"team": pulumi.String("prod"),
					},
					Record: pulumi.String("job_type:billing_jobs_duration_seconds:99p5m"),
				},
				{
					Actions: alertsmanagement.PrometheusRuleGroupActionArray{
						{
							ActionGroupId: pulumi.String("/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourcegroups/myrg/providers/microsoft.insights/actiongroups/myactiongroup"),
							ActionProperties: {
								"key11": pulumi.String("value11"),
								"key12": pulumi.String("value12"),
							},
						},
						{
							ActionGroupId: pulumi.String("/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourcegroups/myrg/providers/microsoft.insights/actiongroups/myotheractiongroup"),
							ActionProperties: {
								"key21": pulumi.String("value21"),
								"key22": pulumi.String("value22"),
							},
						},
					},
					Alert: pulumi.String("Billing_Processing_Very_Slow"),
					Annotations: {
						"annotationName1": pulumi.String("annotationValue1"),
					},
					Enabled:    pulumi.Bool(true),
					Expression: pulumi.String("job_type:billing_jobs_duration_seconds:99p5m > 30"),
					For:        pulumi.String("PT5M"),
					Labels: {
						"team": pulumi.String("prod"),
					},
					ResolveConfiguration: {
						AutoResolved:  pulumi.Bool(true),
						TimeToResolve: pulumi.String("PT10M"),
					},
					Severity: pulumi.Int(2),
				},
			},
			Scopes: pulumi.StringArray{
				pulumi.String("/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/myResourceGroup/providers/microsoft.monitor/accounts/myAzureMonitorWorkspace"),
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
import com.pulumi.azurenative.alertsmanagement.PrometheusRuleGroup;
import com.pulumi.azurenative.alertsmanagement.PrometheusRuleGroupArgs;
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
        var prometheusRuleGroup = new PrometheusRuleGroup("prometheusRuleGroup", PrometheusRuleGroupArgs.builder()        
            .clusterName("myClusterName")
            .description("This is the description of the following rule group")
            .enabled(true)
            .interval("PT10M")
            .location("East US")
            .resourceGroupName("promResourceGroup")
            .ruleGroupName("myPrometheusRuleGroup")
            .rules(            
                Map.ofEntries(
                    Map.entry("expression", "histogram_quantile(0.99, sum(rate(jobs_duration_seconds_bucket{service=\"billing-processing\"}[5m])) by (job_type))"),
                    Map.entry("labels", Map.of("team", "prod")),
                    Map.entry("record", "job_type:billing_jobs_duration_seconds:99p5m")
                ),
                Map.ofEntries(
                    Map.entry("actions",                     
                        Map.ofEntries(
                            Map.entry("actionGroupId", "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourcegroups/myrg/providers/microsoft.insights/actiongroups/myactiongroup"),
                            Map.entry("actionProperties", Map.ofEntries(
                                Map.entry("key11", "value11"),
                                Map.entry("key12", "value12")
                            ))
                        ),
                        Map.ofEntries(
                            Map.entry("actionGroupId", "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourcegroups/myrg/providers/microsoft.insights/actiongroups/myotheractiongroup"),
                            Map.entry("actionProperties", Map.ofEntries(
                                Map.entry("key21", "value21"),
                                Map.entry("key22", "value22")
                            ))
                        )),
                    Map.entry("alert", "Billing_Processing_Very_Slow"),
                    Map.entry("annotations", Map.of("annotationName1", "annotationValue1")),
                    Map.entry("enabled", true),
                    Map.entry("expression", "job_type:billing_jobs_duration_seconds:99p5m > 30"),
                    Map.entry("for", "PT5M"),
                    Map.entry("labels", Map.of("team", "prod")),
                    Map.entry("resolveConfiguration", Map.ofEntries(
                        Map.entry("autoResolved", true),
                        Map.entry("timeToResolve", "PT10M")
                    )),
                    Map.entry("severity", 2)
                ))
            .scopes("/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/myResourceGroup/providers/microsoft.monitor/accounts/myAzureMonitorWorkspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const prometheusRuleGroup = new azure_native.alertsmanagement.PrometheusRuleGroup("prometheusRuleGroup", {
    clusterName: "myClusterName",
    description: "This is the description of the following rule group",
    enabled: true,
    interval: "PT10M",
    location: "East US",
    resourceGroupName: "promResourceGroup",
    ruleGroupName: "myPrometheusRuleGroup",
    rules: [
        {
            expression: "histogram_quantile(0.99, sum(rate(jobs_duration_seconds_bucket{service=\"billing-processing\"}[5m])) by (job_type))",
            labels: {
                team: "prod",
            },
            record: "job_type:billing_jobs_duration_seconds:99p5m",
        },
        {
            actions: [
                {
                    actionGroupId: "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourcegroups/myrg/providers/microsoft.insights/actiongroups/myactiongroup",
                    actionProperties: {
                        key11: "value11",
                        key12: "value12",
                    },
                },
                {
                    actionGroupId: "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourcegroups/myrg/providers/microsoft.insights/actiongroups/myotheractiongroup",
                    actionProperties: {
                        key21: "value21",
                        key22: "value22",
                    },
                },
            ],
            alert: "Billing_Processing_Very_Slow",
            annotations: {
                annotationName1: "annotationValue1",
            },
            enabled: true,
            expression: "job_type:billing_jobs_duration_seconds:99p5m > 30",
            "for": "PT5M",
            labels: {
                team: "prod",
            },
            resolveConfiguration: {
                autoResolved: true,
                timeToResolve: "PT10M",
            },
            severity: 2,
        },
    ],
    scopes: ["/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/myResourceGroup/providers/microsoft.monitor/accounts/myAzureMonitorWorkspace"],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

prometheus_rule_group = azure_native.alertsmanagement.PrometheusRuleGroup("prometheusRuleGroup",
    cluster_name="myClusterName",
    description="This is the description of the following rule group",
    enabled=True,
    interval="PT10M",
    location="East US",
    resource_group_name="promResourceGroup",
    rule_group_name="myPrometheusRuleGroup",
    rules=[
        azure_native.alertsmanagement.PrometheusRuleArgs(
            expression="histogram_quantile(0.99, sum(rate(jobs_duration_seconds_bucket{service=\"billing-processing\"}[5m])) by (job_type))",
            labels={
                "team": "prod",
            },
            record="job_type:billing_jobs_duration_seconds:99p5m",
        ),
        {
            "actions": [
                azure_native.alertsmanagement.PrometheusRuleGroupActionArgs(
                    action_group_id="/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourcegroups/myrg/providers/microsoft.insights/actiongroups/myactiongroup",
                    action_properties={
                        "key11": "value11",
                        "key12": "value12",
                    },
                ),
                azure_native.alertsmanagement.PrometheusRuleGroupActionArgs(
                    action_group_id="/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourcegroups/myrg/providers/microsoft.insights/actiongroups/myotheractiongroup",
                    action_properties={
                        "key21": "value21",
                        "key22": "value22",
                    },
                ),
            ],
            "alert": "Billing_Processing_Very_Slow",
            "annotations": {
                "annotationName1": "annotationValue1",
            },
            "enabled": True,
            "expression": "job_type:billing_jobs_duration_seconds:99p5m > 30",
            "for": "PT5M",
            "labels": {
                "team": "prod",
            },
            "resolveConfiguration": azure_native.alertsmanagement.PrometheusRuleResolveConfigurationArgs(
                auto_resolved=True,
                time_to_resolve="PT10M",
            ),
            "severity": 2,
        },
    ],
    scopes=["/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/myResourceGroup/providers/microsoft.monitor/accounts/myAzureMonitorWorkspace"])

```

```yaml
resources:
  prometheusRuleGroup:
    type: azure-native:alertsmanagement:PrometheusRuleGroup
    properties:
      clusterName: myClusterName
      description: This is the description of the following rule group
      enabled: true
      interval: PT10M
      location: East US
      resourceGroupName: promResourceGroup
      ruleGroupName: myPrometheusRuleGroup
      rules:
        - expression: histogram_quantile(0.99, sum(rate(jobs_duration_seconds_bucket{service="billing-processing"}[5m])) by (job_type))
          labels:
            team: prod
          record: job_type:billing_jobs_duration_seconds:99p5m
        - actions:
            - actionGroupId: /subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourcegroups/myrg/providers/microsoft.insights/actiongroups/myactiongroup
              actionProperties:
                key11: value11
                key12: value12
            - actionGroupId: /subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourcegroups/myrg/providers/microsoft.insights/actiongroups/myotheractiongroup
              actionProperties:
                key21: value21
                key22: value22
          alert: Billing_Processing_Very_Slow
          annotations:
            annotationName1: annotationValue1
          enabled: true
          expression: job_type:billing_jobs_duration_seconds:99p5m > 30
          for: PT5M
          labels:
            team: prod
          resolveConfiguration:
            autoResolved: true
            timeToResolve: PT10M
          severity: 2
      scopes:
        - /subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/myResourceGroup/providers/microsoft.monitor/accounts/myAzureMonitorWorkspace

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:alertsmanagement:PrometheusRuleGroup myresource1 /subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/promResourceGroup/providers/Microsoft.AlertsManagement/prometheusRuleGroups/myPrometheusRuleGroup 
```
