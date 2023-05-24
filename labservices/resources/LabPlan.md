Lab Plans act as a permission container for creating labs via labs.azure.com. Additionally, they can provide a set of default configurations that will apply at the time of creating a lab, but these defaults can still be overwritten.
API Version: 2022-08-01.
Previous API Version: 2021-10-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### putLabPlan
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var labPlan = new AzureNative.LabServices.LabPlan("labPlan", new()
    {
        DefaultAutoShutdownProfile = new AzureNative.LabServices.Inputs.AutoShutdownProfileArgs
        {
            DisconnectDelay = "PT5M",
            IdleDelay = "PT5M",
            NoConnectDelay = "PT5M",
            ShutdownOnDisconnect = AzureNative.LabServices.EnableState.Enabled,
            ShutdownOnIdle = AzureNative.LabServices.ShutdownOnIdleMode.UserAbsence,
            ShutdownWhenNotConnected = AzureNative.LabServices.EnableState.Enabled,
        },
        DefaultConnectionProfile = new AzureNative.LabServices.Inputs.ConnectionProfileArgs
        {
            ClientRdpAccess = AzureNative.LabServices.ConnectionType.Public,
            ClientSshAccess = AzureNative.LabServices.ConnectionType.Public,
            WebRdpAccess = AzureNative.LabServices.ConnectionType.None,
            WebSshAccess = AzureNative.LabServices.ConnectionType.None,
        },
        DefaultNetworkProfile = new AzureNative.LabServices.Inputs.LabPlanNetworkProfileArgs
        {
            SubnetId = "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/default",
        },
        LabPlanName = "testlabplan",
        Location = "westus",
        ResourceGroupName = "testrg123",
        SharedGalleryId = "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.Compute/galleries/testsig",
        SupportInfo = new AzureNative.LabServices.Inputs.SupportInfoArgs
        {
            Email = "help@contoso.com",
            Instructions = "Contact support for help.",
            Phone = "+1-202-555-0123",
            Url = "help.contoso.com",
        },
    });

});


```

```go
package main

