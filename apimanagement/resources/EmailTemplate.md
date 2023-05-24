Email Template details.
API Version: 2022-08-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ApiManagementCreateTemplate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var emailTemplate = new AzureNative.ApiManagement.EmailTemplate("emailTemplate", new()
    {
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
        Subject = "Your request for $IssueName was successfully received.",
        TemplateName = "newIssueNotificationMessage",
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
		_, err := apimanagement.NewEmailTemplate(ctx, "emailTemplate", &apimanagement.EmailTemplateArgs{
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("apimService1"),
			Subject:           pulumi.String("Your request for $IssueName was successfully received."),
			TemplateName:      pulumi.String("newIssueNotificationMessage"),
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
import com.pulumi.azurenative.apimanagement.EmailTemplate;
import com.pulumi.azurenative.apimanagement.EmailTemplateArgs;
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
        var emailTemplate = new EmailTemplate("emailTemplate", EmailTemplateArgs.builder()        
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .subject("Your request for $IssueName was successfully received.")
            .templateName("newIssueNotificationMessage")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const emailTemplate = new azure_native.apimanagement.EmailTemplate("emailTemplate", {
    resourceGroupName: "rg1",
    serviceName: "apimService1",
    subject: "Your request for $IssueName was successfully received.",
    templateName: "newIssueNotificationMessage",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

email_template = azure_native.apimanagement.EmailTemplate("emailTemplate",
    resource_group_name="rg1",
    service_name="apimService1",
    subject="Your request for $IssueName was successfully received.",
    template_name="newIssueNotificationMessage")

```

```yaml
resources:
  emailTemplate:
    type: azure-native:apimanagement:EmailTemplate
    properties:
      resourceGroupName: rg1
      serviceName: apimService1
      subject: Your request for $IssueName was successfully received.
      templateName: newIssueNotificationMessage

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:apimanagement:EmailTemplate NewIssueNotificationMessage /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/templates/NewIssueNotificationMessage 
```
