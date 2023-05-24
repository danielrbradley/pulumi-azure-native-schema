Software update configuration properties.
API Version: 2019-06-01.
Previous API Version: 2019-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create software update configuration
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var softwareUpdateConfigurationByName = new AzureNative.Automation.SoftwareUpdateConfigurationByName("softwareUpdateConfigurationByName", new()
    {
        AutomationAccountName = "myaccount",
        ResourceGroupName = "mygroup",
        ScheduleInfo = new AzureNative.Automation.Inputs.SUCSchedulePropertiesArgs
        {
            AdvancedSchedule = new AzureNative.Automation.Inputs.AdvancedScheduleArgs
            {
                WeekDays = new[]
                {
                    "Monday",
                    "Thursday",
                },
            },
            ExpiryTime = "2018-11-09T11:22:57+00:00",
            Frequency = "Hour",
            Interval = 1,
            StartTime = "2017-10-19T12:22:57+00:00",
            TimeZone = "America/Los_Angeles",
        },
        SoftwareUpdateConfigurationName = "testpatch",
        Tasks = new AzureNative.Automation.Inputs.SoftwareUpdateConfigurationTasksArgs
        {
            PostTask = new AzureNative.Automation.Inputs.TaskPropertiesArgs
            {
                Source = "GetCache",
            },
            PreTask = new AzureNative.Automation.Inputs.TaskPropertiesArgs
            {
                Parameters = 
                {
                    { "COMPUTERNAME", "Computer1" },
                },
                Source = "HelloWorld",
            },
        },
        UpdateConfiguration = new AzureNative.Automation.Inputs.UpdateConfigurationArgs
        {
            AzureVirtualMachines = new[]
            {
                "/subscriptions/5ae68d89-69a4-454f-b5ce-e443cc4e0067/resourceGroups/myresources/providers/Microsoft.Compute/virtualMachines/vm-01",
                "/subscriptions/5ae68d89-69a4-454f-b5ce-e443cc4e0067/resourceGroups/myresources/providers/Microsoft.Compute/virtualMachines/vm-02",
                "/subscriptions/5ae68d89-69a4-454f-b5ce-e443cc4e0067/resourceGroups/myresources/providers/Microsoft.Compute/virtualMachines/vm-03",
            },
            Duration = "PT2H0M",
            NonAzureComputerNames = new[]
            {
                "box1.contoso.com",
                "box2.contoso.com",
            },
            OperatingSystem = AzureNative.Automation.OperatingSystemType.Windows,
            Targets = new AzureNative.Automation.Inputs.TargetPropertiesArgs
            {
                AzureQueries = new[]
                {
                    new AzureNative.Automation.Inputs.AzureQueryPropertiesArgs
                    {
                        Locations = new[]
                        {
                            "Japan East",
                            "UK South",
                        },
                        Scope = new[]
                        {
                            "/subscriptions/5ae68d89-69a4-454f-b5ce-e443cc4e0067/resourceGroups/myresources",
                            "/subscriptions/5ae68d89-69a4-454f-b5ce-e443cc4e0067",
                        },
                        TagSettings = new AzureNative.Automation.Inputs.TagSettingsPropertiesArgs
                        {
                            FilterOperator = AzureNative.Automation.TagOperators.All,
                            Tags = 
                            {
                                { "tag1", new[]
                                {
                                    "tag1Value1",
                                    "tag1Value2",
                                    "tag1Value3",
                                } },
                                { "tag2", new[]
                                {
                                    "tag2Value1",
                                    "tag2Value2",
                                    "tag2Value3",
                                } },
                            },
                        },
                    },
                },
                NonAzureQueries = new[]
                {
                    new AzureNative.Automation.Inputs.NonAzureQueryPropertiesArgs
                    {
                        FunctionAlias = "SavedSearch1",
                        WorkspaceId = "WorkspaceId1",
                    },
                    new AzureNative.Automation.Inputs.NonAzureQueryPropertiesArgs
                    {
                        FunctionAlias = "SavedSearch2",
                        WorkspaceId = "WorkspaceId2",
                    },
                },
            },
            Windows = new AzureNative.Automation.Inputs.WindowsPropertiesArgs
            {
                ExcludedKbNumbers = new[]
                {
                    "168934",
                    "168973",
                },
                IncludedUpdateClassifications = "Critical",
                RebootSetting = "IfRequired",
            },
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.automation.SoftwareUpdateConfigurationByName;
import com.pulumi.azurenative.automation.SoftwareUpdateConfigurationByNameArgs;
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
        var softwareUpdateConfigurationByName = new SoftwareUpdateConfigurationByName("softwareUpdateConfigurationByName", SoftwareUpdateConfigurationByNameArgs.builder()        
            .automationAccountName("myaccount")
            .resourceGroupName("mygroup")
            .scheduleInfo(Map.ofEntries(
                Map.entry("advancedSchedule", Map.of("weekDays",                 
                    "Monday",
                    "Thursday")),
                Map.entry("expiryTime", "2018-11-09T11:22:57+00:00"),
                Map.entry("frequency", "Hour"),
                Map.entry("interval", 1),
                Map.entry("startTime", "2017-10-19T12:22:57+00:00"),
                Map.entry("timeZone", "America/Los_Angeles")
            ))
            .softwareUpdateConfigurationName("testpatch")
            .tasks(Map.ofEntries(
                Map.entry("postTask", Map.of("source", "GetCache")),
                Map.entry("preTask", Map.ofEntries(
                    Map.entry("parameters", Map.of("COMPUTERNAME", "Computer1")),
                    Map.entry("source", "HelloWorld")
                ))
            ))
            .updateConfiguration(Map.ofEntries(
                Map.entry("azureVirtualMachines",                 
                    "/subscriptions/5ae68d89-69a4-454f-b5ce-e443cc4e0067/resourceGroups/myresources/providers/Microsoft.Compute/virtualMachines/vm-01",
                    "/subscriptions/5ae68d89-69a4-454f-b5ce-e443cc4e0067/resourceGroups/myresources/providers/Microsoft.Compute/virtualMachines/vm-02",
                    "/subscriptions/5ae68d89-69a4-454f-b5ce-e443cc4e0067/resourceGroups/myresources/providers/Microsoft.Compute/virtualMachines/vm-03"),
                Map.entry("duration", "PT2H0M"),
                Map.entry("nonAzureComputerNames",                 
                    "box1.contoso.com",
                    "box2.contoso.com"),
                Map.entry("operatingSystem", "Windows"),
                Map.entry("targets", Map.ofEntries(
                    Map.entry("azureQueries", Map.ofEntries(
                        Map.entry("locations",                         
                            "Japan East",
                            "UK South"),
                        Map.entry("scope",                         
                            "/subscriptions/5ae68d89-69a4-454f-b5ce-e443cc4e0067/resourceGroups/myresources",
                            "/subscriptions/5ae68d89-69a4-454f-b5ce-e443cc4e0067"),
                        Map.entry("tagSettings", Map.ofEntries(
                            Map.entry("filterOperator", "All"),
                            Map.entry("tags", Map.ofEntries(
                                Map.entry("tag1",                                 
                                    "tag1Value1",
                                    "tag1Value2",
                                    "tag1Value3"),
                                Map.entry("tag2",                                 
                                    "tag2Value1",
                                    "tag2Value2",
                                    "tag2Value3")
                            ))
                        ))
                    )),
                    Map.entry("nonAzureQueries",                     
                        Map.ofEntries(
                            Map.entry("functionAlias", "SavedSearch1"),
                            Map.entry("workspaceId", "WorkspaceId1")
                        ),
                        Map.ofEntries(
                            Map.entry("functionAlias", "SavedSearch2"),
                            Map.entry("workspaceId", "WorkspaceId2")
                        ))
                )),
                Map.entry("windows", Map.ofEntries(
                    Map.entry("excludedKbNumbers",                     
                        "168934",
                        "168973"),
                    Map.entry("includedUpdateClassifications", "Critical"),
                    Map.entry("rebootSetting", "IfRequired")
                ))
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const softwareUpdateConfigurationByName = new azure_native.automation.SoftwareUpdateConfigurationByName("softwareUpdateConfigurationByName", {
    automationAccountName: "myaccount",
    resourceGroupName: "mygroup",
    scheduleInfo: {
        advancedSchedule: {
            weekDays: [
                "Monday",
                "Thursday",
            ],
        },
        expiryTime: "2018-11-09T11:22:57+00:00",
        frequency: "Hour",
        interval: 1,
        startTime: "2017-10-19T12:22:57+00:00",
        timeZone: "America/Los_Angeles",
    },
    softwareUpdateConfigurationName: "testpatch",
    tasks: {
        postTask: {
            source: "GetCache",
        },
        preTask: {
            parameters: {
                COMPUTERNAME: "Computer1",
            },
            source: "HelloWorld",
        },
    },
    updateConfiguration: {
        azureVirtualMachines: [
            "/subscriptions/5ae68d89-69a4-454f-b5ce-e443cc4e0067/resourceGroups/myresources/providers/Microsoft.Compute/virtualMachines/vm-01",
            "/subscriptions/5ae68d89-69a4-454f-b5ce-e443cc4e0067/resourceGroups/myresources/providers/Microsoft.Compute/virtualMachines/vm-02",
            "/subscriptions/5ae68d89-69a4-454f-b5ce-e443cc4e0067/resourceGroups/myresources/providers/Microsoft.Compute/virtualMachines/vm-03",
        ],
        duration: "PT2H0M",
        nonAzureComputerNames: [
            "box1.contoso.com",
            "box2.contoso.com",
        ],
        operatingSystem: azure_native.automation.OperatingSystemType.Windows,
        targets: {
            azureQueries: [{
                locations: [
                    "Japan East",
                    "UK South",
                ],
                scope: [
                    "/subscriptions/5ae68d89-69a4-454f-b5ce-e443cc4e0067/resourceGroups/myresources",
                    "/subscriptions/5ae68d89-69a4-454f-b5ce-e443cc4e0067",
                ],
                tagSettings: {
                    filterOperator: azure_native.automation.TagOperators.All,
                    tags: {
                        tag1: [
                            "tag1Value1",
                            "tag1Value2",
                            "tag1Value3",
                        ],
                        tag2: [
                            "tag2Value1",
                            "tag2Value2",
                            "tag2Value3",
                        ],
                    },
                },
            }],
            nonAzureQueries: [
                {
                    functionAlias: "SavedSearch1",
                    workspaceId: "WorkspaceId1",
                },
                {
                    functionAlias: "SavedSearch2",
                    workspaceId: "WorkspaceId2",
                },
            ],
        },
        windows: {
            excludedKbNumbers: [
                "168934",
                "168973",
            ],
            includedUpdateClassifications: "Critical",
            rebootSetting: "IfRequired",
        },
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

software_update_configuration_by_name = azure_native.automation.SoftwareUpdateConfigurationByName("softwareUpdateConfigurationByName",
    automation_account_name="myaccount",
    resource_group_name="mygroup",
    schedule_info=azure_native.automation.SUCSchedulePropertiesResponseArgs(
        advanced_schedule=azure_native.automation.AdvancedScheduleArgs(
            week_days=[
                "Monday",
                "Thursday",
            ],
        ),
        expiry_time="2018-11-09T11:22:57+00:00",
        frequency="Hour",
        interval=1,
        start_time="2017-10-19T12:22:57+00:00",
        time_zone="America/Los_Angeles",
    ),
    software_update_configuration_name="testpatch",
    tasks=azure_native.automation.SoftwareUpdateConfigurationTasksResponseArgs(
        post_task=azure_native.automation.TaskPropertiesArgs(
            source="GetCache",
        ),
        pre_task=azure_native.automation.TaskPropertiesArgs(
            parameters={
                "COMPUTERNAME": "Computer1",
            },
            source="HelloWorld",
        ),
    ),
    update_configuration=azure_native.automation.UpdateConfigurationResponseArgs(
        azure_virtual_machines=[
            "/subscriptions/5ae68d89-69a4-454f-b5ce-e443cc4e0067/resourceGroups/myresources/providers/Microsoft.Compute/virtualMachines/vm-01",
            "/subscriptions/5ae68d89-69a4-454f-b5ce-e443cc4e0067/resourceGroups/myresources/providers/Microsoft.Compute/virtualMachines/vm-02",
            "/subscriptions/5ae68d89-69a4-454f-b5ce-e443cc4e0067/resourceGroups/myresources/providers/Microsoft.Compute/virtualMachines/vm-03",
        ],
        duration="PT2H0M",
        non_azure_computer_names=[
            "box1.contoso.com",
            "box2.contoso.com",
        ],
        operating_system=azure_native.automation.OperatingSystemType.WINDOWS,
        targets={
            "azureQueries": [{
                "locations": [
                    "Japan East",
                    "UK South",
                ],
                "scope": [
                    "/subscriptions/5ae68d89-69a4-454f-b5ce-e443cc4e0067/resourceGroups/myresources",
                    "/subscriptions/5ae68d89-69a4-454f-b5ce-e443cc4e0067",
                ],
                "tagSettings": azure_native.automation.TagSettingsPropertiesArgs(
                    filter_operator=azure_native.automation.TagOperators.ALL,
                    tags={
                        "tag1": [
                            "tag1Value1",
                            "tag1Value2",
                            "tag1Value3",
                        ],
                        "tag2": [
                            "tag2Value1",
                            "tag2Value2",
                            "tag2Value3",
                        ],
                    },
                ),
            }],
            "nonAzureQueries": [
                azure_native.automation.NonAzureQueryPropertiesArgs(
                    function_alias="SavedSearch1",
                    workspace_id="WorkspaceId1",
                ),
                azure_native.automation.NonAzureQueryPropertiesArgs(
                    function_alias="SavedSearch2",
                    workspace_id="WorkspaceId2",
                ),
            ],
        },
        windows=azure_native.automation.WindowsPropertiesArgs(
            excluded_kb_numbers=[
                "168934",
                "168973",
            ],
            included_update_classifications="Critical",
            reboot_setting="IfRequired",
        ),
    ))

```

```yaml
resources:
  softwareUpdateConfigurationByName:
    type: azure-native:automation:SoftwareUpdateConfigurationByName
    properties:
      automationAccountName: myaccount
      resourceGroupName: mygroup
      scheduleInfo:
        advancedSchedule:
          weekDays:
            - Monday
            - Thursday
        expiryTime: 2018-11-09T11:22:57+00:00
        frequency: Hour
        interval: 1
        startTime: 2017-10-19T12:22:57+00:00
        timeZone: America/Los_Angeles
      softwareUpdateConfigurationName: testpatch
      tasks:
        postTask:
          source: GetCache
        preTask:
          parameters:
            COMPUTERNAME: Computer1
          source: HelloWorld
      updateConfiguration:
        azureVirtualMachines:
          - /subscriptions/5ae68d89-69a4-454f-b5ce-e443cc4e0067/resourceGroups/myresources/providers/Microsoft.Compute/virtualMachines/vm-01
          - /subscriptions/5ae68d89-69a4-454f-b5ce-e443cc4e0067/resourceGroups/myresources/providers/Microsoft.Compute/virtualMachines/vm-02
          - /subscriptions/5ae68d89-69a4-454f-b5ce-e443cc4e0067/resourceGroups/myresources/providers/Microsoft.Compute/virtualMachines/vm-03
        duration: PT2H0M
        nonAzureComputerNames:
          - box1.contoso.com
          - box2.contoso.com
        operatingSystem: Windows
        targets:
          azureQueries:
            - locations:
                - Japan East
                - UK South
              scope:
                - /subscriptions/5ae68d89-69a4-454f-b5ce-e443cc4e0067/resourceGroups/myresources
                - /subscriptions/5ae68d89-69a4-454f-b5ce-e443cc4e0067
              tagSettings:
                filterOperator: All
                tags:
                  tag1:
                    - tag1Value1
                    - tag1Value2
                    - tag1Value3
                  tag2:
                    - tag2Value1
                    - tag2Value2
                    - tag2Value3
          nonAzureQueries:
            - functionAlias: SavedSearch1
              workspaceId: WorkspaceId1
            - functionAlias: SavedSearch2
              workspaceId: WorkspaceId2
        windows:
          excludedKbNumbers:
            - '168934'
            - '168973'
          includedUpdateClassifications: Critical
          rebootSetting: IfRequired

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:automation:SoftwareUpdateConfigurationByName testpatch /subscriptions/51766542-3ed7-4a72-a187-0c8ab644ddab/resourceGroups/mygroup/providers/Microsoft.Automation/automationAccounts/myaccount/softwareUpdateConfigurations/testpatch 
```
