A stored credential that can be used by a job to connect to target databases.
API Version: 2021-11-01.
Previous API Version: 2020-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a credential
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var jobCredential = new AzureNative.Sql.JobCredential("jobCredential", new()
    {
        CredentialName = "cred1",
        JobAgentName = "agent1",
        Password = "<password>",
        ResourceGroupName = "group1",
        ServerName = "server1",
        Username = "myuser",
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
		_, err := sql.NewJobCredential(ctx, "jobCredential", &sql.JobCredentialArgs{
			CredentialName:    pulumi.String("cred1"),
			JobAgentName:      pulumi.String("agent1"),
			Password:          pulumi.String("<password>"),
			ResourceGroupName: pulumi.String("group1"),
			ServerName:        pulumi.String("server1"),
			Username:          pulumi.String("myuser"),
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
import com.pulumi.azurenative.sql.JobCredential;
import com.pulumi.azurenative.sql.JobCredentialArgs;
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
        var jobCredential = new JobCredential("jobCredential", JobCredentialArgs.builder()        
            .credentialName("cred1")
            .jobAgentName("agent1")
            .password("<password>")
            .resourceGroupName("group1")
            .serverName("server1")
            .username("myuser")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const jobCredential = new azure_native.sql.JobCredential("jobCredential", {
    credentialName: "cred1",
    jobAgentName: "agent1",
    password: "<password>",
    resourceGroupName: "group1",
    serverName: "server1",
    username: "myuser",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

job_credential = azure_native.sql.JobCredential("jobCredential",
    credential_name="cred1",
    job_agent_name="agent1",
    password="<password>",
    resource_group_name="group1",
    server_name="server1",
    username="myuser")

```

```yaml
resources:
  jobCredential:
    type: azure-native:sql:JobCredential
    properties:
      credentialName: cred1
      jobAgentName: agent1
      password: <password>
      resourceGroupName: group1
      serverName: server1
      username: myuser

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:sql:JobCredential cred1 /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1/credentials/cred1 
```
