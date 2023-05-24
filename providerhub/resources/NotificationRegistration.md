The notification registration definition.
API Version: 2020-11-20.
Previous API Version: 2020-11-20. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### NotificationRegistrations_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var notificationRegistration = new AzureNative.ProviderHub.NotificationRegistration("notificationRegistration", new()
    {
        NotificationRegistrationName = "fooNotificationRegistration",
        Properties = new AzureNative.ProviderHub.Inputs.NotificationRegistrationPropertiesArgs
        {
            IncludedEvents = new[]
            {
                "*/write",
                "Microsoft.Contoso/employees/delete",
            },
            MessageScope = "RegisteredSubscriptions",
            NotificationEndpoints = new[]
            {
                new AzureNative.ProviderHub.Inputs.NotificationEndpointArgs
                {
                    Locations = new[]
                    {
                        "",
                        "East US",
                    },
                    NotificationDestination = "/subscriptions/ac6bcfb5-3dc1-491f-95a6-646b89bf3e88/resourceGroups/mgmtexp-eastus/providers/Microsoft.EventHub/namespaces/unitedstates-mgmtexpint/eventhubs/armlinkednotifications",
                },
                new AzureNative.ProviderHub.Inputs.NotificationEndpointArgs
                {
                    Locations = new[]
                    {
                        "North Europe",
                    },
                    NotificationDestination = "/subscriptions/ac6bcfb5-3dc1-491f-95a6-646b89bf3e88/resourceGroups/mgmtexp-northeurope/providers/Microsoft.EventHub/namespaces/europe-mgmtexpint/eventhubs/armlinkednotifications",
                },
            },
            NotificationMode = "EventHub",
        },
        ProviderNamespace = "Microsoft.Contoso",
    });

});


```

```go
package main

