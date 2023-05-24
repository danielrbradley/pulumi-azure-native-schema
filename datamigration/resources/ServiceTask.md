A task resource
API Version: 2021-06-30.

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
    var serviceTask = new AzureNative.DataMigration.ServiceTask("serviceTask", new()
    {
        GroupName = "DmsSdkRg",
        Properties = 
        {
            { "input", new AzureNative.DataMigration.Inputs.MongoDbConnectionInfoArgs
            {
                ServerVersion = "NA",
            } },
            { "taskType", "Service.Check.OCI" },
        },
        ServiceName = "DmsSdkService",
        TaskName = "DmsSdkTask",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.datamigration.ServiceTask;
import com.pulumi.azurenative.datamigration.ServiceTaskArgs;
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
        var serviceTask = new ServiceTask("serviceTask", ServiceTaskArgs.builder()        
            .groupName("DmsSdkRg")
            .properties(Map.ofEntries(
                Map.entry("input", Map.of("serverVersion", "NA")),
                Map.entry("taskType", "Service.Check.OCI")
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

const serviceTask = new azure_native.datamigration.ServiceTask("serviceTask", {
    groupName: "DmsSdkRg",
    properties: {
        input: {
            serverVersion: "NA",
        },
        taskType: "Service.Check.OCI",
    },
    serviceName: "DmsSdkService",
    taskName: "DmsSdkTask",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

service_task = azure_native.datamigration.ServiceTask("serviceTask",
    group_name="DmsSdkRg",
    properties={
        "input": azure_native.datamigration.MongoDbConnectionInfoArgs(
            server_version="NA",
        ),
        "taskType": "Service.Check.OCI",
    },
    service_name="DmsSdkService",
    task_name="DmsSdkTask")

```

```yaml
resources:
  serviceTask:
    type: azure-native:datamigration:ServiceTask
    properties:
      groupName: DmsSdkRg
      properties:
        input:
          serverVersion: NA
        taskType: Service.Check.OCI
      serviceName: DmsSdkService
      taskName: DmsSdkTask

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:datamigration:ServiceTask DmsSdkTask /subscriptions/fc04246f-04c5-437e-ac5e-206a19e7193f/resourceGroups/DmsSdkRg/providers/Microsoft.DataMigration/services/DmsSdkService/serviceTasks/DmsSdkTask 
```
