The volume container.
API Version: 2017-06-01.
Previous API Version: 2017-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### VolumeContainersCreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var volumeContainer = new AzureNative.StorSimple.VolumeContainer("volumeContainer", new()
    {
        BandwidthSettingId = "/subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/ResourceGroupForSDKTest/providers/Microsoft.StorSimple/managers/ManagerForSDKTest1/bandwidthSettings/bandwidthSetting1",
        DeviceName = "Device05ForSDKTest",
        EncryptionKey = new AzureNative.StorSimple.Inputs.AsymmetricEncryptedSecretArgs
        {
            EncryptionAlgorithm = AzureNative.StorSimple.EncryptionAlgorithm.RSAES_PKCS1_v_1_5,
            EncryptionCertThumbprint = "A872A2DF196AC7682EE24791E7DE2E2A360F5926",
            Value = "R//pyVLx/fn58ia098JiLgZB5RY7fVT+6o8a4fmsvjy+ls2UgJphMf25XVqEQCZnsp/5uxteN1M/9ArPIICdhM7M1+b/Ur7kJ0FH0ktxfk7CrPWWJLI4q20LZoduJGI56lREav1VpuLdqw5F9fRcq7zbfgPQ3B/SD0mfumNRiV+AnwbC6msfavIuWrhVDl9iSzEPE+zU06/kpsexnrS81yYT2QlVVUbvpY4F3zfH8TQPpAROTbv2pld6JO4eGOrZ5O1iOr6XCg2TY2W/jf+Ev4z5tqC9VWXE5kh65gjBfpWN0bDWXKekqEhor2crHAxZi4dybdY8Ok1MDWd1CSU8kw==",
        },
        ManagerName = "ManagerForSDKTest1",
        ResourceGroupName = "ResourceGroupForSDKTest",
        StorageAccountCredentialId = "/subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/ResourceGroupForSDKTest/providers/Microsoft.StorSimple/managers/ManagerForSDKTest1/storageAccountCredentials/safortestrecording",
        VolumeContainerName = "VolumeContainerForSDKTest",
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
		_, err := storsimple.NewVolumeContainer(ctx, "volumeContainer", &storsimple.VolumeContainerArgs{
			BandwidthSettingId: pulumi.String("/subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/ResourceGroupForSDKTest/providers/Microsoft.StorSimple/managers/ManagerForSDKTest1/bandwidthSettings/bandwidthSetting1"),
			DeviceName:         pulumi.String("Device05ForSDKTest"),
			EncryptionKey: &storsimple.AsymmetricEncryptedSecretArgs{
				EncryptionAlgorithm:      storsimple.EncryptionAlgorithm_RSAES_PKCS1_v_1_5,
				EncryptionCertThumbprint: pulumi.String("A872A2DF196AC7682EE24791E7DE2E2A360F5926"),
				Value:                    pulumi.String("R//pyVLx/fn58ia098JiLgZB5RY7fVT+6o8a4fmsvjy+ls2UgJphMf25XVqEQCZnsp/5uxteN1M/9ArPIICdhM7M1+b/Ur7kJ0FH0ktxfk7CrPWWJLI4q20LZoduJGI56lREav1VpuLdqw5F9fRcq7zbfgPQ3B/SD0mfumNRiV+AnwbC6msfavIuWrhVDl9iSzEPE+zU06/kpsexnrS81yYT2QlVVUbvpY4F3zfH8TQPpAROTbv2pld6JO4eGOrZ5O1iOr6XCg2TY2W/jf+Ev4z5tqC9VWXE5kh65gjBfpWN0bDWXKekqEhor2crHAxZi4dybdY8Ok1MDWd1CSU8kw=="),
			},
			ManagerName:                pulumi.String("ManagerForSDKTest1"),
			ResourceGroupName:          pulumi.String("ResourceGroupForSDKTest"),
			StorageAccountCredentialId: pulumi.String("/subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/ResourceGroupForSDKTest/providers/Microsoft.StorSimple/managers/ManagerForSDKTest1/storageAccountCredentials/safortestrecording"),
			VolumeContainerName:        pulumi.String("VolumeContainerForSDKTest"),
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
import com.pulumi.azurenative.storsimple.VolumeContainer;
import com.pulumi.azurenative.storsimple.VolumeContainerArgs;
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
        var volumeContainer = new VolumeContainer("volumeContainer", VolumeContainerArgs.builder()        
            .bandwidthSettingId("/subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/ResourceGroupForSDKTest/providers/Microsoft.StorSimple/managers/ManagerForSDKTest1/bandwidthSettings/bandwidthSetting1")
            .deviceName("Device05ForSDKTest")
            .encryptionKey(Map.ofEntries(
                Map.entry("encryptionAlgorithm", "RSAES_PKCS1_v_1_5"),
                Map.entry("encryptionCertThumbprint", "A872A2DF196AC7682EE24791E7DE2E2A360F5926"),
                Map.entry("value", "R//pyVLx/fn58ia098JiLgZB5RY7fVT+6o8a4fmsvjy+ls2UgJphMf25XVqEQCZnsp/5uxteN1M/9ArPIICdhM7M1+b/Ur7kJ0FH0ktxfk7CrPWWJLI4q20LZoduJGI56lREav1VpuLdqw5F9fRcq7zbfgPQ3B/SD0mfumNRiV+AnwbC6msfavIuWrhVDl9iSzEPE+zU06/kpsexnrS81yYT2QlVVUbvpY4F3zfH8TQPpAROTbv2pld6JO4eGOrZ5O1iOr6XCg2TY2W/jf+Ev4z5tqC9VWXE5kh65gjBfpWN0bDWXKekqEhor2crHAxZi4dybdY8Ok1MDWd1CSU8kw==")
            ))
            .managerName("ManagerForSDKTest1")
            .resourceGroupName("ResourceGroupForSDKTest")
            .storageAccountCredentialId("/subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/ResourceGroupForSDKTest/providers/Microsoft.StorSimple/managers/ManagerForSDKTest1/storageAccountCredentials/safortestrecording")
            .volumeContainerName("VolumeContainerForSDKTest")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const volumeContainer = new azure_native.storsimple.VolumeContainer("volumeContainer", {
    bandwidthSettingId: "/subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/ResourceGroupForSDKTest/providers/Microsoft.StorSimple/managers/ManagerForSDKTest1/bandwidthSettings/bandwidthSetting1",
    deviceName: "Device05ForSDKTest",
    encryptionKey: {
        encryptionAlgorithm: azure_native.storsimple.EncryptionAlgorithm.RSAES_PKCS1_v_1_5,
        encryptionCertThumbprint: "A872A2DF196AC7682EE24791E7DE2E2A360F5926",
        value: "R//pyVLx/fn58ia098JiLgZB5RY7fVT+6o8a4fmsvjy+ls2UgJphMf25XVqEQCZnsp/5uxteN1M/9ArPIICdhM7M1+b/Ur7kJ0FH0ktxfk7CrPWWJLI4q20LZoduJGI56lREav1VpuLdqw5F9fRcq7zbfgPQ3B/SD0mfumNRiV+AnwbC6msfavIuWrhVDl9iSzEPE+zU06/kpsexnrS81yYT2QlVVUbvpY4F3zfH8TQPpAROTbv2pld6JO4eGOrZ5O1iOr6XCg2TY2W/jf+Ev4z5tqC9VWXE5kh65gjBfpWN0bDWXKekqEhor2crHAxZi4dybdY8Ok1MDWd1CSU8kw==",
    },
    managerName: "ManagerForSDKTest1",
    resourceGroupName: "ResourceGroupForSDKTest",
    storageAccountCredentialId: "/subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/ResourceGroupForSDKTest/providers/Microsoft.StorSimple/managers/ManagerForSDKTest1/storageAccountCredentials/safortestrecording",
    volumeContainerName: "VolumeContainerForSDKTest",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

volume_container = azure_native.storsimple.VolumeContainer("volumeContainer",
    bandwidth_setting_id="/subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/ResourceGroupForSDKTest/providers/Microsoft.StorSimple/managers/ManagerForSDKTest1/bandwidthSettings/bandwidthSetting1",
    device_name="Device05ForSDKTest",
    encryption_key=azure_native.storsimple.AsymmetricEncryptedSecretArgs(
        encryption_algorithm=azure_native.storsimple.EncryptionAlgorithm.RSAE_S_PKCS1_V_1_5,
        encryption_cert_thumbprint="A872A2DF196AC7682EE24791E7DE2E2A360F5926",
        value="R//pyVLx/fn58ia098JiLgZB5RY7fVT+6o8a4fmsvjy+ls2UgJphMf25XVqEQCZnsp/5uxteN1M/9ArPIICdhM7M1+b/Ur7kJ0FH0ktxfk7CrPWWJLI4q20LZoduJGI56lREav1VpuLdqw5F9fRcq7zbfgPQ3B/SD0mfumNRiV+AnwbC6msfavIuWrhVDl9iSzEPE+zU06/kpsexnrS81yYT2QlVVUbvpY4F3zfH8TQPpAROTbv2pld6JO4eGOrZ5O1iOr6XCg2TY2W/jf+Ev4z5tqC9VWXE5kh65gjBfpWN0bDWXKekqEhor2crHAxZi4dybdY8Ok1MDWd1CSU8kw==",
    ),
    manager_name="ManagerForSDKTest1",
    resource_group_name="ResourceGroupForSDKTest",
    storage_account_credential_id="/subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/ResourceGroupForSDKTest/providers/Microsoft.StorSimple/managers/ManagerForSDKTest1/storageAccountCredentials/safortestrecording",
    volume_container_name="VolumeContainerForSDKTest")

```

```yaml
resources:
  volumeContainer:
    type: azure-native:storsimple:VolumeContainer
    properties:
      bandwidthSettingId: /subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/ResourceGroupForSDKTest/providers/Microsoft.StorSimple/managers/ManagerForSDKTest1/bandwidthSettings/bandwidthSetting1
      deviceName: Device05ForSDKTest
      encryptionKey:
        encryptionAlgorithm: RSAES_PKCS1_v_1_5
        encryptionCertThumbprint: A872A2DF196AC7682EE24791E7DE2E2A360F5926
        value: R//pyVLx/fn58ia098JiLgZB5RY7fVT+6o8a4fmsvjy+ls2UgJphMf25XVqEQCZnsp/5uxteN1M/9ArPIICdhM7M1+b/Ur7kJ0FH0ktxfk7CrPWWJLI4q20LZoduJGI56lREav1VpuLdqw5F9fRcq7zbfgPQ3B/SD0mfumNRiV+AnwbC6msfavIuWrhVDl9iSzEPE+zU06/kpsexnrS81yYT2QlVVUbvpY4F3zfH8TQPpAROTbv2pld6JO4eGOrZ5O1iOr6XCg2TY2W/jf+Ev4z5tqC9VWXE5kh65gjBfpWN0bDWXKekqEhor2crHAxZi4dybdY8Ok1MDWd1CSU8kw==
      managerName: ManagerForSDKTest1
      resourceGroupName: ResourceGroupForSDKTest
      storageAccountCredentialId: /subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/ResourceGroupForSDKTest/providers/Microsoft.StorSimple/managers/ManagerForSDKTest1/storageAccountCredentials/safortestrecording
      volumeContainerName: VolumeContainerForSDKTest

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:storsimple:VolumeContainer VolumeContainerForSDKTest /subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/ResourceGroupForSDKTest/providers/Microsoft.StorSimple/managers/ManagerForSDKTest1/devices/Device05ForSDKTest/volumeContainers/VolumeContainerForSDKTest 
```
