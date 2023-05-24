Information about the connection monitor.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create connection monitor V1
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var connectionMonitor = new AzureNative.Network.ConnectionMonitor("connectionMonitor", new()
    {
        ConnectionMonitorName = "cm1",
        Endpoints = new[]
        {
            new AzureNative.Network.Inputs.ConnectionMonitorEndpointArgs
            {
                Name = "source",
                ResourceId = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Compute/virtualMachines/ct1",
            },
            new AzureNative.Network.Inputs.ConnectionMonitorEndpointArgs
            {
                Address = "bing.com",
                Name = "destination",
            },
        },
        Location = "eastus",
        NetworkWatcherName = "nw1",
        ResourceGroupName = "rg1",
        TestConfigurations = new[]
        {
            new AzureNative.Network.Inputs.ConnectionMonitorTestConfigurationArgs
            {
                Name = "tcp",
                Protocol = "Tcp",
                TcpConfiguration = new AzureNative.Network.Inputs.ConnectionMonitorTcpConfigurationArgs
                {
                    Port = 80,
                },
                TestFrequencySec = 60,
            },
        },
        TestGroups = new[]
        {
            new AzureNative.Network.Inputs.ConnectionMonitorTestGroupArgs
            {
                Destinations = new[]
                {
                    "destination",
                },
                Name = "tg",
                Sources = new[]
                {
                    "source",
                },
                TestConfigurations = new[]
                {
                    "tcp",
                },
            },
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
		_, err := network.NewConnectionMonitor(ctx, "connectionMonitor", &network.ConnectionMonitorArgs{
			ConnectionMonitorName: pulumi.String("cm1"),
			Endpoints: []network.ConnectionMonitorEndpointArgs{
				{
					Name:       pulumi.String("source"),
					ResourceId: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Compute/virtualMachines/ct1"),
				},
				{
					Address: pulumi.String("bing.com"),
					Name:    pulumi.String("destination"),
				},
			},
			Location:           pulumi.String("eastus"),
			NetworkWatcherName: pulumi.String("nw1"),
			ResourceGroupName:  pulumi.String("rg1"),
			TestConfigurations: []network.ConnectionMonitorTestConfigurationArgs{
				{
					Name:     pulumi.String("tcp"),
					Protocol: pulumi.String("Tcp"),
					TcpConfiguration: {
						Port: pulumi.Int(80),
					},
					TestFrequencySec: pulumi.Int(60),
				},
			},
			TestGroups: []network.ConnectionMonitorTestGroupArgs{
				{
					Destinations: pulumi.StringArray{
						pulumi.String("destination"),
					},
					Name: pulumi.String("tg"),
					Sources: pulumi.StringArray{
						pulumi.String("source"),
					},
					TestConfigurations: pulumi.StringArray{
						pulumi.String("tcp"),
					},
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
import com.pulumi.azurenative.network.ConnectionMonitor;
import com.pulumi.azurenative.network.ConnectionMonitorArgs;
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
        var connectionMonitor = new ConnectionMonitor("connectionMonitor", ConnectionMonitorArgs.builder()        
            .connectionMonitorName("cm1")
            .endpoints(            
                Map.ofEntries(
                    Map.entry("name", "source"),
                    Map.entry("resourceId", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Compute/virtualMachines/ct1")
                ),
                Map.ofEntries(
                    Map.entry("address", "bing.com"),
                    Map.entry("name", "destination")
                ))
            .location("eastus")
            .networkWatcherName("nw1")
            .resourceGroupName("rg1")
            .testConfigurations(Map.ofEntries(
                Map.entry("name", "tcp"),
                Map.entry("protocol", "Tcp"),
                Map.entry("tcpConfiguration", Map.of("port", 80)),
                Map.entry("testFrequencySec", 60)
            ))
            .testGroups(Map.ofEntries(
                Map.entry("destinations", "destination"),
                Map.entry("name", "tg"),
                Map.entry("sources", "source"),
                Map.entry("testConfigurations", "tcp")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const connectionMonitor = new azure_native.network.ConnectionMonitor("connectionMonitor", {
    connectionMonitorName: "cm1",
    endpoints: [
        {
            name: "source",
            resourceId: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Compute/virtualMachines/ct1",
        },
        {
            address: "bing.com",
            name: "destination",
        },
    ],
    location: "eastus",
    networkWatcherName: "nw1",
    resourceGroupName: "rg1",
    testConfigurations: [{
        name: "tcp",
        protocol: "Tcp",
        tcpConfiguration: {
            port: 80,
        },
        testFrequencySec: 60,
    }],
    testGroups: [{
        destinations: ["destination"],
        name: "tg",
        sources: ["source"],
        testConfigurations: ["tcp"],
    }],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

connection_monitor = azure_native.network.ConnectionMonitor("connectionMonitor",
    connection_monitor_name="cm1",
    endpoints=[
        azure_native.network.ConnectionMonitorEndpointArgs(
            name="source",
            resource_id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Compute/virtualMachines/ct1",
        ),
        azure_native.network.ConnectionMonitorEndpointArgs(
            address="bing.com",
            name="destination",
        ),
    ],
    location="eastus",
    network_watcher_name="nw1",
    resource_group_name="rg1",
    test_configurations=[{
        "name": "tcp",
        "protocol": "Tcp",
        "tcpConfiguration": azure_native.network.ConnectionMonitorTcpConfigurationArgs(
            port=80,
        ),
        "testFrequencySec": 60,
    }],
    test_groups=[azure_native.network.ConnectionMonitorTestGroupArgs(
        destinations=["destination"],
        name="tg",
        sources=["source"],
        test_configurations=["tcp"],
    )])

```

```yaml
resources:
  connectionMonitor:
    type: azure-native:network:ConnectionMonitor
    properties:
      connectionMonitorName: cm1
      endpoints:
        - name: source
          resourceId: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Compute/virtualMachines/ct1
        - address: bing.com
          name: destination
      location: eastus
      networkWatcherName: nw1
      resourceGroupName: rg1
      testConfigurations:
        - name: tcp
          protocol: Tcp
          tcpConfiguration:
            port: 80
          testFrequencySec: 60
      testGroups:
        - destinations:
            - destination
          name: tg
          sources:
            - source
          testConfigurations:
            - tcp

```

{{% /example %}}
{{% example %}}
### Create connection monitor V2
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var connectionMonitor = new AzureNative.Network.ConnectionMonitor("connectionMonitor", new()
    {
        ConnectionMonitorName = "cm1",
        Endpoints = new[]
        {
            new AzureNative.Network.Inputs.ConnectionMonitorEndpointArgs
            {
                Name = "vm1",
                ResourceId = "/subscriptions/96e68903-0a56-4819-9987-8d08ad6a1f99/resourceGroups/NwRgIrinaCentralUSEUAP/providers/Microsoft.Compute/virtualMachines/vm1",
            },
            new AzureNative.Network.Inputs.ConnectionMonitorEndpointArgs
            {
                Filter = new AzureNative.Network.Inputs.ConnectionMonitorEndpointFilterArgs
                {
                    Items = new[]
                    {
                        new AzureNative.Network.Inputs.ConnectionMonitorEndpointFilterItemArgs
                        {
                            Address = "npmuser",
                            Type = "AgentAddress",
                        },
                    },
                    Type = "Include",
                },
                Name = "CanaryWorkspaceVamshi",
                ResourceId = "/subscriptions/96e68903-0a56-4819-9987-8d08ad6a1f99/resourceGroups/vasamudrRG/providers/Microsoft.OperationalInsights/workspaces/vasamudrWorkspace",
            },
            new AzureNative.Network.Inputs.ConnectionMonitorEndpointArgs
            {
                Address = "bing.com",
                Name = "bing",
            },
            new AzureNative.Network.Inputs.ConnectionMonitorEndpointArgs
            {
                Address = "google.com",
                Name = "google",
            },
        },
        NetworkWatcherName = "nw1",
        Outputs = new[] {},
        ResourceGroupName = "rg1",
        TestConfigurations = new[]
        {
            new AzureNative.Network.Inputs.ConnectionMonitorTestConfigurationArgs
            {
                Name = "testConfig1",
                Protocol = "Tcp",
                TcpConfiguration = new AzureNative.Network.Inputs.ConnectionMonitorTcpConfigurationArgs
                {
                    DisableTraceRoute = false,
                    Port = 80,
                },
                TestFrequencySec = 60,
            },
        },
        TestGroups = new[]
        {
            new AzureNative.Network.Inputs.ConnectionMonitorTestGroupArgs
            {
                Destinations = new[]
                {
                    "bing",
                    "google",
                },
                Disable = false,
                Name = "test1",
                Sources = new[]
                {
                    "vm1",
                    "CanaryWorkspaceVamshi",
                },
                TestConfigurations = new[]
                {
                    "testConfig1",
                },
            },
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
		_, err := network.NewConnectionMonitor(ctx, "connectionMonitor", &network.ConnectionMonitorArgs{
			ConnectionMonitorName: pulumi.String("cm1"),
			Endpoints: []network.ConnectionMonitorEndpointArgs{
				{
					Name:       pulumi.String("vm1"),
					ResourceId: pulumi.String("/subscriptions/96e68903-0a56-4819-9987-8d08ad6a1f99/resourceGroups/NwRgIrinaCentralUSEUAP/providers/Microsoft.Compute/virtualMachines/vm1"),
				},
				{
					Filter: {
						Items: network.ConnectionMonitorEndpointFilterItemArray{
							{
								Address: pulumi.String("npmuser"),
								Type:    pulumi.String("AgentAddress"),
							},
						},
						Type: pulumi.String("Include"),
					},
					Name:       pulumi.String("CanaryWorkspaceVamshi"),
					ResourceId: pulumi.String("/subscriptions/96e68903-0a56-4819-9987-8d08ad6a1f99/resourceGroups/vasamudrRG/providers/Microsoft.OperationalInsights/workspaces/vasamudrWorkspace"),
				},
				{
					Address: pulumi.String("bing.com"),
					Name:    pulumi.String("bing"),
				},
				{
					Address: pulumi.String("google.com"),
					Name:    pulumi.String("google"),
				},
			},
			NetworkWatcherName: pulumi.String("nw1"),
			Outputs:            network.ConnectionMonitorOutputTypeArray{},
			ResourceGroupName:  pulumi.String("rg1"),
			TestConfigurations: []network.ConnectionMonitorTestConfigurationArgs{
				{
					Name:     pulumi.String("testConfig1"),
					Protocol: pulumi.String("Tcp"),
					TcpConfiguration: {
						DisableTraceRoute: pulumi.Bool(false),
						Port:              pulumi.Int(80),
					},
					TestFrequencySec: pulumi.Int(60),
				},
			},
			TestGroups: []network.ConnectionMonitorTestGroupArgs{
				{
					Destinations: pulumi.StringArray{
						pulumi.String("bing"),
						pulumi.String("google"),
					},
					Disable: pulumi.Bool(false),
					Name:    pulumi.String("test1"),
					Sources: pulumi.StringArray{
						pulumi.String("vm1"),
						pulumi.String("CanaryWorkspaceVamshi"),
					},
					TestConfigurations: pulumi.StringArray{
						pulumi.String("testConfig1"),
					},
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
import com.pulumi.azurenative.network.ConnectionMonitor;
import com.pulumi.azurenative.network.ConnectionMonitorArgs;
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
        var connectionMonitor = new ConnectionMonitor("connectionMonitor", ConnectionMonitorArgs.builder()        
            .connectionMonitorName("cm1")
            .endpoints(            
                Map.ofEntries(
                    Map.entry("name", "vm1"),
                    Map.entry("resourceId", "/subscriptions/96e68903-0a56-4819-9987-8d08ad6a1f99/resourceGroups/NwRgIrinaCentralUSEUAP/providers/Microsoft.Compute/virtualMachines/vm1")
                ),
                Map.ofEntries(
                    Map.entry("filter", Map.ofEntries(
                        Map.entry("items", Map.ofEntries(
                            Map.entry("address", "npmuser"),
                            Map.entry("type", "AgentAddress")
                        )),
                        Map.entry("type", "Include")
                    )),
                    Map.entry("name", "CanaryWorkspaceVamshi"),
                    Map.entry("resourceId", "/subscriptions/96e68903-0a56-4819-9987-8d08ad6a1f99/resourceGroups/vasamudrRG/providers/Microsoft.OperationalInsights/workspaces/vasamudrWorkspace")
                ),
                Map.ofEntries(
                    Map.entry("address", "bing.com"),
                    Map.entry("name", "bing")
                ),
                Map.ofEntries(
                    Map.entry("address", "google.com"),
                    Map.entry("name", "google")
                ))
            .networkWatcherName("nw1")
            .outputs()
            .resourceGroupName("rg1")
            .testConfigurations(Map.ofEntries(
                Map.entry("name", "testConfig1"),
                Map.entry("protocol", "Tcp"),
                Map.entry("tcpConfiguration", Map.ofEntries(
                    Map.entry("disableTraceRoute", false),
                    Map.entry("port", 80)
                )),
                Map.entry("testFrequencySec", 60)
            ))
            .testGroups(Map.ofEntries(
                Map.entry("destinations",                 
                    "bing",
                    "google"),
                Map.entry("disable", false),
                Map.entry("name", "test1"),
                Map.entry("sources",                 
                    "vm1",
                    "CanaryWorkspaceVamshi"),
                Map.entry("testConfigurations", "testConfig1")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const connectionMonitor = new azure_native.network.ConnectionMonitor("connectionMonitor", {
    connectionMonitorName: "cm1",
    endpoints: [
        {
            name: "vm1",
            resourceId: "/subscriptions/96e68903-0a56-4819-9987-8d08ad6a1f99/resourceGroups/NwRgIrinaCentralUSEUAP/providers/Microsoft.Compute/virtualMachines/vm1",
        },
        {
            filter: {
                items: [{
                    address: "npmuser",
                    type: "AgentAddress",
                }],
                type: "Include",
            },
            name: "CanaryWorkspaceVamshi",
            resourceId: "/subscriptions/96e68903-0a56-4819-9987-8d08ad6a1f99/resourceGroups/vasamudrRG/providers/Microsoft.OperationalInsights/workspaces/vasamudrWorkspace",
        },
        {
            address: "bing.com",
            name: "bing",
        },
        {
            address: "google.com",
            name: "google",
        },
    ],
    networkWatcherName: "nw1",
    outputs: [],
    resourceGroupName: "rg1",
    testConfigurations: [{
        name: "testConfig1",
        protocol: "Tcp",
        tcpConfiguration: {
            disableTraceRoute: false,
            port: 80,
        },
        testFrequencySec: 60,
    }],
    testGroups: [{
        destinations: [
            "bing",
            "google",
        ],
        disable: false,
        name: "test1",
        sources: [
            "vm1",
            "CanaryWorkspaceVamshi",
        ],
        testConfigurations: ["testConfig1"],
    }],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

connection_monitor = azure_native.network.ConnectionMonitor("connectionMonitor",
    connection_monitor_name="cm1",
    endpoints=[
        azure_native.network.ConnectionMonitorEndpointArgs(
            name="vm1",
            resource_id="/subscriptions/96e68903-0a56-4819-9987-8d08ad6a1f99/resourceGroups/NwRgIrinaCentralUSEUAP/providers/Microsoft.Compute/virtualMachines/vm1",
        ),
        {
            "filter": {
                "items": [azure_native.network.ConnectionMonitorEndpointFilterItemArgs(
                    address="npmuser",
                    type="AgentAddress",
                )],
                "type": "Include",
            },
            "name": "CanaryWorkspaceVamshi",
            "resourceId": "/subscriptions/96e68903-0a56-4819-9987-8d08ad6a1f99/resourceGroups/vasamudrRG/providers/Microsoft.OperationalInsights/workspaces/vasamudrWorkspace",
        },
        azure_native.network.ConnectionMonitorEndpointArgs(
            address="bing.com",
            name="bing",
        ),
        azure_native.network.ConnectionMonitorEndpointArgs(
            address="google.com",
            name="google",
        ),
    ],
    network_watcher_name="nw1",
    outputs=[],
    resource_group_name="rg1",
    test_configurations=[{
        "name": "testConfig1",
        "protocol": "Tcp",
        "tcpConfiguration": azure_native.network.ConnectionMonitorTcpConfigurationArgs(
            disable_trace_route=False,
            port=80,
        ),
        "testFrequencySec": 60,
    }],
    test_groups=[azure_native.network.ConnectionMonitorTestGroupArgs(
        destinations=[
            "bing",
            "google",
        ],
        disable=False,
        name="test1",
        sources=[
            "vm1",
            "CanaryWorkspaceVamshi",
        ],
        test_configurations=["testConfig1"],
    )])

```

```yaml
resources:
  connectionMonitor:
    type: azure-native:network:ConnectionMonitor
    properties:
      connectionMonitorName: cm1
      endpoints:
        - name: vm1
          resourceId: /subscriptions/96e68903-0a56-4819-9987-8d08ad6a1f99/resourceGroups/NwRgIrinaCentralUSEUAP/providers/Microsoft.Compute/virtualMachines/vm1
        - filter:
            items:
              - address: npmuser
                type: AgentAddress
            type: Include
          name: CanaryWorkspaceVamshi
          resourceId: /subscriptions/96e68903-0a56-4819-9987-8d08ad6a1f99/resourceGroups/vasamudrRG/providers/Microsoft.OperationalInsights/workspaces/vasamudrWorkspace
        - address: bing.com
          name: bing
        - address: google.com
          name: google
      networkWatcherName: nw1
      outputs: []
      resourceGroupName: rg1
      testConfigurations:
        - name: testConfig1
          protocol: Tcp
          tcpConfiguration:
            disableTraceRoute: false
            port: 80
          testFrequencySec: 60
      testGroups:
        - destinations:
            - bing
            - google
          disable: false
          name: test1
          sources:
            - vm1
            - CanaryWorkspaceVamshi
          testConfigurations:
            - testConfig1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:ConnectionMonitor cm1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/networkWatchers/nw1/connectionMonitors/cm1 
```
