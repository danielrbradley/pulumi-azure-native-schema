Specifies information about the availability set that the virtual machine should be assigned to. Virtual machines specified in the same availability set are allocated to different nodes to maximize availability. For more information about availability sets, see [Availability sets overview](https://docs.microsoft.com/azure/virtual-machines/availability-set-overview). <br><br> For more information on Azure planned maintenance, see [Maintenance and updates for Virtual Machines in Azure](https://docs.microsoft.com/azure/virtual-machines/maintenance-and-updates) <br><br> Currently, a VM can only be added to availability set at creation time. An existing VM cannot be added to an availability set.
API Version: 2022-11-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create an availability set.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var availabilitySet = new AzureNative.Compute.AvailabilitySet("availabilitySet", new()
    {
        AvailabilitySetName = "myAvailabilitySet",
        Location = "westus",
        PlatformFaultDomainCount = 2,
        PlatformUpdateDomainCount = 20,
        ResourceGroupName = "myResourceGroup",
    });

});


```

```go
package main

import (
	compute "github.com/pulumi/pulumi-azure-native-sdk/compute"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := compute.NewAvailabilitySet(ctx, "availabilitySet", &compute.AvailabilitySetArgs{
			AvailabilitySetName:       pulumi.String("myAvailabilitySet"),
			Location:                  pulumi.String("westus"),
			PlatformFaultDomainCount:  pulumi.Int(2),
			PlatformUpdateDomainCount: pulumi.Int(20),
			ResourceGroupName:         pulumi.String("myResourceGroup"),
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
import com.pulumi.azurenative.compute.AvailabilitySet;
import com.pulumi.azurenative.compute.AvailabilitySetArgs;
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
        var availabilitySet = new AvailabilitySet("availabilitySet", AvailabilitySetArgs.builder()        
            .availabilitySetName("myAvailabilitySet")
            .location("westus")
            .platformFaultDomainCount(2)
            .platformUpdateDomainCount(20)
            .resourceGroupName("myResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const availabilitySet = new azure_native.compute.AvailabilitySet("availabilitySet", {
    availabilitySetName: "myAvailabilitySet",
    location: "westus",
    platformFaultDomainCount: 2,
    platformUpdateDomainCount: 20,
    resourceGroupName: "myResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

availability_set = azure_native.compute.AvailabilitySet("availabilitySet",
    availability_set_name="myAvailabilitySet",
    location="westus",
    platform_fault_domain_count=2,
    platform_update_domain_count=20,
    resource_group_name="myResourceGroup")

```

```yaml
resources:
  availabilitySet:
    type: azure-native:compute:AvailabilitySet
    properties:
      availabilitySetName: myAvailabilitySet
      location: westus
      platformFaultDomainCount: 2
      platformUpdateDomainCount: 20
      resourceGroupName: myResourceGroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:compute:AvailabilitySet myAvailabilitySet /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/availabilitySets/myAvailabilitySet 
```
