Peering is a logical representation of a set of connections to the Microsoft Cloud Edge at a location.
API Version: 2022-10-01.
Previous API Version: 2021-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a direct peering
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var peering = new AzureNative.Peering.Peering("peering", new()
    {
        Direct = new AzureNative.Peering.Inputs.PeeringPropertiesDirectArgs
        {
            Connections = new[]
            {
                new AzureNative.Peering.Inputs.DirectConnectionArgs
                {
                    BandwidthInMbps = 10000,
                    BgpSession = new AzureNative.Peering.Inputs.BgpSessionArgs
                    {
                        MaxPrefixesAdvertisedV4 = 1000,
                        MaxPrefixesAdvertisedV6 = 100,
                        Md5AuthenticationKey = "test-md5-auth-key",
                        SessionPrefixV4 = "192.168.0.0/31",
                        SessionPrefixV6 = "fd00::0/127",
                    },
                    ConnectionIdentifier = "5F4CB5C7-6B43-4444-9338-9ABC72606C16",
                    PeeringDBFacilityId = 99999,
                    SessionAddressProvider = "Peer",
                    UseForPeeringService = false,
                },
                new AzureNative.Peering.Inputs.DirectConnectionArgs
                {
                    BandwidthInMbps = 10000,
                    ConnectionIdentifier = "8AB00818-D533-4504-A25A-03A17F61201C",
                    PeeringDBFacilityId = 99999,
                    SessionAddressProvider = "Microsoft",
                    UseForPeeringService = true,
                },
            },
            DirectPeeringType = "Edge",
            PeerAsn = new AzureNative.Peering.Inputs.SubResourceArgs
            {
                Id = "/subscriptions/subId/providers/Microsoft.Peering/peerAsns/myAsn1",
            },
        },
        Kind = "Direct",
        Location = "eastus",
        PeeringLocation = "peeringLocation0",
        PeeringName = "peeringName",
        ResourceGroupName = "rgName",
        Sku = new AzureNative.Peering.Inputs.PeeringSkuArgs
        {
            Name = "Basic_Direct_Free",
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.peering.Peering;
import com.pulumi.azurenative.peering.PeeringArgs;
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
        var peering = new Peering("peering", PeeringArgs.builder()        
            .direct(Map.ofEntries(
                Map.entry("connections",                 
                    Map.ofEntries(
                        Map.entry("bandwidthInMbps", 10000),
                        Map.entry("bgpSession", Map.ofEntries(
                            Map.entry("maxPrefixesAdvertisedV4", 1000),
                            Map.entry("maxPrefixesAdvertisedV6", 100),
                            Map.entry("md5AuthenticationKey", "test-md5-auth-key"),
                            Map.entry("sessionPrefixV4", "192.168.0.0/31"),
                            Map.entry("sessionPrefixV6", "fd00::0/127")
                        )),
                        Map.entry("connectionIdentifier", "5F4CB5C7-6B43-4444-9338-9ABC72606C16"),
                        Map.entry("peeringDBFacilityId", 99999),
                        Map.entry("sessionAddressProvider", "Peer"),
                        Map.entry("useForPeeringService", false)
                    ),
                    Map.ofEntries(
                        Map.entry("bandwidthInMbps", 10000),
                        Map.entry("connectionIdentifier", "8AB00818-D533-4504-A25A-03A17F61201C"),
                        Map.entry("peeringDBFacilityId", 99999),
                        Map.entry("sessionAddressProvider", "Microsoft"),
                        Map.entry("useForPeeringService", true)
                    )),
                Map.entry("directPeeringType", "Edge"),
                Map.entry("peerAsn", Map.of("id", "/subscriptions/subId/providers/Microsoft.Peering/peerAsns/myAsn1"))
            ))
            .kind("Direct")
            .location("eastus")
            .peeringLocation("peeringLocation0")
            .peeringName("peeringName")
            .resourceGroupName("rgName")
            .sku(Map.of("name", "Basic_Direct_Free"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const peering = new azure_native.peering.Peering("peering", {
    direct: {
        connections: [
            {
                bandwidthInMbps: 10000,
                bgpSession: {
                    maxPrefixesAdvertisedV4: 1000,
                    maxPrefixesAdvertisedV6: 100,
                    md5AuthenticationKey: "test-md5-auth-key",
                    sessionPrefixV4: "192.168.0.0/31",
                    sessionPrefixV6: "fd00::0/127",
                },
                connectionIdentifier: "5F4CB5C7-6B43-4444-9338-9ABC72606C16",
                peeringDBFacilityId: 99999,
                sessionAddressProvider: "Peer",
                useForPeeringService: false,
            },
            {
                bandwidthInMbps: 10000,
                connectionIdentifier: "8AB00818-D533-4504-A25A-03A17F61201C",
                peeringDBFacilityId: 99999,
                sessionAddressProvider: "Microsoft",
                useForPeeringService: true,
            },
        ],
        directPeeringType: "Edge",
        peerAsn: {
            id: "/subscriptions/subId/providers/Microsoft.Peering/peerAsns/myAsn1",
        },
    },
    kind: "Direct",
    location: "eastus",
    peeringLocation: "peeringLocation0",
    peeringName: "peeringName",
    resourceGroupName: "rgName",
    sku: {
        name: "Basic_Direct_Free",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

peering = azure_native.peering.Peering("peering",
    direct=azure_native.peering.PeeringPropertiesDirectResponseArgs(
        connections=[
            {
                "bandwidthInMbps": 10000,
                "bgpSession": azure_native.peering.BgpSessionArgs(
                    max_prefixes_advertised_v4=1000,
                    max_prefixes_advertised_v6=100,
                    md5_authentication_key="test-md5-auth-key",
                    session_prefix_v4="192.168.0.0/31",
                    session_prefix_v6="fd00::0/127",
                ),
                "connectionIdentifier": "5F4CB5C7-6B43-4444-9338-9ABC72606C16",
                "peeringDBFacilityId": 99999,
                "sessionAddressProvider": "Peer",
                "useForPeeringService": False,
            },
            azure_native.peering.DirectConnectionArgs(
                bandwidth_in_mbps=10000,
                connection_identifier="8AB00818-D533-4504-A25A-03A17F61201C",
                peering_db_facility_id=99999,
                session_address_provider="Microsoft",
                use_for_peering_service=True,
            ),
        ],
        direct_peering_type="Edge",
        peer_asn=azure_native.peering.SubResourceArgs(
            id="/subscriptions/subId/providers/Microsoft.Peering/peerAsns/myAsn1",
        ),
    ),
    kind="Direct",
    location="eastus",
    peering_location="peeringLocation0",
    peering_name="peeringName",
    resource_group_name="rgName",
    sku=azure_native.peering.PeeringSkuArgs(
        name="Basic_Direct_Free",
    ))

```

```yaml
resources:
  peering:
    type: azure-native:peering:Peering
    properties:
      direct:
        connections:
          - bandwidthInMbps: 10000
            bgpSession:
              maxPrefixesAdvertisedV4: 1000
              maxPrefixesAdvertisedV6: 100
              md5AuthenticationKey: test-md5-auth-key
              sessionPrefixV4: 192.168.0.0/31
              sessionPrefixV6: fd00::0/127
            connectionIdentifier: 5F4CB5C7-6B43-4444-9338-9ABC72606C16
            peeringDBFacilityId: 99999
            sessionAddressProvider: Peer
            useForPeeringService: false
          - bandwidthInMbps: 10000
            connectionIdentifier: 8AB00818-D533-4504-A25A-03A17F61201C
            peeringDBFacilityId: 99999
            sessionAddressProvider: Microsoft
            useForPeeringService: true
        directPeeringType: Edge
        peerAsn:
          id: /subscriptions/subId/providers/Microsoft.Peering/peerAsns/myAsn1
      kind: Direct
      location: eastus
      peeringLocation: peeringLocation0
      peeringName: peeringName
      resourceGroupName: rgName
      sku:
        name: Basic_Direct_Free

```

{{% /example %}}
{{% example %}}
### Create a peering with exchange route server
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var peering = new AzureNative.Peering.Peering("peering", new()
    {
        Direct = new AzureNative.Peering.Inputs.PeeringPropertiesDirectArgs
        {
            Connections = new[]
            {
                new AzureNative.Peering.Inputs.DirectConnectionArgs
                {
                    BandwidthInMbps = 10000,
                    BgpSession = new AzureNative.Peering.Inputs.BgpSessionArgs
                    {
                        MaxPrefixesAdvertisedV4 = 1000,
                        MaxPrefixesAdvertisedV6 = 100,
                        MicrosoftSessionIPv4Address = "192.168.0.123",
                        PeerSessionIPv4Address = "192.168.0.234",
                        SessionPrefixV4 = "192.168.0.0/24",
                    },
                    ConnectionIdentifier = "5F4CB5C7-6B43-4444-9338-9ABC72606C16",
                    PeeringDBFacilityId = 99999,
                    SessionAddressProvider = "Peer",
                    UseForPeeringService = true,
                },
            },
            DirectPeeringType = "IxRs",
            PeerAsn = new AzureNative.Peering.Inputs.SubResourceArgs
            {
                Id = "/subscriptions/subId/providers/Microsoft.Peering/peerAsns/myAsn1",
            },
        },
        Kind = "Direct",
        Location = "eastus",
        PeeringLocation = "peeringLocation0",
        PeeringName = "peeringName",
        ResourceGroupName = "rgName",
        Sku = new AzureNative.Peering.Inputs.PeeringSkuArgs
        {
            Name = "Premium_Direct_Free",
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.peering.Peering;
import com.pulumi.azurenative.peering.PeeringArgs;
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
        var peering = new Peering("peering", PeeringArgs.builder()        
            .direct(Map.ofEntries(
                Map.entry("connections", Map.ofEntries(
                    Map.entry("bandwidthInMbps", 10000),
                    Map.entry("bgpSession", Map.ofEntries(
                        Map.entry("maxPrefixesAdvertisedV4", 1000),
                        Map.entry("maxPrefixesAdvertisedV6", 100),
                        Map.entry("microsoftSessionIPv4Address", "192.168.0.123"),
                        Map.entry("peerSessionIPv4Address", "192.168.0.234"),
                        Map.entry("sessionPrefixV4", "192.168.0.0/24")
                    )),
                    Map.entry("connectionIdentifier", "5F4CB5C7-6B43-4444-9338-9ABC72606C16"),
                    Map.entry("peeringDBFacilityId", 99999),
                    Map.entry("sessionAddressProvider", "Peer"),
                    Map.entry("useForPeeringService", true)
                )),
                Map.entry("directPeeringType", "IxRs"),
                Map.entry("peerAsn", Map.of("id", "/subscriptions/subId/providers/Microsoft.Peering/peerAsns/myAsn1"))
            ))
            .kind("Direct")
            .location("eastus")
            .peeringLocation("peeringLocation0")
            .peeringName("peeringName")
            .resourceGroupName("rgName")
            .sku(Map.of("name", "Premium_Direct_Free"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const peering = new azure_native.peering.Peering("peering", {
    direct: {
        connections: [{
            bandwidthInMbps: 10000,
            bgpSession: {
                maxPrefixesAdvertisedV4: 1000,
                maxPrefixesAdvertisedV6: 100,
                microsoftSessionIPv4Address: "192.168.0.123",
                peerSessionIPv4Address: "192.168.0.234",
                sessionPrefixV4: "192.168.0.0/24",
            },
            connectionIdentifier: "5F4CB5C7-6B43-4444-9338-9ABC72606C16",
            peeringDBFacilityId: 99999,
            sessionAddressProvider: "Peer",
            useForPeeringService: true,
        }],
        directPeeringType: "IxRs",
        peerAsn: {
            id: "/subscriptions/subId/providers/Microsoft.Peering/peerAsns/myAsn1",
        },
    },
    kind: "Direct",
    location: "eastus",
    peeringLocation: "peeringLocation0",
    peeringName: "peeringName",
    resourceGroupName: "rgName",
    sku: {
        name: "Premium_Direct_Free",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

peering = azure_native.peering.Peering("peering",
    direct=azure_native.peering.PeeringPropertiesDirectResponseArgs(
        connections=[{
            "bandwidthInMbps": 10000,
            "bgpSession": azure_native.peering.BgpSessionArgs(
                max_prefixes_advertised_v4=1000,
                max_prefixes_advertised_v6=100,
                microsoft_session_i_pv4_address="192.168.0.123",
                peer_session_i_pv4_address="192.168.0.234",
                session_prefix_v4="192.168.0.0/24",
            ),
            "connectionIdentifier": "5F4CB5C7-6B43-4444-9338-9ABC72606C16",
            "peeringDBFacilityId": 99999,
            "sessionAddressProvider": "Peer",
            "useForPeeringService": True,
        }],
        direct_peering_type="IxRs",
        peer_asn=azure_native.peering.SubResourceArgs(
            id="/subscriptions/subId/providers/Microsoft.Peering/peerAsns/myAsn1",
        ),
    ),
    kind="Direct",
    location="eastus",
    peering_location="peeringLocation0",
    peering_name="peeringName",
    resource_group_name="rgName",
    sku=azure_native.peering.PeeringSkuArgs(
        name="Premium_Direct_Free",
    ))

```

```yaml
resources:
  peering:
    type: azure-native:peering:Peering
    properties:
      direct:
        connections:
          - bandwidthInMbps: 10000
            bgpSession:
              maxPrefixesAdvertisedV4: 1000
              maxPrefixesAdvertisedV6: 100
              microsoftSessionIPv4Address: 192.168.0.123
              peerSessionIPv4Address: 192.168.0.234
              sessionPrefixV4: 192.168.0.0/24
            connectionIdentifier: 5F4CB5C7-6B43-4444-9338-9ABC72606C16
            peeringDBFacilityId: 99999
            sessionAddressProvider: Peer
            useForPeeringService: true
        directPeeringType: IxRs
        peerAsn:
          id: /subscriptions/subId/providers/Microsoft.Peering/peerAsns/myAsn1
      kind: Direct
      location: eastus
      peeringLocation: peeringLocation0
      peeringName: peeringName
      resourceGroupName: rgName
      sku:
        name: Premium_Direct_Free

```

{{% /example %}}
{{% example %}}
### Create an exchange peering
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var peering = new AzureNative.Peering.Peering("peering", new()
    {
        Exchange = new AzureNative.Peering.Inputs.PeeringPropertiesExchangeArgs
        {
            Connections = new[]
            {
                new AzureNative.Peering.Inputs.ExchangeConnectionArgs
                {
                    BgpSession = new AzureNative.Peering.Inputs.BgpSessionArgs
                    {
                        MaxPrefixesAdvertisedV4 = 1000,
                        MaxPrefixesAdvertisedV6 = 100,
                        Md5AuthenticationKey = "test-md5-auth-key",
                        PeerSessionIPv4Address = "192.168.2.1",
                        PeerSessionIPv6Address = "fd00::1",
                    },
                    ConnectionIdentifier = "CE495334-0E94-4E51-8164-8116D6CD284D",
                    PeeringDBFacilityId = 99999,
                },
                new AzureNative.Peering.Inputs.ExchangeConnectionArgs
                {
                    BgpSession = new AzureNative.Peering.Inputs.BgpSessionArgs
                    {
                        MaxPrefixesAdvertisedV4 = 1000,
                        MaxPrefixesAdvertisedV6 = 100,
                        Md5AuthenticationKey = "test-md5-auth-key",
                        PeerSessionIPv4Address = "192.168.2.2",
                        PeerSessionIPv6Address = "fd00::2",
                    },
                    ConnectionIdentifier = "CDD8E673-CB07-47E6-84DE-3739F778762B",
                    PeeringDBFacilityId = 99999,
                },
            },
            PeerAsn = new AzureNative.Peering.Inputs.SubResourceArgs
            {
                Id = "/subscriptions/subId/providers/Microsoft.Peering/peerAsns/myAsn1",
            },
        },
        Kind = "Exchange",
        Location = "eastus",
        PeeringLocation = "peeringLocation0",
        PeeringName = "peeringName",
        ResourceGroupName = "rgName",
        Sku = new AzureNative.Peering.Inputs.PeeringSkuArgs
        {
            Name = "Basic_Exchange_Free",
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.peering.Peering;
import com.pulumi.azurenative.peering.PeeringArgs;
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
        var peering = new Peering("peering", PeeringArgs.builder()        
            .exchange(Map.ofEntries(
                Map.entry("connections",                 
                    Map.ofEntries(
                        Map.entry("bgpSession", Map.ofEntries(
                            Map.entry("maxPrefixesAdvertisedV4", 1000),
                            Map.entry("maxPrefixesAdvertisedV6", 100),
                            Map.entry("md5AuthenticationKey", "test-md5-auth-key"),
                            Map.entry("peerSessionIPv4Address", "192.168.2.1"),
                            Map.entry("peerSessionIPv6Address", "fd00::1")
                        )),
                        Map.entry("connectionIdentifier", "CE495334-0E94-4E51-8164-8116D6CD284D"),
                        Map.entry("peeringDBFacilityId", 99999)
                    ),
                    Map.ofEntries(
                        Map.entry("bgpSession", Map.ofEntries(
                            Map.entry("maxPrefixesAdvertisedV4", 1000),
                            Map.entry("maxPrefixesAdvertisedV6", 100),
                            Map.entry("md5AuthenticationKey", "test-md5-auth-key"),
                            Map.entry("peerSessionIPv4Address", "192.168.2.2"),
                            Map.entry("peerSessionIPv6Address", "fd00::2")
                        )),
                        Map.entry("connectionIdentifier", "CDD8E673-CB07-47E6-84DE-3739F778762B"),
                        Map.entry("peeringDBFacilityId", 99999)
                    )),
                Map.entry("peerAsn", Map.of("id", "/subscriptions/subId/providers/Microsoft.Peering/peerAsns/myAsn1"))
            ))
            .kind("Exchange")
            .location("eastus")
            .peeringLocation("peeringLocation0")
            .peeringName("peeringName")
            .resourceGroupName("rgName")
            .sku(Map.of("name", "Basic_Exchange_Free"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const peering = new azure_native.peering.Peering("peering", {
    exchange: {
        connections: [
            {
                bgpSession: {
                    maxPrefixesAdvertisedV4: 1000,
                    maxPrefixesAdvertisedV6: 100,
                    md5AuthenticationKey: "test-md5-auth-key",
                    peerSessionIPv4Address: "192.168.2.1",
                    peerSessionIPv6Address: "fd00::1",
                },
                connectionIdentifier: "CE495334-0E94-4E51-8164-8116D6CD284D",
                peeringDBFacilityId: 99999,
            },
            {
                bgpSession: {
                    maxPrefixesAdvertisedV4: 1000,
                    maxPrefixesAdvertisedV6: 100,
                    md5AuthenticationKey: "test-md5-auth-key",
                    peerSessionIPv4Address: "192.168.2.2",
                    peerSessionIPv6Address: "fd00::2",
                },
                connectionIdentifier: "CDD8E673-CB07-47E6-84DE-3739F778762B",
                peeringDBFacilityId: 99999,
            },
        ],
        peerAsn: {
            id: "/subscriptions/subId/providers/Microsoft.Peering/peerAsns/myAsn1",
        },
    },
    kind: "Exchange",
    location: "eastus",
    peeringLocation: "peeringLocation0",
    peeringName: "peeringName",
    resourceGroupName: "rgName",
    sku: {
        name: "Basic_Exchange_Free",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

peering = azure_native.peering.Peering("peering",
    exchange=azure_native.peering.PeeringPropertiesExchangeResponseArgs(
        connections=[
            {
                "bgpSession": azure_native.peering.BgpSessionArgs(
                    max_prefixes_advertised_v4=1000,
                    max_prefixes_advertised_v6=100,
                    md5_authentication_key="test-md5-auth-key",
                    peer_session_i_pv4_address="192.168.2.1",
                    peer_session_i_pv6_address="fd00::1",
                ),
                "connectionIdentifier": "CE495334-0E94-4E51-8164-8116D6CD284D",
                "peeringDBFacilityId": 99999,
            },
            {
                "bgpSession": azure_native.peering.BgpSessionArgs(
                    max_prefixes_advertised_v4=1000,
                    max_prefixes_advertised_v6=100,
                    md5_authentication_key="test-md5-auth-key",
                    peer_session_i_pv4_address="192.168.2.2",
                    peer_session_i_pv6_address="fd00::2",
                ),
                "connectionIdentifier": "CDD8E673-CB07-47E6-84DE-3739F778762B",
                "peeringDBFacilityId": 99999,
            },
        ],
        peer_asn=azure_native.peering.SubResourceArgs(
            id="/subscriptions/subId/providers/Microsoft.Peering/peerAsns/myAsn1",
        ),
    ),
    kind="Exchange",
    location="eastus",
    peering_location="peeringLocation0",
    peering_name="peeringName",
    resource_group_name="rgName",
    sku=azure_native.peering.PeeringSkuArgs(
        name="Basic_Exchange_Free",
    ))

```

```yaml
resources:
  peering:
    type: azure-native:peering:Peering
    properties:
      exchange:
        connections:
          - bgpSession:
              maxPrefixesAdvertisedV4: 1000
              maxPrefixesAdvertisedV6: 100
              md5AuthenticationKey: test-md5-auth-key
              peerSessionIPv4Address: 192.168.2.1
              peerSessionIPv6Address: fd00::1
            connectionIdentifier: CE495334-0E94-4E51-8164-8116D6CD284D
            peeringDBFacilityId: 99999
          - bgpSession:
              maxPrefixesAdvertisedV4: 1000
              maxPrefixesAdvertisedV6: 100
              md5AuthenticationKey: test-md5-auth-key
              peerSessionIPv4Address: 192.168.2.2
              peerSessionIPv6Address: fd00::2
            connectionIdentifier: CDD8E673-CB07-47E6-84DE-3739F778762B
            peeringDBFacilityId: 99999
        peerAsn:
          id: /subscriptions/subId/providers/Microsoft.Peering/peerAsns/myAsn1
      kind: Exchange
      location: eastus
      peeringLocation: peeringLocation0
      peeringName: peeringName
      resourceGroupName: rgName
      sku:
        name: Basic_Exchange_Free

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:peering:Peering peeringName /subscriptions/subId/resourceGroups/rgName/providers/Microsoft.Peering/peerings/peeringName 
```
