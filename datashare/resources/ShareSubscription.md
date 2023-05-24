A share subscription data transfer object.
API Version: 2021-08-01.
Previous API Version: 2020-09-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ShareSubscriptions_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var shareSubscription = new AzureNative.DataShare.ShareSubscription("shareSubscription", new()
    {
        AccountName = "Account1",
        ExpirationDate = "2020-08-26T22:33:24.5785265Z",
        InvitationId = "12345678-1234-1234-12345678abd",
        ResourceGroupName = "SampleResourceGroup",
        ShareSubscriptionName = "ShareSubscription1",
        SourceShareLocation = "eastus2",
    });

});


```

```go
package main

import (
	datashare "github.com/pulumi/pulumi-azure-native-sdk/datashare"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := datashare.NewShareSubscription(ctx, "shareSubscription", &datashare.ShareSubscriptionArgs{
			AccountName:           pulumi.String("Account1"),
			ExpirationDate:        pulumi.String("2020-08-26T22:33:24.5785265Z"),
			InvitationId:          pulumi.String("12345678-1234-1234-12345678abd"),
			ResourceGroupName:     pulumi.String("SampleResourceGroup"),
			ShareSubscriptionName: pulumi.String("ShareSubscription1"),
			SourceShareLocation:   pulumi.String("eastus2"),
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
import com.pulumi.azurenative.datashare.ShareSubscription;
import com.pulumi.azurenative.datashare.ShareSubscriptionArgs;
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
        var shareSubscription = new ShareSubscription("shareSubscription", ShareSubscriptionArgs.builder()        
            .accountName("Account1")
            .expirationDate("2020-08-26T22:33:24.5785265Z")
            .invitationId("12345678-1234-1234-12345678abd")
            .resourceGroupName("SampleResourceGroup")
            .shareSubscriptionName("ShareSubscription1")
            .sourceShareLocation("eastus2")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const shareSubscription = new azure_native.datashare.ShareSubscription("shareSubscription", {
    accountName: "Account1",
    expirationDate: "2020-08-26T22:33:24.5785265Z",
    invitationId: "12345678-1234-1234-12345678abd",
    resourceGroupName: "SampleResourceGroup",
    shareSubscriptionName: "ShareSubscription1",
    sourceShareLocation: "eastus2",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

share_subscription = azure_native.datashare.ShareSubscription("shareSubscription",
    account_name="Account1",
    expiration_date="2020-08-26T22:33:24.5785265Z",
    invitation_id="12345678-1234-1234-12345678abd",
    resource_group_name="SampleResourceGroup",
    share_subscription_name="ShareSubscription1",
    source_share_location="eastus2")

```

```yaml
resources:
  shareSubscription:
    type: azure-native:datashare:ShareSubscription
    properties:
      accountName: Account1
      expirationDate: 2020-08-26T22:33:24.5785265Z
      invitationId: 12345678-1234-1234-12345678abd
      resourceGroupName: SampleResourceGroup
      shareSubscriptionName: ShareSubscription1
      sourceShareLocation: eastus2

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:datashare:ShareSubscription ShareSubscription1 /subscriptions/433a8dfd-e5d5-4e77-ad86-90acdc75eb1a/resourceGroups/SampleResourceGroup/providers/Microsoft.DataShare/accounts/Account1/sharesubscriptions/ShareSubscription1 
```
