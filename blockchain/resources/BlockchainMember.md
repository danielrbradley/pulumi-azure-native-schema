Payload of the blockchain member which is exposed in the request/response of the resource provider.
API Version: 2018-06-01-preview.
Previous API Version: 2018-06-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### BlockchainMembers_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var blockchainMember = new AzureNative.Blockchain.BlockchainMember("blockchainMember", new()
    {
        BlockchainMemberName = "contosemember1",
        Consortium = "ContoseConsortium",
        ConsortiumManagementAccountPassword = "<consortiumManagementAccountPassword>",
        Location = "southeastasia",
        Password = "<password>",
        Protocol = "Quorum",
        ResourceGroupName = "mygroup",
        ValidatorNodesSku = new AzureNative.Blockchain.Inputs.BlockchainMemberNodesSkuArgs
        {
            Capacity = 2,
        },
    });

});


```

```go
package main

import (
	blockchain "github.com/pulumi/pulumi-azure-native-sdk/blockchain"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := blockchain.NewBlockchainMember(ctx, "blockchainMember", &blockchain.BlockchainMemberArgs{
			BlockchainMemberName:                pulumi.String("contosemember1"),
			Consortium:                          pulumi.String("ContoseConsortium"),
			ConsortiumManagementAccountPassword: pulumi.String("<consortiumManagementAccountPassword>"),
			Location:                            pulumi.String("southeastasia"),
			Password:                            pulumi.String("<password>"),
			Protocol:                            pulumi.String("Quorum"),
			ResourceGroupName:                   pulumi.String("mygroup"),
			ValidatorNodesSku: &blockchain.BlockchainMemberNodesSkuArgs{
				Capacity: pulumi.Int(2),
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
import com.pulumi.azurenative.blockchain.BlockchainMember;
import com.pulumi.azurenative.blockchain.BlockchainMemberArgs;
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
        var blockchainMember = new BlockchainMember("blockchainMember", BlockchainMemberArgs.builder()        
            .blockchainMemberName("contosemember1")
            .consortium("ContoseConsortium")
            .consortiumManagementAccountPassword("<consortiumManagementAccountPassword>")
            .location("southeastasia")
            .password("<password>")
            .protocol("Quorum")
            .resourceGroupName("mygroup")
            .validatorNodesSku(Map.of("capacity", 2))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const blockchainMember = new azure_native.blockchain.BlockchainMember("blockchainMember", {
    blockchainMemberName: "contosemember1",
    consortium: "ContoseConsortium",
    consortiumManagementAccountPassword: "<consortiumManagementAccountPassword>",
    location: "southeastasia",
    password: "<password>",
    protocol: "Quorum",
    resourceGroupName: "mygroup",
    validatorNodesSku: {
        capacity: 2,
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

blockchain_member = azure_native.blockchain.BlockchainMember("blockchainMember",
    blockchain_member_name="contosemember1",
    consortium="ContoseConsortium",
    consortium_management_account_password="<consortiumManagementAccountPassword>",
    location="southeastasia",
    password="<password>",
    protocol="Quorum",
    resource_group_name="mygroup",
    validator_nodes_sku=azure_native.blockchain.BlockchainMemberNodesSkuArgs(
        capacity=2,
    ))

```

```yaml
resources:
  blockchainMember:
    type: azure-native:blockchain:BlockchainMember
    properties:
      blockchainMemberName: contosemember1
      consortium: ContoseConsortium
      consortiumManagementAccountPassword: <consortiumManagementAccountPassword>
      location: southeastasia
      password: <password>
      protocol: Quorum
      resourceGroupName: mygroup
      validatorNodesSku:
        capacity: 2

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:blockchain:BlockchainMember contosemember1 /subscriptions/51766542-3ed7-4a72-a187-0c8ab644ddab/resourceGroups/mygroup/providers/Microsoft.Blockchain/blockchainMembers/contosemember1 
```
