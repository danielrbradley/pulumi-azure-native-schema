A task resource
API Version: 2021-06-30.
Previous API Version: 2018-04-19. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Tasks_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var task = new AzureNative.DataMigration.Task("task", new()
    {
        GroupName = "DmsSdkRg",
        ProjectName = "DmsSdkProject",
        Properties = new AzureNative.DataMigration.Inputs.ConnectToTargetSqlDbTaskPropertiesArgs
        {
            Input = new AzureNative.DataMigration.Inputs.ConnectToTargetSqlDbTaskInputArgs
            {
                TargetConnectionInfo = new AzureNative.DataMigration.Inputs.SqlConnectionInfoArgs
                {
                    Authentication = "SqlAuthentication",
                    DataSource = "ssma-test-server.database.windows.net",
                    EncryptConnection = true,
                    Password = "testpassword",
                    TrustServerCertificate = true,
                    Type = "SqlConnectionInfo",
                    UserName = "testuser",
                },
            },
            TaskType = "ConnectToTarget.SqlDb",
        },
        ServiceName = "DmsSdkService",
        TaskName = "DmsSdkTask",
    });

});


```

```go
package main

import (
	datamigration "github.com/pulumi/pulumi-azure-native-sdk/datamigration"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := datamigration.NewTask(ctx, "task", &datamigration.TaskArgs{
			GroupName:   pulumi.String("DmsSdkRg"),
			ProjectName: pulumi.String("DmsSdkProject"),
			Properties: datamigration.ConnectToTargetSqlDbTaskProperties{
				Input: datamigration.ConnectToTargetSqlDbTaskInput{
					TargetConnectionInfo: datamigration.SqlConnectionInfo{
						Authentication:         "SqlAuthentication",
						DataSource:             "ssma-test-server.database.windows.net",
						EncryptConnection:      true,
						Password:               "testpassword",
						TrustServerCertificate: true,
						Type:                   "SqlConnectionInfo",
						UserName:               "testuser",
					},
				},
				TaskType: "ConnectToTarget.SqlDb",
			},
			ServiceName: pulumi.String("DmsSdkService"),
			TaskName:    pulumi.String("DmsSdkTask"),
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
import com.pulumi.azurenative.datamigration.Task;
import com.pulumi.azurenative.datamigration.TaskArgs;
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
        var task = new Task("task", TaskArgs.builder()        
            .groupName("DmsSdkRg")
            .projectName("DmsSdkProject")
            .properties(Map.ofEntries(
                Map.entry("input", Map.of("targetConnectionInfo", Map.ofEntries(
                    Map.entry("authentication", "SqlAuthentication"),
                    Map.entry("dataSource", "ssma-test-server.database.windows.net"),
                    Map.entry("encryptConnection", true),
                    Map.entry("password", "testpassword"),
                    Map.entry("trustServerCertificate", true),
                    Map.entry("type", "SqlConnectionInfo"),
                    Map.entry("userName", "testuser")
                ))),
                Map.entry("taskType", "ConnectToTarget.SqlDb")
            ))
            .serviceName("DmsSdkService")
            .taskName("DmsSdkTask")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const task = new azure_native.datamigration.Task("task", {
    groupName: "DmsSdkRg",
    projectName: "DmsSdkProject",
    properties: {
        input: {
            targetConnectionInfo: {
                authentication: "SqlAuthentication",
                dataSource: "ssma-test-server.database.windows.net",
                encryptConnection: true,
                password: "testpassword",
                trustServerCertificate: true,
                type: "SqlConnectionInfo",
                userName: "testuser",
            },
        },
        taskType: "ConnectToTarget.SqlDb",
    },
    serviceName: "DmsSdkService",
    taskName: "DmsSdkTask",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

task = azure_native.datamigration.Task("task",
    group_name="DmsSdkRg",
    project_name="DmsSdkProject",
    properties=azure_native.datamigration.ConnectToTargetSqlDbTaskPropertiesArgs(
        input=azure_native.datamigration.ConnectToTargetSqlDbTaskInputArgs(
            target_connection_info=azure_native.datamigration.SqlConnectionInfoArgs(
                authentication="SqlAuthentication",
                data_source="ssma-test-server.database.windows.net",
                encrypt_connection=True,
                password="testpassword",
                trust_server_certificate=True,
                type="SqlConnectionInfo",
                user_name="testuser",
            ),
        ),
        task_type="ConnectToTarget.SqlDb",
    ),
    service_name="DmsSdkService",
    task_name="DmsSdkTask")

```

```yaml
resources:
  task:
    type: azure-native:datamigration:Task
    properties:
      groupName: DmsSdkRg
      projectName: DmsSdkProject
      properties:
        input:
          targetConnectionInfo:
            authentication: SqlAuthentication
            dataSource: ssma-test-server.database.windows.net
            encryptConnection: true
            password: testpassword
            trustServerCertificate: true
            type: SqlConnectionInfo
            userName: testuser
        taskType: ConnectToTarget.SqlDb
      serviceName: DmsSdkService
      taskName: DmsSdkTask

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:datamigration:Task DmsSdkTask /subscriptions/fc04246f-04c5-437e-ac5e-206a19e7193f/resourceGroups/DmsSdkRg/providers/Microsoft.DataMigration/services/DmsSdkService/projects/DmsSdkProject/tasks/DmsSdkTask 
```
