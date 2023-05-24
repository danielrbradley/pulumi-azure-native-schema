OpenShiftCluster represents an Azure Red Hat OpenShift cluster.
API Version: 2022-09-04.
Previous API Version: 2020-04-30. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Creates or updates a OpenShift cluster with the specified subscription, resource group and resource name.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var openShiftCluster = new AzureNative.RedHatOpenShift.OpenShiftCluster("openShiftCluster", new()
    {
        ApiserverProfile = new AzureNative.RedHatOpenShift.Inputs.APIServerProfileArgs
        {
            Visibility = "Public",
        },
        ClusterProfile = new AzureNative.RedHatOpenShift.Inputs.ClusterProfileArgs
        {
            Domain = "cluster.location.aroapp.io",
            FipsValidatedModules = "Enabled",
            PullSecret = "{\"auths\":{\"registry.connect.redhat.com\":{\"auth\":\"\"},\"registry.redhat.io\":{\"auth\":\"\"}}}",
            ResourceGroupId = "/subscriptions/subscriptionId/resourceGroups/clusterResourceGroup",
        },
        ConsoleProfile = null,
        IngressProfiles = new[]
        {
            new AzureNative.RedHatOpenShift.Inputs.IngressProfileArgs
            {
                Name = "default",
                Visibility = "Public",
            },
        },
        Location = "location",
        MasterProfile = new AzureNative.RedHatOpenShift.Inputs.MasterProfileArgs
        {
            EncryptionAtHost = "Enabled",
            SubnetId = "/subscriptions/subscriptionId/resourceGroups/vnetResourceGroup/providers/Microsoft.Network/virtualNetworks/vnet/subnets/master",
            VmSize = "Standard_D8s_v3",
        },
        NetworkProfile = new AzureNative.RedHatOpenShift.Inputs.NetworkProfileArgs
        {
            PodCidr = "10.128.0.0/14",
            ServiceCidr = "172.30.0.0/16",
        },
        ResourceGroupName = "resourceGroup",
        ResourceName = "resourceName",
        ServicePrincipalProfile = new AzureNative.RedHatOpenShift.Inputs.ServicePrincipalProfileArgs
        {
            ClientId = "clientId",
            ClientSecret = "clientSecret",
        },
        Tags = 
        {
            { "key", "value" },
        },
        WorkerProfiles = new[]
        {
            new AzureNative.RedHatOpenShift.Inputs.WorkerProfileArgs
            {
                Count = 3,
                DiskSizeGB = 128,
                Name = "worker",
                SubnetId = "/subscriptions/subscriptionId/resourceGroups/vnetResourceGroup/providers/Microsoft.Network/virtualNetworks/vnet/subnets/worker",
                VmSize = "Standard_D2s_v3",
            },
        },
    });

});


```

```go
package main

