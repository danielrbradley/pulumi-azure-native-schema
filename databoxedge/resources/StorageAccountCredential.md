The storage account credential.
API Version: 2022-03-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### SACPut
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var storageAccountCredential = new AzureNative.DataBoxEdge.StorageAccountCredential("storageAccountCredential", new()
    {
        AccountKey = new AzureNative.DataBoxEdge.Inputs.AsymmetricEncryptedSecretArgs
        {
            EncryptionAlgorithm = "AES256",
            EncryptionCertThumbprint = "2A9D8D6BE51574B5461230AEF02F162C5F01AD31",
            Value = "lAeZEYi6rNP1/EyNaVUYmTSZEYyaIaWmwUsGwek0+xiZj54GM9Ue9/UA2ed/ClC03wuSit2XzM/cLRU5eYiFBwks23rGwiQOr3sruEL2a74EjPD050xYjA6M1I2hu/w2yjVHhn5j+DbXS4Xzi+rHHNZK3DgfDO3PkbECjPck+PbpSBjy9+6Mrjcld5DIZhUAeMlMHrFlg+WKRKB14o/og56u5/xX6WKlrMLEQ+y6E18dUwvWs2elTNoVO8PBE8SM/CfooX4AMNvaNdSObNBPdP+F6Lzc556nFNWXrBLRt0vC7s9qTiVRO4x/qCNaK/B4y7IqXMllwQFf4Np9UQ2ECA==",
        },
        AccountType = "BlobStorage",
        Alias = "sac1",
        DeviceName = "testedgedevice",
        Name = "sac1",
        ResourceGroupName = "GroupForEdgeAutomation",
        SslStatus = "Disabled",
        UserName = "cisbvt",
    });

});


```

```go
package main

