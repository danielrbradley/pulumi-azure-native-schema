User of a lab that can register for and use virtual machines within the lab.
API Version: 2022-08-01.
Previous API Version: 2018-10-15. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### putUser
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var user = new AzureNative.LabServices.User("user", new()
    {
        AdditionalUsageQuota = "PT10H",
        Email = "testuser@contoso.com",
        LabName = "testlab",
        ResourceGroupName = "testrg123",
        UserName = "testuser",
    });

});


```

```go
package main

import (
	labservices "github.com/pulumi/pulumi-azure-native-sdk/labservices"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := labservices.NewUser(ctx, "user", &labservices.UserArgs{
			AdditionalUsageQuota: pulumi.String("PT10H"),
			Email:                pulumi.String("testuser@contoso.com"),
			LabName:              pulumi.String("testlab"),
			ResourceGroupName:    pulumi.String("testrg123"),
			UserName:             pulumi.String("testuser"),
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
import com.pulumi.azurenative.labservices.User;
import com.pulumi.azurenative.labservices.UserArgs;
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
            .additionalUsageQuota("PT10H")
            .email("testuser@contoso.com")
            .labName("testlab")
            .resourceGroupName("testrg123")
            .userName("testuser")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const user = new azure_native.labservices.User("user", {
    additionalUsageQuota: "PT10H",
    email: "testuser@contoso.com",
    labName: "testlab",
    resourceGroupName: "testrg123",
    userName: "testuser",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

user = azure_native.labservices.User("user",
    additional_usage_quota="PT10H",
    email="testuser@contoso.com",
    lab_name="testlab",
    resource_group_name="testrg123",
    user_name="testuser")

```

```yaml
resources:
  user:
    type: azure-native:labservices:User
    properties:
      additionalUsageQuota: PT10H
      email: testuser@contoso.com
      labName: testlab
      resourceGroupName: testrg123
      userName: testuser

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:labservices:User default /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.LabServices/labs/testlab/users/testuser 
```