import (
	labservices "github.com/pulumi/pulumi-azure-native-sdk/labservices"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := labservices.NewLabPlan(ctx, "labPlan", &labservices.LabPlanArgs{
			DefaultAutoShutdownProfile: &labservices.AutoShutdownProfileArgs{
				DisconnectDelay:          pulumi.String("PT5M"),
				IdleDelay:                pulumi.String("PT5M"),
				NoConnectDelay:           pulumi.String("PT5M"),
				ShutdownOnDisconnect:     labservices.EnableStateEnabled,
				ShutdownOnIdle:           labservices.ShutdownOnIdleModeUserAbsence,
				ShutdownWhenNotConnected: labservices.EnableStateEnabled,
			},
			DefaultConnectionProfile: &labservices.ConnectionProfileArgs{
				ClientRdpAccess: labservices.ConnectionTypePublic,
				ClientSshAccess: labservices.ConnectionTypePublic,
				WebRdpAccess:    labservices.ConnectionTypeNone,
				WebSshAccess:    labservices.ConnectionTypeNone,
			},
			DefaultNetworkProfile: &labservices.LabPlanNetworkProfileArgs{
				SubnetId: pulumi.String("/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/default"),
			},
			LabPlanName:       pulumi.String("testlabplan"),
			Location:          pulumi.String("westus"),
			ResourceGroupName: pulumi.String("testrg123"),
			SharedGalleryId:   pulumi.String("/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.Compute/galleries/testsig"),
			SupportInfo: &labservices.SupportInfoArgs{
				Email:        pulumi.String("help@contoso.com"),
				Instructions: pulumi.String("Contact support for help."),
				Phone:        pulumi.String("+1-202-555-0123"),
				Url:          pulumi.String("help.contoso.com"),
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
import com.pulumi.azurenative.labservices.LabPlan;
import com.pulumi.azurenative.labservices.LabPlanArgs;
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
        var labPlan = new LabPlan("labPlan", LabPlanArgs.builder()        
            .defaultAutoShutdownProfile(Map.ofEntries(
                Map.entry("disconnectDelay", "PT5M"),
                Map.entry("idleDelay", "PT5M"),
                Map.entry("noConnectDelay", "PT5M"),
                Map.entry("shutdownOnDisconnect", "Enabled"),
                Map.entry("shutdownOnIdle", "UserAbsence"),
                Map.entry("shutdownWhenNotConnected", "Enabled")
            ))
            .defaultConnectionProfile(Map.ofEntries(
                Map.entry("clientRdpAccess", "Public"),
                Map.entry("clientSshAccess", "Public"),
                Map.entry("webRdpAccess", "None"),
                Map.entry("webSshAccess", "None")
            ))
            .defaultNetworkProfile(Map.of("subnetId", "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/default"))
            .labPlanName("testlabplan")
            .location("westus")
            .resourceGroupName("testrg123")
            .sharedGalleryId("/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.Compute/galleries/testsig")
            .supportInfo(Map.ofEntries(
                Map.entry("email", "help@contoso.com"),
                Map.entry("instructions", "Contact support for help."),
                Map.entry("phone", "+1-202-555-0123"),
                Map.entry("url", "help.contoso.com")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const labPlan = new azure_native.labservices.LabPlan("labPlan", {
    defaultAutoShutdownProfile: {
        disconnectDelay: "PT5M",
        idleDelay: "PT5M",
        noConnectDelay: "PT5M",
        shutdownOnDisconnect: azure_native.labservices.EnableState.Enabled,
        shutdownOnIdle: azure_native.labservices.ShutdownOnIdleMode.UserAbsence,
        shutdownWhenNotConnected: azure_native.labservices.EnableState.Enabled,
    },
    defaultConnectionProfile: {
        clientRdpAccess: azure_native.labservices.ConnectionType.Public,
        clientSshAccess: azure_native.labservices.ConnectionType.Public,
        webRdpAccess: azure_native.labservices.ConnectionType.None,
        webSshAccess: azure_native.labservices.ConnectionType.None,
    },
    defaultNetworkProfile: {
        subnetId: "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/default",
    },
    labPlanName: "testlabplan",
    location: "westus",
    resourceGroupName: "testrg123",
    sharedGalleryId: "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.Compute/galleries/testsig",
    supportInfo: {
        email: "help@contoso.com",
        instructions: "Contact support for help.",
        phone: "+1-202-555-0123",
        url: "help.contoso.com",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

lab_plan = azure_native.labservices.LabPlan("labPlan",
    default_auto_shutdown_profile=azure_native.labservices.AutoShutdownProfileArgs(
        disconnect_delay="PT5M",
        idle_delay="PT5M",
        no_connect_delay="PT5M",
        shutdown_on_disconnect=azure_native.labservices.EnableState.ENABLED,
        shutdown_on_idle=azure_native.labservices.ShutdownOnIdleMode.USER_ABSENCE,
        shutdown_when_not_connected=azure_native.labservices.EnableState.ENABLED,
    ),
    default_connection_profile=azure_native.labservices.ConnectionProfileArgs(
        client_rdp_access=azure_native.labservices.ConnectionType.PUBLIC,
        client_ssh_access=azure_native.labservices.ConnectionType.PUBLIC,
        web_rdp_access=azure_native.labservices.ConnectionType.NONE,
        web_ssh_access=azure_native.labservices.ConnectionType.NONE,
    ),
    default_network_profile=azure_native.labservices.LabPlanNetworkProfileArgs(
        subnet_id="/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/default",
    ),
    lab_plan_name="testlabplan",
    location="westus",
    resource_group_name="testrg123",
    shared_gallery_id="/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.Compute/galleries/testsig",
    support_info=azure_native.labservices.SupportInfoArgs(
        email="help@contoso.com",
        instructions="Contact support for help.",
        phone="+1-202-555-0123",
        url="help.contoso.com",
    ))

```

```yaml
resources:
  labPlan:
    type: azure-native:labservices:LabPlan
    properties:
      defaultAutoShutdownProfile:
        disconnectDelay: PT5M
        idleDelay: PT5M
        noConnectDelay: PT5M
        shutdownOnDisconnect: Enabled
        shutdownOnIdle: UserAbsence
        shutdownWhenNotConnected: Enabled
      defaultConnectionProfile:
        clientRdpAccess: Public
        clientSshAccess: Public
        webRdpAccess: None
        webSshAccess: None
      defaultNetworkProfile:
        subnetId: /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/default
      labPlanName: testlabplan
      location: westus
      resourceGroupName: testrg123
      sharedGalleryId: /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.Compute/galleries/testsig
      supportInfo:
        email: help@contoso.com
        instructions: Contact support for help.
        phone: +1-202-555-0123
        url: help.contoso.com

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:labservices:LabPlan testlabplan /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.LabServices/labPlans/testlabplan 
```
