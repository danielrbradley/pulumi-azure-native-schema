Factory resource type.
API Version: 2018-06-01.
Previous API Version: 2018-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Factories_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var factory = new AzureNative.DataFactory.Factory("factory", new()
    {
        FactoryName = "exampleFactoryName",
        Location = "East US",
        ResourceGroupName = "exampleResourceGroup",
    });

});


```

```go
package main

import (
	datafactory "github.com/pulumi/pulumi-azure-native-sdk/datafactory"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := datafactory.NewFactory(ctx, "factory", &datafactory.FactoryArgs{
			FactoryName:       pulumi.String("exampleFactoryName"),
			Location:          pulumi.String("East US"),
			ResourceGroupName: pulumi.String("exampleResourceGroup"),
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
import com.pulumi.azurenative.datafactory.Factory;
import com.pulumi.azurenative.datafactory.FactoryArgs;
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
        var factory = new Factory("factory", FactoryArgs.builder()        
            .factoryName("exampleFactoryName")
            .location("East US")
            .resourceGroupName("exampleResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const factory = new azure_native.datafactory.Factory("factory", {
    factoryName: "exampleFactoryName",
    location: "East US",
    resourceGroupName: "exampleResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

factory = azure_native.datafactory.Factory("factory",
    factory_name="exampleFactoryName",
    location="East US",
    resource_group_name="exampleResourceGroup")

```

```yaml
resources:
  factory:
    type: azure-native:datafactory:Factory
    properties:
      factoryName: exampleFactoryName
      location: East US
      resourceGroupName: exampleResourceGroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:datafactory:Factory exampleFactoryName /subscriptions/12345678-1234-1234-1234-12345678abc/resourceGroups/exampleResourceGroup/providers/Microsoft.DataFactory/factories/exampleFactoryName 
```
