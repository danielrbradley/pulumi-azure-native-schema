Customer creates a contact resource for a spacecraft resource.
API Version: 2022-11-01.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a contact
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var contact = new AzureNative.Orbital.Contact("contact", new()
    {
        ContactName = "contact1",
        ContactProfile = new AzureNative.Orbital.Inputs.ContactsPropertiesContactProfileArgs
        {
            Id = "/subscriptions/c1be1141-a7c9-4aac-9608-3c2e2f1152c3/resourceGroups/contoso-Rgp/providers/Microsoft.Orbital/contactProfiles/CONTOSO-CP",
        },
        GroundStationName = "EASTUS2_0",
        ReservationEndTime = "2023-02-22T11:10:45Z",
        ReservationStartTime = "2023-02-22T10:58:30Z",
        ResourceGroupName = "contoso-Rgp",
        SpacecraftName = "CONTOSO_SAT",
    });

});


```

```go
package main

import (
	orbital "github.com/pulumi/pulumi-azure-native-sdk/orbital"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := orbital.NewContact(ctx, "contact", &orbital.ContactArgs{
			ContactName: pulumi.String("contact1"),
			ContactProfile: &orbital.ContactsPropertiesContactProfileArgs{
				Id: pulumi.String("/subscriptions/c1be1141-a7c9-4aac-9608-3c2e2f1152c3/resourceGroups/contoso-Rgp/providers/Microsoft.Orbital/contactProfiles/CONTOSO-CP"),
			},
			GroundStationName:    pulumi.String("EASTUS2_0"),
			ReservationEndTime:   pulumi.String("2023-02-22T11:10:45Z"),
			ReservationStartTime: pulumi.String("2023-02-22T10:58:30Z"),
			ResourceGroupName:    pulumi.String("contoso-Rgp"),
			SpacecraftName:       pulumi.String("CONTOSO_SAT"),
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
import com.pulumi.azurenative.orbital.Contact;
import com.pulumi.azurenative.orbital.ContactArgs;
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
        var contact = new Contact("contact", ContactArgs.builder()        
            .contactName("contact1")
            .contactProfile(Map.of("id", "/subscriptions/c1be1141-a7c9-4aac-9608-3c2e2f1152c3/resourceGroups/contoso-Rgp/providers/Microsoft.Orbital/contactProfiles/CONTOSO-CP"))
            .groundStationName("EASTUS2_0")
            .reservationEndTime("2023-02-22T11:10:45Z")
            .reservationStartTime("2023-02-22T10:58:30Z")
            .resourceGroupName("contoso-Rgp")
            .spacecraftName("CONTOSO_SAT")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const contact = new azure_native.orbital.Contact("contact", {
    contactName: "contact1",
    contactProfile: {
        id: "/subscriptions/c1be1141-a7c9-4aac-9608-3c2e2f1152c3/resourceGroups/contoso-Rgp/providers/Microsoft.Orbital/contactProfiles/CONTOSO-CP",
    },
    groundStationName: "EASTUS2_0",
    reservationEndTime: "2023-02-22T11:10:45Z",
    reservationStartTime: "2023-02-22T10:58:30Z",
    resourceGroupName: "contoso-Rgp",
    spacecraftName: "CONTOSO_SAT",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

contact = azure_native.orbital.Contact("contact",
    contact_name="contact1",
    contact_profile=azure_native.orbital.ContactsPropertiesContactProfileArgs(
        id="/subscriptions/c1be1141-a7c9-4aac-9608-3c2e2f1152c3/resourceGroups/contoso-Rgp/providers/Microsoft.Orbital/contactProfiles/CONTOSO-CP",
    ),
    ground_station_name="EASTUS2_0",
    reservation_end_time="2023-02-22T11:10:45Z",
    reservation_start_time="2023-02-22T10:58:30Z",
    resource_group_name="contoso-Rgp",
    spacecraft_name="CONTOSO_SAT")

```

```yaml
resources:
  contact:
    type: azure-native:orbital:Contact
    properties:
      contactName: contact1
      contactProfile:
        id: /subscriptions/c1be1141-a7c9-4aac-9608-3c2e2f1152c3/resourceGroups/contoso-Rgp/providers/Microsoft.Orbital/contactProfiles/CONTOSO-CP
      groundStationName: EASTUS2_0
      reservationEndTime: 2023-02-22T11:10:45Z
      reservationStartTime: 2023-02-22T10:58:30Z
      resourceGroupName: contoso-Rgp
      spacecraftName: CONTOSO_SAT

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:orbital:Contact contact1 /subscriptions/c1be1141-a7c9-4aac-9608-3c2e2f1152c3/resourceGroups/contoso-Rgp/providers/Microsoft.Orbital/spacecrafts/CONTOSO_SAT/contacts/contact1 
```
