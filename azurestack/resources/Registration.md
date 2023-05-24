Registration information.
API Version: 2022-06-01.
Previous API Version: 2017-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update an Azure Stack registration.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var registration = new AzureNative.AzureStack.Registration("registration", new()
    {
        Location = "global",
        RegistrationName = "testregistration",
        RegistrationToken = "EyjIAWXSAw5nTw9KZWWiOiJeZxZlbg9wBwvUdCiSIM9iaMVjdeLkijoinwIzyJa2Ytgtowm2yy00OdG4lTlLyJmtztHjZGfJZTC0NZK1iIWiY2XvdWRJzCi6iJy5nDy0oDk1LTNHmWeTnDUwyS05oDI0LTrINzYwoGq5mjAzziIsim1HCmtldHBsYwnLu3LuZGljYXrpB25FBmfIbgVkIJp0CNvLLCJOYXJkd2FYzuLUZM8iOlt7IM51bunvcMVZiJoYlCjcaw9ZiJPBIjNkzDJHmda3yte5ndqZMdq4YmZkZmi5oDM3OTY3ZwNMIL0SIM5PyYI6WyJLZTy0ztJJMwZKy2m0OWNLODDLMwm2zTm0ymzKyjmWySisiJA3njlHmtdlY2q4NjRjnwFIZtC1YZi5ZGyZodM3Y2vjIl0siMnwDsi6wyi2oDUZoTbiY2RhNDa0ymrKoWe4YtK5otblzWrJzGyzNCISIjmYnzC4M2vmnZdIoDRKM2i5ytfkmJlhnDc1zdhLzWm1il0sim5HBwuiOijIqzF1MTvhmDIXmIIsimrpc2SiolsioWNlZjVhnZM1otQ0nDu3NmjlN2M3zmfjzmyZMTJhZtiiLcjLZjLmmZJhmWVhytG0NTu0OTqZNWu1Mda0MZbIYtfjyijdLCj1DWlKijoinwM5Mwu3NjytMju5Os00oTIwlWi0OdmTnGzHotiWm2RjyTCxIIwiBWvTb3J5ijPbijAYZDA3M2fjNzu0YTRMZTfhodkxzDnkogY5ZtAWzdyXIiwINZcWzThLnDQ4otrJndAzZGI5MGzlYtY1ZJA5ZdfiNMQIXX1DlcJpC3n1zxiiOijZb21lB25LIIWIdmVyC2LVbiI6IJeuMcJ9",
        ResourceGroup = "azurestack",
    });

});


```

```go
package main

