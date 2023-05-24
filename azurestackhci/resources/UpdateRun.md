Details of an Update run
API Version: 2023-02-01.

{{% examples %}}
## Example Usage
{{% example %}}
### Get Update runs under cluster resource
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var updateRun = new AzureNative.AzureStackHCI.UpdateRun("updateRun", new()
    {
        ClusterName = "testcluster",
        Description = "Update Azure Stack.",
        EndTimeUtc = "2022-04-06T13:58:42.969006+00:00",
        ErrorMessage = "",
        LastUpdatedTimeUtc = "2022-04-06T13:58:42.969006+00:00",
        Name = "Unnamed step",
        ResourceGroupName = "testrg",
        StartTimeUtc = "2022-04-06T01:36:33.3876751+00:00",
        Status = "Success",
        Steps = new[]
        {
            new AzureNative.AzureStackHCI.Inputs.StepArgs
            {
                Description = "Prepare for SSU update",
                EndTimeUtc = "2022-04-06T01:37:16.8728314+00:00",
                ErrorMessage = "",
                LastUpdatedTimeUtc = "2022-04-06T01:37:16.8728314+00:00",
                Name = "PreUpdate Cloud",
                StartTimeUtc = "2022-04-06T01:36:33.3876751+00:00",
                Status = "Success",
                Steps = new[] {},
            },
        },
        UpdateName = "Microsoft4.2203.2.32",
        UpdateRunName = "23b779ba-0d52-4a80-8571-45ca74664ec3",
    });

});


```

```go
package main

