MAK key details.
API Version: 2019-09-16-preview.
Previous API Version: 2019-09-16-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateMultipleActivationKey
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var multipleActivationKey = new AzureNative.WindowsESU.MultipleActivationKey("multipleActivationKey", new()
    {
        AgreementNumber = "1a2b45ag",
        InstalledServerNumber = 100,
        IsEligible = true,
        Location = "East US",
        MultipleActivationKeyName = "server08-key-2019",
        OsType = "WindowsServer2008",
        ResourceGroupName = "testgr1",
        SupportType = "SupplementalServicing",
    });

});


```

```go
package main

import (
	windowsesu "github.com/pulumi/pulumi-azure-native-sdk/windowsesu"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := windowsesu.NewMultipleActivationKey(ctx, "multipleActivationKey", &windowsesu.MultipleActivationKeyArgs{
			AgreementNumber:           pulumi.String("1a2b45ag"),
			InstalledServerNumber:     pulumi.Int(100),
			IsEligible:                pulumi.Bool(true),
			Location:                  pulumi.String("East US"),
			MultipleActivationKeyName: pulumi.String("server08-key-2019"),
			OsType:                    pulumi.String("WindowsServer2008"),
			ResourceGroupName:         pulumi.String("testgr1"),
			SupportType:               pulumi.String("SupplementalServicing"),
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
import com.pulumi.azurenative.windowsesu.MultipleActivationKey;
import com.pulumi.azurenative.windowsesu.MultipleActivationKeyArgs;
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
        var multipleActivationKey = new MultipleActivationKey("multipleActivationKey", MultipleActivationKeyArgs.builder()        
            .agreementNumber("1a2b45ag")
            .installedServerNumber(100)
            .isEligible(true)
            .location("East US")
            .multipleActivationKeyName("server08-key-2019")
            .osType("WindowsServer2008")
            .resourceGroupName("testgr1")
            .supportType("SupplementalServicing")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const multipleActivationKey = new azure_native.windowsesu.MultipleActivationKey("multipleActivationKey", {
    agreementNumber: "1a2b45ag",
    installedServerNumber: 100,
    isEligible: true,
    location: "East US",
    multipleActivationKeyName: "server08-key-2019",
    osType: "WindowsServer2008",
    resourceGroupName: "testgr1",
    supportType: "SupplementalServicing",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

multiple_activation_key = azure_native.windowsesu.MultipleActivationKey("multipleActivationKey",
    agreement_number="1a2b45ag",
    installed_server_number=100,
    is_eligible=True,
    location="East US",
    multiple_activation_key_name="server08-key-2019",
    os_type="WindowsServer2008",
    resource_group_name="testgr1",
    support_type="SupplementalServicing")

```

```yaml
resources:
  multipleActivationKey:
    type: azure-native:windowsesu:MultipleActivationKey
    properties:
      agreementNumber: 1a2b45ag
      installedServerNumber: 100
      isEligible: true
      location: East US
      multipleActivationKeyName: server08-key-2019
      osType: WindowsServer2008
      resourceGroupName: testgr1
      supportType: SupplementalServicing

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:windowsesu:MultipleActivationKey server08-key-2019 /subscriptions/fd3c3665-1729-4b7b-9a38-238e83b0f98b/resourceGroups/testgr1/providers/Microsoft.WindowsESU/multipleActivationKeys/server08-key-2019 
```
