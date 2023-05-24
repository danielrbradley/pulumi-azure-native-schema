The container for solution.
API Version: 2015-11-01-preview.
Previous API Version: 2015-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ManagementConfigurationCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managementConfiguration = new AzureNative.OperationsManagement.ManagementConfiguration("managementConfiguration", new()
    {
        Location = "East US",
        ManagementConfigurationName = "managementConfiguration1",
        ResourceGroupName = "rg1",
    });

});


```

```go
package main

import (
	operationsmanagement "github.com/pulumi/pulumi-azure-native-sdk/operationsmanagement"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := operationsmanagement.NewManagementConfiguration(ctx, "managementConfiguration", &operationsmanagement.ManagementConfigurationArgs{
			Location:                    pulumi.String("East US"),
			ManagementConfigurationName: pulumi.String("managementConfiguration1"),
			ResourceGroupName:           pulumi.String("rg1"),
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
import com.pulumi.azurenative.operationsmanagement.ManagementConfiguration;
import com.pulumi.azurenative.operationsmanagement.ManagementConfigurationArgs;
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
        var managementConfiguration = new ManagementConfiguration("managementConfiguration", ManagementConfigurationArgs.builder()        
            .location("East US")
            .managementConfigurationName("managementConfiguration1")
            .resourceGroupName("rg1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managementConfiguration = new azure_native.operationsmanagement.ManagementConfiguration("managementConfiguration", {
    location: "East US",
    managementConfigurationName: "managementConfiguration1",
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

management_configuration = azure_native.operationsmanagement.ManagementConfiguration("managementConfiguration",
    location="East US",
    management_configuration_name="managementConfiguration1",
    resource_group_name="rg1")

```

```yaml
resources:
  managementConfiguration:
    type: azure-native:operationsmanagement:ManagementConfiguration
    properties:
      location: East US
      managementConfigurationName: managementConfiguration1
      resourceGroupName: rg1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:operationsmanagement:ManagementConfiguration managementConfiguration1 subscriptions/subid/resourcegroups/rg1/providers/Microsoft.OperationsManagement/ManagementConfigurations/managementConfiguration1 
```
