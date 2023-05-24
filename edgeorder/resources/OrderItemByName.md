Represents order item contract
API Version: 2021-12-01.
Previous API Version: 2021-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateOrderItem
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var orderItemByName = new AzureNative.EdgeOrder.OrderItemByName("orderItemByName", new()
    {
        AddressDetails = new AzureNative.EdgeOrder.Inputs.AddressDetailsArgs
        {
            ForwardAddress = new AzureNative.EdgeOrder.Inputs.AddressPropertiesArgs
            {
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
            },
        },
        Location = "eastus",
        OrderId = "/subscriptions/YourSubscriptionId/resourceGroups/YourResourceGroupName/providers/Microsoft.EdgeOrder/locations/eastus/orders/TestOrderName2",
        OrderItemDetails = new AzureNative.EdgeOrder.Inputs.OrderItemDetailsArgs
        {
            OrderItemType = "Purchase",
            Preferences = new AzureNative.EdgeOrder.Inputs.PreferencesArgs
            {
                TransportPreferences = new AzureNative.EdgeOrder.Inputs.TransportPreferencesArgs
                {
                    PreferredShipmentType = "MicrosoftManaged",
                },
            },
            ProductDetails = new AzureNative.EdgeOrder.Inputs.ProductDetailsArgs
            {
                HierarchyInformation = new AzureNative.EdgeOrder.Inputs.HierarchyInformationArgs
                {
                    ConfigurationName = "edgep_base",
                    ProductFamilyName = "azurestackedge",
                    ProductLineName = "azurestackedge",
                    ProductName = "azurestackedgegpu",
                },
            },
        },
        OrderItemName = "TestOrderItemName2",
        ResourceGroupName = "YourResourceGroupName",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.edgeorder.OrderItemByName;
import com.pulumi.azurenative.edgeorder.OrderItemByNameArgs;
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
        var orderItemByName = new OrderItemByName("orderItemByName", OrderItemByNameArgs.builder()        
            .addressDetails(Map.of("forwardAddress", Map.ofEntries(
                Map.entry("contactDetails", Map.ofEntries(
                    Map.entry("contactName", "XXXX XXXX"),
                    Map.entry("emailList", "xxxx@xxxx.xxx"),
                    Map.entry("phone", "0000000000"),
                    Map.entry("phoneExtension", "")
                )),
                Map.entry("shippingAddress", Map.ofEntries(
                    Map.entry("addressType", "None"),
                    Map.entry("city", "San Francisco"),
                    Map.entry("companyName", "Microsoft"),
                    Map.entry("country", "US"),
                    Map.entry("postalCode", "94107"),
                    Map.entry("stateOrProvince", "CA"),
                    Map.entry("streetAddress1", "16 TOWNSEND ST"),
                    Map.entry("streetAddress2", "UNIT 1")
                ))
            )))
            .location("eastus")
            .orderId("/subscriptions/YourSubscriptionId/resourceGroups/YourResourceGroupName/providers/Microsoft.EdgeOrder/locations/eastus/orders/TestOrderName2")
            .orderItemDetails(Map.ofEntries(
                Map.entry("orderItemType", "Purchase"),
                Map.entry("preferences", Map.of("transportPreferences", Map.of("preferredShipmentType", "MicrosoftManaged"))),
                Map.entry("productDetails", Map.of("hierarchyInformation", Map.ofEntries(
                    Map.entry("configurationName", "edgep_base"),
                    Map.entry("productFamilyName", "azurestackedge"),
                    Map.entry("productLineName", "azurestackedge"),
                    Map.entry("productName", "azurestackedgegpu")
                )))
            ))
            .orderItemName("TestOrderItemName2")
            .resourceGroupName("YourResourceGroupName")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const orderItemByName = new azure_native.edgeorder.OrderItemByName("orderItemByName", {
    addressDetails: {
        forwardAddress: {
            contactDetails: {
                contactName: "XXXX XXXX",
                emailList: ["xxxx@xxxx.xxx"],
                phone: "0000000000",
                phoneExtension: "",
            },
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
        },
    },
    location: "eastus",
    orderId: "/subscriptions/YourSubscriptionId/resourceGroups/YourResourceGroupName/providers/Microsoft.EdgeOrder/locations/eastus/orders/TestOrderName2",
    orderItemDetails: {
        orderItemType: "Purchase",
        preferences: {
            transportPreferences: {
                preferredShipmentType: "MicrosoftManaged",
            },
        },
        productDetails: {
            hierarchyInformation: {
                configurationName: "edgep_base",
                productFamilyName: "azurestackedge",
                productLineName: "azurestackedge",
                productName: "azurestackedgegpu",
            },
        },
    },
    orderItemName: "TestOrderItemName2",
    resourceGroupName: "YourResourceGroupName",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

order_item_by_name = azure_native.edgeorder.OrderItemByName("orderItemByName",
    address_details=azure_native.edgeorder.AddressDetailsResponseArgs(
        forward_address={
            "contactDetails": azure_native.edgeorder.ContactDetailsArgs(
                contact_name="XXXX XXXX",
                email_list=["xxxx@xxxx.xxx"],
                phone="0000000000",
                phone_extension="",
            ),
            "shippingAddress": azure_native.edgeorder.ShippingAddressArgs(
                address_type="None",
                city="San Francisco",
                company_name="Microsoft",
                country="US",
                postal_code="94107",
                state_or_province="CA",
                street_address1="16 TOWNSEND ST",
                street_address2="UNIT 1",
            ),
        },
    ),
    location="eastus",
    order_id="/subscriptions/YourSubscriptionId/resourceGroups/YourResourceGroupName/providers/Microsoft.EdgeOrder/locations/eastus/orders/TestOrderName2",
    order_item_details=azure_native.edgeorder.OrderItemDetailsResponseArgs(
        order_item_type="Purchase",
        preferences={
            "transportPreferences": azure_native.edgeorder.TransportPreferencesArgs(
                preferred_shipment_type="MicrosoftManaged",
            ),
        },
        product_details={
            "hierarchyInformation": azure_native.edgeorder.HierarchyInformationArgs(
                configuration_name="edgep_base",
                product_family_name="azurestackedge",
                product_line_name="azurestackedge",
                product_name="azurestackedgegpu",
            ),
        },
    ),
    order_item_name="TestOrderItemName2",
    resource_group_name="YourResourceGroupName")

```

```yaml
resources:
  orderItemByName:
    type: azure-native:edgeorder:OrderItemByName
    properties:
      addressDetails:
        forwardAddress:
          contactDetails:
            contactName: XXXX XXXX
            emailList:
              - xxxx@xxxx.xxx
            phone: '0000000000'
            phoneExtension:
          shippingAddress:
            addressType: None
            city: San Francisco
            companyName: Microsoft
            country: US
            postalCode: '94107'
            stateOrProvince: CA
            streetAddress1: 16 TOWNSEND ST
            streetAddress2: UNIT 1
      location: eastus
      orderId: /subscriptions/YourSubscriptionId/resourceGroups/YourResourceGroupName/providers/Microsoft.EdgeOrder/locations/eastus/orders/TestOrderName2
      orderItemDetails:
        orderItemType: Purchase
        preferences:
          transportPreferences:
            preferredShipmentType: MicrosoftManaged
        productDetails:
          hierarchyInformation:
            configurationName: edgep_base
            productFamilyName: azurestackedge
            productLineName: azurestackedge
            productName: azurestackedgegpu
      orderItemName: TestOrderItemName2
      resourceGroupName: YourResourceGroupName

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:edgeorder:OrderItemByName TestOrderItemName2 /subscriptions/YourSubscriptionId/resourceGroups/YourResourceGroupName/providers/Microsoft.EdgeOrder/orderItems/TestOrderItemName2 
```
