The description of the DigitalTwins service.
API Version: 2023-01-31.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Put a DigitalTwinsInstance resource
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var digitalTwin = new AzureNative.DigitalTwins.DigitalTwin("digitalTwin", new()
    {
        Location = "WestUS2",
        ResourceGroupName = "resRg",
        ResourceName = "myDigitalTwinsService",
    });

});


```

```go
package main

import (
	digitaltwins "github.com/pulumi/pulumi-azure-native-sdk/digitaltwins"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := digitaltwins.NewDigitalTwin(ctx, "digitalTwin", &digitaltwins.DigitalTwinArgs{
			Location:          pulumi.String("WestUS2"),
			ResourceGroupName: pulumi.String("resRg"),
			ResourceName:      pulumi.String("myDigitalTwinsService"),
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
import com.pulumi.azurenative.digitaltwins.DigitalTwin;
import com.pulumi.azurenative.digitaltwins.DigitalTwinArgs;
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
        var digitalTwin = new DigitalTwin("digitalTwin", DigitalTwinArgs.builder()        
            .location("WestUS2")
            .resourceGroupName("resRg")
            .resourceName("myDigitalTwinsService")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const digitalTwin = new azure_native.digitaltwins.DigitalTwin("digitalTwin", {
    location: "WestUS2",
    resourceGroupName: "resRg",
    resourceName: "myDigitalTwinsService",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

digital_twin = azure_native.digitaltwins.DigitalTwin("digitalTwin",
    location="WestUS2",
    resource_group_name="resRg",
    resource_name_="myDigitalTwinsService")

```

```yaml
resources:
  digitalTwin:
    type: azure-native:digitaltwins:DigitalTwin
    properties:
      location: WestUS2
      resourceGroupName: resRg
      resourceName: myDigitalTwinsService

```

{{% /example %}}
{{% example %}}
### Put a DigitalTwinsInstance resource with publicNetworkAccess property
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var digitalTwin = new AzureNative.DigitalTwins.DigitalTwin("digitalTwin", new()
    {
        Location = "WestUS2",
        PublicNetworkAccess = "Enabled",
        ResourceGroupName = "resRg",
        ResourceName = "myDigitalTwinsService",
    });

});


```

```go
package main

import (
	digitaltwins "github.com/pulumi/pulumi-azure-native-sdk/digitaltwins"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := digitaltwins.NewDigitalTwin(ctx, "digitalTwin", &digitaltwins.DigitalTwinArgs{
			Location:            pulumi.String("WestUS2"),
			PublicNetworkAccess: pulumi.String("Enabled"),
			ResourceGroupName:   pulumi.String("resRg"),
			ResourceName:        pulumi.String("myDigitalTwinsService"),
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
import com.pulumi.azurenative.digitaltwins.DigitalTwin;
import com.pulumi.azurenative.digitaltwins.DigitalTwinArgs;
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
        var digitalTwin = new DigitalTwin("digitalTwin", DigitalTwinArgs.builder()        
            .location("WestUS2")
            .publicNetworkAccess("Enabled")
            .resourceGroupName("resRg")
            .resourceName("myDigitalTwinsService")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const digitalTwin = new azure_native.digitaltwins.DigitalTwin("digitalTwin", {
    location: "WestUS2",
    publicNetworkAccess: "Enabled",
    resourceGroupName: "resRg",
    resourceName: "myDigitalTwinsService",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

digital_twin = azure_native.digitaltwins.DigitalTwin("digitalTwin",
    location="WestUS2",
    public_network_access="Enabled",
    resource_group_name="resRg",
    resource_name_="myDigitalTwinsService")

```

```yaml
resources:
  digitalTwin:
    type: azure-native:digitaltwins:DigitalTwin
    properties:
      location: WestUS2
      publicNetworkAccess: Enabled
      resourceGroupName: resRg
      resourceName: myDigitalTwinsService

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:digitaltwins:DigitalTwin myDigitalTwinsService /subscriptions/50016170-c839-41ba-a724-51e9df440b9e/resourcegroups/resRg/providers/Microsoft.DigitalTwins/digitalTwinsInstances/myDigitalTwinsService 
```
