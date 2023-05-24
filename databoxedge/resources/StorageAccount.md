Represents a Storage Account on the  Data Box Edge/Gateway device.
API Version: 2022-03-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### StorageAccountPut
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var storageAccount = new AzureNative.DataBoxEdge.StorageAccount("storageAccount", new()
    {
        DataPolicy = "Cloud",
        Description = "It's an awesome storage account",
        DeviceName = "testedgedevice",
        ResourceGroupName = "GroupForEdgeAutomation",
        StorageAccountCredentialId = "/subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/GroupForDataBoxEdgeAutomation/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/testedgedevice/storageAccountCredentials/cisbvt",
        StorageAccountName = "blobstorageaccount1",
        StorageAccountStatus = "OK",
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
		_, err := databoxedge.NewStorageAccount(ctx, "storageAccount", &databoxedge.StorageAccountArgs{
			DataPolicy:                 pulumi.String("Cloud"),
			Description:                pulumi.String("It's an awesome storage account"),
			DeviceName:                 pulumi.String("testedgedevice"),
			ResourceGroupName:          pulumi.String("GroupForEdgeAutomation"),
			StorageAccountCredentialId: pulumi.String("/subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/GroupForDataBoxEdgeAutomation/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/testedgedevice/storageAccountCredentials/cisbvt"),
			StorageAccountName:         pulumi.String("blobstorageaccount1"),
			StorageAccountStatus:       pulumi.String("OK"),
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
import com.pulumi.azurenative.databoxedge.StorageAccount;
import com.pulumi.azurenative.databoxedge.StorageAccountArgs;
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
        var storageAccount = new StorageAccount("storageAccount", StorageAccountArgs.builder()        
            .dataPolicy("Cloud")
            .description("It's an awesome storage account")
            .deviceName("testedgedevice")
            .resourceGroupName("GroupForEdgeAutomation")
            .storageAccountCredentialId("/subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/GroupForDataBoxEdgeAutomation/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/testedgedevice/storageAccountCredentials/cisbvt")
            .storageAccountName("blobstorageaccount1")
            .storageAccountStatus("OK")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const storageAccount = new azure_native.databoxedge.StorageAccount("storageAccount", {
    dataPolicy: "Cloud",
    description: "It's an awesome storage account",
    deviceName: "testedgedevice",
    resourceGroupName: "GroupForEdgeAutomation",
    storageAccountCredentialId: "/subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/GroupForDataBoxEdgeAutomation/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/testedgedevice/storageAccountCredentials/cisbvt",
    storageAccountName: "blobstorageaccount1",
    storageAccountStatus: "OK",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

storage_account = azure_native.databoxedge.StorageAccount("storageAccount",
    data_policy="Cloud",
    description="It's an awesome storage account",
    device_name="testedgedevice",
    resource_group_name="GroupForEdgeAutomation",
    storage_account_credential_id="/subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/GroupForDataBoxEdgeAutomation/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/testedgedevice/storageAccountCredentials/cisbvt",
    storage_account_name="blobstorageaccount1",
    storage_account_status="OK")

```

```yaml
resources:
  storageAccount:
    type: azure-native:databoxedge:StorageAccount
    properties:
      dataPolicy: Cloud
      description: It's an awesome storage account
      deviceName: testedgedevice
      resourceGroupName: GroupForEdgeAutomation
      storageAccountCredentialId: /subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/GroupForDataBoxEdgeAutomation/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/testedgedevice/storageAccountCredentials/cisbvt
      storageAccountName: blobstorageaccount1
      storageAccountStatus: OK

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:databoxedge:StorageAccount blobstorageaccount1 /subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/GroupForDataBoxEdgeAutomation/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/testedgedevice/storageAccounts/blobstorageaccount1 
```
