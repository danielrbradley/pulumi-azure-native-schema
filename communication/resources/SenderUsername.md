A class representing a SenderUsername resource.
API Version: 2023-03-01-preview.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update SenderUsernames resource
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var senderUsername = new AzureNative.Communication.SenderUsername("senderUsername", new()
    {
        DisplayName = "Contoso News Alerts",
        DomainName = "contoso.com",
        EmailServiceName = "contosoEmailService",
        ResourceGroupName = "contosoResourceGroup",
        SenderUsername = "contosoNewsAlerts",
        Username = "contosoNewsAlerts",
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
		_, err := communication.NewSenderUsername(ctx, "senderUsername", &communication.SenderUsernameArgs{
			DisplayName:       pulumi.String("Contoso News Alerts"),
			DomainName:        pulumi.String("contoso.com"),
			EmailServiceName:  pulumi.String("contosoEmailService"),
			ResourceGroupName: pulumi.String("contosoResourceGroup"),
			SenderUsername:    pulumi.String("contosoNewsAlerts"),
			Username:          pulumi.String("contosoNewsAlerts"),
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
import com.pulumi.azurenative.communication.SenderUsername;
import com.pulumi.azurenative.communication.SenderUsernameArgs;
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
        var senderUsername = new SenderUsername("senderUsername", SenderUsernameArgs.builder()        
            .displayName("Contoso News Alerts")
            .domainName("contoso.com")
            .emailServiceName("contosoEmailService")
            .resourceGroupName("contosoResourceGroup")
            .senderUsername("contosoNewsAlerts")
            .username("contosoNewsAlerts")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const senderUsername = new azure_native.communication.SenderUsername("senderUsername", {
    displayName: "Contoso News Alerts",
    domainName: "contoso.com",
    emailServiceName: "contosoEmailService",
    resourceGroupName: "contosoResourceGroup",
    senderUsername: "contosoNewsAlerts",
    username: "contosoNewsAlerts",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sender_username = azure_native.communication.SenderUsername("senderUsername",
    display_name="Contoso News Alerts",
    domain_name="contoso.com",
    email_service_name="contosoEmailService",
    resource_group_name="contosoResourceGroup",
    sender_username="contosoNewsAlerts",
    username="contosoNewsAlerts")

```

```yaml
resources:
  senderUsername:
    type: azure-native:communication:SenderUsername
    properties:
      displayName: Contoso News Alerts
      domainName: contoso.com
      emailServiceName: contosoEmailService
      resourceGroupName: contosoResourceGroup
      senderUsername: contosoNewsAlerts
      username: contosoNewsAlerts

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:communication:SenderUsername contoso.com /subscriptions/11112222-3333-4444-5555-666677778888/resourceGroups/contosoResourceGroup/providers/Microsoft.Communication/EmailServices/contosoEmailService/Domains/contoso.com/senderUsernames/contosoNewsAlerts 
```
