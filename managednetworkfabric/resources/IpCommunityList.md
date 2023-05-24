The IpCommunityList resource definition.
API Version: 2023-02-01-preview.
Previous API Version: 2023-02-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### IpCommunityLists_Create_MinimumSet_Gen
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var ipCommunityList = new AzureNative.ManagedNetworkFabric.IpCommunityList("ipCommunityList", new()
    {
        Action = "allow",
        Advertise = "true",
        Annotation = "aaaa",
        CommunityMembers = new[]
        {
            new AzureNative.ManagedNetworkFabric.Inputs.IpCommunityListPropertiesCommunityMembersArgs
            {
                Annotation = "app2",
                CommunityMember = "1234:5678",
            },
        },
        EvpnEsImportRouteTargets = new[]
        {
            new AzureNative.ManagedNetworkFabric.Inputs.IpCommunityListPropertiesEvpnEsImportRouteTargetsArgs
            {
                Annotation = "app1",
                EvpnEsImportRouteTarget = "1.1.1",
            },
        },
        Export = "true",
        IpCommunityListName = "aaaaa",
        LocalAS = "true",
        Location = "EastUS",
        ResourceGroupName = "rgIpCommunityLists",
        Tags = 
        {
            { "key2814", "" },
        },
    });

});


```

```go
package main

import (
	managednetworkfabric "github.com/pulumi/pulumi-azure-native-sdk/managednetworkfabric"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := managednetworkfabric.NewIpCommunityList(ctx, "ipCommunityList", &managednetworkfabric.IpCommunityListArgs{
			Action:     pulumi.String("allow"),
			Advertise:  pulumi.String("true"),
			Annotation: pulumi.String("aaaa"),
			CommunityMembers: []managednetworkfabric.IpCommunityListPropertiesCommunityMembersArgs{
				{
					Annotation:      pulumi.String("app2"),
					CommunityMember: pulumi.String("1234:5678"),
				},
			},
			EvpnEsImportRouteTargets: []managednetworkfabric.IpCommunityListPropertiesEvpnEsImportRouteTargetsArgs{
				{
					Annotation:              pulumi.String("app1"),
					EvpnEsImportRouteTarget: pulumi.String("1.1.1"),
				},
			},
			Export:              pulumi.String("true"),
			IpCommunityListName: pulumi.String("aaaaa"),
			LocalAS:             pulumi.String("true"),
			Location:            pulumi.String("EastUS"),
			ResourceGroupName:   pulumi.String("rgIpCommunityLists"),
			Tags: pulumi.StringMap{
				"key2814": pulumi.String(""),
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
import com.pulumi.azurenative.managednetworkfabric.IpCommunityList;
import com.pulumi.azurenative.managednetworkfabric.IpCommunityListArgs;
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
        var ipCommunityList = new IpCommunityList("ipCommunityList", IpCommunityListArgs.builder()        
            .action("allow")
            .advertise("true")
            .annotation("aaaa")
            .communityMembers(Map.ofEntries(
                Map.entry("annotation", "app2"),
                Map.entry("communityMember", "1234:5678")
            ))
            .evpnEsImportRouteTargets(Map.ofEntries(
                Map.entry("annotation", "app1"),
                Map.entry("evpnEsImportRouteTarget", "1.1.1")
            ))
            .export("true")
            .ipCommunityListName("aaaaa")
            .localAS("true")
            .location("EastUS")
            .resourceGroupName("rgIpCommunityLists")
            .tags(Map.of("key2814", ""))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const ipCommunityList = new azure_native.managednetworkfabric.IpCommunityList("ipCommunityList", {
    action: "allow",
    advertise: "true",
    annotation: "aaaa",
    communityMembers: [{
        annotation: "app2",
        communityMember: "1234:5678",
    }],
    evpnEsImportRouteTargets: [{
        annotation: "app1",
        evpnEsImportRouteTarget: "1.1.1",
    }],
    "export": "true",
    ipCommunityListName: "aaaaa",
    localAS: "true",
    location: "EastUS",
    resourceGroupName: "rgIpCommunityLists",
    tags: {
        key2814: "",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

ip_community_list = azure_native.managednetworkfabric.IpCommunityList("ipCommunityList",
    action="allow",
    advertise="true",
    annotation="aaaa",
    community_members=[azure_native.managednetworkfabric.IpCommunityListPropertiesCommunityMembersArgs(
        annotation="app2",
        community_member="1234:5678",
    )],
    evpn_es_import_route_targets=[azure_native.managednetworkfabric.IpCommunityListPropertiesEvpnEsImportRouteTargetsArgs(
        annotation="app1",
        evpn_es_import_route_target="1.1.1",
    )],
    export="true",
    ip_community_list_name="aaaaa",
    local_as="true",
    location="EastUS",
    resource_group_name="rgIpCommunityLists",
    tags={
        "key2814": "",
    })

```

```yaml
resources:
  ipCommunityList:
    type: azure-native:managednetworkfabric:IpCommunityList
    properties:
      action: allow
      advertise: 'true'
      annotation: aaaa
      communityMembers:
        - annotation: app2
          communityMember: 1234:5678
      evpnEsImportRouteTargets:
        - annotation: app1
          evpnEsImportRouteTarget: 1.1.1
      export: 'true'
      ipCommunityListName: aaaaa
      localAS: 'true'
      location: EastUS
      resourceGroupName: rgIpCommunityLists
      tags:
        key2814:

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:managednetworkfabric:IpCommunityList aaaaa /subscriptions/xxxxxx/resourceGroups/resourcegroupname/providers/Microsoft.ManagedNetworkFabric/IpCommunityList/ipCommunityListName 
```
