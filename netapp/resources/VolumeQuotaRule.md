Quota Rule of a Volume
API Version: 2022-09-01.
Previous API Version: 2022-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### VolumeQuotaRules_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var volumeQuotaRule = new AzureNative.NetApp.VolumeQuotaRule("volumeQuotaRule", new()
    {
        AccountName = "account-9957",
        Location = "westus",
        PoolName = "pool-5210",
        QuotaSizeInKiBs = 100005,
        QuotaTarget = "1821",
        QuotaType = "IndividualUserQuota",
        ResourceGroupName = "myRG",
        VolumeName = "volume-6387",
        VolumeQuotaRuleName = "rule-0004",
    });

});


```

```go
package main

import (
	netapp "github.com/pulumi/pulumi-azure-native-sdk/netapp"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := netapp.NewVolumeQuotaRule(ctx, "volumeQuotaRule", &netapp.VolumeQuotaRuleArgs{
			AccountName:         pulumi.String("account-9957"),
			Location:            pulumi.String("westus"),
			PoolName:            pulumi.String("pool-5210"),
			QuotaSizeInKiBs:     pulumi.Float64(100005),
			QuotaTarget:         pulumi.String("1821"),
			QuotaType:           pulumi.String("IndividualUserQuota"),
			ResourceGroupName:   pulumi.String("myRG"),
			VolumeName:          pulumi.String("volume-6387"),
			VolumeQuotaRuleName: pulumi.String("rule-0004"),
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
import com.pulumi.azurenative.netapp.VolumeQuotaRule;
import com.pulumi.azurenative.netapp.VolumeQuotaRuleArgs;
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
        var volumeQuotaRule = new VolumeQuotaRule("volumeQuotaRule", VolumeQuotaRuleArgs.builder()        
            .accountName("account-9957")
            .location("westus")
            .poolName("pool-5210")
            .quotaSizeInKiBs(100005)
            .quotaTarget("1821")
            .quotaType("IndividualUserQuota")
            .resourceGroupName("myRG")
            .volumeName("volume-6387")
            .volumeQuotaRuleName("rule-0004")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const volumeQuotaRule = new azure_native.netapp.VolumeQuotaRule("volumeQuotaRule", {
    accountName: "account-9957",
    location: "westus",
    poolName: "pool-5210",
    quotaSizeInKiBs: 100005,
    quotaTarget: "1821",
    quotaType: "IndividualUserQuota",
    resourceGroupName: "myRG",
    volumeName: "volume-6387",
    volumeQuotaRuleName: "rule-0004",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

volume_quota_rule = azure_native.netapp.VolumeQuotaRule("volumeQuotaRule",
    account_name="account-9957",
    location="westus",
    pool_name="pool-5210",
    quota_size_in_ki_bs=100005,
    quota_target="1821",
    quota_type="IndividualUserQuota",
    resource_group_name="myRG",
    volume_name="volume-6387",
    volume_quota_rule_name="rule-0004")

```

```yaml
resources:
  volumeQuotaRule:
    type: azure-native:netapp:VolumeQuotaRule
    properties:
      accountName: account-9957
      location: westus
      poolName: pool-5210
      quotaSizeInKiBs: 100005
      quotaTarget: '1821'
      quotaType: IndividualUserQuota
      resourceGroupName: myRG
      volumeName: volume-6387
      volumeQuotaRuleName: rule-0004

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:netapp:VolumeQuotaRule account-9957/pool-5210/volume-6387/rule-0004 /subscriptions/5275316f-a498-48d6-b324-2cbfdc4311b9/resourceGroups/myRG/providers/Microsoft.NetApp/netAppAccounts/account-9957/capacityPools/pool-5210/volumes/volume-6387/volumeQuotaRules/rule-0004 
```