import (
	databoxedge "github.com/pulumi/pulumi-azure-native-sdk/databoxedge"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := databoxedge.NewStorageAccountCredential(ctx, "storageAccountCredential", &databoxedge.StorageAccountCredentialArgs{
			AccountKey: &databoxedge.AsymmetricEncryptedSecretArgs{
				EncryptionAlgorithm:      pulumi.String("AES256"),
				EncryptionCertThumbprint: pulumi.String("2A9D8D6BE51574B5461230AEF02F162C5F01AD31"),
				Value:                    pulumi.String("lAeZEYi6rNP1/EyNaVUYmTSZEYyaIaWmwUsGwek0+xiZj54GM9Ue9/UA2ed/ClC03wuSit2XzM/cLRU5eYiFBwks23rGwiQOr3sruEL2a74EjPD050xYjA6M1I2hu/w2yjVHhn5j+DbXS4Xzi+rHHNZK3DgfDO3PkbECjPck+PbpSBjy9+6Mrjcld5DIZhUAeMlMHrFlg+WKRKB14o/og56u5/xX6WKlrMLEQ+y6E18dUwvWs2elTNoVO8PBE8SM/CfooX4AMNvaNdSObNBPdP+F6Lzc556nFNWXrBLRt0vC7s9qTiVRO4x/qCNaK/B4y7IqXMllwQFf4Np9UQ2ECA=="),
			},
			AccountType:       pulumi.String("BlobStorage"),
			Alias:             pulumi.String("sac1"),
			DeviceName:        pulumi.String("testedgedevice"),
			Name:              pulumi.String("sac1"),
			ResourceGroupName: pulumi.String("GroupForEdgeAutomation"),
			SslStatus:         pulumi.String("Disabled"),
			UserName:          pulumi.String("cisbvt"),
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
import com.pulumi.azurenative.databoxedge.StorageAccountCredential;
import com.pulumi.azurenative.databoxedge.StorageAccountCredentialArgs;
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
        var storageAccountCredential = new StorageAccountCredential("storageAccountCredential", StorageAccountCredentialArgs.builder()        
            .accountKey(Map.ofEntries(
                Map.entry("encryptionAlgorithm", "AES256"),
                Map.entry("encryptionCertThumbprint", "2A9D8D6BE51574B5461230AEF02F162C5F01AD31"),
                Map.entry("value", "lAeZEYi6rNP1/EyNaVUYmTSZEYyaIaWmwUsGwek0+xiZj54GM9Ue9/UA2ed/ClC03wuSit2XzM/cLRU5eYiFBwks23rGwiQOr3sruEL2a74EjPD050xYjA6M1I2hu/w2yjVHhn5j+DbXS4Xzi+rHHNZK3DgfDO3PkbECjPck+PbpSBjy9+6Mrjcld5DIZhUAeMlMHrFlg+WKRKB14o/og56u5/xX6WKlrMLEQ+y6E18dUwvWs2elTNoVO8PBE8SM/CfooX4AMNvaNdSObNBPdP+F6Lzc556nFNWXrBLRt0vC7s9qTiVRO4x/qCNaK/B4y7IqXMllwQFf4Np9UQ2ECA==")
            ))
            .accountType("BlobStorage")
            .alias("sac1")
            .deviceName("testedgedevice")
            .name("sac1")
            .resourceGroupName("GroupForEdgeAutomation")
            .sslStatus("Disabled")
            .userName("cisbvt")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const storageAccountCredential = new azure_native.databoxedge.StorageAccountCredential("storageAccountCredential", {
    accountKey: {
        encryptionAlgorithm: "AES256",
        encryptionCertThumbprint: "2A9D8D6BE51574B5461230AEF02F162C5F01AD31",
        value: "lAeZEYi6rNP1/EyNaVUYmTSZEYyaIaWmwUsGwek0+xiZj54GM9Ue9/UA2ed/ClC03wuSit2XzM/cLRU5eYiFBwks23rGwiQOr3sruEL2a74EjPD050xYjA6M1I2hu/w2yjVHhn5j+DbXS4Xzi+rHHNZK3DgfDO3PkbECjPck+PbpSBjy9+6Mrjcld5DIZhUAeMlMHrFlg+WKRKB14o/og56u5/xX6WKlrMLEQ+y6E18dUwvWs2elTNoVO8PBE8SM/CfooX4AMNvaNdSObNBPdP+F6Lzc556nFNWXrBLRt0vC7s9qTiVRO4x/qCNaK/B4y7IqXMllwQFf4Np9UQ2ECA==",
    },
    accountType: "BlobStorage",
    alias: "sac1",
    deviceName: "testedgedevice",
    name: "sac1",
    resourceGroupName: "GroupForEdgeAutomation",
    sslStatus: "Disabled",
    userName: "cisbvt",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

storage_account_credential = azure_native.databoxedge.StorageAccountCredential("storageAccountCredential",
    account_key=azure_native.databoxedge.AsymmetricEncryptedSecretArgs(
        encryption_algorithm="AES256",
        encryption_cert_thumbprint="2A9D8D6BE51574B5461230AEF02F162C5F01AD31",
        value="lAeZEYi6rNP1/EyNaVUYmTSZEYyaIaWmwUsGwek0+xiZj54GM9Ue9/UA2ed/ClC03wuSit2XzM/cLRU5eYiFBwks23rGwiQOr3sruEL2a74EjPD050xYjA6M1I2hu/w2yjVHhn5j+DbXS4Xzi+rHHNZK3DgfDO3PkbECjPck+PbpSBjy9+6Mrjcld5DIZhUAeMlMHrFlg+WKRKB14o/og56u5/xX6WKlrMLEQ+y6E18dUwvWs2elTNoVO8PBE8SM/CfooX4AMNvaNdSObNBPdP+F6Lzc556nFNWXrBLRt0vC7s9qTiVRO4x/qCNaK/B4y7IqXMllwQFf4Np9UQ2ECA==",
    ),
    account_type="BlobStorage",
    alias="sac1",
    device_name="testedgedevice",
    name="sac1",
    resource_group_name="GroupForEdgeAutomation",
    ssl_status="Disabled",
    user_name="cisbvt")

```

```yaml
resources:
  storageAccountCredential:
    type: azure-native:databoxedge:StorageAccountCredential
    properties:
      accountKey:
        encryptionAlgorithm: AES256
        encryptionCertThumbprint: 2A9D8D6BE51574B5461230AEF02F162C5F01AD31
        value: lAeZEYi6rNP1/EyNaVUYmTSZEYyaIaWmwUsGwek0+xiZj54GM9Ue9/UA2ed/ClC03wuSit2XzM/cLRU5eYiFBwks23rGwiQOr3sruEL2a74EjPD050xYjA6M1I2hu/w2yjVHhn5j+DbXS4Xzi+rHHNZK3DgfDO3PkbECjPck+PbpSBjy9+6Mrjcld5DIZhUAeMlMHrFlg+WKRKB14o/og56u5/xX6WKlrMLEQ+y6E18dUwvWs2elTNoVO8PBE8SM/CfooX4AMNvaNdSObNBPdP+F6Lzc556nFNWXrBLRt0vC7s9qTiVRO4x/qCNaK/B4y7IqXMllwQFf4Np9UQ2ECA==
      accountType: BlobStorage
      alias: sac1
      deviceName: testedgedevice
      name: sac1
      resourceGroupName: GroupForEdgeAutomation
      sslStatus: Disabled
      userName: cisbvt

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:databoxedge:StorageAccountCredential sac1 /subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/GroupForEdgeAutomation/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/testedgedevice/storageAccountCredentials/sac1 
```