import (
	azurestackhci "github.com/pulumi/pulumi-azure-native-sdk/azurestackhci"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := azurestackhci.NewUpdateRun(ctx, "updateRun", &azurestackhci.UpdateRunArgs{
			ClusterName:        pulumi.String("testcluster"),
			Description:        pulumi.String("Update Azure Stack."),
			EndTimeUtc:         pulumi.String("2022-04-06T13:58:42.969006+00:00"),
			ErrorMessage:       pulumi.String(""),
			LastUpdatedTimeUtc: pulumi.String("2022-04-06T13:58:42.969006+00:00"),
			Name:               pulumi.String("Unnamed step"),
			ResourceGroupName:  pulumi.String("testrg"),
			StartTimeUtc:       pulumi.String("2022-04-06T01:36:33.3876751+00:00"),
			Status:             pulumi.String("Success"),
			Steps: []azurestackhci.StepArgs{
				{
					Description:        pulumi.String("Prepare for SSU update"),
					EndTimeUtc:         pulumi.String("2022-04-06T01:37:16.8728314+00:00"),
					ErrorMessage:       pulumi.String(""),
					LastUpdatedTimeUtc: pulumi.String("2022-04-06T01:37:16.8728314+00:00"),
					Name:               pulumi.String("PreUpdate Cloud"),
					StartTimeUtc:       pulumi.String("2022-04-06T01:36:33.3876751+00:00"),
					Status:             pulumi.String("Success"),
					Steps:              azurestackhci.StepArray{},
				},
			},
			UpdateName:    pulumi.String("Microsoft4.2203.2.32"),
			UpdateRunName: pulumi.String("23b779ba-0d52-4a80-8571-45ca74664ec3"),
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
import com.pulumi.azurenative.azurestackhci.UpdateRun;
import com.pulumi.azurenative.azurestackhci.UpdateRunArgs;
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
        var updateRun = new UpdateRun("updateRun", UpdateRunArgs.builder()        
            .clusterName("testcluster")
            .description("Update Azure Stack.")
            .endTimeUtc("2022-04-06T13:58:42.969006+00:00")
            .errorMessage("")
            .lastUpdatedTimeUtc("2022-04-06T13:58:42.969006+00:00")
            .name("Unnamed step")
            .resourceGroupName("testrg")
            .startTimeUtc("2022-04-06T01:36:33.3876751+00:00")
            .status("Success")
            .steps(Map.ofEntries(
                Map.entry("description", "Prepare for SSU update"),
                Map.entry("endTimeUtc", "2022-04-06T01:37:16.8728314+00:00"),
                Map.entry("errorMessage", ""),
                Map.entry("lastUpdatedTimeUtc", "2022-04-06T01:37:16.8728314+00:00"),
                Map.entry("name", "PreUpdate Cloud"),
                Map.entry("startTimeUtc", "2022-04-06T01:36:33.3876751+00:00"),
                Map.entry("status", "Success"),
                Map.entry("steps", )
            ))
            .updateName("Microsoft4.2203.2.32")
            .updateRunName("23b779ba-0d52-4a80-8571-45ca74664ec3")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const updateRun = new azure_native.azurestackhci.UpdateRun("updateRun", {
    clusterName: "testcluster",
    description: "Update Azure Stack.",
    endTimeUtc: "2022-04-06T13:58:42.969006+00:00",
    errorMessage: "",
    lastUpdatedTimeUtc: "2022-04-06T13:58:42.969006+00:00",
    name: "Unnamed step",
    resourceGroupName: "testrg",
    startTimeUtc: "2022-04-06T01:36:33.3876751+00:00",
    status: "Success",
    steps: [{
        description: "Prepare for SSU update",
        endTimeUtc: "2022-04-06T01:37:16.8728314+00:00",
        errorMessage: "",
        lastUpdatedTimeUtc: "2022-04-06T01:37:16.8728314+00:00",
        name: "PreUpdate Cloud",
        startTimeUtc: "2022-04-06T01:36:33.3876751+00:00",
        status: "Success",
        steps: [],
    }],
    updateName: "Microsoft4.2203.2.32",
    updateRunName: "23b779ba-0d52-4a80-8571-45ca74664ec3",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

update_run = azure_native.azurestackhci.UpdateRun("updateRun",
    cluster_name="testcluster",
    description="Update Azure Stack.",
    end_time_utc="2022-04-06T13:58:42.969006+00:00",
    error_message="",
    last_updated_time_utc="2022-04-06T13:58:42.969006+00:00",
    name="Unnamed step",
    resource_group_name="testrg",
    start_time_utc="2022-04-06T01:36:33.3876751+00:00",
    status="Success",
    steps=[azure_native.azurestackhci.StepArgs(
        description="Prepare for SSU update",
        end_time_utc="2022-04-06T01:37:16.8728314+00:00",
        error_message="",
        last_updated_time_utc="2022-04-06T01:37:16.8728314+00:00",
        name="PreUpdate Cloud",
        start_time_utc="2022-04-06T01:36:33.3876751+00:00",
        status="Success",
        steps=[],
    )],
    update_name="Microsoft4.2203.2.32",
    update_run_name="23b779ba-0d52-4a80-8571-45ca74664ec3")

```

```yaml
resources:
  updateRun:
    type: azure-native:azurestackhci:UpdateRun
    properties:
      clusterName: testcluster
      description: Update Azure Stack.
      endTimeUtc: 2022-04-06T13:58:42.969006+00:00
      errorMessage:
      lastUpdatedTimeUtc: 2022-04-06T13:58:42.969006+00:00
      name: Unnamed step
      resourceGroupName: testrg
      startTimeUtc: 2022-04-06T01:36:33.3876751+00:00
      status: Success
      steps:
        - description: Prepare for SSU update
          endTimeUtc: 2022-04-06T01:37:16.8728314+00:00
          errorMessage:
          lastUpdatedTimeUtc: 2022-04-06T01:37:16.8728314+00:00
          name: PreUpdate Cloud
          startTimeUtc: 2022-04-06T01:36:33.3876751+00:00
          status: Success
          steps: []
      updateName: Microsoft4.2203.2.32
      updateRunName: 23b779ba-0d52-4a80-8571-45ca74664ec3

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:azurestackhci:UpdateRun Microsoft4.2203.2.32/23b779ba-0d52-4a80-8571-45ca74664ec3 /subscriptions/b8d594e5-51f3-4c11-9c54-a7771b81c712/resourceGroups/testrg/providers/Microsoft.AzureStackHCI/clusters/testcluster/updates/Microsoft4.2203.2.32/updateRuns/23b779ba-0d52-4a80-8571-45ca74664ec3 
```
