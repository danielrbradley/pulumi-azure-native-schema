The Collection data structure.
API Version: 2022-09-01.
Previous API Version: 2021-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CreatePrivateStoreCollection
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateStoreCollection = new AzureNative.Marketplace.PrivateStoreCollection("privateStoreCollection", new()
    {
        AllSubscriptions = false,
        Claim = "",
        CollectionId = "d0f5aa2c-ecc3-4d87-906a-f8c486dcc4f1",
        CollectionName = "Test Collection",
        PrivateStoreId = "a0e28e55-90c4-41d8-8e34-bb7ef7775406",
        SubscriptionsList = new[]
        {
            "b340914e-353d-453a-85fb-8f9b65b51f91",
            "f2baa04d-5bfc-461b-b6d8-61b403c9ec48",
        },
    });

});


```

```go
package main

import (
	marketplace "github.com/pulumi/pulumi-azure-native-sdk/marketplace"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := marketplace.NewPrivateStoreCollection(ctx, "privateStoreCollection", &marketplace.PrivateStoreCollectionArgs{
			AllSubscriptions: pulumi.Bool(false),
			Claim:            pulumi.String(""),
			CollectionId:     pulumi.String("d0f5aa2c-ecc3-4d87-906a-f8c486dcc4f1"),
			CollectionName:   pulumi.String("Test Collection"),
			PrivateStoreId:   pulumi.String("a0e28e55-90c4-41d8-8e34-bb7ef7775406"),
			SubscriptionsList: pulumi.StringArray{
				pulumi.String("b340914e-353d-453a-85fb-8f9b65b51f91"),
				pulumi.String("f2baa04d-5bfc-461b-b6d8-61b403c9ec48"),
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
import com.pulumi.azurenative.marketplace.PrivateStoreCollection;
import com.pulumi.azurenative.marketplace.PrivateStoreCollectionArgs;
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
        var privateStoreCollection = new PrivateStoreCollection("privateStoreCollection", PrivateStoreCollectionArgs.builder()        
            .allSubscriptions(false)
            .claim("")
            .collectionId("d0f5aa2c-ecc3-4d87-906a-f8c486dcc4f1")
            .collectionName("Test Collection")
            .privateStoreId("a0e28e55-90c4-41d8-8e34-bb7ef7775406")
            .subscriptionsList(            
                "b340914e-353d-453a-85fb-8f9b65b51f91",
                "f2baa04d-5bfc-461b-b6d8-61b403c9ec48")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateStoreCollection = new azure_native.marketplace.PrivateStoreCollection("privateStoreCollection", {
    allSubscriptions: false,
    claim: "",
    collectionId: "d0f5aa2c-ecc3-4d87-906a-f8c486dcc4f1",
    collectionName: "Test Collection",
    privateStoreId: "a0e28e55-90c4-41d8-8e34-bb7ef7775406",
    subscriptionsList: [
        "b340914e-353d-453a-85fb-8f9b65b51f91",
        "f2baa04d-5bfc-461b-b6d8-61b403c9ec48",
    ],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_store_collection = azure_native.marketplace.PrivateStoreCollection("privateStoreCollection",
    all_subscriptions=False,
    claim="",
    collection_id="d0f5aa2c-ecc3-4d87-906a-f8c486dcc4f1",
    collection_name="Test Collection",
    private_store_id="a0e28e55-90c4-41d8-8e34-bb7ef7775406",
    subscriptions_list=[
        "b340914e-353d-453a-85fb-8f9b65b51f91",
        "f2baa04d-5bfc-461b-b6d8-61b403c9ec48",
    ])

```

```yaml
resources:
  privateStoreCollection:
    type: azure-native:marketplace:PrivateStoreCollection
    properties:
      allSubscriptions: false
      claim:
      collectionId: d0f5aa2c-ecc3-4d87-906a-f8c486dcc4f1
      collectionName: Test Collection
      privateStoreId: a0e28e55-90c4-41d8-8e34-bb7ef7775406
      subscriptionsList:
        - b340914e-353d-453a-85fb-8f9b65b51f91
        - f2baa04d-5bfc-461b-b6d8-61b403c9ec48

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:marketplace:PrivateStoreCollection d0f5aa2c-ecc3-4d87-906a-f8c486dcc4f1 providers/Microsoft.Marketplace/privateStores/a0e28e55-90c4-41d8-8e34-bb7ef7775406/collections/d0f5aa2c-ecc3-4d87-906a-f8c486dcc4f1 
```
