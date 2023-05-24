Database, Server or Elastic Pool Advisor.
API Version: 2021-11-01.
Previous API Version: 2020-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Update server advisor
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var serverAdvisor = new AzureNative.Sql.ServerAdvisor("serverAdvisor", new()
    {
        AdvisorName = "CreateIndex",
        AutoExecuteStatus = AzureNative.Sql.AutoExecuteStatus.Disabled,
        ResourceGroupName = "workloadinsight-demos",
        ServerName = "misosisvr",
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
		_, err := sql.NewServerAdvisor(ctx, "serverAdvisor", &sql.ServerAdvisorArgs{
			AdvisorName:       pulumi.String("CreateIndex"),
			AutoExecuteStatus: sql.AutoExecuteStatusDisabled,
			ResourceGroupName: pulumi.String("workloadinsight-demos"),
			ServerName:        pulumi.String("misosisvr"),
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
import com.pulumi.azurenative.sql.ServerAdvisor;
import com.pulumi.azurenative.sql.ServerAdvisorArgs;
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
        var serverAdvisor = new ServerAdvisor("serverAdvisor", ServerAdvisorArgs.builder()        
            .advisorName("CreateIndex")
            .autoExecuteStatus("Disabled")
            .resourceGroupName("workloadinsight-demos")
            .serverName("misosisvr")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const serverAdvisor = new azure_native.sql.ServerAdvisor("serverAdvisor", {
    advisorName: "CreateIndex",
    autoExecuteStatus: azure_native.sql.AutoExecuteStatus.Disabled,
    resourceGroupName: "workloadinsight-demos",
    serverName: "misosisvr",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

server_advisor = azure_native.sql.ServerAdvisor("serverAdvisor",
    advisor_name="CreateIndex",
    auto_execute_status=azure_native.sql.AutoExecuteStatus.DISABLED,
    resource_group_name="workloadinsight-demos",
    server_name="misosisvr")

```

```yaml
resources:
  serverAdvisor:
    type: azure-native:sql:ServerAdvisor
    properties:
      advisorName: CreateIndex
      autoExecuteStatus: Disabled
      resourceGroupName: workloadinsight-demos
      serverName: misosisvr

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:sql:ServerAdvisor CreateIndex /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/workloadinsight-demos/providers/Microsoft.Sql/servers/misosisvr/advisors/CreateIndex 
```
