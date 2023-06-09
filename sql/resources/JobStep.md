A job step.
API Version: 2021-11-01.
Previous API Version: 2020-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a job step with all properties specified.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var jobStep = new AzureNative.Sql.JobStep("jobStep", new()
    {
        Action = new AzureNative.Sql.Inputs.JobStepActionArgs
        {
            Source = "Inline",
            Type = "TSql",
            Value = "select 2",
        },
        Credential = "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1/credentials/cred1",
        ExecutionOptions = new AzureNative.Sql.Inputs.JobStepExecutionOptionsArgs
        {
            InitialRetryIntervalSeconds = 11,
            MaximumRetryIntervalSeconds = 222,
            RetryAttempts = 42,
            RetryIntervalBackoffMultiplier = 3,
            TimeoutSeconds = 1234,
        },
        JobAgentName = "agent1",
        JobName = "job1",
        Output = new AzureNative.Sql.Inputs.JobStepOutputArgs
        {
            Credential = "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1/credentials/cred0",
            DatabaseName = "database3",
            ResourceGroupName = "group3",
            SchemaName = "myschema1234",
            ServerName = "server3",
            SubscriptionId = "3501b905-a848-4b5d-96e8-b253f62d735a",
            TableName = "mytable5678",
            Type = "SqlDatabase",
        },
        ResourceGroupName = "group1",
        ServerName = "server1",
        StepId = 1,
        StepName = "step1",
        TargetGroup = "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1/targetGroups/targetGroup1",
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
		_, err := sql.NewJobStep(ctx, "jobStep", &sql.JobStepArgs{
			Action: &sql.JobStepActionArgs{
				Source: pulumi.String("Inline"),
				Type:   pulumi.String("TSql"),
				Value:  pulumi.String("select 2"),
			},
			Credential: pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1/credentials/cred1"),
			ExecutionOptions: &sql.JobStepExecutionOptionsArgs{
				InitialRetryIntervalSeconds:    pulumi.Int(11),
				MaximumRetryIntervalSeconds:    pulumi.Int(222),
				RetryAttempts:                  pulumi.Int(42),
				RetryIntervalBackoffMultiplier: pulumi.Float64(3),
				TimeoutSeconds:                 pulumi.Int(1234),
			},
			JobAgentName: pulumi.String("agent1"),
			JobName:      pulumi.String("job1"),
			Output: &sql.JobStepOutputTypeArgs{
				Credential:        pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1/credentials/cred0"),
				DatabaseName:      pulumi.String("database3"),
				ResourceGroupName: pulumi.String("group3"),
				SchemaName:        pulumi.String("myschema1234"),
				ServerName:        pulumi.String("server3"),
				SubscriptionId:    pulumi.String("3501b905-a848-4b5d-96e8-b253f62d735a"),
				TableName:         pulumi.String("mytable5678"),
				Type:              pulumi.String("SqlDatabase"),
			},
			ResourceGroupName: pulumi.String("group1"),
			ServerName:        pulumi.String("server1"),
			StepId:            pulumi.Int(1),
			StepName:          pulumi.String("step1"),
			TargetGroup:       pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1/targetGroups/targetGroup1"),
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
import com.pulumi.azurenative.sql.JobStep;
import com.pulumi.azurenative.sql.JobStepArgs;
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
        var jobStep = new JobStep("jobStep", JobStepArgs.builder()        
            .action(Map.ofEntries(
                Map.entry("source", "Inline"),
                Map.entry("type", "TSql"),
                Map.entry("value", "select 2")
            ))
            .credential("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1/credentials/cred1")
            .executionOptions(Map.ofEntries(
                Map.entry("initialRetryIntervalSeconds", 11),
                Map.entry("maximumRetryIntervalSeconds", 222),
                Map.entry("retryAttempts", 42),
                Map.entry("retryIntervalBackoffMultiplier", 3),
                Map.entry("timeoutSeconds", 1234)
            ))
            .jobAgentName("agent1")
            .jobName("job1")
            .output(Map.ofEntries(
                Map.entry("credential", "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1/credentials/cred0"),
                Map.entry("databaseName", "database3"),
                Map.entry("resourceGroupName", "group3"),
                Map.entry("schemaName", "myschema1234"),
                Map.entry("serverName", "server3"),
                Map.entry("subscriptionId", "3501b905-a848-4b5d-96e8-b253f62d735a"),
                Map.entry("tableName", "mytable5678"),
                Map.entry("type", "SqlDatabase")
            ))
            .resourceGroupName("group1")
            .serverName("server1")
            .stepId(1)
            .stepName("step1")
            .targetGroup("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1/targetGroups/targetGroup1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const jobStep = new azure_native.sql.JobStep("jobStep", {
    action: {
        source: "Inline",
        type: "TSql",
        value: "select 2",
    },
    credential: "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1/credentials/cred1",
    executionOptions: {
        initialRetryIntervalSeconds: 11,
        maximumRetryIntervalSeconds: 222,
        retryAttempts: 42,
        retryIntervalBackoffMultiplier: 3,
        timeoutSeconds: 1234,
    },
    jobAgentName: "agent1",
    jobName: "job1",
    output: {
        credential: "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1/credentials/cred0",
        databaseName: "database3",
        resourceGroupName: "group3",
        schemaName: "myschema1234",
        serverName: "server3",
        subscriptionId: "3501b905-a848-4b5d-96e8-b253f62d735a",
        tableName: "mytable5678",
        type: "SqlDatabase",
    },
    resourceGroupName: "group1",
    serverName: "server1",
    stepId: 1,
    stepName: "step1",
    targetGroup: "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1/targetGroups/targetGroup1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

job_step = azure_native.sql.JobStep("jobStep",
    action=azure_native.sql.JobStepActionArgs(
        source="Inline",
        type="TSql",
        value="select 2",
    ),
    credential="/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1/credentials/cred1",
    execution_options=azure_native.sql.JobStepExecutionOptionsArgs(
        initial_retry_interval_seconds=11,
        maximum_retry_interval_seconds=222,
        retry_attempts=42,
        retry_interval_backoff_multiplier=3,
        timeout_seconds=1234,
    ),
    job_agent_name="agent1",
    job_name="job1",
    output=azure_native.sql.JobStepOutputArgs(
        credential="/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1/credentials/cred0",
        database_name="database3",
        resource_group_name="group3",
        schema_name="myschema1234",
        server_name="server3",
        subscription_id="3501b905-a848-4b5d-96e8-b253f62d735a",
        table_name="mytable5678",
        type="SqlDatabase",
    ),
    resource_group_name="group1",
    server_name="server1",
    step_id=1,
    step_name="step1",
    target_group="/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1/targetGroups/targetGroup1")

```

```yaml
resources:
  jobStep:
    type: azure-native:sql:JobStep
    properties:
      action:
        source: Inline
        type: TSql
        value: select 2
      credential: /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1/credentials/cred1
      executionOptions:
        initialRetryIntervalSeconds: 11
        maximumRetryIntervalSeconds: 222
        retryAttempts: 42
        retryIntervalBackoffMultiplier: 3
        timeoutSeconds: 1234
      jobAgentName: agent1
      jobName: job1
      output:
        credential: /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1/credentials/cred0
        databaseName: database3
        resourceGroupName: group3
        schemaName: myschema1234
        serverName: server3
        subscriptionId: 3501b905-a848-4b5d-96e8-b253f62d735a
        tableName: mytable5678
        type: SqlDatabase
      resourceGroupName: group1
      serverName: server1
      stepId: 1
      stepName: step1
      targetGroup: /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1/targetGroups/targetGroup1

```

{{% /example %}}
{{% example %}}
### Create or update a job step with minimal properties specified.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var jobStep = new AzureNative.Sql.JobStep("jobStep", new()
    {
        Action = new AzureNative.Sql.Inputs.JobStepActionArgs
        {
            Value = "select 1",
        },
        Credential = "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1/credentials/cred0",
        JobAgentName = "agent1",
        JobName = "job1",
        ResourceGroupName = "group1",
        ServerName = "server1",
        StepName = "step1",
        TargetGroup = "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1/targetGroups/targetGroup0",
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
		_, err := sql.NewJobStep(ctx, "jobStep", &sql.JobStepArgs{
			Action: &sql.JobStepActionArgs{
				Value: pulumi.String("select 1"),
			},
			Credential:        pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1/credentials/cred0"),
			JobAgentName:      pulumi.String("agent1"),
			JobName:           pulumi.String("job1"),
			ResourceGroupName: pulumi.String("group1"),
			ServerName:        pulumi.String("server1"),
			StepName:          pulumi.String("step1"),
			TargetGroup:       pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1/targetGroups/targetGroup0"),
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
import com.pulumi.azurenative.sql.JobStep;
import com.pulumi.azurenative.sql.JobStepArgs;
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
        var jobStep = new JobStep("jobStep", JobStepArgs.builder()        
            .action(Map.of("value", "select 1"))
            .credential("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1/credentials/cred0")
            .jobAgentName("agent1")
            .jobName("job1")
            .resourceGroupName("group1")
            .serverName("server1")
            .stepName("step1")
            .targetGroup("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1/targetGroups/targetGroup0")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const jobStep = new azure_native.sql.JobStep("jobStep", {
    action: {
        value: "select 1",
    },
    credential: "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1/credentials/cred0",
    jobAgentName: "agent1",
    jobName: "job1",
    resourceGroupName: "group1",
    serverName: "server1",
    stepName: "step1",
    targetGroup: "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1/targetGroups/targetGroup0",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

job_step = azure_native.sql.JobStep("jobStep",
    action=azure_native.sql.JobStepActionArgs(
        value="select 1",
    ),
    credential="/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1/credentials/cred0",
    job_agent_name="agent1",
    job_name="job1",
    resource_group_name="group1",
    server_name="server1",
    step_name="step1",
    target_group="/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1/targetGroups/targetGroup0")

```

```yaml
resources:
  jobStep:
    type: azure-native:sql:JobStep
    properties:
      action:
        value: select 1
      credential: /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1/credentials/cred0
      jobAgentName: agent1
      jobName: job1
      resourceGroupName: group1
      serverName: server1
      stepName: step1
      targetGroup: /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1/targetGroups/targetGroup0

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:sql:JobStep step1 /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1/jobs/job1/steps/step1 
```
