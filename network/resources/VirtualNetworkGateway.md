A common class for general resource information.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### UpdateVirtualNetworkGateway
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualNetworkGateway = new AzureNative.Network.VirtualNetworkGateway("virtualNetworkGateway", new()
    {
        ActiveActive = false,
        AllowRemoteVnetTraffic = false,
        AllowVirtualWanTraffic = false,
        BgpSettings = new AzureNative.Network.Inputs.BgpSettingsArgs
        {
            Asn = 65515,
            BgpPeeringAddress = "10.0.1.30",
            PeerWeight = 0,
        },
        CustomRoutes = new AzureNative.Network.Inputs.AddressSpaceArgs
        {
            AddressPrefixes = new[]
            {
                "101.168.0.6/32",
            },
        },
        DisableIPSecReplayProtection = false,
        EnableBgp = false,
        EnableBgpRouteTranslationForNat = false,
        EnableDnsForwarding = true,
        GatewayType = "Vpn",
        IpConfigurations = new[]
        {
            new AzureNative.Network.Inputs.VirtualNetworkGatewayIPConfigurationArgs
            {
                Name = "gwipconfig1",
                PrivateIPAllocationMethod = "Dynamic",
                PublicIPAddress = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/gwpip",
                },
                Subnet = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet1/subnets/GatewaySubnet",
                },
            },
        },
        Location = "centralus",
        NatRules = new[]
        {
            new AzureNative.Network.Inputs.VirtualNetworkGatewayNatRuleArgs
            {
                ExternalMappings = new[]
                {
                    new AzureNative.Network.Inputs.VpnNatRuleMappingArgs
                    {
                        AddressSpace = "50.0.0.0/24",
                    },
                },
                Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/vpngw/natRules/natRule1",
                InternalMappings = new[]
                {
                    new AzureNative.Network.Inputs.VpnNatRuleMappingArgs
                    {
                        AddressSpace = "10.10.0.0/24",
                    },
                },
                IpConfigurationId = "",
                Mode = "EgressSnat",
                Name = "natRule1",
                Type = "Static",
            },
            new AzureNative.Network.Inputs.VirtualNetworkGatewayNatRuleArgs
            {
                ExternalMappings = new[]
                {
                    new AzureNative.Network.Inputs.VpnNatRuleMappingArgs
                    {
                        AddressSpace = "30.0.0.0/24",
                    },
                },
                Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/vpngw/natRules/natRule2",
                InternalMappings = new[]
                {
                    new AzureNative.Network.Inputs.VpnNatRuleMappingArgs
                    {
                        AddressSpace = "20.10.0.0/24",
                    },
                },
                IpConfigurationId = "",
                Mode = "IngressSnat",
                Name = "natRule2",
                Type = "Static",
            },
        },
        ResourceGroupName = "rg1",
        Sku = new AzureNative.Network.Inputs.VirtualNetworkGatewaySkuArgs
        {
            Name = "VpnGw1",
            Tier = "VpnGw1",
        },
        VirtualNetworkGatewayName = "vpngw",
        VpnClientConfiguration = new AzureNative.Network.Inputs.VpnClientConfigurationArgs
        {
            RadiusServers = new[]
            {
                new AzureNative.Network.Inputs.RadiusServerArgs
                {
                    RadiusServerAddress = "10.2.0.0",
                    RadiusServerScore = 20,
                    RadiusServerSecret = "radiusServerSecret",
                },
            },
            VpnClientProtocols = new[]
            {
                "OpenVPN",
            },
            VpnClientRevokedCertificates = new[] {},
            VpnClientRootCertificates = new[] {},
        },
        VpnType = "RouteBased",
    });

});


```

```go
package main

