Address Resource.
API Version: 2021-12-01.
Previous API Version: 2021-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateAddress
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var addressByName = new AzureNative.EdgeOrder.AddressByName("addressByName", new()
    {
        AddressName = "TestAddressName2",
        ContactDetails = new AzureNative.EdgeOrder.Inputs.ContactDetailsArgs
        {
            ContactName = "XXXX XXXX",
            EmailList = new[]
            {
                "xxxx@xxxx.xxx",
            },
            Phone = "0000000000",
            PhoneExtension = "",
        },
        Location = "eastus",
        ResourceGroupName = "YourResourceGroupName",
        ShippingAddress = new AzureNative.EdgeOrder.Inputs.ShippingAddressArgs
        {
            AddressType = "None",
            City = "San Francisco",
            CompanyName = "Microsoft",
            Country = "US",
            PostalCode = "94107",
            StateOrProvince = "CA",
            StreetAddress1 = "16 TOWNSEND ST",
            StreetAddress2 = "UNIT 1",
        },
    });

});


```

```go
package main

import (
	edgeorder "github.com/pulumi/pulumi-azure-native-sdk/edgeorder"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := edgeorder.NewAddressByName(ctx, "addressByName", &edgeorder.AddressByNameArgs{
			AddressName: pulumi.String("TestAddressName2"),
			ContactDetails: &edgeorder.ContactDetailsArgs{
				ContactName: pulumi.String("XXXX XXXX"),
				EmailList: pulumi.StringArray{
					pulumi.String("xxxx@xxxx.xxx"),
				},
				Phone:          pulumi.String("0000000000"),
				PhoneExtension: pulumi.String(""),
			},
			Location:          pulumi.String("eastus"),
			ResourceGroupName: pulumi.String("YourResourceGroupName"),
			ShippingAddress: &edgeorder.ShippingAddressArgs{
				AddressType:     pulumi.String("None"),
				City:            pulumi.String("San Francisco"),
				CompanyName:     pulumi.String("Microsoft"),
				Country:         pulumi.String("US"),
				PostalCode:      pulumi.String("94107"),
				StateOrProvince: pulumi.String("CA"),
				StreetAddress1:  pulumi.String("16 TOWNSEND ST"),
				StreetAddress2:  pulumi.String("UNIT 1"),
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
import com.pulumi.azurenative.edgeorder.AddressByName;
import com.pulumi.azurenative.edgeorder.AddressByNameArgs;
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
        var addressByName = new AddressByName("addressByName", AddressByNameArgs.builder()        
            .addressName("TestAddressName2")
            .contactDetails(Map.ofEntries(
                Map.entry("contactName", "XXXX XXXX"),
                Map.entry("emailList", "xxxx@xxxx.xxx"),
                Map.entry("phone", "0000000000"),
                Map.entry("phoneExtension", "")
            ))
            .location("eastus")
            .resourceGroupName("YourResourceGroupName")
            .shippingAddress(Map.ofEntries(
                Map.entry("addressType", "None"),
                Map.entry("city", "San Francisco"),
                Map.entry("companyName", "Microsoft"),
                Map.entry("country", "US"),
                Map.entry("postalCode", "94107"),
                Map.entry("stateOrProvince", "CA"),
                Map.entry("streetAddress1", "16 TOWNSEND ST"),
                Map.entry("streetAddress2", "UNIT 1")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const addressByName = new azure_native.edgeorder.AddressByName("addressByName", {
    addressName: "TestAddressName2",
    contactDetails: {
        contactName: "XXXX XXXX",
        emailList: ["xxxx@xxxx.xxx"],
        phone: "0000000000",
        phoneExtension: "",
    },
    location: "eastus",
    resourceGroupName: "YourResourceGroupName",
    shippingAddress: {
        addressType: "None",
        city: "San Francisco",
        companyName: "Microsoft",
        country: "US",
        postalCode: "94107",
        stateOrProvince: "CA",
        streetAddress1: "16 TOWNSEND ST",
        streetAddress2: "UNIT 1",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

address_by_name = azure_native.edgeorder.AddressByName("addressByName",
    address_name="TestAddressName2",
    contact_details=azure_native.edgeorder.ContactDetailsArgs(
        contact_name="XXXX XXXX",
        email_list=["xxxx@xxxx.xxx"],
        phone="0000000000",
        phone_extension="",
    ),
    location="eastus",
    resource_group_name="YourResourceGroupName",
    shipping_address=azure_native.edgeorder.ShippingAddressArgs(
        address_type="None",
        city="San Francisco",
        company_name="Microsoft",
        country="US",
        postal_code="94107",
        state_or_province="CA",
        street_address1="16 TOWNSEND ST",
        street_address2="UNIT 1",
    ))

```

```yaml
resources:
  addressByName:
    type: azure-native:edgeorder:AddressByName
    properties:
      addressName: TestAddressName2
      contactDetails:
        contactName: XXXX XXXX
        emailList:
          - xxxx@xxxx.xxx
        phone: '0000000000'
        phoneExtension:
      location: eastus
      resourceGroupName: YourResourceGroupName
      shippingAddress:
        addressType: None
        city: San Francisco
        companyName: Microsoft
        country: US
        postalCode: '94107'
        stateOrProvince: CA
        streetAddress1: 16 TOWNSEND ST
        streetAddress2: UNIT 1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:edgeorder:AddressByName TestAddressName2 /subscriptions/YourSubscriptionId/resourceGroups/YourResourceGroupName/providers/Microsoft.EdgeOrder/addresses/TestAddressName2 
```
