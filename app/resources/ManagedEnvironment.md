An environment for hosting container apps
API Version: 2022-10-01.
Previous API Version: 2022-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create environments
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managedEnvironment = new AzureNative.App.ManagedEnvironment("managedEnvironment", new()
    {
        AppLogsConfiguration = new AzureNative.App.Inputs.AppLogsConfigurationArgs
        {
            LogAnalyticsConfiguration = new AzureNative.App.Inputs.LogAnalyticsConfigurationArgs
            {
                CustomerId = "string",
                SharedKey = "string",
            },
        },
        CustomDomainConfiguration = new AzureNative.App.Inputs.CustomDomainConfigurationArgs
        {
            CertificatePassword = "private key password",
            CertificateValue = "Y2VydA==",
            DnsSuffix = "www.my-name.com",
        },
        DaprAIConnectionString = "InstrumentationKey=00000000-0000-0000-0000-000000000000;IngestionEndpoint=https://northcentralus-0.in.applicationinsights.azure.com/",
        EnvironmentName = "testcontainerenv",
        Kind = "serverless",
        Location = "East US",
        ResourceGroupName = "examplerg",
        Sku = new AzureNative.App.Inputs.EnvironmentSkuPropertiesArgs
        {
            Name = "Premium",
        },
        VnetConfiguration = new AzureNative.App.Inputs.VnetConfigurationArgs
        {
            OutboundSettings = new AzureNative.App.Inputs.ManagedEnvironmentOutboundSettingsArgs
            {
                OutBoundType = "UserDefinedRouting",
                VirtualNetworkApplianceIp = "192.168.1.20",
            },
        },
        WorkloadProfiles = new[]
        {
            new AzureNative.App.Inputs.WorkloadProfileArgs
            {
                MaximumCount = 12,
                MinimumCount = 3,
                WorkloadProfileType = "GeneralPurpose",
            },
            new AzureNative.App.Inputs.WorkloadProfileArgs
            {
                MaximumCount = 6,
                MinimumCount = 3,
                WorkloadProfileType = "MemoryOptimized",
            },
            new AzureNative.App.Inputs.WorkloadProfileArgs
            {
                MaximumCount = 6,
                MinimumCount = 3,
                WorkloadProfileType = "ComputeOptimized",
            },
        },
        ZoneRedundant = true,
    });

});


```

```go
package main

