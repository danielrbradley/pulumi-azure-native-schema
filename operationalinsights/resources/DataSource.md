Datasources under OMS Workspace.
API Version: 2020-08-01.
Previous API Version: 2020-08-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### DataSourcesCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var dataSource = new AzureNative.OperationalInsights.DataSource("dataSource", new()
    {
        DataSourceName = "AzTestDS774",
        Kind = "AzureActivityLog",
        Properties = 
        {
            { "LinkedResourceId", "/subscriptions/00000000-0000-0000-0000-00000000000/providers/microsoft.insights/eventtypes/management" },
        },
        ResourceGroupName = "OIAutoRest5123",
        WorkspaceName = "AzTest9724",
    });

});


```

```go
package main

import (
	operationalinsights "github.com/pulumi/pulumi-azure-native-sdk/operationalinsights"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := operationalinsights.NewDataSource(ctx, "dataSource", &operationalinsights.DataSourceArgs{
			DataSourceName: pulumi.String("AzTestDS774"),
			Kind:           pulumi.String("AzureActivityLog"),
			Properties: pulumi.Any{
				LinkedResourceId: "/subscriptions/00000000-0000-0000-0000-00000000000/providers/microsoft.insights/eventtypes/management",
			},
			ResourceGroupName: pulumi.String("OIAutoRest5123"),
			WorkspaceName:     pulumi.String("AzTest9724"),
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
import com.pulumi.azurenative.operationalinsights.DataSource;
import com.pulumi.azurenative.operationalinsights.DataSourceArgs;
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
        var dataSource = new DataSource("dataSource", DataSourceArgs.builder()        
            .dataSourceName("AzTestDS774")
            .kind("AzureActivityLog")
            .properties(Map.of("LinkedResourceId", "/subscriptions/00000000-0000-0000-0000-00000000000/providers/microsoft.insights/eventtypes/management"))
            .resourceGroupName("OIAutoRest5123")
            .workspaceName("AzTest9724")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const dataSource = new azure_native.operationalinsights.DataSource("dataSource", {
    dataSourceName: "AzTestDS774",
    kind: "AzureActivityLog",
    properties: {
        LinkedResourceId: "/subscriptions/00000000-0000-0000-0000-00000000000/providers/microsoft.insights/eventtypes/management",
    },
    resourceGroupName: "OIAutoRest5123",
    workspaceName: "AzTest9724",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

data_source = azure_native.operationalinsights.DataSource("dataSource",
    data_source_name="AzTestDS774",
    kind="AzureActivityLog",
    properties={
        "LinkedResourceId": "/subscriptions/00000000-0000-0000-0000-00000000000/providers/microsoft.insights/eventtypes/management",
    },
    resource_group_name="OIAutoRest5123",
    workspace_name="AzTest9724")

```

```yaml
resources:
  dataSource:
    type: azure-native:operationalinsights:DataSource
    properties:
      dataSourceName: AzTestDS774
      kind: AzureActivityLog
      properties:
        LinkedResourceId: /subscriptions/00000000-0000-0000-0000-00000000000/providers/microsoft.insights/eventtypes/management
      resourceGroupName: OIAutoRest5123
      workspaceName: AzTest9724

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:operationalinsights:DataSource AzTestDS774 /subscriptions/00000000-0000-0000-0000-000000000005/resourceGroups/OIAutoRest5123/providers/Microsoft.OperationalInsights/workspaces/AzTest9724/datasources/AzTestDS774 
```
