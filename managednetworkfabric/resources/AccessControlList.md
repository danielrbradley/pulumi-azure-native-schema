The AccessControlList resource definition.
API Version: 2023-02-01-preview.
Previous API Version: 2023-02-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### AccessControlLists_Create_MinimumSet_Gen
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var accessControlList = new AzureNative.ManagedNetworkFabric.AccessControlList("accessControlList", new()
    {
        AccessControlListName = "aclOne",
        AddressFamily = "ipv4",
        Conditions = new[]
        {
            new AzureNative.ManagedNetworkFabric.Inputs.AccessControlListPropertiesConditionsArgs
            {
                Action = "allow",
                DestinationAddress = "1.1.1.1",
                DestinationPort = "21",
                Protocol = 6,
                SequenceNumber = 3,
                SourceAddress = "2.2.2.2",
                SourcePort = "65000",
            },
        },
        Location = "EastUs",
        ResourceGroupName = "resourceGroupName",
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
		_, err := managednetworkfabric.NewAccessControlList(ctx, "accessControlList", &managednetworkfabric.AccessControlListArgs{
			AccessControlListName: pulumi.String("aclOne"),
			AddressFamily:         pulumi.String("ipv4"),
			Conditions: []managednetworkfabric.AccessControlListPropertiesConditionsArgs{
				{
					Action:             pulumi.String("allow"),
					DestinationAddress: pulumi.String("1.1.1.1"),
					DestinationPort:    pulumi.String("21"),
					Protocol:           pulumi.Int(6),
					SequenceNumber:     pulumi.Int(3),
					SourceAddress:      pulumi.String("2.2.2.2"),
					SourcePort:         pulumi.String("65000"),
				},
			},
			Location:          pulumi.String("EastUs"),
			ResourceGroupName: pulumi.String("resourceGroupName"),
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
import com.pulumi.azurenative.managednetworkfabric.AccessControlList;
import com.pulumi.azurenative.managednetworkfabric.AccessControlListArgs;
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
        var accessControlList = new AccessControlList("accessControlList", AccessControlListArgs.builder()        
            .accessControlListName("aclOne")
            .addressFamily("ipv4")
            .conditions(Map.ofEntries(
                Map.entry("action", "allow"),
                Map.entry("destinationAddress", "1.1.1.1"),
                Map.entry("destinationPort", "21"),
                Map.entry("protocol", 6),
                Map.entry("sequenceNumber", 3),
                Map.entry("sourceAddress", "2.2.2.2"),
                Map.entry("sourcePort", "65000")
            ))
            .location("EastUs")
            .resourceGroupName("resourceGroupName")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const accessControlList = new azure_native.managednetworkfabric.AccessControlList("accessControlList", {
    accessControlListName: "aclOne",
    addressFamily: "ipv4",
    conditions: [{
        action: "allow",
        destinationAddress: "1.1.1.1",
        destinationPort: "21",
        protocol: 6,
        sequenceNumber: 3,
        sourceAddress: "2.2.2.2",
        sourcePort: "65000",
    }],
    location: "EastUs",
    resourceGroupName: "resourceGroupName",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

access_control_list = azure_native.managednetworkfabric.AccessControlList("accessControlList",
    access_control_list_name="aclOne",
    address_family="ipv4",
    conditions=[azure_native.managednetworkfabric.AccessControlListPropertiesConditionsArgs(
        action="allow",
        destination_address="1.1.1.1",
        destination_port="21",
        protocol=6,
        sequence_number=3,
        source_address="2.2.2.2",
        source_port="65000",
    )],
    location="EastUs",
    resource_group_name="resourceGroupName")

```

```yaml
resources:
  accessControlList:
    type: azure-native:managednetworkfabric:AccessControlList
    properties:
      accessControlListName: aclOne
      addressFamily: ipv4
      conditions:
        - action: allow
          destinationAddress: 1.1.1.1
          destinationPort: '21'
          protocol: 6
          sequenceNumber: 3
          sourceAddress: 2.2.2.2
          sourcePort: '65000'
      location: EastUs
      resourceGroupName: resourceGroupName

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:managednetworkfabric:AccessControlList aaaaaaaaaaaaaa aaaaaaaaaaaaaaaaaaaaaaaaa 
```