import (
	azurestack "github.com/pulumi/pulumi-azure-native-sdk/azurestack"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := azurestack.NewRegistration(ctx, "registration", &azurestack.RegistrationArgs{
			Location:          pulumi.String("global"),
			RegistrationName:  pulumi.String("testregistration"),
			RegistrationToken: pulumi.String("EyjIAWXSAw5nTw9KZWWiOiJeZxZlbg9wBwvUdCiSIM9iaMVjdeLkijoinwIzyJa2Ytgtowm2yy00OdG4lTlLyJmtztHjZGfJZTC0NZK1iIWiY2XvdWRJzCi6iJy5nDy0oDk1LTNHmWeTnDUwyS05oDI0LTrINzYwoGq5mjAzziIsim1HCmtldHBsYwnLu3LuZGljYXrpB25FBmfIbgVkIJp0CNvLLCJOYXJkd2FYzuLUZM8iOlt7IM51bunvcMVZiJoYlCjcaw9ZiJPBIjNkzDJHmda3yte5ndqZMdq4YmZkZmi5oDM3OTY3ZwNMIL0SIM5PyYI6WyJLZTy0ztJJMwZKy2m0OWNLODDLMwm2zTm0ymzKyjmWySisiJA3njlHmtdlY2q4NjRjnwFIZtC1YZi5ZGyZodM3Y2vjIl0siMnwDsi6wyi2oDUZoTbiY2RhNDa0ymrKoWe4YtK5otblzWrJzGyzNCISIjmYnzC4M2vmnZdIoDRKM2i5ytfkmJlhnDc1zdhLzWm1il0sim5HBwuiOijIqzF1MTvhmDIXmIIsimrpc2SiolsioWNlZjVhnZM1otQ0nDu3NmjlN2M3zmfjzmyZMTJhZtiiLcjLZjLmmZJhmWVhytG0NTu0OTqZNWu1Mda0MZbIYtfjyijdLCj1DWlKijoinwM5Mwu3NjytMju5Os00oTIwlWi0OdmTnGzHotiWm2RjyTCxIIwiBWvTb3J5ijPbijAYZDA3M2fjNzu0YTRMZTfhodkxzDnkogY5ZtAWzdyXIiwINZcWzThLnDQ4otrJndAzZGI5MGzlYtY1ZJA5ZdfiNMQIXX1DlcJpC3n1zxiiOijZb21lB25LIIWIdmVyC2LVbiI6IJeuMcJ9"),
			ResourceGroup:     pulumi.String("azurestack"),
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
import com.pulumi.azurenative.azurestack.Registration;
import com.pulumi.azurenative.azurestack.RegistrationArgs;
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
        var registration = new Registration("registration", RegistrationArgs.builder()        
            .location("global")
            .registrationName("testregistration")
            .registrationToken("EyjIAWXSAw5nTw9KZWWiOiJeZxZlbg9wBwvUdCiSIM9iaMVjdeLkijoinwIzyJa2Ytgtowm2yy00OdG4lTlLyJmtztHjZGfJZTC0NZK1iIWiY2XvdWRJzCi6iJy5nDy0oDk1LTNHmWeTnDUwyS05oDI0LTrINzYwoGq5mjAzziIsim1HCmtldHBsYwnLu3LuZGljYXrpB25FBmfIbgVkIJp0CNvLLCJOYXJkd2FYzuLUZM8iOlt7IM51bunvcMVZiJoYlCjcaw9ZiJPBIjNkzDJHmda3yte5ndqZMdq4YmZkZmi5oDM3OTY3ZwNMIL0SIM5PyYI6WyJLZTy0ztJJMwZKy2m0OWNLODDLMwm2zTm0ymzKyjmWySisiJA3njlHmtdlY2q4NjRjnwFIZtC1YZi5ZGyZodM3Y2vjIl0siMnwDsi6wyi2oDUZoTbiY2RhNDa0ymrKoWe4YtK5otblzWrJzGyzNCISIjmYnzC4M2vmnZdIoDRKM2i5ytfkmJlhnDc1zdhLzWm1il0sim5HBwuiOijIqzF1MTvhmDIXmIIsimrpc2SiolsioWNlZjVhnZM1otQ0nDu3NmjlN2M3zmfjzmyZMTJhZtiiLcjLZjLmmZJhmWVhytG0NTu0OTqZNWu1Mda0MZbIYtfjyijdLCj1DWlKijoinwM5Mwu3NjytMju5Os00oTIwlWi0OdmTnGzHotiWm2RjyTCxIIwiBWvTb3J5ijPbijAYZDA3M2fjNzu0YTRMZTfhodkxzDnkogY5ZtAWzdyXIiwINZcWzThLnDQ4otrJndAzZGI5MGzlYtY1ZJA5ZdfiNMQIXX1DlcJpC3n1zxiiOijZb21lB25LIIWIdmVyC2LVbiI6IJeuMcJ9")
            .resourceGroup("azurestack")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const registration = new azure_native.azurestack.Registration("registration", {
    location: "global",
    registrationName: "testregistration",
    registrationToken: "EyjIAWXSAw5nTw9KZWWiOiJeZxZlbg9wBwvUdCiSIM9iaMVjdeLkijoinwIzyJa2Ytgtowm2yy00OdG4lTlLyJmtztHjZGfJZTC0NZK1iIWiY2XvdWRJzCi6iJy5nDy0oDk1LTNHmWeTnDUwyS05oDI0LTrINzYwoGq5mjAzziIsim1HCmtldHBsYwnLu3LuZGljYXrpB25FBmfIbgVkIJp0CNvLLCJOYXJkd2FYzuLUZM8iOlt7IM51bunvcMVZiJoYlCjcaw9ZiJPBIjNkzDJHmda3yte5ndqZMdq4YmZkZmi5oDM3OTY3ZwNMIL0SIM5PyYI6WyJLZTy0ztJJMwZKy2m0OWNLODDLMwm2zTm0ymzKyjmWySisiJA3njlHmtdlY2q4NjRjnwFIZtC1YZi5ZGyZodM3Y2vjIl0siMnwDsi6wyi2oDUZoTbiY2RhNDa0ymrKoWe4YtK5otblzWrJzGyzNCISIjmYnzC4M2vmnZdIoDRKM2i5ytfkmJlhnDc1zdhLzWm1il0sim5HBwuiOijIqzF1MTvhmDIXmIIsimrpc2SiolsioWNlZjVhnZM1otQ0nDu3NmjlN2M3zmfjzmyZMTJhZtiiLcjLZjLmmZJhmWVhytG0NTu0OTqZNWu1Mda0MZbIYtfjyijdLCj1DWlKijoinwM5Mwu3NjytMju5Os00oTIwlWi0OdmTnGzHotiWm2RjyTCxIIwiBWvTb3J5ijPbijAYZDA3M2fjNzu0YTRMZTfhodkxzDnkogY5ZtAWzdyXIiwINZcWzThLnDQ4otrJndAzZGI5MGzlYtY1ZJA5ZdfiNMQIXX1DlcJpC3n1zxiiOijZb21lB25LIIWIdmVyC2LVbiI6IJeuMcJ9",
    resourceGroup: "azurestack",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

registration = azure_native.azurestack.Registration("registration",
    location="global",
    registration_name="testregistration",
    registration_token="EyjIAWXSAw5nTw9KZWWiOiJeZxZlbg9wBwvUdCiSIM9iaMVjdeLkijoinwIzyJa2Ytgtowm2yy00OdG4lTlLyJmtztHjZGfJZTC0NZK1iIWiY2XvdWRJzCi6iJy5nDy0oDk1LTNHmWeTnDUwyS05oDI0LTrINzYwoGq5mjAzziIsim1HCmtldHBsYwnLu3LuZGljYXrpB25FBmfIbgVkIJp0CNvLLCJOYXJkd2FYzuLUZM8iOlt7IM51bunvcMVZiJoYlCjcaw9ZiJPBIjNkzDJHmda3yte5ndqZMdq4YmZkZmi5oDM3OTY3ZwNMIL0SIM5PyYI6WyJLZTy0ztJJMwZKy2m0OWNLODDLMwm2zTm0ymzKyjmWySisiJA3njlHmtdlY2q4NjRjnwFIZtC1YZi5ZGyZodM3Y2vjIl0siMnwDsi6wyi2oDUZoTbiY2RhNDa0ymrKoWe4YtK5otblzWrJzGyzNCISIjmYnzC4M2vmnZdIoDRKM2i5ytfkmJlhnDc1zdhLzWm1il0sim5HBwuiOijIqzF1MTvhmDIXmIIsimrpc2SiolsioWNlZjVhnZM1otQ0nDu3NmjlN2M3zmfjzmyZMTJhZtiiLcjLZjLmmZJhmWVhytG0NTu0OTqZNWu1Mda0MZbIYtfjyijdLCj1DWlKijoinwM5Mwu3NjytMju5Os00oTIwlWi0OdmTnGzHotiWm2RjyTCxIIwiBWvTb3J5ijPbijAYZDA3M2fjNzu0YTRMZTfhodkxzDnkogY5ZtAWzdyXIiwINZcWzThLnDQ4otrJndAzZGI5MGzlYtY1ZJA5ZdfiNMQIXX1DlcJpC3n1zxiiOijZb21lB25LIIWIdmVyC2LVbiI6IJeuMcJ9",
    resource_group="azurestack")

```

```yaml
resources:
  registration:
    type: azure-native:azurestack:Registration
    properties:
      location: global
      registrationName: testregistration
      registrationToken: EyjIAWXSAw5nTw9KZWWiOiJeZxZlbg9wBwvUdCiSIM9iaMVjdeLkijoinwIzyJa2Ytgtowm2yy00OdG4lTlLyJmtztHjZGfJZTC0NZK1iIWiY2XvdWRJzCi6iJy5nDy0oDk1LTNHmWeTnDUwyS05oDI0LTrINzYwoGq5mjAzziIsim1HCmtldHBsYwnLu3LuZGljYXrpB25FBmfIbgVkIJp0CNvLLCJOYXJkd2FYzuLUZM8iOlt7IM51bunvcMVZiJoYlCjcaw9ZiJPBIjNkzDJHmda3yte5ndqZMdq4YmZkZmi5oDM3OTY3ZwNMIL0SIM5PyYI6WyJLZTy0ztJJMwZKy2m0OWNLODDLMwm2zTm0ymzKyjmWySisiJA3njlHmtdlY2q4NjRjnwFIZtC1YZi5ZGyZodM3Y2vjIl0siMnwDsi6wyi2oDUZoTbiY2RhNDa0ymrKoWe4YtK5otblzWrJzGyzNCISIjmYnzC4M2vmnZdIoDRKM2i5ytfkmJlhnDc1zdhLzWm1il0sim5HBwuiOijIqzF1MTvhmDIXmIIsimrpc2SiolsioWNlZjVhnZM1otQ0nDu3NmjlN2M3zmfjzmyZMTJhZtiiLcjLZjLmmZJhmWVhytG0NTu0OTqZNWu1Mda0MZbIYtfjyijdLCj1DWlKijoinwM5Mwu3NjytMju5Os00oTIwlWi0OdmTnGzHotiWm2RjyTCxIIwiBWvTb3J5ijPbijAYZDA3M2fjNzu0YTRMZTfhodkxzDnkogY5ZtAWzdyXIiwINZcWzThLnDQ4otrJndAzZGI5MGzlYtY1ZJA5ZdfiNMQIXX1DlcJpC3n1zxiiOijZb21lB25LIIWIdmVyC2LVbiI6IJeuMcJ9
      resourceGroup: azurestack

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:azurestack:Registration testregistration /subscriptions/dd8597b4-8739-4467-8b10-f8679f62bfbf/resourceGroups/azurestack/providers/Microsoft.AzureStack/registrations/testregistration 
```
