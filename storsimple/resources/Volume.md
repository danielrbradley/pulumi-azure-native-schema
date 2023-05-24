The volume.
API Version: 2017-06-01.
Previous API Version: 2017-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### VolumesCreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var volume = new AzureNative.StorSimple.Volume("volume", new()
    {
        AccessControlRecordIds = new[]
        {
            "/subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/ResourceGroupForSDKTest/providers/Microsoft.StorSimple/managers/ManagerForSDKTest1/accessControlRecords/ACR2",
        },
        DeviceName = "Device05ForSDKTest",
        ManagerName = "ManagerForSDKTest1",
        MonitoringStatus = AzureNative.StorSimple.MonitoringStatus.Enabled,
        ResourceGroupName = "ResourceGroupForSDKTest",
        SizeInBytes = 5368709120,
        VolumeContainerName = "VolumeContainerForSDKTest",
        VolumeName = "Volume1ForSDKTest",
        VolumeStatus = AzureNative.StorSimple.VolumeStatus.Offline,
        VolumeType = AzureNative.StorSimple.VolumeType.Tiered,
    });

});


```

```go
package main

import (
	storsimple "github.com/pulumi/pulumi-azure-native-sdk/storsimple"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := storsimple.NewVolume(ctx, "volume", &storsimple.VolumeArgs{
			AccessControlRecordIds: pulumi.StringArray{
				pulumi.String("/subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/ResourceGroupForSDKTest/providers/Microsoft.StorSimple/managers/ManagerForSDKTest1/accessControlRecords/ACR2"),
			},
			DeviceName:          pulumi.String("Device05ForSDKTest"),
			ManagerName:         pulumi.String("ManagerForSDKTest1"),
			MonitoringStatus:    storsimple.MonitoringStatusEnabled,
			ResourceGroupName:   pulumi.String("ResourceGroupForSDKTest"),
			SizeInBytes:         pulumi.Float64(5368709120),
			VolumeContainerName: pulumi.String("VolumeContainerForSDKTest"),
			VolumeName:          pulumi.String("Volume1ForSDKTest"),
			VolumeStatus:        storsimple.VolumeStatusOffline,
			VolumeType:          storsimple.VolumeTypeTiered,
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
import com.pulumi.azurenative.storsimple.Volume;
import com.pulumi.azurenative.storsimple.VolumeArgs;
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
        var volume = new Volume("volume", VolumeArgs.builder()        
            .accessControlRecordIds("/subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/ResourceGroupForSDKTest/providers/Microsoft.StorSimple/managers/ManagerForSDKTest1/accessControlRecords/ACR2")
            .deviceName("Device05ForSDKTest")
            .managerName("ManagerForSDKTest1")
            .monitoringStatus("Enabled")
            .resourceGroupName("ResourceGroupForSDKTest")
            .sizeInBytes(5368709120)
            .volumeContainerName("VolumeContainerForSDKTest")
            .volumeName("Volume1ForSDKTest")
            .volumeStatus("Offline")
            .volumeType("Tiered")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const volume = new azure_native.storsimple.Volume("volume", {
    accessControlRecordIds: ["/subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/ResourceGroupForSDKTest/providers/Microsoft.StorSimple/managers/ManagerForSDKTest1/accessControlRecords/ACR2"],
    deviceName: "Device05ForSDKTest",
    managerName: "ManagerForSDKTest1",
    monitoringStatus: azure_native.storsimple.MonitoringStatus.Enabled,
    resourceGroupName: "ResourceGroupForSDKTest",
    sizeInBytes: 5368709120,
    volumeContainerName: "VolumeContainerForSDKTest",
    volumeName: "Volume1ForSDKTest",
    volumeStatus: azure_native.storsimple.VolumeStatus.Offline,
    volumeType: azure_native.storsimple.VolumeType.Tiered,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

volume = azure_native.storsimple.Volume("volume",
    access_control_record_ids=["/subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/ResourceGroupForSDKTest/providers/Microsoft.StorSimple/managers/ManagerForSDKTest1/accessControlRecords/ACR2"],
    device_name="Device05ForSDKTest",
    manager_name="ManagerForSDKTest1",
    monitoring_status=azure_native.storsimple.MonitoringStatus.ENABLED,
    resource_group_name="ResourceGroupForSDKTest",
    size_in_bytes=5368709120,
    volume_container_name="VolumeContainerForSDKTest",
    volume_name="Volume1ForSDKTest",
    volume_status=azure_native.storsimple.VolumeStatus.OFFLINE,
    volume_type=azure_native.storsimple.VolumeType.TIERED)

```

```yaml
resources:
  volume:
    type: azure-native:storsimple:Volume
    properties:
      accessControlRecordIds:
        - /subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/ResourceGroupForSDKTest/providers/Microsoft.StorSimple/managers/ManagerForSDKTest1/accessControlRecords/ACR2
      deviceName: Device05ForSDKTest
      managerName: ManagerForSDKTest1
      monitoringStatus: Enabled
      resourceGroupName: ResourceGroupForSDKTest
      sizeInBytes: 5.36870912e+09
      volumeContainerName: VolumeContainerForSDKTest
      volumeName: Volume1ForSDKTest
      volumeStatus: Offline
      volumeType: Tiered

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:storsimple:Volume Volume1ForSDKTest /subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/ResourceGroupForSDKTest/providers/Microsoft.StorSimple/managers/ManagerForSDKTest1/devices/Device05ForSDKTest/volumeContainers/VolumeContainerForSDKTest/volumes/Volume1ForSDKTest 
```
