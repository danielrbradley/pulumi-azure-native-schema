A type of synchronization setting based on schedule
API Version: 2021-08-01.
Previous API Version: 2020-09-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### SynchronizationSettings_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var scheduledSynchronizationSetting = new AzureNative.DataShare.ScheduledSynchronizationSetting("scheduledSynchronizationSetting", new()
    {
        AccountName = "Account1",
        Kind = "ScheduleBased",
        RecurrenceInterval = "Day",
        ResourceGroupName = "SampleResourceGroup",
        ShareName = "Share1",
        SynchronizationSettingName = "Dataset1",
        SynchronizationTime = "2018-11-14T04:47:52.9614956Z",
    });

});


```

```go
package main

import (
	datashare "github.com/pulumi/pulumi-azure-native-sdk/datashare"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := datashare.NewScheduledSynchronizationSetting(ctx, "scheduledSynchronizationSetting", &datashare.ScheduledSynchronizationSettingArgs{
			AccountName:                pulumi.String("Account1"),
			Kind:                       pulumi.String("ScheduleBased"),
			RecurrenceInterval:         pulumi.String("Day"),
			ResourceGroupName:          pulumi.String("SampleResourceGroup"),
			ShareName:                  pulumi.String("Share1"),
			SynchronizationSettingName: pulumi.String("Dataset1"),
			SynchronizationTime:        pulumi.String("2018-11-14T04:47:52.9614956Z"),
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
import com.pulumi.azurenative.datashare.ScheduledSynchronizationSetting;
import com.pulumi.azurenative.datashare.ScheduledSynchronizationSettingArgs;
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
        var scheduledSynchronizationSetting = new ScheduledSynchronizationSetting("scheduledSynchronizationSetting", ScheduledSynchronizationSettingArgs.builder()        
            .accountName("Account1")
            .kind("ScheduleBased")
            .recurrenceInterval("Day")
            .resourceGroupName("SampleResourceGroup")
            .shareName("Share1")
            .synchronizationSettingName("Dataset1")
            .synchronizationTime("2018-11-14T04:47:52.9614956Z")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const scheduledSynchronizationSetting = new azure_native.datashare.ScheduledSynchronizationSetting("scheduledSynchronizationSetting", {
    accountName: "Account1",
    kind: "ScheduleBased",
    recurrenceInterval: "Day",
    resourceGroupName: "SampleResourceGroup",
    shareName: "Share1",
    synchronizationSettingName: "Dataset1",
    synchronizationTime: "2018-11-14T04:47:52.9614956Z",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

scheduled_synchronization_setting = azure_native.datashare.ScheduledSynchronizationSetting("scheduledSynchronizationSetting",
    account_name="Account1",
    kind="ScheduleBased",
    recurrence_interval="Day",
    resource_group_name="SampleResourceGroup",
    share_name="Share1",
    synchronization_setting_name="Dataset1",
    synchronization_time="2018-11-14T04:47:52.9614956Z")

```

```yaml
resources:
  scheduledSynchronizationSetting:
    type: azure-native:datashare:ScheduledSynchronizationSetting
    properties:
      accountName: Account1
      kind: ScheduleBased
      recurrenceInterval: Day
      resourceGroupName: SampleResourceGroup
      shareName: Share1
      synchronizationSettingName: Dataset1
      synchronizationTime: 2018-11-14T04:47:52.9614956Z

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:datashare:ScheduledSynchronizationSetting SynchronizationSetting1 /subscriptions/433a8dfd-e5d5-4e77-ad86-90acdc75eb1a/resourceGroups/SampleResourceGroup/providers/Microsoft.DataShare/accounts/Account1/shares/Share1/synchronizationSettings/SynchronizationSetting1 
```
