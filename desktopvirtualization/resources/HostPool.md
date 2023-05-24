Represents a HostPool definition.
API Version: 2022-09-09.
Previous API Version: 2021-02-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### HostPool_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var hostPool = new AzureNative.DesktopVirtualization.HostPool("hostPool", new()
    {
        AgentUpdate = new AzureNative.DesktopVirtualization.Inputs.AgentUpdatePropertiesArgs
        {
            MaintenanceWindowTimeZone = "Alaskan Standard Time",
            MaintenanceWindows = new[]
            {
                new AzureNative.DesktopVirtualization.Inputs.MaintenanceWindowPropertiesArgs
                {
                    DayOfWeek = AzureNative.DesktopVirtualization.DayOfWeek.Friday,
                    Hour = 7,
                },
                new AzureNative.DesktopVirtualization.Inputs.MaintenanceWindowPropertiesArgs
                {
                    DayOfWeek = AzureNative.DesktopVirtualization.DayOfWeek.Saturday,
                    Hour = 8,
                },
            },
            Type = "Scheduled",
            UseSessionHostLocalTime = false,
        },
        Description = "des1",
        FriendlyName = "friendly",
        HostPoolName = "hostPool1",
        HostPoolType = "Pooled",
        LoadBalancerType = "BreadthFirst",
        Location = "centralus",
        MaxSessionLimit = 999999,
        PersonalDesktopAssignmentType = "Automatic",
        PreferredAppGroupType = "Desktop",
        RegistrationInfo = new AzureNative.DesktopVirtualization.Inputs.RegistrationInfoArgs
        {
            ExpirationTime = "2020-10-01T14:01:54.9571247Z",
            RegistrationTokenOperation = "Update",
        },
        ResourceGroupName = "resourceGroup1",
        SsoClientId = "client",
        SsoClientSecretKeyVaultPath = "https://keyvault/secret",
        SsoSecretType = "SharedKey",
        SsoadfsAuthority = "https://adfs",
        StartVMOnConnect = false,
        Tags = 
        {
            { "tag1", "value1" },
            { "tag2", "value2" },
        },
        VmTemplate = "{json:json}",
    });

});


```

```go
package main

