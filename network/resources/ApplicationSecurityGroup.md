An application security group in a resource group.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create application security group
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var applicationSecurityGroup = new AzureNative.Network.ApplicationSecurityGroup("applicationSecurityGroup", new()
    {
        ApplicationSecurityGroupName = "test-asg",
        Location = "westus",
        ResourceGroupName = "rg1",
    });

});


```

```go
package main

import (
	network "github.com/pulumi/pulumi-azure-native-sdk/network"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := network.NewApplicationSecurityGroup(ctx, "applicationSecurityGroup", &network.ApplicationSecurityGroupArgs{
			ApplicationSecurityGroupName: pulumi.String("test-asg"),
			Location:                     pulumi.String("westus"),
			ResourceGroupName:            pulumi.String("rg1"),
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
import com.pulumi.azurenative.network.ApplicationSecurityGroup;
import com.pulumi.azurenative.network.ApplicationSecurityGroupArgs;
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
        var applicationSecurityGroup = new ApplicationSecurityGroup("applicationSecurityGroup", ApplicationSecurityGroupArgs.builder()        
            .applicationSecurityGroupName("test-asg")
            .location("westus")
            .resourceGroupName("rg1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const applicationSecurityGroup = new azure_native.network.ApplicationSecurityGroup("applicationSecurityGroup", {
    applicationSecurityGroupName: "test-asg",
    location: "westus",
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

application_security_group = azure_native.network.ApplicationSecurityGroup("applicationSecurityGroup",
    application_security_group_name="test-asg",
    location="westus",
    resource_group_name="rg1")

```

```yaml
resources:
  applicationSecurityGroup:
    type: azure-native:network:ApplicationSecurityGroup
    properties:
      applicationSecurityGroupName: test-asg
      location: westus
      resourceGroupName: rg1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:ApplicationSecurityGroup test-asg /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/applicationSecurityGroups/test-asg 
```
