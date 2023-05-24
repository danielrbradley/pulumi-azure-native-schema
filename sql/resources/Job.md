A job.
API Version: 2021-11-01.
Previous API Version: 2020-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a job with all properties specified
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var job = new AzureNative.Sql.Job("job", new()
    {
        Description = "my favourite job",
        JobAgentName = "agent1",
        JobName = "job1",
        ResourceGroupName = "group1",
        Schedule = new AzureNative.Sql.Inputs.JobScheduleArgs
        {
            Enabled = true,
            EndTime = "2015-09-24T23:59:59Z",
            Interval = "PT5M",
            StartTime = "2015-09-24T18:30:01Z",
            Type = AzureNative.Sql.JobScheduleType.Recurring,
        },
        ServerName = "server1",
    });

});


```

```go
package main

import (
	sql "github.com/pulumi/pulumi-azure-native-sdk/sql"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := sql.NewJob(ctx, "job", &sql.JobArgs{
			Description:       pulumi.String("my favourite job"),
			JobAgentName:      pulumi.String("agent1"),
			JobName:           pulumi.String("job1"),
			ResourceGroupName: pulumi.String("group1"),
			Schedule: &sql.JobScheduleArgs{
				Enabled:   pulumi.Bool(true),
				EndTime:   pulumi.String("2015-09-24T23:59:59Z"),
				Interval:  pulumi.String("PT5M"),
				StartTime: pulumi.String("2015-09-24T18:30:01Z"),
				Type:      sql.JobScheduleTypeRecurring,
			},
			ServerName: pulumi.String("server1"),
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
import com.pulumi.azurenative.sql.Job;
import com.pulumi.azurenative.sql.JobArgs;
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
        var job = new Job("job", JobArgs.builder()        
            .description("my favourite job")
            .jobAgentName("agent1")
            .jobName("job1")
            .resourceGroupName("group1")
            .schedule(Map.ofEntries(
                Map.entry("enabled", true),
                Map.entry("endTime", "2015-09-24T23:59:59Z"),
                Map.entry("interval", "PT5M"),
                Map.entry("startTime", "2015-09-24T18:30:01Z"),
                Map.entry("type", "Recurring")
            ))
            .serverName("server1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const job = new azure_native.sql.Job("job", {
    description: "my favourite job",
    jobAgentName: "agent1",
    jobName: "job1",
    resourceGroupName: "group1",
    schedule: {
        enabled: true,
        endTime: "2015-09-24T23:59:59Z",
        interval: "PT5M",
        startTime: "2015-09-24T18:30:01Z",
        type: azure_native.sql.JobScheduleType.Recurring,
    },
    serverName: "server1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

job = azure_native.sql.Job("job",
    description="my favourite job",
    job_agent_name="agent1",
    job_name="job1",
    resource_group_name="group1",
    schedule=azure_native.sql.JobScheduleArgs(
        enabled=True,
        end_time="2015-09-24T23:59:59Z",
        interval="PT5M",
        start_time="2015-09-24T18:30:01Z",
        type=azure_native.sql.JobScheduleType.RECURRING,
    ),
    server_name="server1")

```

```yaml
resources:
  job:
    type: azure-native:sql:Job
    properties:
      description: my favourite job
      jobAgentName: agent1
      jobName: job1
      resourceGroupName: group1
      schedule:
        enabled: true
        endTime: 2015-09-24T23:59:59Z
        interval: PT5M
        startTime: 2015-09-24T18:30:01Z
        type: Recurring
      serverName: server1

```

{{% /example %}}
{{% example %}}
### Create a job with default properties
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var job = new AzureNative.Sql.Job("job", new()
    {
        JobAgentName = "agent1",
        JobName = "job1",
        ResourceGroupName = "group1",
        ServerName = "server1",
    });

});


```

```go
package main

import (
	sql "github.com/pulumi/pulumi-azure-native-sdk/sql"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := sql.NewJob(ctx, "job", &sql.JobArgs{
			JobAgentName:      pulumi.String("agent1"),
			JobName:           pulumi.String("job1"),
			ResourceGroupName: pulumi.String("group1"),
			ServerName:        pulumi.String("server1"),
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
import com.pulumi.azurenative.sql.Job;
import com.pulumi.azurenative.sql.JobArgs;
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
        var job = new Job("job", JobArgs.builder()        
            .jobAgentName("agent1")
            .jobName("job1")
            .resourceGroupName("group1")
            .serverName("server1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const job = new azure_native.sql.Job("job", {
    jobAgentName: "agent1",
    jobName: "job1",
    resourceGroupName: "group1",
    serverName: "server1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

job = azure_native.sql.Job("job",
    job_agent_name="agent1",
    job_name="job1",
    resource_group_name="group1",
    server_name="server1")

```

```yaml
resources:
  job:
    type: azure-native:sql:Job
    properties:
      jobAgentName: agent1
      jobName: job1
      resourceGroupName: group1
      serverName: server1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:sql:Job job1 /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1/jobs/job1 
```
