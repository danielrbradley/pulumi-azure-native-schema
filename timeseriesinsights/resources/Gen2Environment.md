An environment is a set of time-series data available for query, and is the top level Azure Time Series Insights resource. Gen2 environments do not have set data retention limits.
API Version: 2020-05-15.
Previous API Version: 2020-05-15. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### EnvironmentsCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var gen2Environment = new AzureNative.TimeSeriesInsights.Gen2Environment("gen2Environment", new()
    {
        EnvironmentName = "env1",
        ResourceGroupName = "rg1",
    });

});


```

```go
package main

import (
	timeseriesinsights "github.com/pulumi/pulumi-azure-native-sdk/timeseriesinsights"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := timeseriesinsights.NewGen2Environment(ctx, "gen2Environment", &timeseriesinsights.Gen2EnvironmentArgs{
			EnvironmentName:   pulumi.String("env1"),
			ResourceGroupName: pulumi.String("rg1"),
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
import com.pulumi.azurenative.timeseriesinsights.Gen2Environment;
import com.pulumi.azurenative.timeseriesinsights.Gen2EnvironmentArgs;
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
        var gen2Environment = new Gen2Environment("gen2Environment", Gen2EnvironmentArgs.builder()        
            .environmentName("env1")
            .resourceGroupName("rg1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const gen2Environment = new azure_native.timeseriesinsights.Gen2Environment("gen2Environment", {
    environmentName: "env1",
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

gen2_environment = azure_native.timeseriesinsights.Gen2Environment("gen2Environment",
    environment_name="env1",
    resource_group_name="rg1")

```

```yaml
resources:
  gen2Environment:
    type: azure-native:timeseriesinsights:Gen2Environment
    properties:
      environmentName: env1
      resourceGroupName: rg1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:timeseriesinsights:Gen2Environment env1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.TimeSeriesInsights/Environments/env1 
```
