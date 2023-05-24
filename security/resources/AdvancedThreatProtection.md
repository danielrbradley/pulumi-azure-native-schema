The Advanced Threat Protection resource.
API Version: 2019-01-01.
Previous API Version: 2019-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Creates or updates the Advanced Threat Protection settings on a specified resource.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var advancedThreatProtection = new AzureNative.Security.AdvancedThreatProtection("advancedThreatProtection", new()
    {
        IsEnabled = true,
        ResourceId = "subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourceGroups/SampleRG/providers/Microsoft.Storage/storageAccounts/samplestorageaccount",
        SettingName = "current",
    });

});


```

```go
package main

import (
	security "github.com/pulumi/pulumi-azure-native-sdk/security"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := security.NewAdvancedThreatProtection(ctx, "advancedThreatProtection", &security.AdvancedThreatProtectionArgs{
			IsEnabled:   pulumi.Bool(true),
			ResourceId:  pulumi.String("subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourceGroups/SampleRG/providers/Microsoft.Storage/storageAccounts/samplestorageaccount"),
			SettingName: pulumi.String("current"),
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
import com.pulumi.azurenative.security.AdvancedThreatProtection;
import com.pulumi.azurenative.security.AdvancedThreatProtectionArgs;
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
        var advancedThreatProtection = new AdvancedThreatProtection("advancedThreatProtection", AdvancedThreatProtectionArgs.builder()        
            .isEnabled(true)
            .resourceId("subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourceGroups/SampleRG/providers/Microsoft.Storage/storageAccounts/samplestorageaccount")
            .settingName("current")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const advancedThreatProtection = new azure_native.security.AdvancedThreatProtection("advancedThreatProtection", {
    isEnabled: true,
    resourceId: "subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourceGroups/SampleRG/providers/Microsoft.Storage/storageAccounts/samplestorageaccount",
    settingName: "current",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

advanced_threat_protection = azure_native.security.AdvancedThreatProtection("advancedThreatProtection",
    is_enabled=True,
    resource_id="subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourceGroups/SampleRG/providers/Microsoft.Storage/storageAccounts/samplestorageaccount",
    setting_name="current")

```

```yaml
resources:
  advancedThreatProtection:
    type: azure-native:security:AdvancedThreatProtection
    properties:
      isEnabled: true
      resourceId: subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourceGroups/SampleRG/providers/Microsoft.Storage/storageAccounts/samplestorageaccount
      settingName: current

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:security:AdvancedThreatProtection current /subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourceGroups/SampleRG/providers/Microsoft.Storage/storageAccounts/samplestorageaccount/providers/Microsoft.Security/advancedThreatProtectionSettings/current 
```
