The order details.
API Version: 2022-03-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### OrderPut
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var order = new AzureNative.DataBoxEdge.Order("order", new()
    {
        ContactInformation = new AzureNative.DataBoxEdge.Inputs.ContactDetailsArgs
        {
            CompanyName = "Microsoft",
            ContactPerson = "John Mcclane",
            EmailList = new[]
            {
                "john@microsoft.com",
            },
            Phone = "(800) 426-9400",
        },
        DeviceName = "testedgedevice",
        ResourceGroupName = "GroupForEdgeAutomation",
        ShippingAddress = new AzureNative.DataBoxEdge.Inputs.AddressArgs
        {
            AddressLine1 = "Microsoft Corporation",
            AddressLine2 = "One Microsoft Way",
            AddressLine3 = "Redmond",
            City = "WA",
            Country = "USA",
            PostalCode = "98052",
            State = "WA",
        },
    });

});


```

```go
package main

import (
	databoxedge "github.com/pulumi/pulumi-azure-native-sdk/databoxedge"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := databoxedge.NewOrder(ctx, "order", &databoxedge.OrderArgs{
			ContactInformation: &databoxedge.ContactDetailsArgs{
				CompanyName:   pulumi.String("Microsoft"),
				ContactPerson: pulumi.String("John Mcclane"),
				EmailList: pulumi.StringArray{
					pulumi.String("john@microsoft.com"),
				},
				Phone: pulumi.String("(800) 426-9400"),
			},
			DeviceName:        pulumi.String("testedgedevice"),
			ResourceGroupName: pulumi.String("GroupForEdgeAutomation"),
			ShippingAddress: &databoxedge.AddressArgs{
				AddressLine1: pulumi.String("Microsoft Corporation"),
				AddressLine2: pulumi.String("One Microsoft Way"),
				AddressLine3: pulumi.String("Redmond"),
				City:         pulumi.String("WA"),
				Country:      pulumi.String("USA"),
				PostalCode:   pulumi.String("98052"),
				State:        pulumi.String("WA"),
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
import com.pulumi.azurenative.databoxedge.Order;
import com.pulumi.azurenative.databoxedge.OrderArgs;
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
        var order = new Order("order", OrderArgs.builder()        
            .contactInformation(Map.ofEntries(
                Map.entry("companyName", "Microsoft"),
                Map.entry("contactPerson", "John Mcclane"),
                Map.entry("emailList", "john@microsoft.com"),
                Map.entry("phone", "(800) 426-9400")
            ))
            .deviceName("testedgedevice")
            .resourceGroupName("GroupForEdgeAutomation")
            .shippingAddress(Map.ofEntries(
                Map.entry("addressLine1", "Microsoft Corporation"),
                Map.entry("addressLine2", "One Microsoft Way"),
                Map.entry("addressLine3", "Redmond"),
                Map.entry("city", "WA"),
                Map.entry("country", "USA"),
                Map.entry("postalCode", "98052"),
                Map.entry("state", "WA")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const order = new azure_native.databoxedge.Order("order", {
    contactInformation: {
        companyName: "Microsoft",
        contactPerson: "John Mcclane",
        emailList: ["john@microsoft.com"],
        phone: "(800) 426-9400",
    },
    deviceName: "testedgedevice",
    resourceGroupName: "GroupForEdgeAutomation",
    shippingAddress: {
        addressLine1: "Microsoft Corporation",
        addressLine2: "One Microsoft Way",
        addressLine3: "Redmond",
        city: "WA",
        country: "USA",
        postalCode: "98052",
        state: "WA",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

order = azure_native.databoxedge.Order("order",
    contact_information=azure_native.databoxedge.ContactDetailsArgs(
        company_name="Microsoft",
        contact_person="John Mcclane",
        email_list=["john@microsoft.com"],
        phone="(800) 426-9400",
    ),
    device_name="testedgedevice",
    resource_group_name="GroupForEdgeAutomation",
    shipping_address=azure_native.databoxedge.AddressArgs(
        address_line1="Microsoft Corporation",
        address_line2="One Microsoft Way",
        address_line3="Redmond",
        city="WA",
        country="USA",
        postal_code="98052",
        state="WA",
    ))

```

```yaml
resources:
  order:
    type: azure-native:databoxedge:Order
    properties:
      contactInformation:
        companyName: Microsoft
        contactPerson: John Mcclane
        emailList:
          - john@microsoft.com
        phone: (800) 426-9400
      deviceName: testedgedevice
      resourceGroupName: GroupForEdgeAutomation
      shippingAddress:
        addressLine1: Microsoft Corporation
        addressLine2: One Microsoft Way
        addressLine3: Redmond
        city: WA
        country: USA
        postalCode: '98052'
        state: WA

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:databoxedge:Order default /subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/GroupForEdgeAutomation/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/testedgedevice/orders/default 
```