import (
	redhatopenshift "github.com/pulumi/pulumi-azure-native-sdk/redhatopenshift"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := redhatopenshift.NewOpenShiftCluster(ctx, "openShiftCluster", &redhatopenshift.OpenShiftClusterArgs{
			ApiserverProfile: &redhatopenshift.APIServerProfileArgs{
				Visibility: pulumi.String("Public"),
			},
			ClusterProfile: &redhatopenshift.ClusterProfileArgs{
				Domain:               pulumi.String("cluster.location.aroapp.io"),
				FipsValidatedModules: pulumi.String("Enabled"),
				PullSecret:           pulumi.String("{\"auths\":{\"registry.connect.redhat.com\":{\"auth\":\"\"},\"registry.redhat.io\":{\"auth\":\"\"}}}"),
				ResourceGroupId:      pulumi.String("/subscriptions/subscriptionId/resourceGroups/clusterResourceGroup"),
			},
			ConsoleProfile: nil,
			IngressProfiles: []redhatopenshift.IngressProfileArgs{
				{
					Name:       pulumi.String("default"),
					Visibility: pulumi.String("Public"),
				},
			},
			Location: pulumi.String("location"),
			MasterProfile: &redhatopenshift.MasterProfileArgs{
				EncryptionAtHost: pulumi.String("Enabled"),
				SubnetId:         pulumi.String("/subscriptions/subscriptionId/resourceGroups/vnetResourceGroup/providers/Microsoft.Network/virtualNetworks/vnet/subnets/master"),
				VmSize:           pulumi.String("Standard_D8s_v3"),
			},
			NetworkProfile: &redhatopenshift.NetworkProfileArgs{
				PodCidr:     pulumi.String("10.128.0.0/14"),
				ServiceCidr: pulumi.String("172.30.0.0/16"),
			},
			ResourceGroupName: pulumi.String("resourceGroup"),
			ResourceName:      pulumi.String("resourceName"),
			ServicePrincipalProfile: &redhatopenshift.ServicePrincipalProfileArgs{
				ClientId:     pulumi.String("clientId"),
				ClientSecret: pulumi.String("clientSecret"),
			},
			Tags: pulumi.StringMap{
				"key": pulumi.String("value"),
			},
			WorkerProfiles: []redhatopenshift.WorkerProfileArgs{
				{
					Count:      pulumi.Int(3),
					DiskSizeGB: pulumi.Int(128),
					Name:       pulumi.String("worker"),
					SubnetId:   pulumi.String("/subscriptions/subscriptionId/resourceGroups/vnetResourceGroup/providers/Microsoft.Network/virtualNetworks/vnet/subnets/worker"),
					VmSize:     pulumi.String("Standard_D2s_v3"),
				},
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
import com.pulumi.azurenative.redhatopenshift.OpenShiftCluster;
import com.pulumi.azurenative.redhatopenshift.OpenShiftClusterArgs;
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
        var openShiftCluster = new OpenShiftCluster("openShiftCluster", OpenShiftClusterArgs.builder()        
            .apiserverProfile(Map.of("visibility", "Public"))
            .clusterProfile(Map.ofEntries(
                Map.entry("domain", "cluster.location.aroapp.io"),
                Map.entry("fipsValidatedModules", "Enabled"),
                Map.entry("pullSecret", "{\"auths\":{\"registry.connect.redhat.com\":{\"auth\":\"\"},\"registry.redhat.io\":{\"auth\":\"\"}}}"),
                Map.entry("resourceGroupId", "/subscriptions/subscriptionId/resourceGroups/clusterResourceGroup")
            ))
            .consoleProfile()
            .ingressProfiles(Map.ofEntries(
                Map.entry("name", "default"),
                Map.entry("visibility", "Public")
            ))
            .location("location")
            .masterProfile(Map.ofEntries(
                Map.entry("encryptionAtHost", "Enabled"),
                Map.entry("subnetId", "/subscriptions/subscriptionId/resourceGroups/vnetResourceGroup/providers/Microsoft.Network/virtualNetworks/vnet/subnets/master"),
                Map.entry("vmSize", "Standard_D8s_v3")
            ))
            .networkProfile(Map.ofEntries(
                Map.entry("podCidr", "10.128.0.0/14"),
                Map.entry("serviceCidr", "172.30.0.0/16")
            ))
            .resourceGroupName("resourceGroup")
            .resourceName("resourceName")
            .servicePrincipalProfile(Map.ofEntries(
                Map.entry("clientId", "clientId"),
                Map.entry("clientSecret", "clientSecret")
            ))
            .tags(Map.of("key", "value"))
            .workerProfiles(Map.ofEntries(
                Map.entry("count", 3),
                Map.entry("diskSizeGB", 128),
                Map.entry("name", "worker"),
                Map.entry("subnetId", "/subscriptions/subscriptionId/resourceGroups/vnetResourceGroup/providers/Microsoft.Network/virtualNetworks/vnet/subnets/worker"),
                Map.entry("vmSize", "Standard_D2s_v3")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const openShiftCluster = new azure_native.redhatopenshift.OpenShiftCluster("openShiftCluster", {
    apiserverProfile: {
        visibility: "Public",
    },
    clusterProfile: {
        domain: "cluster.location.aroapp.io",
        fipsValidatedModules: "Enabled",
        pullSecret: "{\"auths\":{\"registry.connect.redhat.com\":{\"auth\":\"\"},\"registry.redhat.io\":{\"auth\":\"\"}}}",
        resourceGroupId: "/subscriptions/subscriptionId/resourceGroups/clusterResourceGroup",
    },
    consoleProfile: {},
    ingressProfiles: [{
        name: "default",
        visibility: "Public",
    }],
    location: "location",
    masterProfile: {
        encryptionAtHost: "Enabled",
        subnetId: "/subscriptions/subscriptionId/resourceGroups/vnetResourceGroup/providers/Microsoft.Network/virtualNetworks/vnet/subnets/master",
        vmSize: "Standard_D8s_v3",
    },
    networkProfile: {
        podCidr: "10.128.0.0/14",
        serviceCidr: "172.30.0.0/16",
    },
    resourceGroupName: "resourceGroup",
    resourceName: "resourceName",
    servicePrincipalProfile: {
        clientId: "clientId",
        clientSecret: "clientSecret",
    },
    tags: {
        key: "value",
    },
    workerProfiles: [{
        count: 3,
        diskSizeGB: 128,
        name: "worker",
        subnetId: "/subscriptions/subscriptionId/resourceGroups/vnetResourceGroup/providers/Microsoft.Network/virtualNetworks/vnet/subnets/worker",
        vmSize: "Standard_D2s_v3",
    }],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

open_shift_cluster = azure_native.redhatopenshift.OpenShiftCluster("openShiftCluster",
    apiserver_profile=azure_native.redhatopenshift.APIServerProfileArgs(
        visibility="Public",
    ),
    cluster_profile=azure_native.redhatopenshift.ClusterProfileArgs(
        domain="cluster.location.aroapp.io",
        fips_validated_modules="Enabled",
        pull_secret="{\"auths\":{\"registry.connect.redhat.com\":{\"auth\":\"\"},\"registry.redhat.io\":{\"auth\":\"\"}}}",
        resource_group_id="/subscriptions/subscriptionId/resourceGroups/clusterResourceGroup",
    ),
    console_profile=azure_native.redhatopenshift.ConsoleProfileArgs(),
    ingress_profiles=[azure_native.redhatopenshift.IngressProfileArgs(
        name="default",
        visibility="Public",
    )],
    location="location",
    master_profile=azure_native.redhatopenshift.MasterProfileArgs(
        encryption_at_host="Enabled",
        subnet_id="/subscriptions/subscriptionId/resourceGroups/vnetResourceGroup/providers/Microsoft.Network/virtualNetworks/vnet/subnets/master",
        vm_size="Standard_D8s_v3",
    ),
    network_profile=azure_native.redhatopenshift.NetworkProfileArgs(
        pod_cidr="10.128.0.0/14",
        service_cidr="172.30.0.0/16",
    ),
    resource_group_name="resourceGroup",
    resource_name_="resourceName",
    service_principal_profile=azure_native.redhatopenshift.ServicePrincipalProfileArgs(
        client_id="clientId",
        client_secret="clientSecret",
    ),
    tags={
        "key": "value",
    },
    worker_profiles=[azure_native.redhatopenshift.WorkerProfileArgs(
        count=3,
        disk_size_gb=128,
        name="worker",
        subnet_id="/subscriptions/subscriptionId/resourceGroups/vnetResourceGroup/providers/Microsoft.Network/virtualNetworks/vnet/subnets/worker",
        vm_size="Standard_D2s_v3",
    )])

```

```yaml
resources:
  openShiftCluster:
    type: azure-native:redhatopenshift:OpenShiftCluster
    properties:
      apiserverProfile:
        visibility: Public
      clusterProfile:
        domain: cluster.location.aroapp.io
        fipsValidatedModules: Enabled
        pullSecret: '{"auths":{"registry.connect.redhat.com":{"auth":""},"registry.redhat.io":{"auth":""}}}'
        resourceGroupId: /subscriptions/subscriptionId/resourceGroups/clusterResourceGroup
      consoleProfile: {}
      ingressProfiles:
        - name: default
          visibility: Public
      location: location
      masterProfile:
        encryptionAtHost: Enabled
        subnetId: /subscriptions/subscriptionId/resourceGroups/vnetResourceGroup/providers/Microsoft.Network/virtualNetworks/vnet/subnets/master
        vmSize: Standard_D8s_v3
      networkProfile:
        podCidr: 10.128.0.0/14
        serviceCidr: 172.30.0.0/16
      resourceGroupName: resourceGroup
      resourceName: resourceName
      servicePrincipalProfile:
        clientId: clientId
        clientSecret: clientSecret
      tags:
        key: value
      workerProfiles:
        - count: 3
          diskSizeGB: 128
          name: worker
          subnetId: /subscriptions/subscriptionId/resourceGroups/vnetResourceGroup/providers/Microsoft.Network/virtualNetworks/vnet/subnets/worker
          vmSize: Standard_D2s_v3

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:redhatopenshift:OpenShiftCluster resourceName /subscriptions/subscriptionId/resourceGroups/resourceGroup/providers/Microsoft.RedHatOpenShift/OpenShiftClusters/resourceName 
```
