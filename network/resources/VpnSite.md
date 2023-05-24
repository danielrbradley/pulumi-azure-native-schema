VpnSite Resource.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### VpnSiteCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var vpnSite = new AzureNative.Network.VpnSite("vpnSite", new()
    {
        AddressSpace = new AzureNative.Network.Inputs.AddressSpaceArgs
        {
            AddressPrefixes = new[]
            {
                "10.0.0.0/16",
            },
        },
        IsSecuritySite = false,
        Location = "West US",
        O365Policy = new AzureNative.Network.Inputs.O365PolicyPropertiesArgs
        {
            BreakOutCategories = new AzureNative.Network.Inputs.O365BreakOutCategoryPoliciesArgs
            {
                Allow = true,
                Default = false,
                Optimize = true,
            },
        },
        ResourceGroupName = "rg1",
        Tags = 
        {
            { "key1", "value1" },
        },
        VirtualWan = new AzureNative.Network.Inputs.SubResourceArgs
        {
            Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualWANs/wan1",
        },
        VpnSiteLinks = new[]
        {
            new AzureNative.Network.Inputs.VpnSiteLinkArgs
            {
                BgpProperties = new AzureNative.Network.Inputs.VpnLinkBgpSettingsArgs
                {
                    Asn = 1234,
                    BgpPeeringAddress = "192.168.0.0",
                },
                Fqdn = "link1.vpnsite1.contoso.com",
                IpAddress = "50.50.50.56",
                LinkProperties = new AzureNative.Network.Inputs.VpnLinkProviderPropertiesArgs
                {
                    LinkProviderName = "vendor1",
                    LinkSpeedInMbps = 0,
                },
                Name = "vpnSiteLink1",
            },
        },
        VpnSiteName = "vpnSite1",
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
		_, err := network.NewVpnSite(ctx, "vpnSite", &network.VpnSiteArgs{
			AddressSpace: &network.AddressSpaceArgs{
				AddressPrefixes: pulumi.StringArray{
					pulumi.String("10.0.0.0/16"),
				},
			},
			IsSecuritySite: pulumi.Bool(false),
			Location:       pulumi.String("West US"),
			O365Policy: network.O365PolicyPropertiesResponse{
				BreakOutCategories: &network.O365BreakOutCategoryPoliciesArgs{
					Allow:    pulumi.Bool(true),
					Default:  pulumi.Bool(false),
					Optimize: pulumi.Bool(true),
				},
			},
			ResourceGroupName: pulumi.String("rg1"),
			Tags: pulumi.StringMap{
				"key1": pulumi.String("value1"),
			},
			VirtualWan: &network.SubResourceArgs{
				Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualWANs/wan1"),
			},
			VpnSiteLinks: []network.VpnSiteLinkArgs{
				{
					BgpProperties: {
						Asn:               pulumi.Float64(1234),
						BgpPeeringAddress: pulumi.String("192.168.0.0"),
					},
					Fqdn:      pulumi.String("link1.vpnsite1.contoso.com"),
					IpAddress: pulumi.String("50.50.50.56"),
					LinkProperties: {
						LinkProviderName: pulumi.String("vendor1"),
						LinkSpeedInMbps:  pulumi.Int(0),
					},
					Name: pulumi.String("vpnSiteLink1"),
				},
			},
			VpnSiteName: pulumi.String("vpnSite1"),
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
import com.pulumi.azurenative.network.VpnSite;
import com.pulumi.azurenative.network.VpnSiteArgs;
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
        var vpnSite = new VpnSite("vpnSite", VpnSiteArgs.builder()        
            .addressSpace(Map.of("addressPrefixes", "10.0.0.0/16"))
            .isSecuritySite(false)
            .location("West US")
            .o365Policy(Map.of("breakOutCategories", Map.ofEntries(
                Map.entry("allow", true),
                Map.entry("default", false),
                Map.entry("optimize", true)
            )))
            .resourceGroupName("rg1")
            .tags(Map.of("key1", "value1"))
            .virtualWan(Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualWANs/wan1"))
            .vpnSiteLinks(Map.ofEntries(
                Map.entry("bgpProperties", Map.ofEntries(
                    Map.entry("asn", 1234),
                    Map.entry("bgpPeeringAddress", "192.168.0.0")
                )),
                Map.entry("fqdn", "link1.vpnsite1.contoso.com"),
                Map.entry("ipAddress", "50.50.50.56"),
                Map.entry("linkProperties", Map.ofEntries(
                    Map.entry("linkProviderName", "vendor1"),
                    Map.entry("linkSpeedInMbps", 0)
                )),
                Map.entry("name", "vpnSiteLink1")
            ))
            .vpnSiteName("vpnSite1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const vpnSite = new azure_native.network.VpnSite("vpnSite", {
    addressSpace: {
        addressPrefixes: ["10.0.0.0/16"],
    },
    isSecuritySite: false,
    location: "West US",
    o365Policy: {
        breakOutCategories: {
            allow: true,
            "default": false,
            optimize: true,
        },
    },
    resourceGroupName: "rg1",
    tags: {
        key1: "value1",
    },
    virtualWan: {
        id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualWANs/wan1",
    },
    vpnSiteLinks: [{
        bgpProperties: {
            asn: 1234,
            bgpPeeringAddress: "192.168.0.0",
        },
        fqdn: "link1.vpnsite1.contoso.com",
        ipAddress: "50.50.50.56",
        linkProperties: {
            linkProviderName: "vendor1",
            linkSpeedInMbps: 0,
        },
        name: "vpnSiteLink1",
    }],
    vpnSiteName: "vpnSite1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

vpn_site = azure_native.network.VpnSite("vpnSite",
    address_space=azure_native.network.AddressSpaceArgs(
        address_prefixes=["10.0.0.0/16"],
    ),
    is_security_site=False,
    location="West US",
    o365_policy=azure_native.network.O365PolicyPropertiesResponseArgs(
        break_out_categories=azure_native.network.O365BreakOutCategoryPoliciesArgs(
            allow=True,
            default=False,
            optimize=True,
        ),
    ),
    resource_group_name="rg1",
    tags={
        "key1": "value1",
    },
    virtual_wan=azure_native.network.SubResourceArgs(
        id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualWANs/wan1",
    ),
    vpn_site_links=[{
        "bgpProperties": azure_native.network.VpnLinkBgpSettingsArgs(
            asn=1234,
            bgp_peering_address="192.168.0.0",
        ),
        "fqdn": "link1.vpnsite1.contoso.com",
        "ipAddress": "50.50.50.56",
        "linkProperties": azure_native.network.VpnLinkProviderPropertiesArgs(
            link_provider_name="vendor1",
            link_speed_in_mbps=0,
        ),
        "name": "vpnSiteLink1",
    }],
    vpn_site_name="vpnSite1")

```

```yaml
resources:
  vpnSite:
    type: azure-native:network:VpnSite
    properties:
      addressSpace:
        addressPrefixes:
          - 10.0.0.0/16
      isSecuritySite: false
      location: West US
      o365Policy:
        breakOutCategories:
          allow: true
          default: false
          optimize: true
      resourceGroupName: rg1
      tags:
        key1: value1
      virtualWan:
        id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualWANs/wan1
      vpnSiteLinks:
        - bgpProperties:
            asn: 1234
            bgpPeeringAddress: 192.168.0.0
          fqdn: link1.vpnsite1.contoso.com
          ipAddress: 50.50.50.56
          linkProperties:
            linkProviderName: vendor1
            linkSpeedInMbps: 0
          name: vpnSiteLink1
      vpnSiteName: vpnSite1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:VpnSite vpnSite1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/vpnSites/vpnSite1 
```
