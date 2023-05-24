Represents an instance of a DNC controller.
API Version: 2021-03-15.
Previous API Version: 2021-03-15. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create controller
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var controllerDetails = new AzureNative.DelegatedNetwork.ControllerDetails("controllerDetails", new()
    {
        Location = "West US",
        ResourceGroupName = "TestRG",
        ResourceName = "testcontroller",
    });

});


```

```go
package main

import (
	delegatednetwork "github.com/pulumi/pulumi-azure-native-sdk/delegatednetwork"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := delegatednetwork.NewControllerDetails(ctx, "controllerDetails", &delegatednetwork.ControllerDetailsArgs{
			Location:          pulumi.String("West US"),
			ResourceGroupName: pulumi.String("TestRG"),
			ResourceName:      pulumi.String("testcontroller"),
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
import com.pulumi.azurenative.delegatednetwork.ControllerDetails;
import com.pulumi.azurenative.delegatednetwork.ControllerDetailsArgs;
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
        var controllerDetails = new ControllerDetails("controllerDetails", ControllerDetailsArgs.builder()        
            .location("West US")
            .resourceGroupName("TestRG")
            .resourceName("testcontroller")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const controllerDetails = new azure_native.delegatednetwork.ControllerDetails("controllerDetails", {
    location: "West US",
    resourceGroupName: "TestRG",
    resourceName: "testcontroller",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

controller_details = azure_native.delegatednetwork.ControllerDetails("controllerDetails",
    location="West US",
    resource_group_name="TestRG",
    resource_name_="testcontroller")

```

```yaml
resources:
  controllerDetails:
    type: azure-native:delegatednetwork:ControllerDetails
    properties:
      location: West US
      resourceGroupName: TestRG
      resourceName: testcontroller

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:delegatednetwork:ControllerDetails testcontroller /subscriptions/613192d7-503f-477a-9cfe-4efc3ee2bd60/resourceGroups/TestRG/providers/Microsoft.DelegatedNetwork/controller/testcontroller 
```
