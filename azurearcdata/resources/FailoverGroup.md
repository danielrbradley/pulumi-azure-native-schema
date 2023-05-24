A failover group resource.
API Version: 2023-03-15-preview.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a failover group instance.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var failoverGroup = new AzureNative.AzureArcData.FailoverGroup("failoverGroup", new()
    {
        FailoverGroupName = "testFailoverGroupName",
        Properties = new AzureNative.AzureArcData.Inputs.FailoverGroupPropertiesArgs
        {
            PartnerManagedInstanceId = "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.AzureArcData/sqlManagedInstances/partnerMI",
            Spec = new AzureNative.AzureArcData.Inputs.FailoverGroupSpecArgs
            {
                PartnerSyncMode = "async",
                Role = "primary",
            },
        },
        ResourceGroupName = "testrg",
        SqlManagedInstanceName = "testSqlManagedInstance",
    });

});


```

```go
package main

import (
	azurearcdata "github.com/pulumi/pulumi-azure-native-sdk/azurearcdata"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := azurearcdata.NewFailoverGroup(ctx, "failoverGroup", &azurearcdata.FailoverGroupArgs{
			FailoverGroupName: pulumi.String("testFailoverGroupName"),
			Properties: azurearcdata.FailoverGroupPropertiesResponse{
				PartnerManagedInstanceId: pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.AzureArcData/sqlManagedInstances/partnerMI"),
				Spec: &azurearcdata.FailoverGroupSpecArgs{
					PartnerSyncMode: pulumi.String("async"),
					Role:            pulumi.String("primary"),
				},
			},
			ResourceGroupName:      pulumi.String("testrg"),
			SqlManagedInstanceName: pulumi.String("testSqlManagedInstance"),
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
import com.pulumi.azurenative.azurearcdata.FailoverGroup;
import com.pulumi.azurenative.azurearcdata.FailoverGroupArgs;
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
        var failoverGroup = new FailoverGroup("failoverGroup", FailoverGroupArgs.builder()        
            .failoverGroupName("testFailoverGroupName")
            .properties(Map.ofEntries(
                Map.entry("partnerManagedInstanceId", "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.AzureArcData/sqlManagedInstances/partnerMI"),
                Map.entry("spec", Map.ofEntries(
                    Map.entry("partnerSyncMode", "async"),
                    Map.entry("role", "primary")
                ))
            ))
            .resourceGroupName("testrg")
            .sqlManagedInstanceName("testSqlManagedInstance")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const failoverGroup = new azure_native.azurearcdata.FailoverGroup("failoverGroup", {
    failoverGroupName: "testFailoverGroupName",
    properties: {
        partnerManagedInstanceId: "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.AzureArcData/sqlManagedInstances/partnerMI",
        spec: {
            partnerSyncMode: "async",
            role: "primary",
        },
    },
    resourceGroupName: "testrg",
    sqlManagedInstanceName: "testSqlManagedInstance",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

failover_group = azure_native.azurearcdata.FailoverGroup("failoverGroup",
    failover_group_name="testFailoverGroupName",
    properties=azure_native.azurearcdata.FailoverGroupPropertiesResponseArgs(
        partner_managed_instance_id="/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.AzureArcData/sqlManagedInstances/partnerMI",
        spec=azure_native.azurearcdata.FailoverGroupSpecArgs(
            partner_sync_mode="async",
            role="primary",
        ),
    ),
    resource_group_name="testrg",
    sql_managed_instance_name="testSqlManagedInstance")

```

```yaml
resources:
  failoverGroup:
    type: azure-native:azurearcdata:FailoverGroup
    properties:
      failoverGroupName: testFailoverGroupName
      properties:
        partnerManagedInstanceId: /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.AzureArcData/sqlManagedInstances/partnerMI
        spec:
          partnerSyncMode: async
          role: primary
      resourceGroupName: testrg
      sqlManagedInstanceName: testSqlManagedInstance

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:azurearcdata:FailoverGroup testFailoverGroupName /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.AzureArcData/sqlManagedInstances/testSqlManagedInstance/failoverGroups/testFailoverGroupName 
```
