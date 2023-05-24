Payload of the transaction node which is the request/response of the resource provider.
API Version: 2018-06-01-preview.
Previous API Version: 2018-06-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### TransactionNodes_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var transactionNode = new AzureNative.Blockchain.TransactionNode("transactionNode", new()
    {
        BlockchainMemberName = "contosemember1",
        Location = "southeastasia",
        Password = "<password>",
        ResourceGroupName = "mygroup",
        TransactionNodeName = "txnode2",
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
		_, err := blockchain.NewTransactionNode(ctx, "transactionNode", &blockchain.TransactionNodeArgs{
			BlockchainMemberName: pulumi.String("contosemember1"),
			Location:             pulumi.String("southeastasia"),
			Password:             pulumi.String("<password>"),
			ResourceGroupName:    pulumi.String("mygroup"),
			TransactionNodeName:  pulumi.String("txnode2"),
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
import com.pulumi.azurenative.blockchain.TransactionNode;
import com.pulumi.azurenative.blockchain.TransactionNodeArgs;
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
        var transactionNode = new TransactionNode("transactionNode", TransactionNodeArgs.builder()        
            .blockchainMemberName("contosemember1")
            .location("southeastasia")
            .password("<password>")
            .resourceGroupName("mygroup")
            .transactionNodeName("txnode2")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const transactionNode = new azure_native.blockchain.TransactionNode("transactionNode", {
    blockchainMemberName: "contosemember1",
    location: "southeastasia",
    password: "<password>",
    resourceGroupName: "mygroup",
    transactionNodeName: "txnode2",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

transaction_node = azure_native.blockchain.TransactionNode("transactionNode",
    blockchain_member_name="contosemember1",
    location="southeastasia",
    password="<password>",
    resource_group_name="mygroup",
    transaction_node_name="txnode2")

```

```yaml
resources:
  transactionNode:
    type: azure-native:blockchain:TransactionNode
    properties:
      blockchainMemberName: contosemember1
      location: southeastasia
      password: <password>
      resourceGroupName: mygroup
      transactionNodeName: txnode2

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:blockchain:TransactionNode txnode2 /subscriptions/51766542-3ed7-4a72-a187-0c8ab644ddab/resourceGroups/mygroup/providers/Microsoft.Blockchain/blockchainMembers/contosemember1/transactionNodes/txnode2 
```
