Differentiated Services Code Point configuration for any given network interface
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create DSCP Configuration
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var dscpConfiguration = new AzureNative.Network.DscpConfiguration("dscpConfiguration", new()
    {
        DscpConfigurationName = "mydscpconfig",
        Location = "eastus",
        QosDefinitionCollection = new[]
        {
            new AzureNative.Network.Inputs.QosDefinitionArgs
            {
                DestinationIpRanges = new[]
                {
                    new AzureNative.Network.Inputs.QosIpRangeArgs
                    {
                        EndIP = "127.0.10.2",
                        StartIP = "127.0.10.1",
                    },
                },
                DestinationPortRanges = new[]
                {
                    new AzureNative.Network.Inputs.QosPortRangeArgs
                    {
                        End = 15,
                        Start = 15,
                    },
                },
                Markings = new[]
                {
                    1,
                },
                Protocol = "Tcp",
                SourceIpRanges = new[]
                {
                    new AzureNative.Network.Inputs.QosIpRangeArgs
                    {
                        EndIP = "127.0.0.2",
                        StartIP = "127.0.0.1",
                    },
                },
                SourcePortRanges = new[]
                {
                    new AzureNative.Network.Inputs.QosPortRangeArgs
                    {
                        End = 11,
                        Start = 10,
                    },
                    new AzureNative.Network.Inputs.QosPortRangeArgs
                    {
                        End = 21,
                        Start = 20,
                    },
                },
            },
            new AzureNative.Network.Inputs.QosDefinitionArgs
            {
                DestinationIpRanges = new[]
                {
                    new AzureNative.Network.Inputs.QosIpRangeArgs
                    {
                        EndIP = "12.0.10.2",
                        StartIP = "12.0.10.1",
                    },
                },
                DestinationPortRanges = new[]
                {
                    new AzureNative.Network.Inputs.QosPortRangeArgs
                    {
                        End = 52,
                        Start = 51,
                    },
                },
                Markings = new[]
                {
                    2,
                },
                Protocol = "Udp",
                SourceIpRanges = new[]
                {
                    new AzureNative.Network.Inputs.QosIpRangeArgs
                    {
                        EndIP = "12.0.0.2",
                        StartIP = "12.0.0.1",
                    },
                },
                SourcePortRanges = new[]
                {
                    new AzureNative.Network.Inputs.QosPortRangeArgs
                    {
                        End = 12,
                        Start = 11,
                    },
                },
            },
        },
        ResourceGroupName = "rg1",
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
		_, err := network.NewDscpConfiguration(ctx, "dscpConfiguration", &network.DscpConfigurationArgs{
			DscpConfigurationName: pulumi.String("mydscpconfig"),
			Location:              pulumi.String("eastus"),
			QosDefinitionCollection: []network.QosDefinitionArgs{
				{
					DestinationIpRanges: network.QosIpRangeArray{
						{
							EndIP:   pulumi.String("127.0.10.2"),
							StartIP: pulumi.String("127.0.10.1"),
						},
					},
					DestinationPortRanges: network.QosPortRangeArray{
						{
							End:   pulumi.Int(15),
							Start: pulumi.Int(15),
						},
					},
					Markings: pulumi.IntArray{
						pulumi.Int(1),
					},
					Protocol: pulumi.String("Tcp"),
					SourceIpRanges: network.QosIpRangeArray{
						{
							EndIP:   pulumi.String("127.0.0.2"),
							StartIP: pulumi.String("127.0.0.1"),
						},
					},
					SourcePortRanges: network.QosPortRangeArray{
						{
							End:   pulumi.Int(11),
							Start: pulumi.Int(10),
						},
						{
							End:   pulumi.Int(21),
							Start: pulumi.Int(20),
						},
					},
				},
				{
					DestinationIpRanges: network.QosIpRangeArray{
						{
							EndIP:   pulumi.String("12.0.10.2"),
							StartIP: pulumi.String("12.0.10.1"),
						},
					},
					DestinationPortRanges: network.QosPortRangeArray{
						{
							End:   pulumi.Int(52),
							Start: pulumi.Int(51),
						},
					},
					Markings: pulumi.IntArray{
						pulumi.Int(2),
					},
					Protocol: pulumi.String("Udp"),
					SourceIpRanges: network.QosIpRangeArray{
						{
							EndIP:   pulumi.String("12.0.0.2"),
							StartIP: pulumi.String("12.0.0.1"),
						},
					},
					SourcePortRanges: network.QosPortRangeArray{
						{
							End:   pulumi.Int(12),
							Start: pulumi.Int(11),
						},
					},
				},
			},
			ResourceGroupName: pulumi.String("rg1"),
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
import com.pulumi.azurenative.network.DscpConfiguration;
import com.pulumi.azurenative.network.DscpConfigurationArgs;
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
        var dscpConfiguration = new DscpConfiguration("dscpConfiguration", DscpConfigurationArgs.builder()        
            .dscpConfigurationName("mydscpconfig")
            .location("eastus")
            .qosDefinitionCollection(            
                Map.ofEntries(
                    Map.entry("destinationIpRanges", Map.ofEntries(
                        Map.entry("endIP", "127.0.10.2"),
                        Map.entry("startIP", "127.0.10.1")
                    )),
                    Map.entry("destinationPortRanges", Map.ofEntries(
                        Map.entry("end", 15),
                        Map.entry("start", 15)
                    )),
                    Map.entry("markings", 1),
                    Map.entry("protocol", "Tcp"),
                    Map.entry("sourceIpRanges", Map.ofEntries(
                        Map.entry("endIP", "127.0.0.2"),
                        Map.entry("startIP", "127.0.0.1")
                    )),
                    Map.entry("sourcePortRanges",                     
                        Map.ofEntries(
                            Map.entry("end", 11),
                            Map.entry("start", 10)
                        ),
                        Map.ofEntries(
                            Map.entry("end", 21),
                            Map.entry("start", 20)
                        ))
                ),
                Map.ofEntries(
                    Map.entry("destinationIpRanges", Map.ofEntries(
                        Map.entry("endIP", "12.0.10.2"),
                        Map.entry("startIP", "12.0.10.1")
                    )),
                    Map.entry("destinationPortRanges", Map.ofEntries(
                        Map.entry("end", 52),
                        Map.entry("start", 51)
                    )),
                    Map.entry("markings", 2),
                    Map.entry("protocol", "Udp"),
                    Map.entry("sourceIpRanges", Map.ofEntries(
                        Map.entry("endIP", "12.0.0.2"),
                        Map.entry("startIP", "12.0.0.1")
                    )),
                    Map.entry("sourcePortRanges", Map.ofEntries(
                        Map.entry("end", 12),
                        Map.entry("start", 11)
                    ))
                ))
            .resourceGroupName("rg1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const dscpConfiguration = new azure_native.network.DscpConfiguration("dscpConfiguration", {
    dscpConfigurationName: "mydscpconfig",
    location: "eastus",
    qosDefinitionCollection: [
        {
            destinationIpRanges: [{
                endIP: "127.0.10.2",
                startIP: "127.0.10.1",
            }],
            destinationPortRanges: [{
                end: 15,
                start: 15,
            }],
            markings: [1],
            protocol: "Tcp",
            sourceIpRanges: [{
                endIP: "127.0.0.2",
                startIP: "127.0.0.1",
            }],
            sourcePortRanges: [
                {
                    end: 11,
                    start: 10,
                },
                {
                    end: 21,
                    start: 20,
                },
            ],
        },
        {
            destinationIpRanges: [{
                endIP: "12.0.10.2",
                startIP: "12.0.10.1",
            }],
            destinationPortRanges: [{
                end: 52,
                start: 51,
            }],
            markings: [2],
            protocol: "Udp",
            sourceIpRanges: [{
                endIP: "12.0.0.2",
                startIP: "12.0.0.1",
            }],
            sourcePortRanges: [{
                end: 12,
                start: 11,
            }],
        },
    ],
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

dscp_configuration = azure_native.network.DscpConfiguration("dscpConfiguration",
    dscp_configuration_name="mydscpconfig",
    location="eastus",
    qos_definition_collection=[
        {
            "destinationIpRanges": [azure_native.network.QosIpRangeArgs(
                end_ip="127.0.10.2",
                start_ip="127.0.10.1",
            )],
            "destinationPortRanges": [azure_native.network.QosPortRangeArgs(
                end=15,
                start=15,
            )],
            "markings": [1],
            "protocol": "Tcp",
            "sourceIpRanges": [azure_native.network.QosIpRangeArgs(
                end_ip="127.0.0.2",
                start_ip="127.0.0.1",
            )],
            "sourcePortRanges": [
                azure_native.network.QosPortRangeArgs(
                    end=11,
                    start=10,
                ),
                azure_native.network.QosPortRangeArgs(
                    end=21,
                    start=20,
                ),
            ],
        },
        {
            "destinationIpRanges": [azure_native.network.QosIpRangeArgs(
                end_ip="12.0.10.2",
                start_ip="12.0.10.1",
            )],
            "destinationPortRanges": [azure_native.network.QosPortRangeArgs(
                end=52,
                start=51,
            )],
            "markings": [2],
            "protocol": "Udp",
            "sourceIpRanges": [azure_native.network.QosIpRangeArgs(
                end_ip="12.0.0.2",
                start_ip="12.0.0.1",
            )],
            "sourcePortRanges": [azure_native.network.QosPortRangeArgs(
                end=12,
                start=11,
            )],
        },
    ],
    resource_group_name="rg1")

```

```yaml
resources:
  dscpConfiguration:
    type: azure-native:network:DscpConfiguration
    properties:
      dscpConfigurationName: mydscpconfig
      location: eastus
      qosDefinitionCollection:
        - destinationIpRanges:
            - endIP: 127.0.10.2
              startIP: 127.0.10.1
          destinationPortRanges:
            - end: 15
              start: 15
          markings:
            - 1
          protocol: Tcp
          sourceIpRanges:
            - endIP: 127.0.0.2
              startIP: 127.0.0.1
          sourcePortRanges:
            - end: 11
              start: 10
            - end: 21
              start: 20
        - destinationIpRanges:
            - endIP: 12.0.10.2
              startIP: 12.0.10.1
          destinationPortRanges:
            - end: 52
              start: 51
          markings:
            - 2
          protocol: Udp
          sourceIpRanges:
            - endIP: 12.0.0.2
              startIP: 12.0.0.1
          sourcePortRanges:
            - end: 12
              start: 11
      resourceGroupName: rg1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:DscpConfiguration mydscpConfig /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/dscpConfiguration/mydscpConfig 
```
