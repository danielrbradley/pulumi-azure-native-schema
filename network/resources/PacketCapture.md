Information about packet capture session.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create packet capture
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var packetCapture = new AzureNative.Network.PacketCapture("packetCapture", new()
    {
        BytesToCapturePerPacket = 10000,
        Filters = new[]
        {
            new AzureNative.Network.Inputs.PacketCaptureFilterArgs
            {
                LocalIPAddress = "10.0.0.4",
                LocalPort = "80",
                Protocol = "TCP",
            },
        },
        NetworkWatcherName = "nw1",
        PacketCaptureName = "pc1",
        ResourceGroupName = "rg1",
        StorageLocation = new AzureNative.Network.Inputs.PacketCaptureStorageLocationArgs
        {
            FilePath = "D:\\capture\\pc1.cap",
            StorageId = "/subscriptions/subid/resourceGroups/rg2/providers/Microsoft.Storage/storageAccounts/pcstore",
            StoragePath = "https://mytestaccountname.blob.core.windows.net/capture/pc1.cap",
        },
        Target = "/subscriptions/subid/resourceGroups/rg2/providers/Microsoft.Compute/virtualMachines/vm1",
        TimeLimitInSeconds = 100,
        TotalBytesPerSession = 100000,
    });

});


```

```go
package main

import (
	network "github.com/pulumi/pulumi-azure-native-sdk/network"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := network.NewPacketCapture(ctx, "packetCapture", &network.PacketCaptureArgs{
			BytesToCapturePerPacket: pulumi.Float64(10000),
			Filters: []network.PacketCaptureFilterArgs{
				{
					LocalIPAddress: pulumi.String("10.0.0.4"),
					LocalPort:      pulumi.String("80"),
					Protocol:       pulumi.String("TCP"),
				},
			},
			NetworkWatcherName: pulumi.String("nw1"),
			PacketCaptureName:  pulumi.String("pc1"),
			ResourceGroupName:  pulumi.String("rg1"),
			StorageLocation: &network.PacketCaptureStorageLocationArgs{
				FilePath:    pulumi.String("D:\\capture\\pc1.cap"),
				StorageId:   pulumi.String("/subscriptions/subid/resourceGroups/rg2/providers/Microsoft.Storage/storageAccounts/pcstore"),
				StoragePath: pulumi.String("https://mytestaccountname.blob.core.windows.net/capture/pc1.cap"),
			},
			Target:               pulumi.String("/subscriptions/subid/resourceGroups/rg2/providers/Microsoft.Compute/virtualMachines/vm1"),
			TimeLimitInSeconds:   pulumi.Int(100),
			TotalBytesPerSession: pulumi.Float64(100000),
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
import com.pulumi.azurenative.network.PacketCapture;
import com.pulumi.azurenative.network.PacketCaptureArgs;
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
        var packetCapture = new PacketCapture("packetCapture", PacketCaptureArgs.builder()        
            .bytesToCapturePerPacket(10000)
            .filters(Map.ofEntries(
                Map.entry("localIPAddress", "10.0.0.4"),
                Map.entry("localPort", "80"),
                Map.entry("protocol", "TCP")
            ))
            .networkWatcherName("nw1")
            .packetCaptureName("pc1")
            .resourceGroupName("rg1")
            .storageLocation(Map.ofEntries(
                Map.entry("filePath", "D:\\capture\\pc1.cap"),
                Map.entry("storageId", "/subscriptions/subid/resourceGroups/rg2/providers/Microsoft.Storage/storageAccounts/pcstore"),
                Map.entry("storagePath", "https://mytestaccountname.blob.core.windows.net/capture/pc1.cap")
            ))
            .target("/subscriptions/subid/resourceGroups/rg2/providers/Microsoft.Compute/virtualMachines/vm1")
            .timeLimitInSeconds(100)
            .totalBytesPerSession(100000)
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const packetCapture = new azure_native.network.PacketCapture("packetCapture", {
    bytesToCapturePerPacket: 10000,
    filters: [{
        localIPAddress: "10.0.0.4",
        localPort: "80",
        protocol: "TCP",
    }],
    networkWatcherName: "nw1",
    packetCaptureName: "pc1",
    resourceGroupName: "rg1",
    storageLocation: {
        filePath: "D:\\capture\\pc1.cap",
        storageId: "/subscriptions/subid/resourceGroups/rg2/providers/Microsoft.Storage/storageAccounts/pcstore",
        storagePath: "https://mytestaccountname.blob.core.windows.net/capture/pc1.cap",
    },
    target: "/subscriptions/subid/resourceGroups/rg2/providers/Microsoft.Compute/virtualMachines/vm1",
    timeLimitInSeconds: 100,
    totalBytesPerSession: 100000,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

packet_capture = azure_native.network.PacketCapture("packetCapture",
    bytes_to_capture_per_packet=10000,
    filters=[azure_native.network.PacketCaptureFilterArgs(
        local_ip_address="10.0.0.4",
        local_port="80",
        protocol="TCP",
    )],
    network_watcher_name="nw1",
    packet_capture_name="pc1",
    resource_group_name="rg1",
    storage_location=azure_native.network.PacketCaptureStorageLocationArgs(
        file_path="D:\\capture\\pc1.cap",
        storage_id="/subscriptions/subid/resourceGroups/rg2/providers/Microsoft.Storage/storageAccounts/pcstore",
        storage_path="https://mytestaccountname.blob.core.windows.net/capture/pc1.cap",
    ),
    target="/subscriptions/subid/resourceGroups/rg2/providers/Microsoft.Compute/virtualMachines/vm1",
    time_limit_in_seconds=100,
    total_bytes_per_session=100000)

```

```yaml
resources:
  packetCapture:
    type: azure-native:network:PacketCapture
    properties:
      bytesToCapturePerPacket: 10000
      filters:
        - localIPAddress: 10.0.0.4
          localPort: '80'
          protocol: TCP
      networkWatcherName: nw1
      packetCaptureName: pc1
      resourceGroupName: rg1
      storageLocation:
        filePath: D:\capture\pc1.cap
        storageId: /subscriptions/subid/resourceGroups/rg2/providers/Microsoft.Storage/storageAccounts/pcstore
        storagePath: https://mytestaccountname.blob.core.windows.net/capture/pc1.cap
      target: /subscriptions/subid/resourceGroups/rg2/providers/Microsoft.Compute/virtualMachines/vm1
      timeLimitInSeconds: 100
      totalBytesPerSession: 100000

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:PacketCapture pc1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/networkWatchers/nw1/packetCaptures/pc1 
```
