The lab resource.
API Version: 2022-08-01.
Previous API Version: 2018-10-15. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### putLab
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var lab = new AzureNative.LabServices.Lab("lab", new()
    {
        AutoShutdownProfile = new AzureNative.LabServices.Inputs.AutoShutdownProfileArgs
        {
            DisconnectDelay = "PT5M",
            IdleDelay = "PT5M",
            NoConnectDelay = "PT5M",
            ShutdownOnDisconnect = AzureNative.LabServices.EnableState.Enabled,
            ShutdownOnIdle = AzureNative.LabServices.ShutdownOnIdleMode.UserAbsence,
            ShutdownWhenNotConnected = AzureNative.LabServices.EnableState.Enabled,
        },
        ConnectionProfile = new AzureNative.LabServices.Inputs.ConnectionProfileArgs
        {
            ClientRdpAccess = AzureNative.LabServices.ConnectionType.Public,
            ClientSshAccess = AzureNative.LabServices.ConnectionType.Public,
            WebRdpAccess = AzureNative.LabServices.ConnectionType.None,
            WebSshAccess = AzureNative.LabServices.ConnectionType.None,
        },
        Description = "This is a test lab.",
        LabName = "testlab",
        LabPlanId = "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.LabServices/labPlans/testlabplan",
        Location = "westus",
        NetworkProfile = new AzureNative.LabServices.Inputs.LabNetworkProfileArgs
        {
            SubnetId = "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/default",
        },
        ResourceGroupName = "testrg123",
        SecurityProfile = new AzureNative.LabServices.Inputs.SecurityProfileArgs
        {
            OpenAccess = AzureNative.LabServices.EnableState.Disabled,
        },
        Title = "Test Lab",
        VirtualMachineProfile = new AzureNative.LabServices.Inputs.VirtualMachineProfileArgs
        {
            AdditionalCapabilities = new AzureNative.LabServices.Inputs.VirtualMachineAdditionalCapabilitiesArgs
            {
                InstallGpuDrivers = AzureNative.LabServices.EnableState.Disabled,
            },
            AdminUser = new AzureNative.LabServices.Inputs.CredentialsArgs
            {
                Username = "test-user",
            },
            CreateOption = AzureNative.LabServices.CreateOption.TemplateVM,
            ImageReference = new AzureNative.LabServices.Inputs.ImageReferenceArgs
            {
                Offer = "WindowsServer",
                Publisher = "Microsoft",
                Sku = "2019-Datacenter",
                Version = "2019.0.20190410",
            },
            Sku = new AzureNative.LabServices.Inputs.SkuArgs
            {
                Name = "Medium",
            },
            UsageQuota = "PT10H",
            UseSharedPassword = AzureNative.LabServices.EnableState.Disabled,
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
		_, err := labservices.NewLab(ctx, "lab", &labservices.LabArgs{
			AutoShutdownProfile: &labservices.AutoShutdownProfileArgs{
				DisconnectDelay:          pulumi.String("PT5M"),
				IdleDelay:                pulumi.String("PT5M"),
				NoConnectDelay:           pulumi.String("PT5M"),
				ShutdownOnDisconnect:     labservices.EnableStateEnabled,
				ShutdownOnIdle:           labservices.ShutdownOnIdleModeUserAbsence,
				ShutdownWhenNotConnected: labservices.EnableStateEnabled,
			},
			ConnectionProfile: &labservices.ConnectionProfileArgs{
				ClientRdpAccess: labservices.ConnectionTypePublic,
				ClientSshAccess: labservices.ConnectionTypePublic,
				WebRdpAccess:    labservices.ConnectionTypeNone,
				WebSshAccess:    labservices.ConnectionTypeNone,
			},
			Description: pulumi.String("This is a test lab."),
			LabName:     pulumi.String("testlab"),
			LabPlanId:   pulumi.String("/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.LabServices/labPlans/testlabplan"),
			Location:    pulumi.String("westus"),
			NetworkProfile: &labservices.LabNetworkProfileArgs{
				SubnetId: pulumi.String("/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/default"),
			},
			ResourceGroupName: pulumi.String("testrg123"),
			SecurityProfile: &labservices.SecurityProfileArgs{
				OpenAccess: labservices.EnableStateDisabled,
			},
			Title: pulumi.String("Test Lab"),
			VirtualMachineProfile: labservices.VirtualMachineProfileResponse{
				AdditionalCapabilities: &labservices.VirtualMachineAdditionalCapabilitiesArgs{
					InstallGpuDrivers: labservices.EnableStateDisabled,
				},
				AdminUser: &labservices.CredentialsArgs{
					Username: pulumi.String("test-user"),
				},
				CreateOption: labservices.CreateOptionTemplateVM,
				ImageReference: &labservices.ImageReferenceArgs{
					Offer:     pulumi.String("WindowsServer"),
					Publisher: pulumi.String("Microsoft"),
					Sku:       pulumi.String("2019-Datacenter"),
					Version:   pulumi.String("2019.0.20190410"),
				},
				Sku: &labservices.SkuArgs{
					Name: pulumi.String("Medium"),
				},
				UsageQuota:        pulumi.String("PT10H"),
				UseSharedPassword: labservices.EnableStateDisabled,
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
import com.pulumi.azurenative.labservices.Lab;
import com.pulumi.azurenative.labservices.LabArgs;
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
        var lab = new Lab("lab", LabArgs.builder()        
            .autoShutdownProfile(Map.ofEntries(
                Map.entry("disconnectDelay", "PT5M"),
                Map.entry("idleDelay", "PT5M"),
                Map.entry("noConnectDelay", "PT5M"),
                Map.entry("shutdownOnDisconnect", "Enabled"),
                Map.entry("shutdownOnIdle", "UserAbsence"),
                Map.entry("shutdownWhenNotConnected", "Enabled")
            ))
            .connectionProfile(Map.ofEntries(
                Map.entry("clientRdpAccess", "Public"),
                Map.entry("clientSshAccess", "Public"),
                Map.entry("webRdpAccess", "None"),
                Map.entry("webSshAccess", "None")
            ))
            .description("This is a test lab.")
            .labName("testlab")
            .labPlanId("/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.LabServices/labPlans/testlabplan")
            .location("westus")
            .networkProfile(Map.of("subnetId", "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/default"))
            .resourceGroupName("testrg123")
            .securityProfile(Map.of("openAccess", "Disabled"))
            .title("Test Lab")
            .virtualMachineProfile(Map.ofEntries(
                Map.entry("additionalCapabilities", Map.of("installGpuDrivers", "Disabled")),
                Map.entry("adminUser", Map.of("username", "test-user")),
                Map.entry("createOption", "TemplateVM"),
                Map.entry("imageReference", Map.ofEntries(
                    Map.entry("offer", "WindowsServer"),
                    Map.entry("publisher", "Microsoft"),
                    Map.entry("sku", "2019-Datacenter"),
                    Map.entry("version", "2019.0.20190410")
                )),
                Map.entry("sku", Map.of("name", "Medium")),
                Map.entry("usageQuota", "PT10H"),
                Map.entry("useSharedPassword", "Disabled")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const lab = new azure_native.labservices.Lab("lab", {
    autoShutdownProfile: {
        disconnectDelay: "PT5M",
        idleDelay: "PT5M",
        noConnectDelay: "PT5M",
        shutdownOnDisconnect: azure_native.labservices.EnableState.Enabled,
        shutdownOnIdle: azure_native.labservices.ShutdownOnIdleMode.UserAbsence,
        shutdownWhenNotConnected: azure_native.labservices.EnableState.Enabled,
    },
    connectionProfile: {
        clientRdpAccess: azure_native.labservices.ConnectionType.Public,
        clientSshAccess: azure_native.labservices.ConnectionType.Public,
        webRdpAccess: azure_native.labservices.ConnectionType.None,
        webSshAccess: azure_native.labservices.ConnectionType.None,
    },
    description: "This is a test lab.",
    labName: "testlab",
    labPlanId: "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.LabServices/labPlans/testlabplan",
    location: "westus",
    networkProfile: {
        subnetId: "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/default",
    },
    resourceGroupName: "testrg123",
    securityProfile: {
        openAccess: azure_native.labservices.EnableState.Disabled,
    },
    title: "Test Lab",
    virtualMachineProfile: {
        additionalCapabilities: {
            installGpuDrivers: azure_native.labservices.EnableState.Disabled,
        },
        adminUser: {
            username: "test-user",
        },
        createOption: azure_native.labservices.CreateOption.TemplateVM,
        imageReference: {
            offer: "WindowsServer",
            publisher: "Microsoft",
            sku: "2019-Datacenter",
            version: "2019.0.20190410",
        },
        sku: {
            name: "Medium",
        },
        usageQuota: "PT10H",
        useSharedPassword: azure_native.labservices.EnableState.Disabled,
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

lab = azure_native.labservices.Lab("lab",
    auto_shutdown_profile=azure_native.labservices.AutoShutdownProfileArgs(
        disconnect_delay="PT5M",
        idle_delay="PT5M",
        no_connect_delay="PT5M",
        shutdown_on_disconnect=azure_native.labservices.EnableState.ENABLED,
        shutdown_on_idle=azure_native.labservices.ShutdownOnIdleMode.USER_ABSENCE,
        shutdown_when_not_connected=azure_native.labservices.EnableState.ENABLED,
    ),
    connection_profile=azure_native.labservices.ConnectionProfileArgs(
        client_rdp_access=azure_native.labservices.ConnectionType.PUBLIC,
        client_ssh_access=azure_native.labservices.ConnectionType.PUBLIC,
        web_rdp_access=azure_native.labservices.ConnectionType.NONE,
        web_ssh_access=azure_native.labservices.ConnectionType.NONE,
    ),
    description="This is a test lab.",
    lab_name="testlab",
    lab_plan_id="/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.LabServices/labPlans/testlabplan",
    location="westus",
    network_profile=azure_native.labservices.LabNetworkProfileArgs(
        subnet_id="/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/default",
    ),
    resource_group_name="testrg123",
    security_profile=azure_native.labservices.SecurityProfileArgs(
        open_access=azure_native.labservices.EnableState.DISABLED,
    ),
    title="Test Lab",
    virtual_machine_profile=azure_native.labservices.VirtualMachineProfileResponseArgs(
        additional_capabilities=azure_native.labservices.VirtualMachineAdditionalCapabilitiesArgs(
            install_gpu_drivers=azure_native.labservices.EnableState.DISABLED,
        ),
        admin_user=azure_native.labservices.CredentialsArgs(
            username="test-user",
        ),
        create_option=azure_native.labservices.CreateOption.TEMPLATE_VM,
        image_reference=azure_native.labservices.ImageReferenceArgs(
            offer="WindowsServer",
            publisher="Microsoft",
            sku="2019-Datacenter",
            version="2019.0.20190410",
        ),
        sku=azure_native.labservices.SkuArgs(
            name="Medium",
        ),
        usage_quota="PT10H",
        use_shared_password=azure_native.labservices.EnableState.DISABLED,
    ))

```

```yaml
resources:
  lab:
    type: azure-native:labservices:Lab
    properties:
      autoShutdownProfile:
        disconnectDelay: PT5M
        idleDelay: PT5M
        noConnectDelay: PT5M
        shutdownOnDisconnect: Enabled
        shutdownOnIdle: UserAbsence
        shutdownWhenNotConnected: Enabled
      connectionProfile:
        clientRdpAccess: Public
        clientSshAccess: Public
        webRdpAccess: None
        webSshAccess: None
      description: This is a test lab.
      labName: testlab
      labPlanId: /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.LabServices/labPlans/testlabplan
      location: westus
      networkProfile:
        subnetId: /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/default
      resourceGroupName: testrg123
      securityProfile:
        openAccess: Disabled
      title: Test Lab
      virtualMachineProfile:
        additionalCapabilities:
          installGpuDrivers: Disabled
        adminUser:
          username: test-user
        createOption: TemplateVM
        imageReference:
          offer: WindowsServer
          publisher: Microsoft
          sku: 2019-Datacenter
          version: 2019.0.20190410
        sku:
          name: Medium
        usageQuota: PT10H
        useSharedPassword: Disabled

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:labservices:Lab testlabplan /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.LabServices/labs/testlab 
```
