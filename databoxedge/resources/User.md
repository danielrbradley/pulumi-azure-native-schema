Represents a user who has access to one or more shares on the Data Box Edge/Gateway device.
API Version: 2022-03-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### UserPut
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var user = new AzureNative.DataBoxEdge.User("user", new()
    {
        DeviceName = "testedgedevice",
        EncryptedPassword = new AzureNative.DataBoxEdge.Inputs.AsymmetricEncryptedSecretArgs
        {
            EncryptionAlgorithm = "None",
            EncryptionCertThumbprint = "blah",
            Value = "<value>",
        },
        Name = "user1",
        ResourceGroupName = "GroupForEdgeAutomation",
        UserType = "Share",
    });

});


```

```go
package main

import (
	databoxedge "github.com/pulumi/pulumi-azure-native-sdk/databoxedge"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := databoxedge.NewUser(ctx, "user", &databoxedge.UserArgs{
			DeviceName: pulumi.String("testedgedevice"),
			EncryptedPassword: &databoxedge.AsymmetricEncryptedSecretArgs{
				EncryptionAlgorithm:      pulumi.String("None"),
				EncryptionCertThumbprint: pulumi.String("blah"),
				Value:                    pulumi.String("<value>"),
			},
			Name:              pulumi.String("user1"),
			ResourceGroupName: pulumi.String("GroupForEdgeAutomation"),
			UserType:          pulumi.String("Share"),
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
import com.pulumi.azurenative.databoxedge.User;
import com.pulumi.azurenative.databoxedge.UserArgs;
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
        var user = new User("user", UserArgs.builder()        
            .deviceName("testedgedevice")
            .encryptedPassword(Map.ofEntries(
                Map.entry("encryptionAlgorithm", "None"),
                Map.entry("encryptionCertThumbprint", "blah"),
                Map.entry("value", "<value>")
            ))
            .name("user1")
            .resourceGroupName("GroupForEdgeAutomation")
            .userType("Share")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const user = new azure_native.databoxedge.User("user", {
    deviceName: "testedgedevice",
    encryptedPassword: {
        encryptionAlgorithm: "None",
        encryptionCertThumbprint: "blah",
        value: "<value>",
    },
    name: "user1",
    resourceGroupName: "GroupForEdgeAutomation",
    userType: "Share",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

user = azure_native.databoxedge.User("user",
    device_name="testedgedevice",
    encrypted_password=azure_native.databoxedge.AsymmetricEncryptedSecretArgs(
        encryption_algorithm="None",
        encryption_cert_thumbprint="blah",
        value="<value>",
    ),
    name="user1",
    resource_group_name="GroupForEdgeAutomation",
    user_type="Share")

```

```yaml
resources:
  user:
    type: azure-native:databoxedge:User
    properties:
      deviceName: testedgedevice
      encryptedPassword:
        encryptionAlgorithm: None
        encryptionCertThumbprint: blah
        value: <value>
      name: user1
      resourceGroupName: GroupForEdgeAutomation
      userType: Share

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:databoxedge:User user1 /subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/GroupForEdgeAutomation/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/testedgedevice/users/user1 
```
