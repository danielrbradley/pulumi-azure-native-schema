User details.
API Version: 2022-08-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ApiManagementCreateUser
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var user = new AzureNative.ApiManagement.User("user", new()
    {
        Confirmation = "signup",
        Email = "foobar@outlook.com",
        FirstName = "foo",
        LastName = "bar",
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
        UserId = "5931a75ae4bbd512288c680b",
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
		_, err := apimanagement.NewUser(ctx, "user", &apimanagement.UserArgs{
			Confirmation:      pulumi.String("signup"),
			Email:             pulumi.String("foobar@outlook.com"),
			FirstName:         pulumi.String("foo"),
			LastName:          pulumi.String("bar"),
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("apimService1"),
			UserId:            pulumi.String("5931a75ae4bbd512288c680b"),
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
import com.pulumi.azurenative.apimanagement.User;
import com.pulumi.azurenative.apimanagement.UserArgs;
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
            .confirmation("signup")
            .email("foobar@outlook.com")
            .firstName("foo")
            .lastName("bar")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .userId("5931a75ae4bbd512288c680b")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const user = new azure_native.apimanagement.User("user", {
    confirmation: "signup",
    email: "foobar@outlook.com",
    firstName: "foo",
    lastName: "bar",
    resourceGroupName: "rg1",
    serviceName: "apimService1",
    userId: "5931a75ae4bbd512288c680b",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

user = azure_native.apimanagement.User("user",
    confirmation="signup",
    email="foobar@outlook.com",
    first_name="foo",
    last_name="bar",
    resource_group_name="rg1",
    service_name="apimService1",
    user_id="5931a75ae4bbd512288c680b")

```

```yaml
resources:
  user:
    type: azure-native:apimanagement:User
    properties:
      confirmation: signup
      email: foobar@outlook.com
      firstName: foo
      lastName: bar
      resourceGroupName: rg1
      serviceName: apimService1
      userId: 5931a75ae4bbd512288c680b

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:apimanagement:User 5931a75ae4bbd512288c680b /subscriptions/subid/resourcegroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/users/5931a75ae4bbd512288c680b 
```
