Definition of ARM tracked top level resource.
API Version: 2022-06-01.
Previous API Version: 2019-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update data collection rule
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var dataCollectionRule = new AzureNative.Insights.DataCollectionRule("dataCollectionRule", new()
    {
        DataCollectionRuleName = "myCollectionRule",
        DataFlows = new[]
        {
            new AzureNative.Insights.Inputs.DataFlowArgs
            {
                Destinations = new[]
                {
                    "centralWorkspace",
                },
                Streams = new[]
                {
                    "Microsoft-Perf",
                    "Microsoft-Syslog",
                    "Microsoft-WindowsEvent",
                },
            },
        },
        DataSources = new AzureNative.Insights.Inputs.DataCollectionRuleDataSourcesArgs
        {
            PerformanceCounters = new[]
            {
                new AzureNative.Insights.Inputs.PerfCounterDataSourceArgs
                {
                    CounterSpecifiers = new[]
                    {
                        "\\Processor(_Total)\\% Processor Time",
                        "\\Memory\\Committed Bytes",
                        "\\LogicalDisk(_Total)\\Free Megabytes",
                        "\\PhysicalDisk(_Total)\\Avg. Disk Queue Length",
                    },
                    Name = "cloudTeamCoreCounters",
                    SamplingFrequencyInSeconds = 15,
                    Streams = new[]
                    {
                        "Microsoft-Perf",
                    },
                },
                new AzureNative.Insights.Inputs.PerfCounterDataSourceArgs
                {
                    CounterSpecifiers = new[]
                    {
                        "\\Process(_Total)\\Thread Count",
                    },
                    Name = "appTeamExtraCounters",
                    SamplingFrequencyInSeconds = 30,
                    Streams = new[]
                    {
                        "Microsoft-Perf",
                    },
                },
            },
            Syslog = new[]
            {
                new AzureNative.Insights.Inputs.SyslogDataSourceArgs
                {
                    FacilityNames = new[]
                    {
                        "cron",
                    },
                    LogLevels = new[]
                    {
                        "Debug",
                        "Critical",
                        "Emergency",
                    },
                    Name = "cronSyslog",
                    Streams = new[]
                    {
                        "Microsoft-Syslog",
                    },
                },
                new AzureNative.Insights.Inputs.SyslogDataSourceArgs
                {
                    FacilityNames = new[]
                    {
                        "syslog",
                    },
                    LogLevels = new[]
                    {
                        "Alert",
                        "Critical",
                        "Emergency",
                    },
                    Name = "syslogBase",
                    Streams = new[]
                    {
                        "Microsoft-Syslog",
                    },
                },
            },
            WindowsEventLogs = new[]
            {
                new AzureNative.Insights.Inputs.WindowsEventLogDataSourceArgs
                {
                    Name = "cloudSecurityTeamEvents",
                    Streams = new[]
                    {
                        "Microsoft-WindowsEvent",
                    },
                    XPathQueries = new[]
                    {
                        "Security!",
                    },
                },
                new AzureNative.Insights.Inputs.WindowsEventLogDataSourceArgs
                {
                    Name = "appTeam1AppEvents",
                    Streams = new[]
                    {
                        "Microsoft-WindowsEvent",
                    },
                    XPathQueries = new[]
                    {
                        "System![System[(Level = 1 or Level = 2 or Level = 3)]]",
                        "Application!*[System[(Level = 1 or Level = 2 or Level = 3)]]",
                    },
                },
            },
        },
        Destinations = new AzureNative.Insights.Inputs.DataCollectionRuleDestinationsArgs
        {
            LogAnalytics = new[]
            {
                new AzureNative.Insights.Inputs.LogAnalyticsDestinationArgs
                {
                    Name = "centralWorkspace",
                    WorkspaceResourceId = "/subscriptions/703362b3-f278-4e4b-9179-c76eaf41ffc2/resourceGroups/myResourceGroup/providers/Microsoft.OperationalInsights/workspaces/centralTeamWorkspace",
                },
            },
        },
        Location = "eastus",
        ResourceGroupName = "myResourceGroup",
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
		_, err := insights.NewDataCollectionRule(ctx, "dataCollectionRule", &insights.DataCollectionRuleArgs{
			DataCollectionRuleName: pulumi.String("myCollectionRule"),
			DataFlows: []insights.DataFlowArgs{
				{
					Destinations: pulumi.StringArray{
						pulumi.String("centralWorkspace"),
					},
					Streams: pulumi.StringArray{
						pulumi.String("Microsoft-Perf"),
						pulumi.String("Microsoft-Syslog"),
						pulumi.String("Microsoft-WindowsEvent"),
					},
				},
			},
			DataSources: insights.DataCollectionRuleResponseDataSources{
				PerformanceCounters: insights.PerfCounterDataSourceArray{
					&insights.PerfCounterDataSourceArgs{
						CounterSpecifiers: pulumi.StringArray{
							pulumi.String("\\Processor(_Total)\\% Processor Time"),
							pulumi.String("\\Memory\\Committed Bytes"),
							pulumi.String("\\LogicalDisk(_Total)\\Free Megabytes"),
							pulumi.String("\\PhysicalDisk(_Total)\\Avg. Disk Queue Length"),
						},
						Name:                       pulumi.String("cloudTeamCoreCounters"),
						SamplingFrequencyInSeconds: pulumi.Int(15),
						Streams: pulumi.StringArray{
							pulumi.String("Microsoft-Perf"),
						},
					},
					&insights.PerfCounterDataSourceArgs{
						CounterSpecifiers: pulumi.StringArray{
							pulumi.String("\\Process(_Total)\\Thread Count"),
						},
						Name:                       pulumi.String("appTeamExtraCounters"),
						SamplingFrequencyInSeconds: pulumi.Int(30),
						Streams: pulumi.StringArray{
							pulumi.String("Microsoft-Perf"),
						},
					},
				},
				Syslog: insights.SyslogDataSourceArray{
					&insights.SyslogDataSourceArgs{
						FacilityNames: pulumi.StringArray{
							pulumi.String("cron"),
						},
						LogLevels: pulumi.StringArray{
							pulumi.String("Debug"),
							pulumi.String("Critical"),
							pulumi.String("Emergency"),
						},
						Name: pulumi.String("cronSyslog"),
						Streams: pulumi.StringArray{
							pulumi.String("Microsoft-Syslog"),
						},
					},
					&insights.SyslogDataSourceArgs{
						FacilityNames: pulumi.StringArray{
							pulumi.String("syslog"),
						},
						LogLevels: pulumi.StringArray{
							pulumi.String("Alert"),
							pulumi.String("Critical"),
							pulumi.String("Emergency"),
						},
						Name: pulumi.String("syslogBase"),
						Streams: pulumi.StringArray{
							pulumi.String("Microsoft-Syslog"),
						},
					},
				},
				WindowsEventLogs: insights.WindowsEventLogDataSourceArray{
					&insights.WindowsEventLogDataSourceArgs{
						Name: pulumi.String("cloudSecurityTeamEvents"),
						Streams: pulumi.StringArray{
							pulumi.String("Microsoft-WindowsEvent"),
						},
						XPathQueries: pulumi.StringArray{
							pulumi.String("Security!"),
						},
					},
					&insights.WindowsEventLogDataSourceArgs{
						Name: pulumi.String("appTeam1AppEvents"),
						Streams: pulumi.StringArray{
							pulumi.String("Microsoft-WindowsEvent"),
						},
						XPathQueries: pulumi.StringArray{
							pulumi.String("System![System[(Level = 1 or Level = 2 or Level = 3)]]"),
							pulumi.String("Application!*[System[(Level = 1 or Level = 2 or Level = 3)]]"),
						},
					},
				},
			},
			Destinations: insights.DataCollectionRuleResponseDestinations{
				LogAnalytics: insights.LogAnalyticsDestinationArray{
					&insights.LogAnalyticsDestinationArgs{
						Name:                pulumi.String("centralWorkspace"),
						WorkspaceResourceId: pulumi.String("/subscriptions/703362b3-f278-4e4b-9179-c76eaf41ffc2/resourceGroups/myResourceGroup/providers/Microsoft.OperationalInsights/workspaces/centralTeamWorkspace"),
					},
				},
			},
			Location:          pulumi.String("eastus"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
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
import com.pulumi.azurenative.insights.DataCollectionRule;
import com.pulumi.azurenative.insights.DataCollectionRuleArgs;
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
        var dataCollectionRule = new DataCollectionRule("dataCollectionRule", DataCollectionRuleArgs.builder()        
            .dataCollectionRuleName("myCollectionRule")
            .dataFlows(Map.ofEntries(
                Map.entry("destinations", "centralWorkspace"),
                Map.entry("streams",                 
                    "Microsoft-Perf",
                    "Microsoft-Syslog",
                    "Microsoft-WindowsEvent")
            ))
            .dataSources(Map.ofEntries(
                Map.entry("performanceCounters",                 
                    Map.ofEntries(
                        Map.entry("counterSpecifiers",                         
                            "\\Processor(_Total)\\% Processor Time",
                            "\\Memory\\Committed Bytes",
                            "\\LogicalDisk(_Total)\\Free Megabytes",
                            "\\PhysicalDisk(_Total)\\Avg. Disk Queue Length"),
                        Map.entry("name", "cloudTeamCoreCounters"),
                        Map.entry("samplingFrequencyInSeconds", 15),
                        Map.entry("streams", "Microsoft-Perf")
                    ),
                    Map.ofEntries(
                        Map.entry("counterSpecifiers", "\\Process(_Total)\\Thread Count"),
                        Map.entry("name", "appTeamExtraCounters"),
                        Map.entry("samplingFrequencyInSeconds", 30),
                        Map.entry("streams", "Microsoft-Perf")
                    )),
                Map.entry("syslog",                 
                    Map.ofEntries(
                        Map.entry("facilityNames", "cron"),
                        Map.entry("logLevels",                         
                            "Debug",
                            "Critical",
                            "Emergency"),
                        Map.entry("name", "cronSyslog"),
                        Map.entry("streams", "Microsoft-Syslog")
                    ),
                    Map.ofEntries(
                        Map.entry("facilityNames", "syslog"),
                        Map.entry("logLevels",                         
                            "Alert",
                            "Critical",
                            "Emergency"),
                        Map.entry("name", "syslogBase"),
                        Map.entry("streams", "Microsoft-Syslog")
                    )),
                Map.entry("windowsEventLogs",                 
                    Map.ofEntries(
                        Map.entry("name", "cloudSecurityTeamEvents"),
                        Map.entry("streams", "Microsoft-WindowsEvent"),
                        Map.entry("xPathQueries", "Security!")
                    ),
                    Map.ofEntries(
                        Map.entry("name", "appTeam1AppEvents"),
                        Map.entry("streams", "Microsoft-WindowsEvent"),
                        Map.entry("xPathQueries",                         
                            "System![System[(Level = 1 or Level = 2 or Level = 3)]]",
                            "Application!*[System[(Level = 1 or Level = 2 or Level = 3)]]")
                    ))
            ))
            .destinations(Map.of("logAnalytics", Map.ofEntries(
                Map.entry("name", "centralWorkspace"),
                Map.entry("workspaceResourceId", "/subscriptions/703362b3-f278-4e4b-9179-c76eaf41ffc2/resourceGroups/myResourceGroup/providers/Microsoft.OperationalInsights/workspaces/centralTeamWorkspace")
            )))
            .location("eastus")
            .resourceGroupName("myResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const dataCollectionRule = new azure_native.insights.DataCollectionRule("dataCollectionRule", {
    dataCollectionRuleName: "myCollectionRule",
    dataFlows: [{
        destinations: ["centralWorkspace"],
        streams: [
            "Microsoft-Perf",
            "Microsoft-Syslog",
            "Microsoft-WindowsEvent",
        ],
    }],
    dataSources: {
        performanceCounters: [
            {
                counterSpecifiers: [
                    "\\Processor(_Total)\\% Processor Time",
                    "\\Memory\\Committed Bytes",
                    "\\LogicalDisk(_Total)\\Free Megabytes",
                    "\\PhysicalDisk(_Total)\\Avg. Disk Queue Length",
                ],
                name: "cloudTeamCoreCounters",
                samplingFrequencyInSeconds: 15,
                streams: ["Microsoft-Perf"],
            },
            {
                counterSpecifiers: ["\\Process(_Total)\\Thread Count"],
                name: "appTeamExtraCounters",
                samplingFrequencyInSeconds: 30,
                streams: ["Microsoft-Perf"],
            },
        ],
        syslog: [
            {
                facilityNames: ["cron"],
                logLevels: [
                    "Debug",
                    "Critical",
                    "Emergency",
                ],
                name: "cronSyslog",
                streams: ["Microsoft-Syslog"],
            },
            {
                facilityNames: ["syslog"],
                logLevels: [
                    "Alert",
                    "Critical",
                    "Emergency",
                ],
                name: "syslogBase",
                streams: ["Microsoft-Syslog"],
            },
        ],
        windowsEventLogs: [
            {
                name: "cloudSecurityTeamEvents",
                streams: ["Microsoft-WindowsEvent"],
                xPathQueries: ["Security!"],
            },
            {
                name: "appTeam1AppEvents",
                streams: ["Microsoft-WindowsEvent"],
                xPathQueries: [
                    "System![System[(Level = 1 or Level = 2 or Level = 3)]]",
                    "Application!*[System[(Level = 1 or Level = 2 or Level = 3)]]",
                ],
            },
        ],
    },
    destinations: {
        logAnalytics: [{
            name: "centralWorkspace",
            workspaceResourceId: "/subscriptions/703362b3-f278-4e4b-9179-c76eaf41ffc2/resourceGroups/myResourceGroup/providers/Microsoft.OperationalInsights/workspaces/centralTeamWorkspace",
        }],
    },
    location: "eastus",
    resourceGroupName: "myResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

data_collection_rule = azure_native.insights.DataCollectionRule("dataCollectionRule",
    data_collection_rule_name="myCollectionRule",
    data_flows=[azure_native.insights.DataFlowArgs(
        destinations=["centralWorkspace"],
        streams=[
            "Microsoft-Perf",
            "Microsoft-Syslog",
            "Microsoft-WindowsEvent",
        ],
    )],
    data_sources=azure_native.insights.DataCollectionRuleResponseDataSourcesArgs(
        performance_counters=[
            azure_native.insights.PerfCounterDataSourceArgs(
                counter_specifiers=[
                    "\\Processor(_Total)\\% Processor Time",
                    "\\Memory\\Committed Bytes",
                    "\\LogicalDisk(_Total)\\Free Megabytes",
                    "\\PhysicalDisk(_Total)\\Avg. Disk Queue Length",
                ],
                name="cloudTeamCoreCounters",
                sampling_frequency_in_seconds=15,
                streams=["Microsoft-Perf"],
            ),
            azure_native.insights.PerfCounterDataSourceArgs(
                counter_specifiers=["\\Process(_Total)\\Thread Count"],
                name="appTeamExtraCounters",
                sampling_frequency_in_seconds=30,
                streams=["Microsoft-Perf"],
            ),
        ],
        syslog=[
            azure_native.insights.SyslogDataSourceArgs(
                facility_names=["cron"],
                log_levels=[
                    "Debug",
                    "Critical",
                    "Emergency",
                ],
                name="cronSyslog",
                streams=["Microsoft-Syslog"],
            ),
            azure_native.insights.SyslogDataSourceArgs(
                facility_names=["syslog"],
                log_levels=[
                    "Alert",
                    "Critical",
                    "Emergency",
                ],
                name="syslogBase",
                streams=["Microsoft-Syslog"],
            ),
        ],
        windows_event_logs=[
            azure_native.insights.WindowsEventLogDataSourceArgs(
                name="cloudSecurityTeamEvents",
                streams=["Microsoft-WindowsEvent"],
                x_path_queries=["Security!"],
            ),
            azure_native.insights.WindowsEventLogDataSourceArgs(
                name="appTeam1AppEvents",
                streams=["Microsoft-WindowsEvent"],
                x_path_queries=[
                    "System![System[(Level = 1 or Level = 2 or Level = 3)]]",
                    "Application!*[System[(Level = 1 or Level = 2 or Level = 3)]]",
                ],
            ),
        ],
    ),
    destinations=azure_native.insights.DataCollectionRuleResponseDestinationsArgs(
        log_analytics=[azure_native.insights.LogAnalyticsDestinationArgs(
            name="centralWorkspace",
            workspace_resource_id="/subscriptions/703362b3-f278-4e4b-9179-c76eaf41ffc2/resourceGroups/myResourceGroup/providers/Microsoft.OperationalInsights/workspaces/centralTeamWorkspace",
        )],
    ),
    location="eastus",
    resource_group_name="myResourceGroup")

```

```yaml
resources:
  dataCollectionRule:
    type: azure-native:insights:DataCollectionRule
    properties:
      dataCollectionRuleName: myCollectionRule
      dataFlows:
        - destinations:
            - centralWorkspace
          streams:
            - Microsoft-Perf
            - Microsoft-Syslog
            - Microsoft-WindowsEvent
      dataSources:
        performanceCounters:
          - counterSpecifiers:
              - \Processor(_Total)\% Processor Time
              - \Memory\Committed Bytes
              - \LogicalDisk(_Total)\Free Megabytes
              - \PhysicalDisk(_Total)\Avg. Disk Queue Length
            name: cloudTeamCoreCounters
            samplingFrequencyInSeconds: 15
            streams:
              - Microsoft-Perf
          - counterSpecifiers:
              - \Process(_Total)\Thread Count
            name: appTeamExtraCounters
            samplingFrequencyInSeconds: 30
            streams:
              - Microsoft-Perf
        syslog:
          - facilityNames:
              - cron
            logLevels:
              - Debug
              - Critical
              - Emergency
            name: cronSyslog
            streams:
              - Microsoft-Syslog
          - facilityNames:
              - syslog
            logLevels:
              - Alert
              - Critical
              - Emergency
            name: syslogBase
            streams:
              - Microsoft-Syslog
        windowsEventLogs:
          - name: cloudSecurityTeamEvents
            streams:
              - Microsoft-WindowsEvent
            xPathQueries:
              - Security!
          - name: appTeam1AppEvents
            streams:
              - Microsoft-WindowsEvent
            xPathQueries:
              - System![System[(Level = 1 or Level = 2 or Level = 3)]]
              - Application!*[System[(Level = 1 or Level = 2 or Level = 3)]]
      destinations:
        logAnalytics:
          - name: centralWorkspace
            workspaceResourceId: /subscriptions/703362b3-f278-4e4b-9179-c76eaf41ffc2/resourceGroups/myResourceGroup/providers/Microsoft.OperationalInsights/workspaces/centralTeamWorkspace
      location: eastus
      resourceGroupName: myResourceGroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:insights:DataCollectionRule myCollectionRule /subscriptions/703362b3-f278-4e4b-9179-c76eaf41ffc2/resourceGroups/myResourceGroup/providers/Microsoft.Insights/dataCollectionRules/myCollectionRule 
```