import (
	desktopvirtualization "github.com/pulumi/pulumi-azure-native-sdk/desktopvirtualization"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := desktopvirtualization.NewHostPool(ctx, "hostPool", &desktopvirtualization.HostPoolArgs{
			AgentUpdate: desktopvirtualization.AgentUpdatePropertiesResponse{
				MaintenanceWindowTimeZone: pulumi.String("Alaskan Standard Time"),
				MaintenanceWindows: desktopvirtualization.MaintenanceWindowPropertiesArray{
					&desktopvirtualization.MaintenanceWindowPropertiesArgs{
						DayOfWeek: desktopvirtualization.DayOfWeekFriday,
						Hour:      pulumi.Int(7),
					},
					&desktopvirtualization.MaintenanceWindowPropertiesArgs{
						DayOfWeek: desktopvirtualization.DayOfWeekSaturday,
						Hour:      pulumi.Int(8),
					},
				},
				Type:                    pulumi.String("Scheduled"),
				UseSessionHostLocalTime: pulumi.Bool(false),
			},
			Description:                   pulumi.String("des1"),
			FriendlyName:                  pulumi.String("friendly"),
			HostPoolName:                  pulumi.String("hostPool1"),
			HostPoolType:                  pulumi.String("Pooled"),
			LoadBalancerType:              pulumi.String("BreadthFirst"),
			Location:                      pulumi.String("centralus"),
			MaxSessionLimit:               pulumi.Int(999999),
			PersonalDesktopAssignmentType: pulumi.String("Automatic"),
			PreferredAppGroupType:         pulumi.String("Desktop"),
			RegistrationInfo: &desktopvirtualization.RegistrationInfoArgs{
				ExpirationTime:             pulumi.String("2020-10-01T14:01:54.9571247Z"),
				RegistrationTokenOperation: pulumi.String("Update"),
			},
			ResourceGroupName:           pulumi.String("resourceGroup1"),
			SsoClientId:                 pulumi.String("client"),
			SsoClientSecretKeyVaultPath: pulumi.String("https://keyvault/secret"),
			SsoSecretType:               pulumi.String("SharedKey"),
			SsoadfsAuthority:            pulumi.String("https://adfs"),
			StartVMOnConnect:            pulumi.Bool(false),
			Tags: pulumi.StringMap{
				"tag1": pulumi.String("value1"),
				"tag2": pulumi.String("value2"),
			},
			VmTemplate: pulumi.String("{json:json}"),
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
import com.pulumi.azurenative.desktopvirtualization.HostPool;
import com.pulumi.azurenative.desktopvirtualization.HostPoolArgs;
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
        var hostPool = new HostPool("hostPool", HostPoolArgs.builder()        
            .agentUpdate(Map.ofEntries(
                Map.entry("maintenanceWindowTimeZone", "Alaskan Standard Time"),
                Map.entry("maintenanceWindows",                 
                    Map.ofEntries(
                        Map.entry("dayOfWeek", "Friday"),
                        Map.entry("hour", 7)
                    ),
                    Map.ofEntries(
                        Map.entry("dayOfWeek", "Saturday"),
                        Map.entry("hour", 8)
                    )),
                Map.entry("type", "Scheduled"),
                Map.entry("useSessionHostLocalTime", false)
            ))
            .description("des1")
            .friendlyName("friendly")
            .hostPoolName("hostPool1")
            .hostPoolType("Pooled")
            .loadBalancerType("BreadthFirst")
            .location("centralus")
            .maxSessionLimit(999999)
            .personalDesktopAssignmentType("Automatic")
            .preferredAppGroupType("Desktop")
            .registrationInfo(Map.ofEntries(
                Map.entry("expirationTime", "2020-10-01T14:01:54.9571247Z"),
                Map.entry("registrationTokenOperation", "Update")
            ))
            .resourceGroupName("resourceGroup1")
            .ssoClientId("client")
            .ssoClientSecretKeyVaultPath("https://keyvault/secret")
            .ssoSecretType("SharedKey")
            .ssoadfsAuthority("https://adfs")
            .startVMOnConnect(false)
            .tags(Map.ofEntries(
                Map.entry("tag1", "value1"),
                Map.entry("tag2", "value2")
            ))
            .vmTemplate("{json:json}")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const hostPool = new azure_native.desktopvirtualization.HostPool("hostPool", {
    agentUpdate: {
        maintenanceWindowTimeZone: "Alaskan Standard Time",
        maintenanceWindows: [
            {
                dayOfWeek: azure_native.desktopvirtualization.DayOfWeek.Friday,
                hour: 7,
            },
            {
                dayOfWeek: azure_native.desktopvirtualization.DayOfWeek.Saturday,
                hour: 8,
            },
        ],
        type: "Scheduled",
        useSessionHostLocalTime: false,
    },
    description: "des1",
    friendlyName: "friendly",
    hostPoolName: "hostPool1",
    hostPoolType: "Pooled",
    loadBalancerType: "BreadthFirst",
    location: "centralus",
    maxSessionLimit: 999999,
    personalDesktopAssignmentType: "Automatic",
    preferredAppGroupType: "Desktop",
    registrationInfo: {
        expirationTime: "2020-10-01T14:01:54.9571247Z",
        registrationTokenOperation: "Update",
    },
    resourceGroupName: "resourceGroup1",
    ssoClientId: "client",
    ssoClientSecretKeyVaultPath: "https://keyvault/secret",
    ssoSecretType: "SharedKey",
    ssoadfsAuthority: "https://adfs",
    startVMOnConnect: false,
    tags: {
        tag1: "value1",
        tag2: "value2",
    },
    vmTemplate: "{json:json}",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

host_pool = azure_native.desktopvirtualization.HostPool("hostPool",
    agent_update=azure_native.desktopvirtualization.AgentUpdatePropertiesResponseArgs(
        maintenance_window_time_zone="Alaskan Standard Time",
        maintenance_windows=[
            azure_native.desktopvirtualization.MaintenanceWindowPropertiesArgs(
                day_of_week=azure_native.desktopvirtualization.DayOfWeek.FRIDAY,
                hour=7,
            ),
            azure_native.desktopvirtualization.MaintenanceWindowPropertiesArgs(
                day_of_week=azure_native.desktopvirtualization.DayOfWeek.SATURDAY,
                hour=8,
            ),
        ],
        type="Scheduled",
        use_session_host_local_time=False,
    ),
    description="des1",
    friendly_name="friendly",
    host_pool_name="hostPool1",
    host_pool_type="Pooled",
    load_balancer_type="BreadthFirst",
    location="centralus",
    max_session_limit=999999,
    personal_desktop_assignment_type="Automatic",
    preferred_app_group_type="Desktop",
    registration_info=azure_native.desktopvirtualization.RegistrationInfoArgs(
        expiration_time="2020-10-01T14:01:54.9571247Z",
        registration_token_operation="Update",
    ),
    resource_group_name="resourceGroup1",
    sso_client_id="client",
    sso_client_secret_key_vault_path="https://keyvault/secret",
    sso_secret_type="SharedKey",
    ssoadfs_authority="https://adfs",
    start_vm_on_connect=False,
    tags={
        "tag1": "value1",
        "tag2": "value2",
    },
    vm_template="{json:json}")

```

```yaml
resources:
  hostPool:
    type: azure-native:desktopvirtualization:HostPool
    properties:
      agentUpdate:
        maintenanceWindowTimeZone: Alaskan Standard Time
        maintenanceWindows:
          - dayOfWeek: Friday
            hour: 7
          - dayOfWeek: Saturday
            hour: 8
        type: Scheduled
        useSessionHostLocalTime: false
      description: des1
      friendlyName: friendly
      hostPoolName: hostPool1
      hostPoolType: Pooled
      loadBalancerType: BreadthFirst
      location: centralus
      maxSessionLimit: 999999
      personalDesktopAssignmentType: Automatic
      preferredAppGroupType: Desktop
      registrationInfo:
        expirationTime: 2020-10-01T14:01:54.9571247Z
        registrationTokenOperation: Update
      resourceGroupName: resourceGroup1
      ssoClientId: client
      ssoClientSecretKeyVaultPath: https://keyvault/secret
      ssoSecretType: SharedKey
      ssoadfsAuthority: https://adfs
      startVMOnConnect: false
      tags:
        tag1: value1
        tag2: value2
      vmTemplate: '{json:json}'

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:desktopvirtualization:HostPool hostPool1 /subscriptions/daefabc0-95b4-48b3-b645-8a753a63c4fa/resourceGroups/resourceGroup1/providers/Microsoft.DesktopVirtualization/hostPools/hostPool1 
```
