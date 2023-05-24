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
    var console = new AzureNative.Portal.Console("console", new()
    {
        ConsoleName = "default",
        Properties = new AzureNative.Portal.Inputs.ConsoleCreatePropertiesArgs
        {
            OsType = "Linux",
        },
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
		_, err := portal.NewConsole(ctx, "console", &portal.ConsoleArgs{
			ConsoleName: pulumi.String("default"),
			Properties: &portal.ConsoleCreatePropertiesArgs{
				OsType: pulumi.String("Linux"),
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
import com.pulumi.azurenative.portal.Console;
import com.pulumi.azurenative.portal.ConsoleArgs;
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
        var console = new Console("console", ConsoleArgs.builder()        
            .consoleName("default")
            .properties(Map.of("osType", "Linux"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const console = new azure_native.portal.Console("console", {
    consoleName: "default",
    properties: {
        osType: "Linux",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

console = azure_native.portal.Console("console",
    console_name="default",
    properties=azure_native.portal.ConsoleCreatePropertiesArgs(
        os_type="Linux",
    ))

```

```yaml
resources:
  console:
    type: azure-native:portal:Console
    properties:
      consoleName: default
      properties:
        osType: Linux

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:portal:Console myresource1 /providers/Microsoft.Portal/consoles/{consoleName} 
```