import (
	app "github.com/pulumi/pulumi-azure-native-sdk/app"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := app.NewManagedEnvironment(ctx, "managedEnvironment", &app.ManagedEnvironmentArgs{
			AppLogsConfiguration: app.AppLogsConfigurationResponse{
				LogAnalyticsConfiguration: &app.LogAnalyticsConfigurationArgs{
					CustomerId: pulumi.String("string"),
					SharedKey:  pulumi.String("string"),
				},
			},
			CustomDomainConfiguration: &app.CustomDomainConfigurationArgs{
				CertificatePassword: pulumi.String("private key password"),
				CertificateValue:    pulumi.String("Y2VydA=="),
				DnsSuffix:           pulumi.String("www.my-name.com"),
			},
			DaprAIConnectionString: pulumi.String("InstrumentationKey=00000000-0000-0000-0000-000000000000;IngestionEndpoint=https://northcentralus-0.in.applicationinsights.azure.com/"),
			EnvironmentName:        pulumi.String("testcontainerenv"),
			Kind:                   pulumi.String("serverless"),
			Location:               pulumi.String("East US"),
			ResourceGroupName:      pulumi.String("examplerg"),
			Sku: &app.EnvironmentSkuPropertiesArgs{
				Name: pulumi.String("Premium"),
			},
			VnetConfiguration: app.VnetConfigurationResponse{
				OutboundSettings: &app.ManagedEnvironmentOutboundSettingsArgs{
					OutBoundType:              pulumi.String("UserDefinedRouting"),
					VirtualNetworkApplianceIp: pulumi.String("192.168.1.20"),
				},
			},
			WorkloadProfiles: []app.WorkloadProfileArgs{
				{
					MaximumCount:        pulumi.Int(12),
					MinimumCount:        pulumi.Int(3),
					WorkloadProfileType: pulumi.String("GeneralPurpose"),
				},
				{
					MaximumCount:        pulumi.Int(6),
					MinimumCount:        pulumi.Int(3),
					WorkloadProfileType: pulumi.String("MemoryOptimized"),
				},
				{
					MaximumCount:        pulumi.Int(6),
					MinimumCount:        pulumi.Int(3),
					WorkloadProfileType: pulumi.String("ComputeOptimized"),
				},
			},
			ZoneRedundant: pulumi.Bool(true),
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
import com.pulumi.azurenative.app.ManagedEnvironment;
import com.pulumi.azurenative.app.ManagedEnvironmentArgs;
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
        var managedEnvironment = new ManagedEnvironment("managedEnvironment", ManagedEnvironmentArgs.builder()        
            .appLogsConfiguration(Map.of("logAnalyticsConfiguration", Map.ofEntries(
                Map.entry("customerId", "string"),
                Map.entry("sharedKey", "string")
            )))
            .customDomainConfiguration(Map.ofEntries(
                Map.entry("certificatePassword", "private key password"),
                Map.entry("certificateValue", "Y2VydA=="),
                Map.entry("dnsSuffix", "www.my-name.com")
            ))
            .daprAIConnectionString("InstrumentationKey=00000000-0000-0000-0000-000000000000;IngestionEndpoint=https://northcentralus-0.in.applicationinsights.azure.com/")
            .environmentName("testcontainerenv")
            .kind("serverless")
            .location("East US")
            .resourceGroupName("examplerg")
            .sku(Map.of("name", "Premium"))
            .vnetConfiguration(Map.of("outboundSettings", Map.ofEntries(
                Map.entry("outBoundType", "UserDefinedRouting"),
                Map.entry("virtualNetworkApplianceIp", "192.168.1.20")
            )))
            .workloadProfiles(            
                Map.ofEntries(
                    Map.entry("maximumCount", 12),
                    Map.entry("minimumCount", 3),
                    Map.entry("workloadProfileType", "GeneralPurpose")
                ),
                Map.ofEntries(
                    Map.entry("maximumCount", 6),
                    Map.entry("minimumCount", 3),
                    Map.entry("workloadProfileType", "MemoryOptimized")
                ),
                Map.ofEntries(
                    Map.entry("maximumCount", 6),
                    Map.entry("minimumCount", 3),
                    Map.entry("workloadProfileType", "ComputeOptimized")
                ))
            .zoneRedundant(true)
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managedEnvironment = new azure_native.app.ManagedEnvironment("managedEnvironment", {
    appLogsConfiguration: {
        logAnalyticsConfiguration: {
            customerId: "string",
            sharedKey: "string",
        },
    },
    customDomainConfiguration: {
        certificatePassword: "private key password",
        certificateValue: "Y2VydA==",
        dnsSuffix: "www.my-name.com",
    },
    daprAIConnectionString: "InstrumentationKey=00000000-0000-0000-0000-000000000000;IngestionEndpoint=https://northcentralus-0.in.applicationinsights.azure.com/",
    environmentName: "testcontainerenv",
    kind: "serverless",
    location: "East US",
    resourceGroupName: "examplerg",
    sku: {
        name: "Premium",
    },
    vnetConfiguration: {
        outboundSettings: {
            outBoundType: "UserDefinedRouting",
            virtualNetworkApplianceIp: "192.168.1.20",
        },
    },
    workloadProfiles: [
        {
            maximumCount: 12,
            minimumCount: 3,
            workloadProfileType: "GeneralPurpose",
        },
        {
            maximumCount: 6,
            minimumCount: 3,
            workloadProfileType: "MemoryOptimized",
        },
        {
            maximumCount: 6,
            minimumCount: 3,
            workloadProfileType: "ComputeOptimized",
        },
    ],
    zoneRedundant: true,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

managed_environment = azure_native.app.ManagedEnvironment("managedEnvironment",
    app_logs_configuration=azure_native.app.AppLogsConfigurationResponseArgs(
        log_analytics_configuration=azure_native.app.LogAnalyticsConfigurationArgs(
            customer_id="string",
            shared_key="string",
        ),
    ),
    custom_domain_configuration=azure_native.app.CustomDomainConfigurationArgs(
        certificate_password="private key password",
        certificate_value="Y2VydA==",
        dns_suffix="www.my-name.com",
    ),
    dapr_ai_connection_string="InstrumentationKey=00000000-0000-0000-0000-000000000000;IngestionEndpoint=https://northcentralus-0.in.applicationinsights.azure.com/",
    environment_name="testcontainerenv",
    kind="serverless",
    location="East US",
    resource_group_name="examplerg",
    sku=azure_native.app.EnvironmentSkuPropertiesArgs(
        name="Premium",
    ),
    vnet_configuration=azure_native.app.VnetConfigurationResponseArgs(
        outbound_settings=azure_native.app.ManagedEnvironmentOutboundSettingsArgs(
            out_bound_type="UserDefinedRouting",
            virtual_network_appliance_ip="192.168.1.20",
        ),
    ),
    workload_profiles=[
        azure_native.app.WorkloadProfileArgs(
            maximum_count=12,
            minimum_count=3,
            workload_profile_type="GeneralPurpose",
        ),
        azure_native.app.WorkloadProfileArgs(
            maximum_count=6,
            minimum_count=3,
            workload_profile_type="MemoryOptimized",
        ),
        azure_native.app.WorkloadProfileArgs(
            maximum_count=6,
            minimum_count=3,
            workload_profile_type="ComputeOptimized",
        ),
    ],
    zone_redundant=True)

```

```yaml
resources:
  managedEnvironment:
    type: azure-native:app:ManagedEnvironment
    properties:
      appLogsConfiguration:
        logAnalyticsConfiguration:
          customerId: string
          sharedKey: string
      customDomainConfiguration:
        certificatePassword: private key password
        certificateValue: Y2VydA==
        dnsSuffix: www.my-name.com
      daprAIConnectionString: InstrumentationKey=00000000-0000-0000-0000-000000000000;IngestionEndpoint=https://northcentralus-0.in.applicationinsights.azure.com/
      environmentName: testcontainerenv
      kind: serverless
      location: East US
      resourceGroupName: examplerg
      sku:
        name: Premium
      vnetConfiguration:
        outboundSettings:
          outBoundType: UserDefinedRouting
          virtualNetworkApplianceIp: 192.168.1.20
      workloadProfiles:
        - maximumCount: 12
          minimumCount: 3
          workloadProfileType: GeneralPurpose
        - maximumCount: 6
          minimumCount: 3
          workloadProfileType: MemoryOptimized
        - maximumCount: 6
          minimumCount: 3
          workloadProfileType: ComputeOptimized
      zoneRedundant: true

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:app:ManagedEnvironment testcontainerenv /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/examplerg/providers/Microsoft.App/managedEnvironments/testcontainerenv 
```
