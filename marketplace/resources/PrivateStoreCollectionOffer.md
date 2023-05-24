The privateStore offer data structure.
API Version: 2022-09-01.
Previous API Version: 2021-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### PrivateStoreOffer_update
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateStoreCollectionOffer = new AzureNative.Marketplace.PrivateStoreCollectionOffer("privateStoreCollectionOffer", new()
    {
        CollectionId = "56a1a02d-8cf8-45df-bf37-d5f7120fcb3d",
        ETag = "\"9301f4fd-0000-0100-0000-5e248b350666\"",
        OfferId = "marketplacetestthirdparty.md-test-third-party-2",
        PrivateStoreId = "a0e28e55-90c4-41d8-8e34-bb7ef7775406",
        SpecificPlanIdsLimitation = new[]
        {
            "0001",
            "0002",
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
		_, err := marketplace.NewPrivateStoreCollectionOffer(ctx, "privateStoreCollectionOffer", &marketplace.PrivateStoreCollectionOfferArgs{
			CollectionId:   pulumi.String("56a1a02d-8cf8-45df-bf37-d5f7120fcb3d"),
			ETag:           pulumi.String("\"9301f4fd-0000-0100-0000-5e248b350666\""),
			OfferId:        pulumi.String("marketplacetestthirdparty.md-test-third-party-2"),
			PrivateStoreId: pulumi.String("a0e28e55-90c4-41d8-8e34-bb7ef7775406"),
			SpecificPlanIdsLimitation: pulumi.StringArray{
				pulumi.String("0001"),
				pulumi.String("0002"),
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
import com.pulumi.azurenative.marketplace.PrivateStoreCollectionOffer;
import com.pulumi.azurenative.marketplace.PrivateStoreCollectionOfferArgs;
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
        var privateStoreCollectionOffer = new PrivateStoreCollectionOffer("privateStoreCollectionOffer", PrivateStoreCollectionOfferArgs.builder()        
            .collectionId("56a1a02d-8cf8-45df-bf37-d5f7120fcb3d")
            .eTag("\"9301f4fd-0000-0100-0000-5e248b350666\"")
            .offerId("marketplacetestthirdparty.md-test-third-party-2")
            .privateStoreId("a0e28e55-90c4-41d8-8e34-bb7ef7775406")
            .specificPlanIdsLimitation(            
                "0001",
                "0002")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateStoreCollectionOffer = new azure_native.marketplace.PrivateStoreCollectionOffer("privateStoreCollectionOffer", {
    collectionId: "56a1a02d-8cf8-45df-bf37-d5f7120fcb3d",
    eTag: "\"9301f4fd-0000-0100-0000-5e248b350666\"",
    offerId: "marketplacetestthirdparty.md-test-third-party-2",
    privateStoreId: "a0e28e55-90c4-41d8-8e34-bb7ef7775406",
    specificPlanIdsLimitation: [
        "0001",
        "0002",
    ],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_store_collection_offer = azure_native.marketplace.PrivateStoreCollectionOffer("privateStoreCollectionOffer",
    collection_id="56a1a02d-8cf8-45df-bf37-d5f7120fcb3d",
    e_tag="\"9301f4fd-0000-0100-0000-5e248b350666\"",
    offer_id="marketplacetestthirdparty.md-test-third-party-2",
    private_store_id="a0e28e55-90c4-41d8-8e34-bb7ef7775406",
    specific_plan_ids_limitation=[
        "0001",
        "0002",
    ])

```

```yaml
resources:
  privateStoreCollectionOffer:
    type: azure-native:marketplace:PrivateStoreCollectionOffer
    properties:
      collectionId: 56a1a02d-8cf8-45df-bf37-d5f7120fcb3d
      eTag: '"9301f4fd-0000-0100-0000-5e248b350666"'
      offerId: marketplacetestthirdparty.md-test-third-party-2
      privateStoreId: a0e28e55-90c4-41d8-8e34-bb7ef7775406
      specificPlanIdsLimitation:
        - '0001'
        - '0002'

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:marketplace:PrivateStoreCollectionOffer marketplacetestthirdparty.md-test-third-party-2 /providers/Microsoft.Marketplace/privateStores/a0e28e55-90c4-41d8-8e34-bb7ef7775406/collections/56a1a02d-8cf8-45df-bf37-d5f7120fcb3d/offers/marketplacetestthirdparty.md-test-third-party-2 
```
