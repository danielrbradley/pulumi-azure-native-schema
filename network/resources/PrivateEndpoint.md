Private endpoint resource.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create private endpoint
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateEndpoint = new AzureNative.Network.PrivateEndpoint("privateEndpoint", new()
    {
        CustomNetworkInterfaceName = "testPeNic",
        IpConfigurations = new[]
        {
            new AzureNative.Network.Inputs.PrivateEndpointIPConfigurationArgs
            {
                GroupId = "file",
                MemberName = "file",
                Name = "pestaticconfig",
                PrivateIPAddress = "192.168.0.6",
            },
        },
        Location = "eastus2euap",
        PrivateEndpointName = "testPe",
        PrivateLinkServiceConnections = new[]
        {
            new AzureNative.Network.Inputs.PrivateLinkServiceConnectionArgs
            {
                GroupIds = new[]
                {
                    "groupIdFromResource",
                },
                PrivateLinkServiceId = "/subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/privateLinkServices/testPls",
                RequestMessage = "Please approve my connection.",
            },
        },
        ResourceGroupName = "rg1",
        Subnet = new AzureNative.Network.Inputs.SubnetArgs
        {
            Id = "/subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/myVnet/subnets/mySubnet",
        },
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
		_, err := network.NewPrivateEndpoint(ctx, "privateEndpoint", &network.PrivateEndpointArgs{
			CustomNetworkInterfaceName: pulumi.String("testPeNic"),
			IpConfigurations: []network.PrivateEndpointIPConfigurationArgs{
				{
					GroupId:          pulumi.String("file"),
					MemberName:       pulumi.String("file"),
					Name:             pulumi.String("pestaticconfig"),
					PrivateIPAddress: pulumi.String("192.168.0.6"),
				},
			},
			Location:            pulumi.String("eastus2euap"),
			PrivateEndpointName: pulumi.String("testPe"),
			PrivateLinkServiceConnections: []network.PrivateLinkServiceConnectionArgs{
				{
					GroupIds: pulumi.StringArray{
						pulumi.String("groupIdFromResource"),
					},
					PrivateLinkServiceId: pulumi.String("/subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/privateLinkServices/testPls"),
					RequestMessage:       pulumi.String("Please approve my connection."),
				},
			},
			ResourceGroupName: pulumi.String("rg1"),
			Subnet: &network.SubnetTypeArgs{
				Id: pulumi.String("/subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/myVnet/subnets/mySubnet"),
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
import com.pulumi.azurenative.network.PrivateEndpoint;
import com.pulumi.azurenative.network.PrivateEndpointArgs;
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
        var privateEndpoint = new PrivateEndpoint("privateEndpoint", PrivateEndpointArgs.builder()        
            .customNetworkInterfaceName("testPeNic")
            .ipConfigurations(Map.ofEntries(
                Map.entry("groupId", "file"),
                Map.entry("memberName", "file"),
                Map.entry("name", "pestaticconfig"),
                Map.entry("privateIPAddress", "192.168.0.6")
            ))
            .location("eastus2euap")
            .privateEndpointName("testPe")
            .privateLinkServiceConnections(Map.ofEntries(
                Map.entry("groupIds", "groupIdFromResource"),
                Map.entry("privateLinkServiceId", "/subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/privateLinkServices/testPls"),
                Map.entry("requestMessage", "Please approve my connection.")
            ))
            .resourceGroupName("rg1")
            .subnet(Map.of("id", "/subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/myVnet/subnets/mySubnet"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateEndpoint = new azure_native.network.PrivateEndpoint("privateEndpoint", {
    customNetworkInterfaceName: "testPeNic",
    ipConfigurations: [{
        groupId: "file",
        memberName: "file",
        name: "pestaticconfig",
        privateIPAddress: "192.168.0.6",
    }],
    location: "eastus2euap",
    privateEndpointName: "testPe",
    privateLinkServiceConnections: [{
        groupIds: ["groupIdFromResource"],
        privateLinkServiceId: "/subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/privateLinkServices/testPls",
        requestMessage: "Please approve my connection.",
    }],
    resourceGroupName: "rg1",
    subnet: {
        id: "/subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/myVnet/subnets/mySubnet",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_endpoint = azure_native.network.PrivateEndpoint("privateEndpoint",
    custom_network_interface_name="testPeNic",
    ip_configurations=[azure_native.network.PrivateEndpointIPConfigurationArgs(
        group_id="file",
        member_name="file",
        name="pestaticconfig",
        private_ip_address="192.168.0.6",
    )],
    location="eastus2euap",
    private_endpoint_name="testPe",
    private_link_service_connections=[azure_native.network.PrivateLinkServiceConnectionArgs(
        group_ids=["groupIdFromResource"],
        private_link_service_id="/subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/privateLinkServices/testPls",
        request_message="Please approve my connection.",
    )],
    resource_group_name="rg1",
    subnet=azure_native.network.SubnetArgs(
        id="/subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/myVnet/subnets/mySubnet",
    ))

```

```yaml
resources:
  privateEndpoint:
    type: azure-native:network:PrivateEndpoint
    properties:
      customNetworkInterfaceName: testPeNic
      ipConfigurations:
        - groupId: file
          memberName: file
          name: pestaticconfig
          privateIPAddress: 192.168.0.6
      location: eastus2euap
      privateEndpointName: testPe
      privateLinkServiceConnections:
        - groupIds:
            - groupIdFromResource
          privateLinkServiceId: /subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/privateLinkServices/testPls
          requestMessage: Please approve my connection.
      resourceGroupName: rg1
      subnet:
        id: /subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/myVnet/subnets/mySubnet

```

{{% /example %}}
{{% example %}}
### Create private endpoint with application security groups
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateEndpoint = new AzureNative.Network.PrivateEndpoint("privateEndpoint", new()
    {
        ApplicationSecurityGroups = new[]
        {
            new AzureNative.Network.Inputs.ApplicationSecurityGroupArgs
            {
                Id = "/subscriptions/subId/resourceGroups/rg1/provders/Microsoft.Network/applicationSecurityGroup/asg1",
            },
        },
        Location = "eastus2euap",
        PrivateEndpointName = "testPe",
        PrivateLinkServiceConnections = new[]
        {
            new AzureNative.Network.Inputs.PrivateLinkServiceConnectionArgs
            {
                GroupIds = new[]
                {
                    "groupIdFromResource",
                },
                PrivateLinkServiceId = "/subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/privateLinkServices/testPls",
                RequestMessage = "Please approve my connection.",
            },
        },
        ResourceGroupName = "rg1",
        Subnet = new AzureNative.Network.Inputs.SubnetArgs
        {
            Id = "/subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/myVnet/subnets/mySubnet",
        },
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
		_, err := network.NewPrivateEndpoint(ctx, "privateEndpoint", &network.PrivateEndpointArgs{
			ApplicationSecurityGroups: []network.ApplicationSecurityGroupTypeArgs{
				{
					Id: pulumi.String("/subscriptions/subId/resourceGroups/rg1/provders/Microsoft.Network/applicationSecurityGroup/asg1"),
				},
			},
			Location:            pulumi.String("eastus2euap"),
			PrivateEndpointName: pulumi.String("testPe"),
			PrivateLinkServiceConnections: []network.PrivateLinkServiceConnectionArgs{
				{
					GroupIds: pulumi.StringArray{
						pulumi.String("groupIdFromResource"),
					},
					PrivateLinkServiceId: pulumi.String("/subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/privateLinkServices/testPls"),
					RequestMessage:       pulumi.String("Please approve my connection."),
				},
			},
			ResourceGroupName: pulumi.String("rg1"),
			Subnet: &network.SubnetTypeArgs{
				Id: pulumi.String("/subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/myVnet/subnets/mySubnet"),
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
import com.pulumi.azurenative.network.PrivateEndpoint;
import com.pulumi.azurenative.network.PrivateEndpointArgs;
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
        var privateEndpoint = new PrivateEndpoint("privateEndpoint", PrivateEndpointArgs.builder()        
            .applicationSecurityGroups(Map.of("id", "/subscriptions/subId/resourceGroups/rg1/provders/Microsoft.Network/applicationSecurityGroup/asg1"))
            .location("eastus2euap")
            .privateEndpointName("testPe")
            .privateLinkServiceConnections(Map.ofEntries(
                Map.entry("groupIds", "groupIdFromResource"),
                Map.entry("privateLinkServiceId", "/subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/privateLinkServices/testPls"),
                Map.entry("requestMessage", "Please approve my connection.")
            ))
            .resourceGroupName("rg1")
            .subnet(Map.of("id", "/subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/myVnet/subnets/mySubnet"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateEndpoint = new azure_native.network.PrivateEndpoint("privateEndpoint", {
    applicationSecurityGroups: [{
        id: "/subscriptions/subId/resourceGroups/rg1/provders/Microsoft.Network/applicationSecurityGroup/asg1",
    }],
    location: "eastus2euap",
    privateEndpointName: "testPe",
    privateLinkServiceConnections: [{
        groupIds: ["groupIdFromResource"],
        privateLinkServiceId: "/subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/privateLinkServices/testPls",
        requestMessage: "Please approve my connection.",
    }],
    resourceGroupName: "rg1",
    subnet: {
        id: "/subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/myVnet/subnets/mySubnet",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_endpoint = azure_native.network.PrivateEndpoint("privateEndpoint",
    application_security_groups=[azure_native.network.ApplicationSecurityGroupArgs(
        id="/subscriptions/subId/resourceGroups/rg1/provders/Microsoft.Network/applicationSecurityGroup/asg1",
    )],
    location="eastus2euap",
    private_endpoint_name="testPe",
    private_link_service_connections=[azure_native.network.PrivateLinkServiceConnectionArgs(
        group_ids=["groupIdFromResource"],
        private_link_service_id="/subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/privateLinkServices/testPls",
        request_message="Please approve my connection.",
    )],
    resource_group_name="rg1",
    subnet=azure_native.network.SubnetArgs(
        id="/subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/myVnet/subnets/mySubnet",
    ))

```

```yaml
resources:
  privateEndpoint:
    type: azure-native:network:PrivateEndpoint
    properties:
      applicationSecurityGroups:
        - id: /subscriptions/subId/resourceGroups/rg1/provders/Microsoft.Network/applicationSecurityGroup/asg1
      location: eastus2euap
      privateEndpointName: testPe
      privateLinkServiceConnections:
        - groupIds:
            - groupIdFromResource
          privateLinkServiceId: /subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/privateLinkServices/testPls
          requestMessage: Please approve my connection.
      resourceGroupName: rg1
      subnet:
        id: /subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/myVnet/subnets/mySubnet

```

{{% /example %}}
{{% example %}}
### Create private endpoint with manual approval connection
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateEndpoint = new AzureNative.Network.PrivateEndpoint("privateEndpoint", new()
    {
        CustomNetworkInterfaceName = "testPeNic",
        IpConfigurations = new[]
        {
            new AzureNative.Network.Inputs.PrivateEndpointIPConfigurationArgs
            {
                GroupId = "file",
                MemberName = "file",
                Name = "pestaticconfig",
                PrivateIPAddress = "192.168.0.5",
            },
        },
        Location = "eastus",
        ManualPrivateLinkServiceConnections = new[]
        {
            new AzureNative.Network.Inputs.PrivateLinkServiceConnectionArgs
            {
                GroupIds = new[]
                {
                    "groupIdFromResource",
                },
                PrivateLinkServiceId = "/subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/privateLinkServices/testPls",
                RequestMessage = "Please manually approve my connection.",
            },
        },
        PrivateEndpointName = "testPe",
        ResourceGroupName = "rg1",
        Subnet = new AzureNative.Network.Inputs.SubnetArgs
        {
            Id = "/subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/myVnet/subnets/mySubnet",
        },
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
		_, err := network.NewPrivateEndpoint(ctx, "privateEndpoint", &network.PrivateEndpointArgs{
			CustomNetworkInterfaceName: pulumi.String("testPeNic"),
			IpConfigurations: []network.PrivateEndpointIPConfigurationArgs{
				{
					GroupId:          pulumi.String("file"),
					MemberName:       pulumi.String("file"),
					Name:             pulumi.String("pestaticconfig"),
					PrivateIPAddress: pulumi.String("192.168.0.5"),
				},
			},
			Location: pulumi.String("eastus"),
			ManualPrivateLinkServiceConnections: []network.PrivateLinkServiceConnectionArgs{
				{
					GroupIds: pulumi.StringArray{
						pulumi.String("groupIdFromResource"),
					},
					PrivateLinkServiceId: pulumi.String("/subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/privateLinkServices/testPls"),
					RequestMessage:       pulumi.String("Please manually approve my connection."),
				},
			},
			PrivateEndpointName: pulumi.String("testPe"),
			ResourceGroupName:   pulumi.String("rg1"),
			Subnet: &network.SubnetTypeArgs{
				Id: pulumi.String("/subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/myVnet/subnets/mySubnet"),
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
import com.pulumi.azurenative.network.PrivateEndpoint;
import com.pulumi.azurenative.network.PrivateEndpointArgs;
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
        var privateEndpoint = new PrivateEndpoint("privateEndpoint", PrivateEndpointArgs.builder()        
            .customNetworkInterfaceName("testPeNic")
            .ipConfigurations(Map.ofEntries(
                Map.entry("groupId", "file"),
                Map.entry("memberName", "file"),
                Map.entry("name", "pestaticconfig"),
                Map.entry("privateIPAddress", "192.168.0.5")
            ))
            .location("eastus")
            .manualPrivateLinkServiceConnections(Map.ofEntries(
                Map.entry("groupIds", "groupIdFromResource"),
                Map.entry("privateLinkServiceId", "/subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/privateLinkServices/testPls"),
                Map.entry("requestMessage", "Please manually approve my connection.")
            ))
            .privateEndpointName("testPe")
            .resourceGroupName("rg1")
            .subnet(Map.of("id", "/subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/myVnet/subnets/mySubnet"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateEndpoint = new azure_native.network.PrivateEndpoint("privateEndpoint", {
    customNetworkInterfaceName: "testPeNic",
    ipConfigurations: [{
        groupId: "file",
        memberName: "file",
        name: "pestaticconfig",
        privateIPAddress: "192.168.0.5",
    }],
    location: "eastus",
    manualPrivateLinkServiceConnections: [{
        groupIds: ["groupIdFromResource"],
        privateLinkServiceId: "/subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/privateLinkServices/testPls",
        requestMessage: "Please manually approve my connection.",
    }],
    privateEndpointName: "testPe",
    resourceGroupName: "rg1",
    subnet: {
        id: "/subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/myVnet/subnets/mySubnet",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_endpoint = azure_native.network.PrivateEndpoint("privateEndpoint",
    custom_network_interface_name="testPeNic",
    ip_configurations=[azure_native.network.PrivateEndpointIPConfigurationArgs(
        group_id="file",
        member_name="file",
        name="pestaticconfig",
        private_ip_address="192.168.0.5",
    )],
    location="eastus",
    manual_private_link_service_connections=[azure_native.network.PrivateLinkServiceConnectionArgs(
        group_ids=["groupIdFromResource"],
        private_link_service_id="/subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/privateLinkServices/testPls",
        request_message="Please manually approve my connection.",
    )],
    private_endpoint_name="testPe",
    resource_group_name="rg1",
    subnet=azure_native.network.SubnetArgs(
        id="/subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/myVnet/subnets/mySubnet",
    ))

```

```yaml
resources:
  privateEndpoint:
    type: azure-native:network:PrivateEndpoint
    properties:
      customNetworkInterfaceName: testPeNic
      ipConfigurations:
        - groupId: file
          memberName: file
          name: pestaticconfig
          privateIPAddress: 192.168.0.5
      location: eastus
      manualPrivateLinkServiceConnections:
        - groupIds:
            - groupIdFromResource
          privateLinkServiceId: /subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/privateLinkServices/testPls
          requestMessage: Please manually approve my connection.
      privateEndpointName: testPe
      resourceGroupName: rg1
      subnet:
        id: /subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/myVnet/subnets/mySubnet

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:PrivateEndpoint testPe /subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/privateEndpoints/testPe 
```
