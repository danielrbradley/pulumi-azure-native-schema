A Invitation data transfer object.
API Version: 2021-08-01.
Previous API Version: 2020-09-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Invitations_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var invitation = new AzureNative.DataShare.Invitation("invitation", new()
    {
        AccountName = "Account1",
        ExpirationDate = "2020-08-26T22:33:24.5785265Z",
        InvitationName = "Invitation1",
        ResourceGroupName = "SampleResourceGroup",
        ShareName = "Share1",
        TargetEmail = "receiver@microsoft.com",
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
		_, err := datashare.NewInvitation(ctx, "invitation", &datashare.InvitationArgs{
			AccountName:       pulumi.String("Account1"),
			ExpirationDate:    pulumi.String("2020-08-26T22:33:24.5785265Z"),
			InvitationName:    pulumi.String("Invitation1"),
			ResourceGroupName: pulumi.String("SampleResourceGroup"),
			ShareName:         pulumi.String("Share1"),
			TargetEmail:       pulumi.String("receiver@microsoft.com"),
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
import com.pulumi.azurenative.datashare.Invitation;
import com.pulumi.azurenative.datashare.InvitationArgs;
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
        var invitation = new Invitation("invitation", InvitationArgs.builder()        
            .accountName("Account1")
            .expirationDate("2020-08-26T22:33:24.5785265Z")
            .invitationName("Invitation1")
            .resourceGroupName("SampleResourceGroup")
            .shareName("Share1")
            .targetEmail("receiver@microsoft.com")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const invitation = new azure_native.datashare.Invitation("invitation", {
    accountName: "Account1",
    expirationDate: "2020-08-26T22:33:24.5785265Z",
    invitationName: "Invitation1",
    resourceGroupName: "SampleResourceGroup",
    shareName: "Share1",
    targetEmail: "receiver@microsoft.com",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

invitation = azure_native.datashare.Invitation("invitation",
    account_name="Account1",
    expiration_date="2020-08-26T22:33:24.5785265Z",
    invitation_name="Invitation1",
    resource_group_name="SampleResourceGroup",
    share_name="Share1",
    target_email="receiver@microsoft.com")

```

```yaml
resources:
  invitation:
    type: azure-native:datashare:Invitation
    properties:
      accountName: Account1
      expirationDate: 2020-08-26T22:33:24.5785265Z
      invitationName: Invitation1
      resourceGroupName: SampleResourceGroup
      shareName: Share1
      targetEmail: receiver@microsoft.com

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:datashare:Invitation Invitation1 /subscriptions/433a8dfd-e5d5-4e77-ad86-90acdc75eb1a/resourceGroups/SampleResourceGroup/providers/Microsoft.DataShare/accounts/Account1/shares/Share1/invitations/Invitation1 
```
