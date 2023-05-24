An Azure SQL job agent.
API Version: 2021-11-01.
Previous API Version: 2020-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a job agent
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var jobAgent = new AzureNative.Sql.JobAgent("jobAgent", new()
    {
        DatabaseId = "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/databases/db1",
        JobAgentName = "agent1",
        Location = "southeastasia",
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
		_, err := sql.NewJobAgent(ctx, "jobAgent", &sql.JobAgentArgs{
			DatabaseId:        pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/databases/db1"),
			JobAgentName:      pulumi.String("agent1"),
			Location:          pulumi.String("southeastasia"),
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
import com.pulumi.azurenative.sql.JobAgent;
import com.pulumi.azurenative.sql.JobAgentArgs;
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
        var jobAgent = new JobAgent("jobAgent", JobAgentArgs.builder()        
            .databaseId("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/databases/db1")
            .jobAgentName("agent1")
            .location("southeastasia")
            .resourceGroupName("group1")
            .serverName("server1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const jobAgent = new azure_native.sql.JobAgent("jobAgent", {
    databaseId: "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/databases/db1",
    jobAgentName: "agent1",
    location: "southeastasia",
    resourceGroupName: "group1",
    serverName: "server1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

job_agent = azure_native.sql.JobAgent("jobAgent",
    database_id="/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/databases/db1",
    job_agent_name="agent1",
    location="southeastasia",
    resource_group_name="group1",
    server_name="server1")

```

```yaml
resources:
  jobAgent:
    type: azure-native:sql:JobAgent
    properties:
      databaseId: /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/databases/db1
      jobAgentName: agent1
      location: southeastasia
      resourceGroupName: group1
      serverName: server1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:sql:JobAgent agent1 /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1 
```
