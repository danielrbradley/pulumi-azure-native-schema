Definition of the job schedule.
API Version: 2022-08-08.
Previous API Version: 2019-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a job schedule
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var jobSchedule = new AzureNative.Automation.JobSchedule("jobSchedule", new()
    {
        AutomationAccountName = "ContoseAutomationAccount",
        JobScheduleId = "0fa462ba-3aa2-4138-83ca-9ebc3bc55cdc",
        Parameters = 
        {
            { "jobscheduletag01", "jobschedulevalue01" },
            { "jobscheduletag02", "jobschedulevalue02" },
        },
        ResourceGroupName = "rg",
        Runbook = new AzureNative.Automation.Inputs.RunbookAssociationPropertyArgs
        {
            Name = "TestRunbook",
        },
        Schedule = new AzureNative.Automation.Inputs.ScheduleAssociationPropertyArgs
        {
            Name = "ScheduleNameGoesHere332204b5-debe-4348-a5c7-6357457189f2",
        },
    });

});


```

```go
package main

import (
	automation "github.com/pulumi/pulumi-azure-native-sdk/automation"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := automation.NewJobSchedule(ctx, "jobSchedule", &automation.JobScheduleArgs{
			AutomationAccountName: pulumi.String("ContoseAutomationAccount"),
			JobScheduleId:         pulumi.String("0fa462ba-3aa2-4138-83ca-9ebc3bc55cdc"),
			Parameters: pulumi.StringMap{
				"jobscheduletag01": pulumi.String("jobschedulevalue01"),
				"jobscheduletag02": pulumi.String("jobschedulevalue02"),
			},
			ResourceGroupName: pulumi.String("rg"),
			Runbook: &automation.RunbookAssociationPropertyArgs{
				Name: pulumi.String("TestRunbook"),
			},
			Schedule: &automation.ScheduleAssociationPropertyArgs{
				Name: pulumi.String("ScheduleNameGoesHere332204b5-debe-4348-a5c7-6357457189f2"),
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
import com.pulumi.azurenative.automation.JobSchedule;
import com.pulumi.azurenative.automation.JobScheduleArgs;
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
        var jobSchedule = new JobSchedule("jobSchedule", JobScheduleArgs.builder()        
            .automationAccountName("ContoseAutomationAccount")
            .jobScheduleId("0fa462ba-3aa2-4138-83ca-9ebc3bc55cdc")
            .parameters(Map.ofEntries(
                Map.entry("jobscheduletag01", "jobschedulevalue01"),
                Map.entry("jobscheduletag02", "jobschedulevalue02")
            ))
            .resourceGroupName("rg")
            .runbook(Map.of("name", "TestRunbook"))
            .schedule(Map.of("name", "ScheduleNameGoesHere332204b5-debe-4348-a5c7-6357457189f2"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const jobSchedule = new azure_native.automation.JobSchedule("jobSchedule", {
    automationAccountName: "ContoseAutomationAccount",
    jobScheduleId: "0fa462ba-3aa2-4138-83ca-9ebc3bc55cdc",
    parameters: {
        jobscheduletag01: "jobschedulevalue01",
        jobscheduletag02: "jobschedulevalue02",
    },
    resourceGroupName: "rg",
    runbook: {
        name: "TestRunbook",
    },
    schedule: {
        name: "ScheduleNameGoesHere332204b5-debe-4348-a5c7-6357457189f2",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

job_schedule = azure_native.automation.JobSchedule("jobSchedule",
    automation_account_name="ContoseAutomationAccount",
    job_schedule_id="0fa462ba-3aa2-4138-83ca-9ebc3bc55cdc",
    parameters={
        "jobscheduletag01": "jobschedulevalue01",
        "jobscheduletag02": "jobschedulevalue02",
    },
    resource_group_name="rg",
    runbook=azure_native.automation.RunbookAssociationPropertyArgs(
        name="TestRunbook",
    ),
    schedule=azure_native.automation.ScheduleAssociationPropertyArgs(
        name="ScheduleNameGoesHere332204b5-debe-4348-a5c7-6357457189f2",
    ))

```

```yaml
resources:
  jobSchedule:
    type: azure-native:automation:JobSchedule
    properties:
      automationAccountName: ContoseAutomationAccount
      jobScheduleId: 0fa462ba-3aa2-4138-83ca-9ebc3bc55cdc
      parameters:
        jobscheduletag01: jobschedulevalue01
        jobscheduletag02: jobschedulevalue02
      resourceGroupName: rg
      runbook:
        name: TestRunbook
      schedule:
        name: ScheduleNameGoesHere332204b5-debe-4348-a5c7-6357457189f2

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:automation:JobSchedule myresource1 /subscriptions/subid/resourceGroups/rg/providers/Microsoft.Automation/automationAccounts/ContoseAutomationAccount/jobSchedules/0fa462ba-3aa2-4138-83ca-9ebc3bc55cdc 
```
