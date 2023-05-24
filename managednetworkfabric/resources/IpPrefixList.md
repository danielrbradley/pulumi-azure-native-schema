The IpPrefixList resource definition.
API Version: 2023-02-01-preview.
Previous API Version: 2023-02-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### IpPrefixLists_Create_MinimumSet_Gen
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var ipPrefixList = new AzureNative.ManagedNetworkFabric.IpPrefixList("ipPrefixList", new()
    {
        Action = "allow",
        IpPrefixListName = "IpPrefixList1",
        Location = "EastUS",
        NetworkAddress = "1.1.1.0/24",
        ResourceGroupName = "resourceGroupName",
        SequenceNumber = 19,
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
		_, err := managednetworkfabric.NewIpPrefixList(ctx, "ipPrefixList", &managednetworkfabric.IpPrefixListArgs{
			Action:            pulumi.String("allow"),
			IpPrefixListName:  pulumi.String("IpPrefixList1"),
			Location:          pulumi.String("EastUS"),
			NetworkAddress:    pulumi.String("1.1.1.0/24"),
			ResourceGroupName: pulumi.String("resourceGroupName"),
			SequenceNumber:    pulumi.Int(19),
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
import com.pulumi.azurenative.managednetworkfabric.IpPrefixList;
import com.pulumi.azurenative.managednetworkfabric.IpPrefixListArgs;
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
        var ipPrefixList = new IpPrefixList("ipPrefixList", IpPrefixListArgs.builder()        
            .action("allow")
            .ipPrefixListName("IpPrefixList1")
            .location("EastUS")
            .networkAddress("1.1.1.0/24")
            .resourceGroupName("resourceGroupName")
            .sequenceNumber(19)
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const ipPrefixList = new azure_native.managednetworkfabric.IpPrefixList("ipPrefixList", {
    action: "allow",
    ipPrefixListName: "IpPrefixList1",
    location: "EastUS",
    networkAddress: "1.1.1.0/24",
    resourceGroupName: "resourceGroupName",
    sequenceNumber: 19,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

ip_prefix_list = azure_native.managednetworkfabric.IpPrefixList("ipPrefixList",
    action="allow",
    ip_prefix_list_name="IpPrefixList1",
    location="EastUS",
    network_address="1.1.1.0/24",
    resource_group_name="resourceGroupName",
    sequence_number=19)

```

```yaml
resources:
  ipPrefixList:
    type: azure-native:managednetworkfabric:IpPrefixList
    properties:
      action: allow
      ipPrefixListName: IpPrefixList1
      location: EastUS
      networkAddress: 1.1.1.0/24
      resourceGroupName: resourceGroupName
      sequenceNumber: 19

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:managednetworkfabric:IpPrefixList myresource1 resourceId 
```
