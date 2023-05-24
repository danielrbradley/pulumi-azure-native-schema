Get the update summaries for the cluster
API Version: 2023-02-01.

{{% examples %}}
## Example Usage
{{% example %}}
### Put Update summaries under cluster resource
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var updateSummary = new AzureNative.AzureStackHCI.UpdateSummary("updateSummary", new()
    {
        ClusterName = "testcluster",
        CurrentVersion = "4.2203.2.32",
        HardwareModel = "PowerEdge R730xd",
        LastChecked = "2022-04-07T18:04:07Z",
        LastUpdated = "2022-04-06T14:08:18.254Z",
        OemFamily = "DellEMC",
        ResourceGroupName = "testrg",
        State = "AppliedSuccessfully",
    });

});


```

```go
package main

import (
	azurestackhci "github.com/pulumi/pulumi-azure-native-sdk/azurestackhci"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := azurestackhci.NewUpdateSummary(ctx, "updateSummary", &azurestackhci.UpdateSummaryArgs{
			ClusterName:       pulumi.String("testcluster"),
			CurrentVersion:    pulumi.String("4.2203.2.32"),
			HardwareModel:     pulumi.String("PowerEdge R730xd"),
			LastChecked:       pulumi.String("2022-04-07T18:04:07Z"),
			LastUpdated:       pulumi.String("2022-04-06T14:08:18.254Z"),
			OemFamily:         pulumi.String("DellEMC"),
			ResourceGroupName: pulumi.String("testrg"),
			State:             pulumi.String("AppliedSuccessfully"),
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
import com.pulumi.azurenative.azurestackhci.UpdateSummary;
import com.pulumi.azurenative.azurestackhci.UpdateSummaryArgs;
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
        var updateSummary = new UpdateSummary("updateSummary", UpdateSummaryArgs.builder()        
            .clusterName("testcluster")
            .currentVersion("4.2203.2.32")
            .hardwareModel("PowerEdge R730xd")
            .lastChecked("2022-04-07T18:04:07Z")
            .lastUpdated("2022-04-06T14:08:18.254Z")
            .oemFamily("DellEMC")
            .resourceGroupName("testrg")
            .state("AppliedSuccessfully")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const updateSummary = new azure_native.azurestackhci.UpdateSummary("updateSummary", {
    clusterName: "testcluster",
    currentVersion: "4.2203.2.32",
    hardwareModel: "PowerEdge R730xd",
    lastChecked: "2022-04-07T18:04:07Z",
    lastUpdated: "2022-04-06T14:08:18.254Z",
    oemFamily: "DellEMC",
    resourceGroupName: "testrg",
    state: "AppliedSuccessfully",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

update_summary = azure_native.azurestackhci.UpdateSummary("updateSummary",
    cluster_name="testcluster",
    current_version="4.2203.2.32",
    hardware_model="PowerEdge R730xd",
    last_checked="2022-04-07T18:04:07Z",
    last_updated="2022-04-06T14:08:18.254Z",
    oem_family="DellEMC",
    resource_group_name="testrg",
    state="AppliedSuccessfully")

```

```yaml
resources:
  updateSummary:
    type: azure-native:azurestackhci:UpdateSummary
    properties:
      clusterName: testcluster
      currentVersion: 4.2203.2.32
      hardwareModel: PowerEdge R730xd
      lastChecked: 2022-04-07T18:04:07Z
      lastUpdated: 2022-04-06T14:08:18.254Z
      oemFamily: DellEMC
      resourceGroupName: testrg
      state: AppliedSuccessfully

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:azurestackhci:UpdateSummary default /subscriptions/b8d594e5-51f3-4c11-9c54-a7771b81c712/resourceGroups/testrg/providers/Microsoft.AzureStackHCI/clusters/testcluster/updateSummaries/default 
```
