The log profile resource.
API Version: 2016-03-01.
Previous API Version: 2016-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a log profile
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var logProfile = new AzureNative.Insights.LogProfile("logProfile", new()
    {
        Categories = new[]
        {
            "Write",
            "Delete",
            "Action",
        },
        Location = "",
        Locations = new[]
        {
            "global",
        },
        LogProfileName = "Rac46PostSwapRG",
        RetentionPolicy = new AzureNative.Insights.Inputs.RetentionPolicyArgs
        {
            Days = 3,
            Enabled = true,
        },
        ServiceBusRuleId = "",
        StorageAccountId = "/subscriptions/df602c9c-7aa0-407d-a6fb-eb20c8bd1192/resourceGroups/JohnKemTest/providers/Microsoft.Storage/storageAccounts/johnkemtest8162",
        Tags = null,
    });

});


```

```go
package main

import (
	insights "github.com/pulumi/pulumi-azure-native-sdk/insights"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := insights.NewLogProfile(ctx, "logProfile", &insights.LogProfileArgs{
			Categories: pulumi.StringArray{
				pulumi.String("Write"),
				pulumi.String("Delete"),
				pulumi.String("Action"),
			},
			Location: pulumi.String(""),
			Locations: pulumi.StringArray{
				pulumi.String("global"),
			},
			LogProfileName: pulumi.String("Rac46PostSwapRG"),
			RetentionPolicy: &insights.RetentionPolicyArgs{
				Days:    pulumi.Int(3),
				Enabled: pulumi.Bool(true),
			},
			ServiceBusRuleId: pulumi.String(""),
			StorageAccountId: pulumi.String("/subscriptions/df602c9c-7aa0-407d-a6fb-eb20c8bd1192/resourceGroups/JohnKemTest/providers/Microsoft.Storage/storageAccounts/johnkemtest8162"),
			Tags:             nil,
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
import com.pulumi.azurenative.insights.LogProfile;
import com.pulumi.azurenative.insights.LogProfileArgs;
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
        var logProfile = new LogProfile("logProfile", LogProfileArgs.builder()        
            .categories(            
                "Write",
                "Delete",
                "Action")
            .location("")
            .locations("global")
            .logProfileName("Rac46PostSwapRG")
            .retentionPolicy(Map.ofEntries(
                Map.entry("days", 3),
                Map.entry("enabled", true)
            ))
            .serviceBusRuleId("")
            .storageAccountId("/subscriptions/df602c9c-7aa0-407d-a6fb-eb20c8bd1192/resourceGroups/JohnKemTest/providers/Microsoft.Storage/storageAccounts/johnkemtest8162")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const logProfile = new azure_native.insights.LogProfile("logProfile", {
    categories: [
        "Write",
        "Delete",
        "Action",
    ],
    location: "",
    locations: ["global"],
    logProfileName: "Rac46PostSwapRG",
    retentionPolicy: {
        days: 3,
        enabled: true,
    },
    serviceBusRuleId: "",
    storageAccountId: "/subscriptions/df602c9c-7aa0-407d-a6fb-eb20c8bd1192/resourceGroups/JohnKemTest/providers/Microsoft.Storage/storageAccounts/johnkemtest8162",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

log_profile = azure_native.insights.LogProfile("logProfile",
    categories=[
        "Write",
        "Delete",
        "Action",
    ],
    location="",
    locations=["global"],
    log_profile_name="Rac46PostSwapRG",
    retention_policy=azure_native.insights.RetentionPolicyArgs(
        days=3,
        enabled=True,
    ),
    service_bus_rule_id="",
    storage_account_id="/subscriptions/df602c9c-7aa0-407d-a6fb-eb20c8bd1192/resourceGroups/JohnKemTest/providers/Microsoft.Storage/storageAccounts/johnkemtest8162",
    tags={})

```

```yaml
resources:
  logProfile:
    type: azure-native:insights:LogProfile
    properties:
      categories:
        - Write
        - Delete
        - Action
      location:
      locations:
        - global
      logProfileName: Rac46PostSwapRG
      retentionPolicy:
        days: 3
        enabled: true
      serviceBusRuleId:
      storageAccountId: /subscriptions/df602c9c-7aa0-407d-a6fb-eb20c8bd1192/resourceGroups/JohnKemTest/providers/Microsoft.Storage/storageAccounts/johnkemtest8162
      tags: {}

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:insights:LogProfile default /subscriptions/df602c9c-7aa0-407d-a6fb-eb20c8bd1192/providers/microsoft.insights/logprofiles/default 
```
