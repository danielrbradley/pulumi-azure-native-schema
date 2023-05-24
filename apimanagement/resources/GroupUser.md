User details.
API Version: 2022-08-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ApiManagementCreateGroupUser
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var groupUser = new AzureNative.ApiManagement.GroupUser("groupUser", new()
    {
        GroupId = "tempgroup",
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
        UserId = "59307d350af58404d8a26300",
    });

});


```

```go
package main

import (
	apimanagement "github.com/pulumi/pulumi-azure-native-sdk/apimanagement"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := apimanagement.NewGroupUser(ctx, "groupUser", &apimanagement.GroupUserArgs{
			GroupId:           pulumi.String("tempgroup"),
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("apimService1"),
			UserId:            pulumi.String("59307d350af58404d8a26300"),
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
import com.pulumi.azurenative.apimanagement.GroupUser;
import com.pulumi.azurenative.apimanagement.GroupUserArgs;
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
        var groupUser = new GroupUser("groupUser", GroupUserArgs.builder()        
            .groupId("tempgroup")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .userId("59307d350af58404d8a26300")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const groupUser = new azure_native.apimanagement.GroupUser("groupUser", {
    groupId: "tempgroup",
    resourceGroupName: "rg1",
    serviceName: "apimService1",
    userId: "59307d350af58404d8a26300",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

group_user = azure_native.apimanagement.GroupUser("groupUser",
    group_id="tempgroup",
    resource_group_name="rg1",
    service_name="apimService1",
    user_id="59307d350af58404d8a26300")

```

```yaml
resources:
  groupUser:
    type: azure-native:apimanagement:GroupUser
    properties:
      groupId: tempgroup
      resourceGroupName: rg1
      serviceName: apimService1
      userId: 59307d350af58404d8a26300

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:apimanagement:GroupUser 59307d350af58404d8a26300 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/users/59307d350af58404d8a26300 
```
