Cloud shell console
API Version: 2018-10-01.
Previous API Version: 2018-10-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### PutConsole
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var consoleWithLocation = new AzureNative.Portal.ConsoleWithLocation("consoleWithLocation", new()
    {
        ConsoleName = "default",
        Location = "eastus",
    });

});


```

```go
package main

import (
	portal "github.com/pulumi/pulumi-azure-native-sdk/portal"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := portal.NewConsoleWithLocation(ctx, "consoleWithLocation", &portal.ConsoleWithLocationArgs{
			ConsoleName: pulumi.String("default"),
			Location:    pulumi.String("eastus"),
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
import com.pulumi.azurenative.portal.ConsoleWithLocation;
import com.pulumi.azurenative.portal.ConsoleWithLocationArgs;
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
        var consoleWithLocation = new ConsoleWithLocation("consoleWithLocation", ConsoleWithLocationArgs.builder()        
            .consoleName("default")
            .location("eastus")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const consoleWithLocation = new azure_native.portal.ConsoleWithLocation("consoleWithLocation", {
    consoleName: "default",
    location: "eastus",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

console_with_location = azure_native.portal.ConsoleWithLocation("consoleWithLocation",
    console_name="default",
    location="eastus")

```

```yaml
resources:
  consoleWithLocation:
    type: azure-native:portal:ConsoleWithLocation
    properties:
      consoleName: default
      location: eastus

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:portal:ConsoleWithLocation myresource1 /providers/Microsoft.Portal/locations/{location}/consoles/{consoleName} 
```
