The DataManager resource.
API Version: 2019-06-01.
Previous API Version: 2019-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### DataManagers_CreatePUT41
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var dataManager = new AzureNative.HybridData.DataManager("dataManager", new()
    {
        DataManagerName = "TestAzureSDKOperations",
        Location = "westus",
        ResourceGroupName = "ResourceGroupForSDKTest",
    });

});


```

```go
package main

import (
	hybriddata "github.com/pulumi/pulumi-azure-native-sdk/hybriddata"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := hybriddata.NewDataManager(ctx, "dataManager", &hybriddata.DataManagerArgs{
			DataManagerName:   pulumi.String("TestAzureSDKOperations"),
			Location:          pulumi.String("westus"),
			ResourceGroupName: pulumi.String("ResourceGroupForSDKTest"),
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
import com.pulumi.azurenative.hybriddata.DataManager;
import com.pulumi.azurenative.hybriddata.DataManagerArgs;
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
        var dataManager = new DataManager("dataManager", DataManagerArgs.builder()        
            .dataManagerName("TestAzureSDKOperations")
            .location("westus")
            .resourceGroupName("ResourceGroupForSDKTest")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const dataManager = new azure_native.hybriddata.DataManager("dataManager", {
    dataManagerName: "TestAzureSDKOperations",
    location: "westus",
    resourceGroupName: "ResourceGroupForSDKTest",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

data_manager = azure_native.hybriddata.DataManager("dataManager",
    data_manager_name="TestAzureSDKOperations",
    location="westus",
    resource_group_name="ResourceGroupForSDKTest")

```

```yaml
resources:
  dataManager:
    type: azure-native:hybriddata:DataManager
    properties:
      dataManagerName: TestAzureSDKOperations
      location: westus
      resourceGroupName: ResourceGroupForSDKTest

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:hybriddata:DataManager TestAzureSDKOperations /subscriptions/6e0219f5-327a-4365-904f-05eed4227ad7/resourceGroups/ResourceGroupForSDKTest/providers/Microsoft.HybridData/dataManagers/TestAzureSDKOperations 
```
