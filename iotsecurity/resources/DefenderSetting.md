IoT Defender settings
API Version: 2021-02-01-preview.
Previous API Version: 2021-02-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update IoT Defender settings
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var defenderSetting = new AzureNative.IoTSecurity.DefenderSetting("defenderSetting", new()
    {
        DeviceQuota = 2000,
        MdeIntegration = new AzureNative.IoTSecurity.Inputs.DefenderSettingsPropertiesMdeIntegrationArgs
        {
            Status = "Enabled",
        },
        OnboardingKind = "Default",
        SentinelWorkspaceResourceIds = new[]
        {
            "/subscriptions/c4930e90-cd72-4aa5-93e9-2d081d129569/resourceGroups/myRg/providers/Microsoft.OperationalInsights/workspaces/myWorkspace1",
        },
    });

});


```

```go
package main

import (
	iotsecurity "github.com/pulumi/pulumi-azure-native-sdk/iotsecurity"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := iotsecurity.NewDefenderSetting(ctx, "defenderSetting", &iotsecurity.DefenderSettingArgs{
			DeviceQuota: pulumi.Int(2000),
			MdeIntegration: &iotsecurity.DefenderSettingsPropertiesMdeIntegrationArgs{
				Status: pulumi.String("Enabled"),
			},
			OnboardingKind: pulumi.String("Default"),
			SentinelWorkspaceResourceIds: pulumi.StringArray{
				pulumi.String("/subscriptions/c4930e90-cd72-4aa5-93e9-2d081d129569/resourceGroups/myRg/providers/Microsoft.OperationalInsights/workspaces/myWorkspace1"),
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
import com.pulumi.azurenative.iotsecurity.DefenderSetting;
import com.pulumi.azurenative.iotsecurity.DefenderSettingArgs;
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
        var defenderSetting = new DefenderSetting("defenderSetting", DefenderSettingArgs.builder()        
            .deviceQuota(2000)
            .mdeIntegration(Map.of("status", "Enabled"))
            .onboardingKind("Default")
            .sentinelWorkspaceResourceIds("/subscriptions/c4930e90-cd72-4aa5-93e9-2d081d129569/resourceGroups/myRg/providers/Microsoft.OperationalInsights/workspaces/myWorkspace1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const defenderSetting = new azure_native.iotsecurity.DefenderSetting("defenderSetting", {
    deviceQuota: 2000,
    mdeIntegration: {
        status: "Enabled",
    },
    onboardingKind: "Default",
    sentinelWorkspaceResourceIds: ["/subscriptions/c4930e90-cd72-4aa5-93e9-2d081d129569/resourceGroups/myRg/providers/Microsoft.OperationalInsights/workspaces/myWorkspace1"],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

defender_setting = azure_native.iotsecurity.DefenderSetting("defenderSetting",
    device_quota=2000,
    mde_integration=azure_native.iotsecurity.DefenderSettingsPropertiesMdeIntegrationArgs(
        status="Enabled",
    ),
    onboarding_kind="Default",
    sentinel_workspace_resource_ids=["/subscriptions/c4930e90-cd72-4aa5-93e9-2d081d129569/resourceGroups/myRg/providers/Microsoft.OperationalInsights/workspaces/myWorkspace1"])

```

```yaml
resources:
  defenderSetting:
    type: azure-native:iotsecurity:DefenderSetting
    properties:
      deviceQuota: 2000
      mdeIntegration:
        status: Enabled
      onboardingKind: Default
      sentinelWorkspaceResourceIds:
        - /subscriptions/c4930e90-cd72-4aa5-93e9-2d081d129569/resourceGroups/myRg/providers/Microsoft.OperationalInsights/workspaces/myWorkspace1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:iotsecurity:DefenderSetting default /subscriptions/{subscriptionId}/providers/Microsoft.IoTSecurity/defenderSettings/default 
```
