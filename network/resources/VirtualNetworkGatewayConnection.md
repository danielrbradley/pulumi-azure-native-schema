A common class for general resource information.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateVirtualNetworkGatewayConnection_S2S
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualNetworkGatewayConnection = new AzureNative.Network.VirtualNetworkGatewayConnection("virtualNetworkGatewayConnection", new()
    {
        ConnectionMode = "Default",
        ConnectionProtocol = "IKEv2",
        ConnectionType = "IPsec",
        DpdTimeoutSeconds = 30,
        EgressNatRules = new[]
        {
            new AzureNative.Network.Inputs.SubResourceArgs
            {
                Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/vpngw/natRules/natRule2",
            },
        },
        EnableBgp = false,
        GatewayCustomBgpIpAddresses = new[]
        {
            new AzureNative.Network.Inputs.GatewayCustomBgpIpAddressIpConfigurationArgs
            {
                CustomBgpIpAddress = "169.254.21.1",
                IpConfigurationId = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/vpngw/ipConfigurations/default",
            },
            new AzureNative.Network.Inputs.GatewayCustomBgpIpAddressIpConfigurationArgs
            {
                CustomBgpIpAddress = "169.254.21.3",
                IpConfigurationId = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/vpngw/ipConfigurations/ActiveActive",
            },
        },
        IngressNatRules = new[]
        {
            new AzureNative.Network.Inputs.SubResourceArgs
            {
                Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/vpngw/natRules/natRule1",
            },
        },
        IpsecPolicies = new[] {},
        LocalNetworkGateway2 = new AzureNative.Network.Inputs.LocalNetworkGatewayArgs
        {
            GatewayIpAddress = "x.x.x.x",
            Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/localNetworkGateways/localgw",
            LocalNetworkAddressSpace = new AzureNative.Network.Inputs.AddressSpaceArgs
            {
                AddressPrefixes = new[]
                {
                    "10.1.0.0/16",
                },
            },
            Location = "centralus",
            Tags = null,
        },
        Location = "centralus",
        ResourceGroupName = "rg1",
        RoutingWeight = 0,
        SharedKey = "Abc123",
        TrafficSelectorPolicies = new[] {},
        UsePolicyBasedTrafficSelectors = false,
        VirtualNetworkGateway1 = new AzureNative.Network.Inputs.VirtualNetworkGatewayArgs
        {
            ActiveActive = false,
            BgpSettings = new AzureNative.Network.Inputs.BgpSettingsArgs
            {
                Asn = 65514,
                BgpPeeringAddress = "10.0.1.30",
                PeerWeight = 0,
            },
            EnableBgp = false,
            GatewayType = "Vpn",
            Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/vpngw",
            IpConfigurations = new[]
            {
                new AzureNative.Network.Inputs.VirtualNetworkGatewayIPConfigurationArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/vpngw/ipConfigurations/gwipconfig1",
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
            Sku = new AzureNative.Network.Inputs.VirtualNetworkGatewaySkuArgs
            {
                Name = "VpnGw1",
                Tier = "VpnGw1",
            },
            Tags = null,
            VpnType = "RouteBased",
        },
        VirtualNetworkGatewayConnectionName = "connS2S",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.network.VirtualNetworkGatewayConnection;
import com.pulumi.azurenative.network.VirtualNetworkGatewayConnectionArgs;
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
        var virtualNetworkGatewayConnection = new VirtualNetworkGatewayConnection("virtualNetworkGatewayConnection", VirtualNetworkGatewayConnectionArgs.builder()        
            .connectionMode("Default")
            .connectionProtocol("IKEv2")
            .connectionType("IPsec")
            .dpdTimeoutSeconds(30)
            .egressNatRules(Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/vpngw/natRules/natRule2"))
            .enableBgp(false)
            .gatewayCustomBgpIpAddresses(            
                Map.ofEntries(
                    Map.entry("customBgpIpAddress", "169.254.21.1"),
                    Map.entry("ipConfigurationId", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/vpngw/ipConfigurations/default")
                ),
                Map.ofEntries(
                    Map.entry("customBgpIpAddress", "169.254.21.3"),
                    Map.entry("ipConfigurationId", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/vpngw/ipConfigurations/ActiveActive")
                ))
            .ingressNatRules(Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/vpngw/natRules/natRule1"))
            .ipsecPolicies()
            .localNetworkGateway2(Map.ofEntries(
                Map.entry("gatewayIpAddress", "x.x.x.x"),
                Map.entry("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/localNetworkGateways/localgw"),
                Map.entry("localNetworkAddressSpace", Map.of("addressPrefixes", "10.1.0.0/16")),
                Map.entry("location", "centralus"),
                Map.entry("tags", )
            ))
            .location("centralus")
            .resourceGroupName("rg1")
            .routingWeight(0)
            .sharedKey("Abc123")
            .trafficSelectorPolicies()
            .usePolicyBasedTrafficSelectors(false)
            .virtualNetworkGateway1(Map.ofEntries(
                Map.entry("activeActive", false),
                Map.entry("bgpSettings", Map.ofEntries(
                    Map.entry("asn", 65514),
                    Map.entry("bgpPeeringAddress", "10.0.1.30"),
                    Map.entry("peerWeight", 0)
                )),
                Map.entry("enableBgp", false),
                Map.entry("gatewayType", "Vpn"),
                Map.entry("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/vpngw"),
                Map.entry("ipConfigurations", Map.ofEntries(
                    Map.entry("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/vpngw/ipConfigurations/gwipconfig1"),
                    Map.entry("name", "gwipconfig1"),
                    Map.entry("privateIPAllocationMethod", "Dynamic"),
                    Map.entry("publicIPAddress", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/gwpip")),
                    Map.entry("subnet", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet1/subnets/GatewaySubnet"))
                )),
                Map.entry("location", "centralus"),
                Map.entry("sku", Map.ofEntries(
                    Map.entry("name", "VpnGw1"),
                    Map.entry("tier", "VpnGw1")
                )),
                Map.entry("tags", ),
                Map.entry("vpnType", "RouteBased")
            ))
            .virtualNetworkGatewayConnectionName("connS2S")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualNetworkGatewayConnection = new azure_native.network.VirtualNetworkGatewayConnection("virtualNetworkGatewayConnection", {
    connectionMode: "Default",
    connectionProtocol: "IKEv2",
    connectionType: "IPsec",
    dpdTimeoutSeconds: 30,
    egressNatRules: [{
        id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/vpngw/natRules/natRule2",
    }],
    enableBgp: false,
    gatewayCustomBgpIpAddresses: [
        {
            customBgpIpAddress: "169.254.21.1",
            ipConfigurationId: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/vpngw/ipConfigurations/default",
        },
        {
            customBgpIpAddress: "169.254.21.3",
            ipConfigurationId: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/vpngw/ipConfigurations/ActiveActive",
        },
    ],
    ingressNatRules: [{
        id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/vpngw/natRules/natRule1",
    }],
    ipsecPolicies: [],
    localNetworkGateway2: {
        gatewayIpAddress: "x.x.x.x",
        id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/localNetworkGateways/localgw",
        localNetworkAddressSpace: {
            addressPrefixes: ["10.1.0.0/16"],
        },
        location: "centralus",
        tags: {},
    },
    location: "centralus",
    resourceGroupName: "rg1",
    routingWeight: 0,
    sharedKey: "Abc123",
    trafficSelectorPolicies: [],
    usePolicyBasedTrafficSelectors: false,
    virtualNetworkGateway1: {
        activeActive: false,
        bgpSettings: {
            asn: 65514,
            bgpPeeringAddress: "10.0.1.30",
            peerWeight: 0,
        },
        enableBgp: false,
        gatewayType: "Vpn",
        id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/vpngw",
        ipConfigurations: [{
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/vpngw/ipConfigurations/gwipconfig1",
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
        sku: {
            name: "VpnGw1",
            tier: "VpnGw1",
        },
        tags: {},
        vpnType: "RouteBased",
    },
    virtualNetworkGatewayConnectionName: "connS2S",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_network_gateway_connection = azure_native.network.VirtualNetworkGatewayConnection("virtualNetworkGatewayConnection",
    connection_mode="Default",
    connection_protocol="IKEv2",
    connection_type="IPsec",
    dpd_timeout_seconds=30,
    egress_nat_rules=[azure_native.network.SubResourceArgs(
        id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/vpngw/natRules/natRule2",
    )],
    enable_bgp=False,
    gateway_custom_bgp_ip_addresses=[
        azure_native.network.GatewayCustomBgpIpAddressIpConfigurationArgs(
            custom_bgp_ip_address="169.254.21.1",
            ip_configuration_id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/vpngw/ipConfigurations/default",
        ),
        azure_native.network.GatewayCustomBgpIpAddressIpConfigurationArgs(
            custom_bgp_ip_address="169.254.21.3",
            ip_configuration_id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/vpngw/ipConfigurations/ActiveActive",
        ),
    ],
    ingress_nat_rules=[azure_native.network.SubResourceArgs(
        id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/vpngw/natRules/natRule1",
    )],
    ipsec_policies=[],
    local_network_gateway2=azure_native.network.LocalNetworkGatewayResponseArgs(
        gateway_ip_address="x.x.x.x",
        id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/localNetworkGateways/localgw",
        local_network_address_space=azure_native.network.AddressSpaceArgs(
            address_prefixes=["10.1.0.0/16"],
        ),
        location="centralus",
        tags={},
    ),
    location="centralus",
    resource_group_name="rg1",
    routing_weight=0,
    shared_key="Abc123",
    traffic_selector_policies=[],
    use_policy_based_traffic_selectors=False,
    virtual_network_gateway1=azure_native.network.VirtualNetworkGatewayResponseArgs(
        active_active=False,
        bgp_settings=azure_native.network.BgpSettingsArgs(
            asn=65514,
            bgp_peering_address="10.0.1.30",
            peer_weight=0,
        ),
        enable_bgp=False,
        gateway_type="Vpn",
        id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/vpngw",
        ip_configurations=[{
            "id": "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/vpngw/ipConfigurations/gwipconfig1",
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
        sku=azure_native.network.VirtualNetworkGatewaySkuArgs(
            name="VpnGw1",
            tier="VpnGw1",
        ),
        tags={},
        vpn_type="RouteBased",
    ),
    virtual_network_gateway_connection_name="connS2S")

```

```yaml
resources:
  virtualNetworkGatewayConnection:
    type: azure-native:network:VirtualNetworkGatewayConnection
    properties:
      connectionMode: Default
      connectionProtocol: IKEv2
      connectionType: IPsec
      dpdTimeoutSeconds: 30
      egressNatRules:
        - id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/vpngw/natRules/natRule2
      enableBgp: false
      gatewayCustomBgpIpAddresses:
        - customBgpIpAddress: 169.254.21.1
          ipConfigurationId: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/vpngw/ipConfigurations/default
        - customBgpIpAddress: 169.254.21.3
          ipConfigurationId: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/vpngw/ipConfigurations/ActiveActive
      ingressNatRules:
        - id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/vpngw/natRules/natRule1
      ipsecPolicies: []
      localNetworkGateway2:
        gatewayIpAddress: x.x.x.x
        id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/localNetworkGateways/localgw
        localNetworkAddressSpace:
          addressPrefixes:
            - 10.1.0.0/16
        location: centralus
        tags: {}
      location: centralus
      resourceGroupName: rg1
      routingWeight: 0
      sharedKey: Abc123
      trafficSelectorPolicies: []
      usePolicyBasedTrafficSelectors: false
      virtualNetworkGateway1:
        activeActive: false
        bgpSettings:
          asn: 65514
          bgpPeeringAddress: 10.0.1.30
          peerWeight: 0
        enableBgp: false
        gatewayType: Vpn
        id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/vpngw
        ipConfigurations:
          - id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/vpngw/ipConfigurations/gwipconfig1
            name: gwipconfig1
            privateIPAllocationMethod: Dynamic
            publicIPAddress:
              id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/gwpip
            subnet:
              id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet1/subnets/GatewaySubnet
        location: centralus
        sku:
          name: VpnGw1
          tier: VpnGw1
        tags: {}
        vpnType: RouteBased
      virtualNetworkGatewayConnectionName: connS2S

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:VirtualNetworkGatewayConnection connS2S /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/connections/connS2S 
```
