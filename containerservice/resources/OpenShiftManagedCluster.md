OpenShift Managed cluster.
API Version: 2019-04-30.
Previous API Version: 2019-04-30. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create/Update OpenShift Managed Cluster
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var openShiftManagedCluster = new AzureNative.ContainerService.OpenShiftManagedCluster("openShiftManagedCluster", new()
    {
        AgentPoolProfiles = new[]
        {
            new AzureNative.ContainerService.Inputs.OpenShiftManagedClusterAgentPoolProfileArgs
            {
                Count = 2,
                Name = "infra",
                OsType = "Linux",
                Role = "infra",
                SubnetCidr = "10.0.0.0/24",
                VmSize = "Standard_D4s_v3",
            },
            new AzureNative.ContainerService.Inputs.OpenShiftManagedClusterAgentPoolProfileArgs
            {
                Count = 4,
                Name = "compute",
                OsType = "Linux",
                Role = "compute",
                SubnetCidr = "10.0.0.0/24",
                VmSize = "Standard_D4s_v3",
            },
        },
        AuthProfile = new AzureNative.ContainerService.Inputs.OpenShiftManagedClusterAuthProfileArgs
        {
            IdentityProviders = new[]
            {
                new AzureNative.ContainerService.Inputs.OpenShiftManagedClusterIdentityProviderArgs
                {
                    Name = "Azure AD",
                    Provider = 
                    {
                        { "clientId", "clientId" },
                        { "customerAdminGroupId", "customerAdminGroupId" },
                        { "kind", "AADIdentityProvider" },
                        { "secret", "secret" },
                        { "tenantId", "tenantId" },
                    },
                },
            },
        },
        Location = "location1",
        MasterPoolProfile = new AzureNative.ContainerService.Inputs.OpenShiftManagedClusterMasterPoolProfileArgs
        {
            Count = 3,
            Name = "master",
            OsType = "Linux",
            SubnetCidr = "10.0.0.0/24",
            VmSize = "Standard_D4s_v3",
        },
        NetworkProfile = new AzureNative.ContainerService.Inputs.NetworkProfileArgs
        {
            VnetCidr = "10.0.0.0/8",
        },
        OpenShiftVersion = "v3.11",
        ResourceGroupName = "rg1",
        ResourceName = "clustername1",
        RouterProfiles = new[]
        {
            new AzureNative.ContainerService.Inputs.OpenShiftRouterProfileArgs
            {
                Name = "default",
            },
        },
        Tags = 
        {
            { "archv2", "" },
            { "tier", "production" },
        },
    });

});


```

```go
package main