import (
	providerhub "github.com/pulumi/pulumi-azure-native-sdk/providerhub"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := providerhub.NewNotificationRegistration(ctx, "notificationRegistration", &providerhub.NotificationRegistrationArgs{
			NotificationRegistrationName: pulumi.String("fooNotificationRegistration"),
			Properties: providerhub.NotificationRegistrationResponseProperties{
				IncludedEvents: pulumi.StringArray{
					pulumi.String("*/write"),
					pulumi.String("Microsoft.Contoso/employees/delete"),
				},
				MessageScope: pulumi.String("RegisteredSubscriptions"),
				NotificationEndpoints: providerhub.NotificationEndpointArray{
					&providerhub.NotificationEndpointArgs{
						Locations: pulumi.StringArray{
							pulumi.String(""),
							pulumi.String("East US"),
						},
						NotificationDestination: pulumi.String("/subscriptions/ac6bcfb5-3dc1-491f-95a6-646b89bf3e88/resourceGroups/mgmtexp-eastus/providers/Microsoft.EventHub/namespaces/unitedstates-mgmtexpint/eventhubs/armlinkednotifications"),
					},
					&providerhub.NotificationEndpointArgs{
						Locations: pulumi.StringArray{
							pulumi.String("North Europe"),
						},
						NotificationDestination: pulumi.String("/subscriptions/ac6bcfb5-3dc1-491f-95a6-646b89bf3e88/resourceGroups/mgmtexp-northeurope/providers/Microsoft.EventHub/namespaces/europe-mgmtexpint/eventhubs/armlinkednotifications"),
					},
				},
				NotificationMode: pulumi.String("EventHub"),
			},
			ProviderNamespace: pulumi.String("Microsoft.Contoso"),
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
import com.pulumi.azurenative.providerhub.NotificationRegistration;
import com.pulumi.azurenative.providerhub.NotificationRegistrationArgs;
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
        var notificationRegistration = new NotificationRegistration("notificationRegistration", NotificationRegistrationArgs.builder()        
            .notificationRegistrationName("fooNotificationRegistration")
            .properties(Map.ofEntries(
                Map.entry("includedEvents",                 
                    "*/write",
                    "Microsoft.Contoso/employees/delete"),
                Map.entry("messageScope", "RegisteredSubscriptions"),
                Map.entry("notificationEndpoints",                 
                    Map.ofEntries(
                        Map.entry("locations",                         
                            "",
                            "East US"),
                        Map.entry("notificationDestination", "/subscriptions/ac6bcfb5-3dc1-491f-95a6-646b89bf3e88/resourceGroups/mgmtexp-eastus/providers/Microsoft.EventHub/namespaces/unitedstates-mgmtexpint/eventhubs/armlinkednotifications")
                    ),
                    Map.ofEntries(
                        Map.entry("locations", "North Europe"),
                        Map.entry("notificationDestination", "/subscriptions/ac6bcfb5-3dc1-491f-95a6-646b89bf3e88/resourceGroups/mgmtexp-northeurope/providers/Microsoft.EventHub/namespaces/europe-mgmtexpint/eventhubs/armlinkednotifications")
                    )),
                Map.entry("notificationMode", "EventHub")
            ))
            .providerNamespace("Microsoft.Contoso")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const notificationRegistration = new azure_native.providerhub.NotificationRegistration("notificationRegistration", {
    notificationRegistrationName: "fooNotificationRegistration",
    properties: {
        includedEvents: [
            "*/write",
            "Microsoft.Contoso/employees/delete",
        ],
        messageScope: "RegisteredSubscriptions",
        notificationEndpoints: [
            {
                locations: [
                    "",
                    "East US",
                ],
                notificationDestination: "/subscriptions/ac6bcfb5-3dc1-491f-95a6-646b89bf3e88/resourceGroups/mgmtexp-eastus/providers/Microsoft.EventHub/namespaces/unitedstates-mgmtexpint/eventhubs/armlinkednotifications",
            },
            {
                locations: ["North Europe"],
                notificationDestination: "/subscriptions/ac6bcfb5-3dc1-491f-95a6-646b89bf3e88/resourceGroups/mgmtexp-northeurope/providers/Microsoft.EventHub/namespaces/europe-mgmtexpint/eventhubs/armlinkednotifications",
            },
        ],
        notificationMode: "EventHub",
    },
    providerNamespace: "Microsoft.Contoso",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

notification_registration = azure_native.providerhub.NotificationRegistration("notificationRegistration",
    notification_registration_name="fooNotificationRegistration",
    properties=azure_native.providerhub.NotificationRegistrationResponsePropertiesArgs(
        included_events=[
            "*/write",
            "Microsoft.Contoso/employees/delete",
        ],
        message_scope="RegisteredSubscriptions",
        notification_endpoints=[
            azure_native.providerhub.NotificationEndpointArgs(
                locations=[
                    "",
                    "East US",
                ],
                notification_destination="/subscriptions/ac6bcfb5-3dc1-491f-95a6-646b89bf3e88/resourceGroups/mgmtexp-eastus/providers/Microsoft.EventHub/namespaces/unitedstates-mgmtexpint/eventhubs/armlinkednotifications",
            ),
            azure_native.providerhub.NotificationEndpointArgs(
                locations=["North Europe"],
                notification_destination="/subscriptions/ac6bcfb5-3dc1-491f-95a6-646b89bf3e88/resourceGroups/mgmtexp-northeurope/providers/Microsoft.EventHub/namespaces/europe-mgmtexpint/eventhubs/armlinkednotifications",
            ),
        ],
        notification_mode="EventHub",
    ),
    provider_namespace="Microsoft.Contoso")

```

```yaml
resources:
  notificationRegistration:
    type: azure-native:providerhub:NotificationRegistration
    properties:
      notificationRegistrationName: fooNotificationRegistration
      properties:
        includedEvents:
          - '*/write'
          - Microsoft.Contoso/employees/delete
        messageScope: RegisteredSubscriptions
        notificationEndpoints:
          - locations:
              -
              - East US
            notificationDestination: /subscriptions/ac6bcfb5-3dc1-491f-95a6-646b89bf3e88/resourceGroups/mgmtexp-eastus/providers/Microsoft.EventHub/namespaces/unitedstates-mgmtexpint/eventhubs/armlinkednotifications
          - locations:
              - North Europe
            notificationDestination: /subscriptions/ac6bcfb5-3dc1-491f-95a6-646b89bf3e88/resourceGroups/mgmtexp-northeurope/providers/Microsoft.EventHub/namespaces/europe-mgmtexpint/eventhubs/armlinkednotifications
        notificationMode: EventHub
      providerNamespace: Microsoft.Contoso

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:providerhub:NotificationRegistration fooNotificationRegistration /subscriptions/ab7a8701-f7ef-471a-a2f4-d0ebbf494f77providers/Microsoft.ProviderHub/providerRegistrations/Microsoft.Contoso/notificationregistrations/fooNotificationRegistration 
```
