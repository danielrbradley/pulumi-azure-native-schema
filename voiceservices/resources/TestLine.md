A TestLine resource
API Version: 2023-01-31.
Previous API Version: 2022-12-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateTestLineResource
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var testLine = new AzureNative.VoiceServices.TestLine("testLine", new()
    {
        CommunicationsGatewayName = "myname",
        Location = "useast",
        PhoneNumber = "+1-555-1234",
        Purpose = "Automated",
        ResourceGroupName = "testrg",
        TestLineName = "myline",
    });

});


```

```go
package main

import (
	voiceservices "github.com/pulumi/pulumi-azure-native-sdk/voiceservices"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := voiceservices.NewTestLine(ctx, "testLine", &voiceservices.TestLineArgs{
			CommunicationsGatewayName: pulumi.String("myname"),
			Location:                  pulumi.String("useast"),
			PhoneNumber:               pulumi.String("+1-555-1234"),
			Purpose:                   pulumi.String("Automated"),
			ResourceGroupName:         pulumi.String("testrg"),
			TestLineName:              pulumi.String("myline"),
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
import com.pulumi.azurenative.voiceservices.TestLine;
import com.pulumi.azurenative.voiceservices.TestLineArgs;
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
        var testLine = new TestLine("testLine", TestLineArgs.builder()        
            .communicationsGatewayName("myname")
            .location("useast")
            .phoneNumber("+1-555-1234")
            .purpose("Automated")
            .resourceGroupName("testrg")
            .testLineName("myline")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const testLine = new azure_native.voiceservices.TestLine("testLine", {
    communicationsGatewayName: "myname",
    location: "useast",
    phoneNumber: "+1-555-1234",
    purpose: "Automated",
    resourceGroupName: "testrg",
    testLineName: "myline",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

test_line = azure_native.voiceservices.TestLine("testLine",
    communications_gateway_name="myname",
    location="useast",
    phone_number="+1-555-1234",
    purpose="Automated",
    resource_group_name="testrg",
    test_line_name="myline")

```

```yaml
resources:
  testLine:
    type: azure-native:voiceservices:TestLine
    properties:
      communicationsGatewayName: myname
      location: useast
      phoneNumber: +1-555-1234
      purpose: Automated
      resourceGroupName: testrg
      testLineName: myline

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:voiceservices:TestLine myline /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/testrg/providers/Microsoft.VoiceServices/communicationsGateways/myname/TestLines/myline 
```
