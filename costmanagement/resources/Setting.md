State of the myscope setting.
API Version: 2019-11-01.
Previous API Version: 2019-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateOrUpdateSetting
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var setting = new AzureNative.CostManagement.Setting("setting", new()
    {
        Cache = new[]
        {
            new AzureNative.CostManagement.Inputs.SettingsPropertiesCacheArgs
            {
                Channel = "Modern",
                Id = "/providers/Microsoft.Management/managementGroups/72f988bf-86f1-41af-91ab-2d7cd011db47",
                Name = "72f988bf-86f1-41af-91ab-2d7cd011db47",
                Parent = "/providers/Microsoft.Management/managementGroups/acm",
                Status = "enabled",
                Subchannel = "NotApplicable",
            },
        },
        Scope = "/subscriptions/00000000-0000-0000-0000-000000000000",
        SettingName = "myscope",
        StartOn = "LastUsed",
    });

});


```

```go
package main

import (
	costmanagement "github.com/pulumi/pulumi-azure-native-sdk/costmanagement"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := costmanagement.NewSetting(ctx, "setting", &costmanagement.SettingArgs{
			Cache: []costmanagement.SettingsPropertiesCacheArgs{
				{
					Channel:    pulumi.String("Modern"),
					Id:         pulumi.String("/providers/Microsoft.Management/managementGroups/72f988bf-86f1-41af-91ab-2d7cd011db47"),
					Name:       pulumi.String("72f988bf-86f1-41af-91ab-2d7cd011db47"),
					Parent:     pulumi.String("/providers/Microsoft.Management/managementGroups/acm"),
					Status:     pulumi.String("enabled"),
					Subchannel: pulumi.String("NotApplicable"),
				},
			},
			Scope:       pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000"),
			SettingName: pulumi.String("myscope"),
			StartOn:     pulumi.String("LastUsed"),
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
import com.pulumi.azurenative.costmanagement.Setting;
import com.pulumi.azurenative.costmanagement.SettingArgs;
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
        var setting = new Setting("setting", SettingArgs.builder()        
            .cache(Map.ofEntries(
                Map.entry("channel", "Modern"),
                Map.entry("id", "/providers/Microsoft.Management/managementGroups/72f988bf-86f1-41af-91ab-2d7cd011db47"),
                Map.entry("name", "72f988bf-86f1-41af-91ab-2d7cd011db47"),
                Map.entry("parent", "/providers/Microsoft.Management/managementGroups/acm"),
                Map.entry("status", "enabled"),
                Map.entry("subchannel", "NotApplicable")
            ))
            .scope("/subscriptions/00000000-0000-0000-0000-000000000000")
            .settingName("myscope")
            .startOn("LastUsed")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const setting = new azure_native.costmanagement.Setting("setting", {
    cache: [{
        channel: "Modern",
        id: "/providers/Microsoft.Management/managementGroups/72f988bf-86f1-41af-91ab-2d7cd011db47",
        name: "72f988bf-86f1-41af-91ab-2d7cd011db47",
        parent: "/providers/Microsoft.Management/managementGroups/acm",
        status: "enabled",
        subchannel: "NotApplicable",
    }],
    scope: "/subscriptions/00000000-0000-0000-0000-000000000000",
    settingName: "myscope",
    startOn: "LastUsed",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

setting = azure_native.costmanagement.Setting("setting",
    cache=[azure_native.costmanagement.SettingsPropertiesCacheArgs(
        channel="Modern",
        id="/providers/Microsoft.Management/managementGroups/72f988bf-86f1-41af-91ab-2d7cd011db47",
        name="72f988bf-86f1-41af-91ab-2d7cd011db47",
        parent="/providers/Microsoft.Management/managementGroups/acm",
        status="enabled",
        subchannel="NotApplicable",
    )],
    scope="/subscriptions/00000000-0000-0000-0000-000000000000",
    setting_name="myscope",
    start_on="LastUsed")

```

```yaml
resources:
  setting:
    type: azure-native:costmanagement:Setting
    properties:
      cache:
        - channel: Modern
          id: /providers/Microsoft.Management/managementGroups/72f988bf-86f1-41af-91ab-2d7cd011db47
          name: 72f988bf-86f1-41af-91ab-2d7cd011db47
          parent: /providers/Microsoft.Management/managementGroups/acm
          status: enabled
          subchannel: NotApplicable
      scope: /subscriptions/00000000-0000-0000-0000-000000000000
      settingName: myscope
      startOn: LastUsed

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:costmanagement:Setting myscope /providers/Microsoft.CostManagement/settings/myscope 
```
