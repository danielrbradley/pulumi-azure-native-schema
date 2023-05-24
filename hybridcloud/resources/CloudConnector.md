Cloud Connector resource.
API Version: 2023-01-01-preview.
Previous API Version: 2023-01-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a Cloud Connector
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var cloudConnector = new AzureNative.HybridCloud.CloudConnector("cloudConnector", new()
    {
        AccountId = "123456789012",
        CloudConnectorName = "123456789012",
        CloudType = "AWS",
        Location = "West US",
        ResourceGroupName = "demo-rg",
    });

});


```

```go
package main

import (
	hybridcloud "github.com/pulumi/pulumi-azure-native-sdk/hybridcloud"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := hybridcloud.NewCloudConnector(ctx, "cloudConnector", &hybridcloud.CloudConnectorArgs{
			AccountId:          pulumi.String("123456789012"),
			CloudConnectorName: pulumi.String("123456789012"),
			CloudType:          pulumi.String("AWS"),
			Location:           pulumi.String("West US"),
			ResourceGroupName:  pulumi.String("demo-rg"),
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
import com.pulumi.azurenative.hybridcloud.CloudConnector;
import com.pulumi.azurenative.hybridcloud.CloudConnectorArgs;
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
        var cloudConnector = new CloudConnector("cloudConnector", CloudConnectorArgs.builder()        
            .accountId("123456789012")
            .cloudConnectorName("123456789012")
            .cloudType("AWS")
            .location("West US")
            .resourceGroupName("demo-rg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const cloudConnector = new azure_native.hybridcloud.CloudConnector("cloudConnector", {
    accountId: "123456789012",
    cloudConnectorName: "123456789012",
    cloudType: "AWS",
    location: "West US",
    resourceGroupName: "demo-rg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

cloud_connector = azure_native.hybridcloud.CloudConnector("cloudConnector",
    account_id="123456789012",
    cloud_connector_name="123456789012",
    cloud_type="AWS",
    location="West US",
    resource_group_name="demo-rg")

```

```yaml
resources:
  cloudConnector:
    type: azure-native:hybridcloud:CloudConnector
    properties:
      accountId: '123456789012'
      cloudConnectorName: '123456789012'
      cloudType: AWS
      location: West US
      resourceGroupName: demo-rg

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:hybridcloud:CloudConnector 123456789012 /subscriptions/subid/resourceGroups/demo-rg/providers/Microsoft.HybridCloud/cloudConnectors/123456789012 
```
