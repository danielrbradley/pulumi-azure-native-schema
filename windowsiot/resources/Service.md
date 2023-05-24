The description of the Windows IoT Device Service.
API Version: 2019-06-01.
Previous API Version: 2019-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Service_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var service = new AzureNative.WindowsIoT.Service("service", new()
    {
        AdminDomainName = "d.e.f",
        BillingDomainName = "a.b.c",
        DeviceName = "service4445",
        Location = "East US",
        Notes = "blah",
        Quantity = 1000000,
        ResourceGroupName = "res9101",
    });

});


```

```go
package main

import (
	windowsiot "github.com/pulumi/pulumi-azure-native-sdk/windowsiot"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := windowsiot.NewService(ctx, "service", &windowsiot.ServiceArgs{
			AdminDomainName:   pulumi.String("d.e.f"),
			BillingDomainName: pulumi.String("a.b.c"),
			DeviceName:        pulumi.String("service4445"),
			Location:          pulumi.String("East US"),
			Notes:             pulumi.String("blah"),
			Quantity:          pulumi.Float64(1000000),
			ResourceGroupName: pulumi.String("res9101"),
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
import com.pulumi.azurenative.windowsiot.Service;
import com.pulumi.azurenative.windowsiot.ServiceArgs;
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
        var service = new Service("service", ServiceArgs.builder()        
            .adminDomainName("d.e.f")
            .billingDomainName("a.b.c")
            .deviceName("service4445")
            .location("East US")
            .notes("blah")
            .quantity(1000000)
            .resourceGroupName("res9101")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const service = new azure_native.windowsiot.Service("service", {
    adminDomainName: "d.e.f",
    billingDomainName: "a.b.c",
    deviceName: "service4445",
    location: "East US",
    notes: "blah",
    quantity: 1000000,
    resourceGroupName: "res9101",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

service = azure_native.windowsiot.Service("service",
    admin_domain_name="d.e.f",
    billing_domain_name="a.b.c",
    device_name="service4445",
    location="East US",
    notes="blah",
    quantity=1000000,
    resource_group_name="res9101")

```

```yaml
resources:
  service:
    type: azure-native:windowsiot:Service
    properties:
      adminDomainName: d.e.f
      billingDomainName: a.b.c
      deviceName: service4445
      location: East US
      notes: blah
      quantity: 1e+06
      resourceGroupName: res9101

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:windowsiot:Service myresource1 /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.WindowsIoT/deviceServices/{deviceName} 
```
