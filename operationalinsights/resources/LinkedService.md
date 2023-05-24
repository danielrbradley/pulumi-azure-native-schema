The top level Linked service resource container.
API Version: 2020-08-01.
Previous API Version: 2020-08-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### LinkedServicesCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var linkedService = new AzureNative.OperationalInsights.LinkedService("linkedService", new()
    {
        LinkedServiceName = "Cluster",
        ResourceGroupName = "mms-eus",
        WorkspaceName = "TestLinkWS",
        WriteAccessResourceId = "/subscriptions/00000000-0000-0000-0000-00000000000/resourceGroups/mms-eus/providers/Microsoft.OperationalInsights/clusters/testcluster",
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
		_, err := operationalinsights.NewLinkedService(ctx, "linkedService", &operationalinsights.LinkedServiceArgs{
			LinkedServiceName:     pulumi.String("Cluster"),
			ResourceGroupName:     pulumi.String("mms-eus"),
			WorkspaceName:         pulumi.String("TestLinkWS"),
			WriteAccessResourceId: pulumi.String("/subscriptions/00000000-0000-0000-0000-00000000000/resourceGroups/mms-eus/providers/Microsoft.OperationalInsights/clusters/testcluster"),
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
import com.pulumi.azurenative.operationalinsights.LinkedService;
import com.pulumi.azurenative.operationalinsights.LinkedServiceArgs;
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
        var linkedService = new LinkedService("linkedService", LinkedServiceArgs.builder()        
            .linkedServiceName("Cluster")
            .resourceGroupName("mms-eus")
            .workspaceName("TestLinkWS")
            .writeAccessResourceId("/subscriptions/00000000-0000-0000-0000-00000000000/resourceGroups/mms-eus/providers/Microsoft.OperationalInsights/clusters/testcluster")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const linkedService = new azure_native.operationalinsights.LinkedService("linkedService", {
    linkedServiceName: "Cluster",
    resourceGroupName: "mms-eus",
    workspaceName: "TestLinkWS",
    writeAccessResourceId: "/subscriptions/00000000-0000-0000-0000-00000000000/resourceGroups/mms-eus/providers/Microsoft.OperationalInsights/clusters/testcluster",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

linked_service = azure_native.operationalinsights.LinkedService("linkedService",
    linked_service_name="Cluster",
    resource_group_name="mms-eus",
    workspace_name="TestLinkWS",
    write_access_resource_id="/subscriptions/00000000-0000-0000-0000-00000000000/resourceGroups/mms-eus/providers/Microsoft.OperationalInsights/clusters/testcluster")

```

```yaml
resources:
  linkedService:
    type: azure-native:operationalinsights:LinkedService
    properties:
      linkedServiceName: Cluster
      resourceGroupName: mms-eus
      workspaceName: TestLinkWS
      writeAccessResourceId: /subscriptions/00000000-0000-0000-0000-00000000000/resourceGroups/mms-eus/providers/Microsoft.OperationalInsights/clusters/testcluster

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:operationalinsights:LinkedService TestLinkWS/Cluster /subscriptions/00000000-0000-0000-0000-00000000000/resourcegroups/mms-eus/providers/microsoft.operationalinsights/workspaces/testlinkws/linkedservices/cluster 
```
