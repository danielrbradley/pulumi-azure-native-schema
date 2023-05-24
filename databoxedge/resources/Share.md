Represents a share on the  Data Box Edge/Gateway device.
API Version: 2022-03-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### SharePut
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var share = new AzureNative.DataBoxEdge.Share("share", new()
    {
        AccessProtocol = "SMB",
        AzureContainerInfo = new AzureNative.DataBoxEdge.Inputs.AzureContainerInfoArgs
        {
            ContainerName = "testContainerSMB",
            DataFormat = "BlockBlob",
            StorageAccountCredentialId = "/subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/GroupForEdgeAutomation/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/testedgedevice/storageAccountCredentials/sac1",
        },
        DataPolicy = "Cloud",
        Description = "",
        DeviceName = "testedgedevice",
        MonitoringStatus = "Enabled",
        Name = "smbshare",
        ResourceGroupName = "GroupForEdgeAutomation",
        ShareStatus = "Online",
        UserAccessRights = new[]
        {
            new AzureNative.DataBoxEdge.Inputs.UserAccessRightArgs
            {
                AccessType = "Change",
                UserId = "/subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/GroupForEdgeAutomation/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/testedgedevice/users/user2",
            },
        },
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
		_, err := databoxedge.NewShare(ctx, "share", &databoxedge.ShareArgs{
			AccessProtocol: pulumi.String("SMB"),
			AzureContainerInfo: &databoxedge.AzureContainerInfoArgs{
				ContainerName:              pulumi.String("testContainerSMB"),
				DataFormat:                 pulumi.String("BlockBlob"),
				StorageAccountCredentialId: pulumi.String("/subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/GroupForEdgeAutomation/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/testedgedevice/storageAccountCredentials/sac1"),
			},
			DataPolicy:        pulumi.String("Cloud"),
			Description:       pulumi.String(""),
			DeviceName:        pulumi.String("testedgedevice"),
			MonitoringStatus:  pulumi.String("Enabled"),
			Name:              pulumi.String("smbshare"),
			ResourceGroupName: pulumi.String("GroupForEdgeAutomation"),
			ShareStatus:       pulumi.String("Online"),
			UserAccessRights: []databoxedge.UserAccessRightArgs{
				{
					AccessType: pulumi.String("Change"),
					UserId:     pulumi.String("/subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/GroupForEdgeAutomation/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/testedgedevice/users/user2"),
				},
			},
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
import com.pulumi.azurenative.databoxedge.Share;
import com.pulumi.azurenative.databoxedge.ShareArgs;
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
        var share = new Share("share", ShareArgs.builder()        
            .accessProtocol("SMB")
            .azureContainerInfo(Map.ofEntries(
                Map.entry("containerName", "testContainerSMB"),
                Map.entry("dataFormat", "BlockBlob"),
                Map.entry("storageAccountCredentialId", "/subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/GroupForEdgeAutomation/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/testedgedevice/storageAccountCredentials/sac1")
            ))
            .dataPolicy("Cloud")
            .description("")
            .deviceName("testedgedevice")
            .monitoringStatus("Enabled")
            .name("smbshare")
            .resourceGroupName("GroupForEdgeAutomation")
            .shareStatus("Online")
            .userAccessRights(Map.ofEntries(
                Map.entry("accessType", "Change"),
                Map.entry("userId", "/subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/GroupForEdgeAutomation/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/testedgedevice/users/user2")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const share = new azure_native.databoxedge.Share("share", {
    accessProtocol: "SMB",
    azureContainerInfo: {
        containerName: "testContainerSMB",
        dataFormat: "BlockBlob",
        storageAccountCredentialId: "/subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/GroupForEdgeAutomation/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/testedgedevice/storageAccountCredentials/sac1",
    },
    dataPolicy: "Cloud",
    description: "",
    deviceName: "testedgedevice",
    monitoringStatus: "Enabled",
    name: "smbshare",
    resourceGroupName: "GroupForEdgeAutomation",
    shareStatus: "Online",
    userAccessRights: [{
        accessType: "Change",
        userId: "/subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/GroupForEdgeAutomation/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/testedgedevice/users/user2",
    }],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

share = azure_native.databoxedge.Share("share",
    access_protocol="SMB",
    azure_container_info=azure_native.databoxedge.AzureContainerInfoArgs(
        container_name="testContainerSMB",
        data_format="BlockBlob",
        storage_account_credential_id="/subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/GroupForEdgeAutomation/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/testedgedevice/storageAccountCredentials/sac1",
    ),
    data_policy="Cloud",
    description="",
    device_name="testedgedevice",
    monitoring_status="Enabled",
    name="smbshare",
    resource_group_name="GroupForEdgeAutomation",
    share_status="Online",
    user_access_rights=[azure_native.databoxedge.UserAccessRightArgs(
        access_type="Change",
        user_id="/subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/GroupForEdgeAutomation/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/testedgedevice/users/user2",
    )])

```

```yaml
resources:
  share:
    type: azure-native:databoxedge:Share
    properties:
      accessProtocol: SMB
      azureContainerInfo:
        containerName: testContainerSMB
        dataFormat: BlockBlob
        storageAccountCredentialId: /subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/GroupForEdgeAutomation/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/testedgedevice/storageAccountCredentials/sac1
      dataPolicy: Cloud
      description:
      deviceName: testedgedevice
      monitoringStatus: Enabled
      name: smbshare
      resourceGroupName: GroupForEdgeAutomation
      shareStatus: Online
      userAccessRights:
        - accessType: Change
          userId: /subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/GroupForEdgeAutomation/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/testedgedevice/users/user2

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:databoxedge:Share smbshare /subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/GroupForEdgeAutomation/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/testedgedevice/shares/smbshare 
```