import (
	network "github.com/pulumi/pulumi-azure-native-sdk/network"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := network.NewVirtualNetworkGateway(ctx, "virtualNetworkGateway", &network.VirtualNetworkGatewayArgs{
			ActiveActive:           pulumi.Bool(false),
			AllowRemoteVnetTraffic: pulumi.Bool(false),
			AllowVirtualWanTraffic: pulumi.Bool(false),
			BgpSettings: &network.BgpSettingsArgs{
				Asn:               pulumi.Float64(65515),
				BgpPeeringAddress: pulumi.String("10.0.1.30"),
				PeerWeight:        pulumi.Int(0),
			},
			CustomRoutes: &network.AddressSpaceArgs{
				AddressPrefixes: pulumi.StringArray{
					pulumi.String("101.168.0.6/32"),
				},
			},
			DisableIPSecReplayProtection:    pulumi.Bool(false),
			EnableBgp:                       pulumi.Bool(false),
			EnableBgpRouteTranslationForNat: pulumi.Bool(false),
			EnableDnsForwarding:             pulumi.Bool(true),
			GatewayType:                     pulumi.String("Vpn"),
			IpConfigurations: []network.VirtualNetworkGatewayIPConfigurationArgs{
				{
					Name:                      pulumi.String("gwipconfig1"),
					PrivateIPAllocationMethod: pulumi.String("Dynamic"),
					PublicIPAddress: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/gwpip"),
					},
					Subnet: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet1/subnets/GatewaySubnet"),
					},
				},
			},
			Location: pulumi.String("centralus"),
			NatRules: []network.VirtualNetworkGatewayNatRuleTypeArgs{
				{
					ExternalMappings: network.VpnNatRuleMappingArray{
						{
							AddressSpace: pulumi.String("50.0.0.0/24"),
						},
					},
					Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/vpngw/natRules/natRule1"),
					InternalMappings: network.VpnNatRuleMappingArray{
						{
							AddressSpace: pulumi.String("10.10.0.0/24"),
						},
					},
					IpConfigurationId: pulumi.String(""),
					Mode:              pulumi.String("EgressSnat"),
					Name:              pulumi.String("natRule1"),
					Type:              pulumi.String("Static"),
				},
				{
					ExternalMappings: network.VpnNatRuleMappingArray{
						{
							AddressSpace: pulumi.String("30.0.0.0/24"),
						},
					},
					Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/vpngw/natRules/natRule2"),
					InternalMappings: network.VpnNatRuleMappingArray{
						{
							AddressSpace: pulumi.String("20.10.0.0/24"),
						},
					},
					IpConfigurationId: pulumi.String(""),
					Mode:              pulumi.String("IngressSnat"),
					Name:              pulumi.String("natRule2"),
					Type:              pulumi.String("Static"),
				},
			},
			ResourceGroupName: pulumi.String("rg1"),
			Sku: &network.VirtualNetworkGatewaySkuArgs{
				Name: pulumi.String("VpnGw1"),
				Tier: pulumi.String("VpnGw1"),
			},
			VirtualNetworkGatewayName: pulumi.String("vpngw"),
			VpnClientConfiguration: network.VpnClientConfigurationResponse{
				RadiusServers: network.RadiusServerArray{
					&network.RadiusServerArgs{
						RadiusServerAddress: pulumi.String("10.2.0.0"),
						RadiusServerScore:   pulumi.Float64(20),
						RadiusServerSecret:  pulumi.String("radiusServerSecret"),
					},
				},
				VpnClientProtocols: pulumi.StringArray{
					pulumi.String("OpenVPN"),
				},
				VpnClientRevokedCertificates: network.VpnClientRevokedCertificateArray{},
				VpnClientRootCertificates:    network.VpnClientRootCertificateArray{},
			},
			VpnType: pulumi.String("RouteBased"),
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
import com.pulumi.azurenative.network.VirtualNetworkGateway;
import com.pulumi.azurenative.network.VirtualNetworkGatewayArgs;
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
        var virtualNetworkGateway = new VirtualNetworkGateway("virtualNetworkGateway", VirtualNetworkGatewayArgs.builder()        
            .activeActive(false)
            .allowRemoteVnetTraffic(false)
            .allowVirtualWanTraffic(false)
            .bgpSettings(Map.ofEntries(
                Map.entry("asn", 65515),
                Map.entry("bgpPeeringAddress", "10.0.1.30"),
                Map.entry("peerWeight", 0)
            ))
            .customRoutes(Map.of("addressPrefixes", "101.168.0.6/32"))
            .disableIPSecReplayProtection(false)
            .enableBgp(false)
            .enableBgpRouteTranslationForNat(false)
            .enableDnsForwarding(true)
            .gatewayType("Vpn")
            .ipConfigurations(Map.ofEntries(
                Map.entry("name", "gwipconfig1"),
                Map.entry("privateIPAllocationMethod", "Dynamic"),
                Map.entry("publicIPAddress", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/gwpip")),
                Map.entry("subnet", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet1/subnets/GatewaySubnet"))
            ))
            .location("centralus")
            .natRules(            
                Map.ofEntries(
                    Map.entry("externalMappings", Map.of("addressSpace", "50.0.0.0/24")),
                    Map.entry("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/vpngw/natRules/natRule1"),
                    Map.entry("internalMappings", Map.of("addressSpace", "10.10.0.0/24")),
                    Map.entry("ipConfigurationId", ""),
                    Map.entry("mode", "EgressSnat"),
                    Map.entry("name", "natRule1"),
                    Map.entry("type", "Static")
                ),
                Map.ofEntries(
                    Map.entry("externalMappings", Map.of("addressSpace", "30.0.0.0/24")),
                    Map.entry("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/vpngw/natRules/natRule2"),
                    Map.entry("internalMappings", Map.of("addressSpace", "20.10.0.0/24")),
                    Map.entry("ipConfigurationId", ""),
                    Map.entry("mode", "IngressSnat"),
                    Map.entry("name", "natRule2"),
                    Map.entry("type", "Static")
                ))
            .resourceGroupName("rg1")
            .sku(Map.ofEntries(
                Map.entry("name", "VpnGw1"),
                Map.entry("tier", "VpnGw1")
            ))
            .virtualNetworkGatewayName("vpngw")
            .vpnClientConfiguration(Map.ofEntries(
                Map.entry("radiusServers", Map.ofEntries(
                    Map.entry("radiusServerAddress", "10.2.0.0"),
                    Map.entry("radiusServerScore", 20),
                    Map.entry("radiusServerSecret", "radiusServerSecret")
                )),
                Map.entry("vpnClientProtocols", "OpenVPN"),
                Map.entry("vpnClientRevokedCertificates", ),
                Map.entry("vpnClientRootCertificates", )
            ))
            .vpnType("RouteBased")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualNetworkGateway = new azure_native.network.VirtualNetworkGateway("virtualNetworkGateway", {
    activeActive: false,
    allowRemoteVnetTraffic: false,
    allowVirtualWanTraffic: false,
    bgpSettings: {
        asn: 65515,
        bgpPeeringAddress: "10.0.1.30",
        peerWeight: 0,
    },
    customRoutes: {
        addressPrefixes: ["101.168.0.6/32"],
    },
    disableIPSecReplayProtection: false,
    enableBgp: false,
    enableBgpRouteTranslationForNat: false,
    enableDnsForwarding: true,
    gatewayType: "Vpn",
    ipConfigurations: [{
        name: "gwipconfig1",
        privateIPAllocationMethod: "Dynamic",
        publicIPAddress: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/gwpip",
        },
        subnet: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet1/subnets/GatewaySubnet",
        },
    }],
    location: "centralus",
    natRules: [
        {
            externalMappings: [{
                addressSpace: "50.0.0.0/24",
            }],
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/vpngw/natRules/natRule1",
            internalMappings: [{
                addressSpace: "10.10.0.0/24",
            }],
            ipConfigurationId: "",
            mode: "EgressSnat",
            name: "natRule1",
            type: "Static",
        },
        {
            externalMappings: [{
                addressSpace: "30.0.0.0/24",
            }],
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/vpngw/natRules/natRule2",
            internalMappings: [{
                addressSpace: "20.10.0.0/24",
            }],
            ipConfigurationId: "",
            mode: "IngressSnat",
            name: "natRule2",
            type: "Static",
        },
    ],
    resourceGroupName: "rg1",
    sku: {
        name: "VpnGw1",
        tier: "VpnGw1",
    },
    virtualNetworkGatewayName: "vpngw",
    vpnClientConfiguration: {
        radiusServers: [{
            radiusServerAddress: "10.2.0.0",
            radiusServerScore: 20,
            radiusServerSecret: "radiusServerSecret",
        }],
        vpnClientProtocols: ["OpenVPN"],
        vpnClientRevokedCertificates: [],
        vpnClientRootCertificates: [],
    },
    vpnType: "RouteBased",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_network_gateway = azure_native.network.VirtualNetworkGateway("virtualNetworkGateway",
    active_active=False,
    allow_remote_vnet_traffic=False,
    allow_virtual_wan_traffic=False,
    bgp_settings=azure_native.network.BgpSettingsArgs(
        asn=65515,
        bgp_peering_address="10.0.1.30",
        peer_weight=0,
    ),
    custom_routes=azure_native.network.AddressSpaceArgs(
        address_prefixes=["101.168.0.6/32"],
    ),
    disable_ip_sec_replay_protection=False,
    enable_bgp=False,
    enable_bgp_route_translation_for_nat=False,
    enable_dns_forwarding=True,
    gateway_type="Vpn",
    ip_configurations=[{
        "name": "gwipconfig1",
        "privateIPAllocationMethod": "Dynamic",
        "publicIPAddress": azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/gwpip",
        ),
        "subnet": azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet1/subnets/GatewaySubnet",
        ),
    }],
    location="centralus",
    nat_rules=[
        {
            "externalMappings": [azure_native.network.VpnNatRuleMappingArgs(
                address_space="50.0.0.0/24",
            )],
            "id": "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/vpngw/natRules/natRule1",
            "internalMappings": [azure_native.network.VpnNatRuleMappingArgs(
                address_space="10.10.0.0/24",
            )],
            "ipConfigurationId": "",
            "mode": "EgressSnat",
            "name": "natRule1",
            "type": "Static",
        },
        {
            "externalMappings": [azure_native.network.VpnNatRuleMappingArgs(
                address_space="30.0.0.0/24",
            )],
            "id": "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/vpngw/natRules/natRule2",
            "internalMappings": [azure_native.network.VpnNatRuleMappingArgs(
                address_space="20.10.0.0/24",
            )],
            "ipConfigurationId": "",
            "mode": "IngressSnat",
            "name": "natRule2",
            "type": "Static",
        },
    ],
    resource_group_name="rg1",
    sku=azure_native.network.VirtualNetworkGatewaySkuArgs(
        name="VpnGw1",
        tier="VpnGw1",
    ),
    virtual_network_gateway_name="vpngw",
    vpn_client_configuration=azure_native.network.VpnClientConfigurationResponseArgs(
        radius_servers=[azure_native.network.RadiusServerArgs(
            radius_server_address="10.2.0.0",
            radius_server_score=20,
            radius_server_secret="radiusServerSecret",
        )],
        vpn_client_protocols=["OpenVPN"],
        vpn_client_revoked_certificates=[],
        vpn_client_root_certificates=[],
    ),
    vpn_type="RouteBased")

```

```yaml
resources:
  virtualNetworkGateway:
    type: azure-native:network:VirtualNetworkGateway
    properties:
      activeActive: false
      allowRemoteVnetTraffic: false
      allowVirtualWanTraffic: false
      bgpSettings:
        asn: 65515
        bgpPeeringAddress: 10.0.1.30
        peerWeight: 0
      customRoutes:
        addressPrefixes:
          - 101.168.0.6/32
      disableIPSecReplayProtection: false
      enableBgp: false
      enableBgpRouteTranslationForNat: false
      enableDnsForwarding: true
      gatewayType: Vpn
      ipConfigurations:
        - name: gwipconfig1
          privateIPAllocationMethod: Dynamic
          publicIPAddress:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/gwpip
          subnet:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet1/subnets/GatewaySubnet
      location: centralus
      natRules:
        - externalMappings:
            - addressSpace: 50.0.0.0/24
          id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/vpngw/natRules/natRule1
          internalMappings:
            - addressSpace: 10.10.0.0/24
          ipConfigurationId:
          mode: EgressSnat
          name: natRule1
          type: Static
        - externalMappings:
            - addressSpace: 30.0.0.0/24
          id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/vpngw/natRules/natRule2
          internalMappings:
            - addressSpace: 20.10.0.0/24
          ipConfigurationId:
          mode: IngressSnat
          name: natRule2
          type: Static
      resourceGroupName: rg1
      sku:
        name: VpnGw1
        tier: VpnGw1
      virtualNetworkGatewayName: vpngw
      vpnClientConfiguration:
        radiusServers:
          - radiusServerAddress: 10.2.0.0
            radiusServerScore: 20
            radiusServerSecret: radiusServerSecret
        vpnClientProtocols:
          - OpenVPN
        vpnClientRevokedCertificates: []
        vpnClientRootCertificates: []
      vpnType: RouteBased

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:VirtualNetworkGateway vpngw /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/vpngw 
```
