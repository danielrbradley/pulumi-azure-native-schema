Represents Anomaly Security ML Analytics Settings
API Version: 2023-02-01.
Previous API Version: 2022-05-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Creates or updates a Anomaly Security ML Analytics Settings.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var anomalySecurityMLAnalyticsSettings = new AzureNative.SecurityInsights.AnomalySecurityMLAnalyticsSettings("anomalySecurityMLAnalyticsSettings", new()
    {
        AnomalySettingsVersion = 0,
        AnomalyVersion = "1.0.5",
        CustomizableObservations = 
        {
            { "multiSelectObservations", null },
            { "prioritizeExcludeObservations", null },
            { "singleSelectObservations", new[]
            {
                
                {
                    { "description", "Select device vendor of network connection logs from CommonSecurityLog" },
                    { "name", "Device vendor" },
                    { "rerun", "RerunAlways" },
                    { "sequenceNumber", 1 },
                    { "supportedValues", new[]
                    {
                        "Palo Alto Networks",
                        "Fortinet",
                        "Check Point",
                    } },
                    { "supportedValuesKql", null },
                    { "value", new[]
                    {
                        "Palo Alto Networks",
                    } },
                    { "valuesKql", null },
                },
            } },
            { "singleValueObservations", null },
            { "thresholdObservations", new[]
            {
                
                {
                    { "description", "Suppress anomalies when daily data transfered (in MB) per hour is less than the chosen value" },
                    { "maximum", "100" },
                    { "minimum", "1" },
                    { "name", "Daily data transfer threshold in MB" },
                    { "rerun", "RerunAlways" },
                    { "sequenceNumber", 1 },
                    { "value", "25" },
                },
                
                {
                    { "description", "Triggers anomalies when number of standard deviations is greater than the chosen value" },
                    { "maximum", "10" },
                    { "minimum", "2" },
                    { "name", "Number of standard deviations" },
                    { "rerun", "RerunAlways" },
                    { "sequenceNumber", 2 },
                    { "value", "3" },
                },
            } },
        },
        Description = "When account logs from a source region that has rarely been logged in from during the last 14 days, an anomaly is triggered.",
        DisplayName = "Login from unusual region",
        Enabled = true,
        Frequency = "PT1H",
        IsDefaultSettings = true,
        Kind = "Anomaly",
        RequiredDataConnectors = new[]
        {
            new AzureNative.SecurityInsights.Inputs.SecurityMLAnalyticsSettingsDataSourceArgs
            {
                ConnectorId = "AWS",
                DataTypes = new[]
                {
                    "AWSCloudTrail",
                },
            },
        },
        ResourceGroupName = "myRg",
        SettingsDefinitionId = "f209187f-1d17-4431-94af-c141bf5f23db",
        SettingsResourceName = "f209187f-1d17-4431-94af-c141bf5f23db",
        SettingsStatus = "Production",
        Tactics = new[]
        {
            "Exfiltration",
            "CommandAndControl",
        },
        Techniques = new[]
        {
            "T1037",
            "T1021",
        },
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
		_, err := securityinsights.NewAnomalySecurityMLAnalyticsSettings(ctx, "anomalySecurityMLAnalyticsSettings", &securityinsights.AnomalySecurityMLAnalyticsSettingsArgs{
			AnomalySettingsVersion: pulumi.Int(0),
			AnomalyVersion:         pulumi.String("1.0.5"),
			CustomizableObservations: pulumi.Any{
				MultiSelectObservations:       nil,
				PrioritizeExcludeObservations: nil,
				SingleSelectObservations: []map[string]interface{}{
					map[string]interface{}{
						"description":    "Select device vendor of network connection logs from CommonSecurityLog",
						"name":           "Device vendor",
						"rerun":          "RerunAlways",
						"sequenceNumber": 1,
						"supportedValues": []string{
							"Palo Alto Networks",
							"Fortinet",
							"Check Point",
						},
						"supportedValuesKql": nil,
						"value": []string{
							"Palo Alto Networks",
						},
						"valuesKql": nil,
					},
				},
				SingleValueObservations: nil,
				ThresholdObservations: []interface{}{
					map[string]interface{}{
						"description":    "Suppress anomalies when daily data transfered (in MB) per hour is less than the chosen value",
						"maximum":        "100",
						"minimum":        "1",
						"name":           "Daily data transfer threshold in MB",
						"rerun":          "RerunAlways",
						"sequenceNumber": 1,
						"value":          "25",
					},
					map[string]interface{}{
						"description":    "Triggers anomalies when number of standard deviations is greater than the chosen value",
						"maximum":        "10",
						"minimum":        "2",
						"name":           "Number of standard deviations",
						"rerun":          "RerunAlways",
						"sequenceNumber": 2,
						"value":          "3",
					},
				},
			},
			Description:       pulumi.String("When account logs from a source region that has rarely been logged in from during the last 14 days, an anomaly is triggered."),
			DisplayName:       pulumi.String("Login from unusual region"),
			Enabled:           pulumi.Bool(true),
			Frequency:         pulumi.String("PT1H"),
			IsDefaultSettings: pulumi.Bool(true),
			Kind:              pulumi.String("Anomaly"),
			RequiredDataConnectors: []securityinsights.SecurityMLAnalyticsSettingsDataSourceArgs{
				{
					ConnectorId: pulumi.String("AWS"),
					DataTypes: pulumi.StringArray{
						pulumi.String("AWSCloudTrail"),
					},
				},
			},
			ResourceGroupName:    pulumi.String("myRg"),
			SettingsDefinitionId: pulumi.String("f209187f-1d17-4431-94af-c141bf5f23db"),
			SettingsResourceName: pulumi.String("f209187f-1d17-4431-94af-c141bf5f23db"),
			SettingsStatus:       pulumi.String("Production"),
			Tactics: pulumi.StringArray{
				pulumi.String("Exfiltration"),
				pulumi.String("CommandAndControl"),
			},
			Techniques: pulumi.StringArray{
				pulumi.String("T1037"),
				pulumi.String("T1021"),
			},
			WorkspaceName: pulumi.String("myWorkspace"),
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
import com.pulumi.azurenative.securityinsights.AnomalySecurityMLAnalyticsSettings;
import com.pulumi.azurenative.securityinsights.AnomalySecurityMLAnalyticsSettingsArgs;
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
        var anomalySecurityMLAnalyticsSettings = new AnomalySecurityMLAnalyticsSettings("anomalySecurityMLAnalyticsSettings", AnomalySecurityMLAnalyticsSettingsArgs.builder()        
            .anomalySettingsVersion(0)
            .anomalyVersion("1.0.5")
            .customizableObservations(Map.ofEntries(
                Map.entry("multiSelectObservations", null),
                Map.entry("prioritizeExcludeObservations", null),
                Map.entry("singleSelectObservations", Map.ofEntries(
                    Map.entry("description", "Select device vendor of network connection logs from CommonSecurityLog"),
                    Map.entry("name", "Device vendor"),
                    Map.entry("rerun", "RerunAlways"),
                    Map.entry("sequenceNumber", 1),
                    Map.entry("supportedValues",                     
                        "Palo Alto Networks",
                        "Fortinet",
                        "Check Point"),
                    Map.entry("supportedValuesKql", null),
                    Map.entry("value", "Palo Alto Networks"),
                    Map.entry("valuesKql", null)
                )),
                Map.entry("singleValueObservations", null),
                Map.entry("thresholdObservations",                 
                    Map.ofEntries(
                        Map.entry("description", "Suppress anomalies when daily data transfered (in MB) per hour is less than the chosen value"),
                        Map.entry("maximum", "100"),
                        Map.entry("minimum", "1"),
                        Map.entry("name", "Daily data transfer threshold in MB"),
                        Map.entry("rerun", "RerunAlways"),
                        Map.entry("sequenceNumber", 1),
                        Map.entry("value", "25")
                    ),
                    Map.ofEntries(
                        Map.entry("description", "Triggers anomalies when number of standard deviations is greater than the chosen value"),
                        Map.entry("maximum", "10"),
                        Map.entry("minimum", "2"),
                        Map.entry("name", "Number of standard deviations"),
                        Map.entry("rerun", "RerunAlways"),
                        Map.entry("sequenceNumber", 2),
                        Map.entry("value", "3")
                    ))
            ))
            .description("When account logs from a source region that has rarely been logged in from during the last 14 days, an anomaly is triggered.")
            .displayName("Login from unusual region")
            .enabled(true)
            .frequency("PT1H")
            .isDefaultSettings(true)
            .kind("Anomaly")
            .requiredDataConnectors(Map.ofEntries(
                Map.entry("connectorId", "AWS"),
                Map.entry("dataTypes", "AWSCloudTrail")
            ))
            .resourceGroupName("myRg")
            .settingsDefinitionId("f209187f-1d17-4431-94af-c141bf5f23db")
            .settingsResourceName("f209187f-1d17-4431-94af-c141bf5f23db")
            .settingsStatus("Production")
            .tactics(            
                "Exfiltration",
                "CommandAndControl")
            .techniques(            
                "T1037",
                "T1021")
            .workspaceName("myWorkspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const anomalySecurityMLAnalyticsSettings = new azure_native.securityinsights.AnomalySecurityMLAnalyticsSettings("anomalySecurityMLAnalyticsSettings", {
    anomalySettingsVersion: 0,
    anomalyVersion: "1.0.5",
    customizableObservations: {
        multiSelectObservations: undefined,
        prioritizeExcludeObservations: undefined,
        singleSelectObservations: [{
            description: "Select device vendor of network connection logs from CommonSecurityLog",
            name: "Device vendor",
            rerun: "RerunAlways",
            sequenceNumber: 1,
            supportedValues: [
                "Palo Alto Networks",
                "Fortinet",
                "Check Point",
            ],
            supportedValuesKql: undefined,
            value: ["Palo Alto Networks"],
            valuesKql: undefined,
        }],
        singleValueObservations: undefined,
        thresholdObservations: [
            {
                description: "Suppress anomalies when daily data transfered (in MB) per hour is less than the chosen value",
                maximum: "100",
                minimum: "1",
                name: "Daily data transfer threshold in MB",
                rerun: "RerunAlways",
                sequenceNumber: 1,
                value: "25",
            },
            {
                description: "Triggers anomalies when number of standard deviations is greater than the chosen value",
                maximum: "10",
                minimum: "2",
                name: "Number of standard deviations",
                rerun: "RerunAlways",
                sequenceNumber: 2,
                value: "3",
            },
        ],
    },
    description: "When account logs from a source region that has rarely been logged in from during the last 14 days, an anomaly is triggered.",
    displayName: "Login from unusual region",
    enabled: true,
    frequency: "PT1H",
    isDefaultSettings: true,
    kind: "Anomaly",
    requiredDataConnectors: [{
        connectorId: "AWS",
        dataTypes: ["AWSCloudTrail"],
    }],
    resourceGroupName: "myRg",
    settingsDefinitionId: "f209187f-1d17-4431-94af-c141bf5f23db",
    settingsResourceName: "f209187f-1d17-4431-94af-c141bf5f23db",
    settingsStatus: "Production",
    tactics: [
        "Exfiltration",
        "CommandAndControl",
    ],
    techniques: [
        "T1037",
        "T1021",
    ],
    workspaceName: "myWorkspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

anomaly_security_ml_analytics_settings = azure_native.securityinsights.AnomalySecurityMLAnalyticsSettings("anomalySecurityMLAnalyticsSettings",
    anomaly_settings_version=0,
    anomaly_version="1.0.5",
    customizable_observations={
        "multiSelectObservations": None,
        "prioritizeExcludeObservations": None,
        "singleSelectObservations": [{
            "description": "Select device vendor of network connection logs from CommonSecurityLog",
            "name": "Device vendor",
            "rerun": "RerunAlways",
            "sequenceNumber": 1,
            "supportedValues": [
                "Palo Alto Networks",
                "Fortinet",
                "Check Point",
            ],
            "supportedValuesKql": None,
            "value": ["Palo Alto Networks"],
            "valuesKql": None,
        }],
        "singleValueObservations": None,
        "thresholdObservations": [
            {
                "description": "Suppress anomalies when daily data transfered (in MB) per hour is less than the chosen value",
                "maximum": "100",
                "minimum": "1",
                "name": "Daily data transfer threshold in MB",
                "rerun": "RerunAlways",
                "sequenceNumber": 1,
                "value": "25",
            },
            {
                "description": "Triggers anomalies when number of standard deviations is greater than the chosen value",
                "maximum": "10",
                "minimum": "2",
                "name": "Number of standard deviations",
                "rerun": "RerunAlways",
                "sequenceNumber": 2,
                "value": "3",
            },
        ],
    },
    description="When account logs from a source region that has rarely been logged in from during the last 14 days, an anomaly is triggered.",
    display_name="Login from unusual region",
    enabled=True,
    frequency="PT1H",
    is_default_settings=True,
    kind="Anomaly",
    required_data_connectors=[azure_native.securityinsights.SecurityMLAnalyticsSettingsDataSourceArgs(
        connector_id="AWS",
        data_types=["AWSCloudTrail"],
    )],
    resource_group_name="myRg",
    settings_definition_id="f209187f-1d17-4431-94af-c141bf5f23db",
    settings_resource_name="f209187f-1d17-4431-94af-c141bf5f23db",
    settings_status="Production",
    tactics=[
        "Exfiltration",
        "CommandAndControl",
    ],
    techniques=[
        "T1037",
        "T1021",
    ],
    workspace_name="myWorkspace")

```

```yaml
resources:
  anomalySecurityMLAnalyticsSettings:
    type: azure-native:securityinsights:AnomalySecurityMLAnalyticsSettings
    properties:
      anomalySettingsVersion: 0
      anomalyVersion: 1.0.5
      customizableObservations:
        multiSelectObservations: null
        prioritizeExcludeObservations: null
        singleSelectObservations:
          - description: Select device vendor of network connection logs from CommonSecurityLog
            name: Device vendor
            rerun: RerunAlways
            sequenceNumber: 1
            supportedValues:
              - Palo Alto Networks
              - Fortinet
              - Check Point
            supportedValuesKql: null
            value:
              - Palo Alto Networks
            valuesKql: null
        singleValueObservations: null
        thresholdObservations:
          - description: Suppress anomalies when daily data transfered (in MB) per hour is less than the chosen value
            maximum: '100'
            minimum: '1'
            name: Daily data transfer threshold in MB
            rerun: RerunAlways
            sequenceNumber: 1
            value: '25'
          - description: Triggers anomalies when number of standard deviations is greater than the chosen value
            maximum: '10'
            minimum: '2'
            name: Number of standard deviations
            rerun: RerunAlways
            sequenceNumber: 2
            value: '3'
      description: When account logs from a source region that has rarely been logged in from during the last 14 days, an anomaly is triggered.
      displayName: Login from unusual region
      enabled: true
      frequency: PT1H
      isDefaultSettings: true
      kind: Anomaly
      requiredDataConnectors:
        - connectorId: AWS
          dataTypes:
            - AWSCloudTrail
      resourceGroupName: myRg
      settingsDefinitionId: f209187f-1d17-4431-94af-c141bf5f23db
      settingsResourceName: f209187f-1d17-4431-94af-c141bf5f23db
      settingsStatus: Production
      tactics:
        - Exfiltration
        - CommandAndControl
      techniques:
        - T1037
        - T1021
      workspaceName: myWorkspace

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:securityinsights:AnomalySecurityMLAnalyticsSettings f209187f-1d17-4431-94af-c141bf5f23db /subscriptions/d0cfe6b2-9ac0-4464-9919-dccaee2e48c0/resourceGroups/myRg/providers/Microsoft.OperationalIinsights/workspaces/myWorkspace/providers/Microsoft.SecurityInsights/securityMLAnalyticsSettings/f209187f-1d17-4431-94af-c141bf5f23db 
```
