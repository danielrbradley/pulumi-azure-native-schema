The Connection Monitor Test class.
API Version: 2022-10-01.
Previous API Version: 2021-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or Update Connection Monitor Test
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var connectionMonitorTest = new AzureNative.Peering.ConnectionMonitorTest("connectionMonitorTest", new()
    {
        ConnectionMonitorTestName = "connectionMonitorTestName",
        Destination = "Example Destination",
        DestinationPort = 443,
        PeeringServiceName = "peeringServiceName",
        ResourceGroupName = "rgName",
        SourceAgent = "Example Source Agent",
        TestFrequencyInSec = 30,
    });

});


```

```go
package main

import (
	peering "github.com/pulumi/pulumi-azure-native-sdk/peering"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := peering.NewConnectionMonitorTest(ctx, "connectionMonitorTest", &peering.ConnectionMonitorTestArgs{
			ConnectionMonitorTestName: pulumi.String("connectionMonitorTestName"),
			Destination:               pulumi.String("Example Destination"),
			DestinationPort:           pulumi.Int(443),
			PeeringServiceName:        pulumi.String("peeringServiceName"),
			ResourceGroupName:         pulumi.String("rgName"),
			SourceAgent:               pulumi.String("Example Source Agent"),
			TestFrequencyInSec:        pulumi.Int(30),
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
import com.pulumi.azurenative.peering.ConnectionMonitorTest;
import com.pulumi.azurenative.peering.ConnectionMonitorTestArgs;
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
        var connectionMonitorTest = new ConnectionMonitorTest("connectionMonitorTest", ConnectionMonitorTestArgs.builder()        
            .connectionMonitorTestName("connectionMonitorTestName")
            .destination("Example Destination")
            .destinationPort(443)
            .peeringServiceName("peeringServiceName")
            .resourceGroupName("rgName")
            .sourceAgent("Example Source Agent")
            .testFrequencyInSec(30)
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const connectionMonitorTest = new azure_native.peering.ConnectionMonitorTest("connectionMonitorTest", {
    connectionMonitorTestName: "connectionMonitorTestName",
    destination: "Example Destination",
    destinationPort: 443,
    peeringServiceName: "peeringServiceName",
    resourceGroupName: "rgName",
    sourceAgent: "Example Source Agent",
    testFrequencyInSec: 30,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

connection_monitor_test = azure_native.peering.ConnectionMonitorTest("connectionMonitorTest",
    connection_monitor_test_name="connectionMonitorTestName",
    destination="Example Destination",
    destination_port=443,
    peering_service_name="peeringServiceName",
    resource_group_name="rgName",
    source_agent="Example Source Agent",
    test_frequency_in_sec=30)

```

```yaml
resources:
  connectionMonitorTest:
    type: azure-native:peering:ConnectionMonitorTest
    properties:
      connectionMonitorTestName: connectionMonitorTestName
      destination: Example Destination
      destinationPort: 443
      peeringServiceName: peeringServiceName
      resourceGroupName: rgName
      sourceAgent: Example Source Agent
      testFrequencyInSec: 30

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:peering:ConnectionMonitorTest connectionMonitorTestName /subscriptions/subId/resourceGroups/rgName/providers/Microsoft.Peering/peeringServices/peeringServiceName/connectionMonitorTests/connectionMonitorTestName 
```