import (
	containerservice "github.com/pulumi/pulumi-azure-native-sdk/containerservice"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := containerservice.NewOpenShiftManagedCluster(ctx, "openShiftManagedCluster", &containerservice.OpenShiftManagedClusterArgs{
			AgentPoolProfiles: []containerservice.OpenShiftManagedClusterAgentPoolProfileArgs{
				{
					Count:      pulumi.Int(2),
					Name:       pulumi.String("infra"),
					OsType:     pulumi.String("Linux"),
					Role:       pulumi.String("infra"),
					SubnetCidr: pulumi.String("10.0.0.0/24"),
					VmSize:     pulumi.String("Standard_D4s_v3"),
				},
				{
					Count:      pulumi.Int(4),
					Name:       pulumi.String("compute"),
					OsType:     pulumi.String("Linux"),
					Role:       pulumi.String("compute"),
					SubnetCidr: pulumi.String("10.0.0.0/24"),
					VmSize:     pulumi.String("Standard_D4s_v3"),
				},
			},
			AuthProfile: containerservice.OpenShiftManagedClusterAuthProfileResponse{
				IdentityProviders: []containerservice.OpenShiftManagedClusterIdentityProviderArgs{
					{
						Name: pulumi.String("Azure AD"),
						Provider: {
							ClientId:             pulumi.String("clientId"),
							CustomerAdminGroupId: pulumi.String("customerAdminGroupId"),
							Kind:                 pulumi.String("AADIdentityProvider"),
							Secret:               pulumi.String("secret"),
							TenantId:             pulumi.String("tenantId"),
						},
					},
				},
			},
			Location: pulumi.String("location1"),
			MasterPoolProfile: &containerservice.OpenShiftManagedClusterMasterPoolProfileArgs{
				Count:      pulumi.Int(3),
				Name:       pulumi.String("master"),
				OsType:     pulumi.String("Linux"),
				SubnetCidr: pulumi.String("10.0.0.0/24"),
				VmSize:     pulumi.String("Standard_D4s_v3"),
			},
			NetworkProfile: &containerservice.NetworkProfileArgs{
				VnetCidr: pulumi.String("10.0.0.0/8"),
			},
			OpenShiftVersion:  pulumi.String("v3.11"),
			ResourceGroupName: pulumi.String("rg1"),
			ResourceName:      pulumi.String("clustername1"),
			RouterProfiles: []containerservice.OpenShiftRouterProfileArgs{
				{
					Name: pulumi.String("default"),
				},
			},
			Tags: pulumi.StringMap{
				"archv2": pulumi.String(""),
				"tier":   pulumi.String("production"),
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
import com.pulumi.azurenative.containerservice.OpenShiftManagedCluster;
import com.pulumi.azurenative.containerservice.OpenShiftManagedClusterArgs;
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
        var openShiftManagedCluster = new OpenShiftManagedCluster("openShiftManagedCluster", OpenShiftManagedClusterArgs.builder()        
            .agentPoolProfiles(            
                Map.ofEntries(
                    Map.entry("count", 2),
                    Map.entry("name", "infra"),
                    Map.entry("osType", "Linux"),
                    Map.entry("role", "infra"),
                    Map.entry("subnetCidr", "10.0.0.0/24"),
                    Map.entry("vmSize", "Standard_D4s_v3")
                ),
                Map.ofEntries(
                    Map.entry("count", 4),
                    Map.entry("name", "compute"),
                    Map.entry("osType", "Linux"),
                    Map.entry("role", "compute"),
                    Map.entry("subnetCidr", "10.0.0.0/24"),
                    Map.entry("vmSize", "Standard_D4s_v3")
                ))
            .authProfile(Map.of("identityProviders", Map.ofEntries(
                Map.entry("name", "Azure AD"),
                Map.entry("provider", Map.ofEntries(
                    Map.entry("clientId", "clientId"),
                    Map.entry("customerAdminGroupId", "customerAdminGroupId"),
                    Map.entry("kind", "AADIdentityProvider"),
                    Map.entry("secret", "secret"),
                    Map.entry("tenantId", "tenantId")
                ))
            )))
            .location("location1")
            .masterPoolProfile(Map.ofEntries(
                Map.entry("count", 3),
                Map.entry("name", "master"),
                Map.entry("osType", "Linux"),
                Map.entry("subnetCidr", "10.0.0.0/24"),
                Map.entry("vmSize", "Standard_D4s_v3")
            ))
            .networkProfile(Map.of("vnetCidr", "10.0.0.0/8"))
            .openShiftVersion("v3.11")
            .resourceGroupName("rg1")
            .resourceName("clustername1")
            .routerProfiles(Map.of("name", "default"))
            .tags(Map.ofEntries(
                Map.entry("archv2", ""),
                Map.entry("tier", "production")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const openShiftManagedCluster = new azure_native.containerservice.OpenShiftManagedCluster("openShiftManagedCluster", {
    agentPoolProfiles: [
        {
            count: 2,
            name: "infra",
            osType: "Linux",
            role: "infra",
            subnetCidr: "10.0.0.0/24",
            vmSize: "Standard_D4s_v3",
        },
        {
            count: 4,
            name: "compute",
            osType: "Linux",
            role: "compute",
            subnetCidr: "10.0.0.0/24",
            vmSize: "Standard_D4s_v3",
        },
    ],
    authProfile: {
        identityProviders: [{
            name: "Azure AD",
            provider: {
                clientId: "clientId",
                customerAdminGroupId: "customerAdminGroupId",
                kind: "AADIdentityProvider",
                secret: "secret",
                tenantId: "tenantId",
            },
        }],
    },
    location: "location1",
    masterPoolProfile: {
        count: 3,
        name: "master",
        osType: "Linux",
        subnetCidr: "10.0.0.0/24",
        vmSize: "Standard_D4s_v3",
    },
    networkProfile: {
        vnetCidr: "10.0.0.0/8",
    },
    openShiftVersion: "v3.11",
    resourceGroupName: "rg1",
    resourceName: "clustername1",
    routerProfiles: [{
        name: "default",
    }],
    tags: {
        archv2: "",
        tier: "production",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

open_shift_managed_cluster = azure_native.containerservice.OpenShiftManagedCluster("openShiftManagedCluster",
    agent_pool_profiles=[
        azure_native.containerservice.OpenShiftManagedClusterAgentPoolProfileArgs(
            count=2,
            name="infra",
            os_type="Linux",
            role="infra",
            subnet_cidr="10.0.0.0/24",
            vm_size="Standard_D4s_v3",
        ),
        azure_native.containerservice.OpenShiftManagedClusterAgentPoolProfileArgs(
            count=4,
            name="compute",
            os_type="Linux",
            role="compute",
            subnet_cidr="10.0.0.0/24",
            vm_size="Standard_D4s_v3",
        ),
    ],
    auth_profile=azure_native.containerservice.OpenShiftManagedClusterAuthProfileResponseArgs(
        identity_providers=[{
            "name": "Azure AD",
            "provider": azure_native.containerservice.OpenShiftManagedClusterAADIdentityProviderResponseArgs(
                client_id="clientId",
                customer_admin_group_id="customerAdminGroupId",
                kind="AADIdentityProvider",
                secret="secret",
                tenant_id="tenantId",
            ),
        }],
    ),
    location="location1",
    master_pool_profile=azure_native.containerservice.OpenShiftManagedClusterMasterPoolProfileArgs(
        count=3,
        name="master",
        os_type="Linux",
        subnet_cidr="10.0.0.0/24",
        vm_size="Standard_D4s_v3",
    ),
    network_profile=azure_native.containerservice.NetworkProfileArgs(
        vnet_cidr="10.0.0.0/8",
    ),
    open_shift_version="v3.11",
    resource_group_name="rg1",
    resource_name_="clustername1",
    router_profiles=[azure_native.containerservice.OpenShiftRouterProfileArgs(
        name="default",
    )],
    tags={
        "archv2": "",
        "tier": "production",
    })

```

```yaml
resources:
  openShiftManagedCluster:
    type: azure-native:containerservice:OpenShiftManagedCluster
    properties:
      agentPoolProfiles:
        - count: 2
          name: infra
          osType: Linux
          role: infra
          subnetCidr: 10.0.0.0/24
          vmSize: Standard_D4s_v3
        - count: 4
          name: compute
          osType: Linux
          role: compute
          subnetCidr: 10.0.0.0/24
          vmSize: Standard_D4s_v3
      authProfile:
        identityProviders:
          - name: Azure AD
            provider:
              clientId: clientId
              customerAdminGroupId: customerAdminGroupId
              kind: AADIdentityProvider
              secret: secret
              tenantId: tenantId
      location: location1
      masterPoolProfile:
        count: 3
        name: master
        osType: Linux
        subnetCidr: 10.0.0.0/24
        vmSize: Standard_D4s_v3
      networkProfile:
        vnetCidr: 10.0.0.0/8
      openShiftVersion: v3.11
      resourceGroupName: rg1
      resourceName: clustername1
      routerProfiles:
        - name: default
      tags:
        archv2:
        tier: production

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:containerservice:OpenShiftManagedCluster clustername1 /subscriptions/subid1/resourcegroups/rg1/providers/Microsoft.ContainerService/openShiftManagedClusters/clustername1 
```
