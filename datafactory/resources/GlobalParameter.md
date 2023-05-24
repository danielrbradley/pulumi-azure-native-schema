Global parameters resource type.
API Version: 2018-06-01.
Previous API Version: 2018-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### GlobalParameters_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var globalParameter = new AzureNative.DataFactory.GlobalParameter("globalParameter", new()
    {
        FactoryName = "exampleFactoryName",
        GlobalParameterName = "default",
        Properties = 
        {
            { "waitTime", new AzureNative.DataFactory.Inputs.GlobalParameterSpecificationArgs
            {
                Type = "Int",
                Value = 5,
            } },
        },
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
		_, err := datafactory.NewGlobalParameter(ctx, "globalParameter", &datafactory.GlobalParameterArgs{
			FactoryName:         pulumi.String("exampleFactoryName"),
			GlobalParameterName: pulumi.String("default"),
			Properties: datafactory.GlobalParameterSpecificationMap{
				"waitTime": &datafactory.GlobalParameterSpecificationArgs{
					Type:  pulumi.String("Int"),
					Value: pulumi.Any(5),
				},
			},
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
import com.pulumi.azurenative.datafactory.GlobalParameter;
import com.pulumi.azurenative.datafactory.GlobalParameterArgs;
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
        var globalParameter = new GlobalParameter("globalParameter", GlobalParameterArgs.builder()        
            .factoryName("exampleFactoryName")
            .globalParameterName("default")
            .properties(Map.of("waitTime", Map.ofEntries(
                Map.entry("type", "Int"),
                Map.entry("value", 5)
            )))
            .resourceGroupName("exampleResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const globalParameter = new azure_native.datafactory.GlobalParameter("globalParameter", {
    factoryName: "exampleFactoryName",
    globalParameterName: "default",
    properties: {
        waitTime: {
            type: "Int",
            value: 5,
        },
    },
    resourceGroupName: "exampleResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

global_parameter = azure_native.datafactory.GlobalParameter("globalParameter",
    factory_name="exampleFactoryName",
    global_parameter_name="default",
    properties={
        "waitTime": azure_native.datafactory.GlobalParameterSpecificationArgs(
            type="Int",
            value=5,
        ),
    },
    resource_group_name="exampleResourceGroup")

```

```yaml
resources:
  globalParameter:
    type: azure-native:datafactory:GlobalParameter
    properties:
      factoryName: exampleFactoryName
      globalParameterName: default
      properties:
        waitTime:
          type: Int
          value: 5
      resourceGroupName: exampleResourceGroup

```

{{% /example %}}
{{% example %}}
### GlobalParameters_Update
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var globalParameter = new AzureNative.DataFactory.GlobalParameter("globalParameter", new()
    {
        FactoryName = "exampleFactoryName",
        GlobalParameterName = "default",
        Properties = 
        {
            { "waitTime", new AzureNative.DataFactory.Inputs.GlobalParameterSpecificationArgs
            {
                Type = "Int",
                Value = 5,
            } },
        },
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
		_, err := datafactory.NewGlobalParameter(ctx, "globalParameter", &datafactory.GlobalParameterArgs{
			FactoryName:         pulumi.String("exampleFactoryName"),
			GlobalParameterName: pulumi.String("default"),
			Properties: datafactory.GlobalParameterSpecificationMap{
				"waitTime": &datafactory.GlobalParameterSpecificationArgs{
					Type:  pulumi.String("Int"),
					Value: pulumi.Any(5),
				},
			},
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
import com.pulumi.azurenative.datafactory.GlobalParameter;
import com.pulumi.azurenative.datafactory.GlobalParameterArgs;
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
        var globalParameter = new GlobalParameter("globalParameter", GlobalParameterArgs.builder()        
            .factoryName("exampleFactoryName")
            .globalParameterName("default")
            .properties(Map.of("waitTime", Map.ofEntries(
                Map.entry("type", "Int"),
                Map.entry("value", 5)
            )))
            .resourceGroupName("exampleResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const globalParameter = new azure_native.datafactory.GlobalParameter("globalParameter", {
    factoryName: "exampleFactoryName",
    globalParameterName: "default",
    properties: {
        waitTime: {
            type: "Int",
            value: 5,
        },
    },
    resourceGroupName: "exampleResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

global_parameter = azure_native.datafactory.GlobalParameter("globalParameter",
    factory_name="exampleFactoryName",
    global_parameter_name="default",
    properties={
        "waitTime": azure_native.datafactory.GlobalParameterSpecificationArgs(
            type="Int",
            value=5,
        ),
    },
    resource_group_name="exampleResourceGroup")

```

```yaml
resources:
  globalParameter:
    type: azure-native:datafactory:GlobalParameter
    properties:
      factoryName: exampleFactoryName
      globalParameterName: default
      properties:
        waitTime:
          type: Int
          value: 5
      resourceGroupName: exampleResourceGroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:datafactory:GlobalParameter default /subscriptions/12345678-1234-1234-1234-12345678abc/resourceGroups/exampleResourceGroup/providers/Microsoft.DataFactory/factories/exampleFactoryName/globalParameters/default 
```
