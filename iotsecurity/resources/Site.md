IoT site model
API Version: 2021-02-01-preview.
Previous API Version: 2021-02-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update IoT site
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var site = new AzureNative.IoTSecurity.Site("site", new()
    {
        DisplayName = "IoT site name",
        Scope = "subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourceGroups/myRg/providers/Microsoft.Devices/IotHubs/myHub",
        Tags = 
        {
            { "key1", "value1" },
            { "key2", "value2" },
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
		_, err := iotsecurity.NewSite(ctx, "site", &iotsecurity.SiteArgs{
			DisplayName: pulumi.String("IoT site name"),
			Scope:       pulumi.String("subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourceGroups/myRg/providers/Microsoft.Devices/IotHubs/myHub"),
			Tags: pulumi.StringMap{
				"key1": pulumi.String("value1"),
				"key2": pulumi.String("value2"),
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
import com.pulumi.azurenative.iotsecurity.Site;
import com.pulumi.azurenative.iotsecurity.SiteArgs;
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
        var site = new Site("site", SiteArgs.builder()        
            .displayName("IoT site name")
            .scope("subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourceGroups/myRg/providers/Microsoft.Devices/IotHubs/myHub")
            .tags(Map.ofEntries(
                Map.entry("key1", "value1"),
                Map.entry("key2", "value2")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const site = new azure_native.iotsecurity.Site("site", {
    displayName: "IoT site name",
    scope: "subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourceGroups/myRg/providers/Microsoft.Devices/IotHubs/myHub",
    tags: {
        key1: "value1",
        key2: "value2",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

site = azure_native.iotsecurity.Site("site",
    display_name="IoT site name",
    scope="subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourceGroups/myRg/providers/Microsoft.Devices/IotHubs/myHub",
    tags={
        "key1": "value1",
        "key2": "value2",
    })

```

```yaml
resources:
  site:
    type: azure-native:iotsecurity:Site
    properties:
      displayName: IoT site name
      scope: subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourceGroups/myRg/providers/Microsoft.Devices/IotHubs/myHub
      tags:
        key1: value1
        key2: value2

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:iotsecurity:Site default subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourceGroups/myRg/providers/Microsoft.Devices/IotHubs/myHub/providers/Microsoft.IoTSecurity/sites/default 
```
