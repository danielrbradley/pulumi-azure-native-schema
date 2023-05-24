A class representing an EmailService resource.
API Version: 2023-03-01-preview.
Previous API Version: 2021-10-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update EmailService resource
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var emailService = new AzureNative.Communication.EmailService("emailService", new()
    {
        DataLocation = "United States",
        EmailServiceName = "MyEmailServiceResource",
        Location = "Global",
        ResourceGroupName = "MyResourceGroup",
    });

});


```

```go
package main

import (
	communication "github.com/pulumi/pulumi-azure-native-sdk/communication"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := communication.NewEmailService(ctx, "emailService", &communication.EmailServiceArgs{
			DataLocation:      pulumi.String("United States"),
			EmailServiceName:  pulumi.String("MyEmailServiceResource"),
			Location:          pulumi.String("Global"),
			ResourceGroupName: pulumi.String("MyResourceGroup"),
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
import com.pulumi.azurenative.communication.EmailService;
import com.pulumi.azurenative.communication.EmailServiceArgs;
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
        var emailService = new EmailService("emailService", EmailServiceArgs.builder()        
            .dataLocation("United States")
            .emailServiceName("MyEmailServiceResource")
            .location("Global")
            .resourceGroupName("MyResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const emailService = new azure_native.communication.EmailService("emailService", {
    dataLocation: "United States",
    emailServiceName: "MyEmailServiceResource",
    location: "Global",
    resourceGroupName: "MyResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

email_service = azure_native.communication.EmailService("emailService",
    data_location="United States",
    email_service_name="MyEmailServiceResource",
    location="Global",
    resource_group_name="MyResourceGroup")

```

```yaml
resources:
  emailService:
    type: azure-native:communication:EmailService
    properties:
      dataLocation: United States
      emailServiceName: MyEmailServiceResource
      location: Global
      resourceGroupName: MyResourceGroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:communication:EmailService MyEmailServiceResource /subscriptions/11112222-3333-4444-5555-666677778888/resourceGroups/MyResourceGroup/providers/Microsoft.Communication/EmailServices/MyEmailServiceResource 
```
