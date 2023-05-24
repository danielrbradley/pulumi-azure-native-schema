A class representing a Domains resource.
API Version: 2023-03-01-preview.
Previous API Version: 2021-10-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update Domains resource
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var domain = new AzureNative.Communication.Domain("domain", new()
    {
        DomainManagement = "CustomerManaged",
        DomainName = "mydomain.com",
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
		_, err := communication.NewDomain(ctx, "domain", &communication.DomainArgs{
			DomainManagement:  pulumi.String("CustomerManaged"),
			DomainName:        pulumi.String("mydomain.com"),
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
import com.pulumi.azurenative.communication.Domain;
import com.pulumi.azurenative.communication.DomainArgs;
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
        var domain = new Domain("domain", DomainArgs.builder()        
            .domainManagement("CustomerManaged")
            .domainName("mydomain.com")
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

const domain = new azure_native.communication.Domain("domain", {
    domainManagement: "CustomerManaged",
    domainName: "mydomain.com",
    emailServiceName: "MyEmailServiceResource",
    location: "Global",
    resourceGroupName: "MyResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

domain = azure_native.communication.Domain("domain",
    domain_management="CustomerManaged",
    domain_name="mydomain.com",
    email_service_name="MyEmailServiceResource",
    location="Global",
    resource_group_name="MyResourceGroup")

```

```yaml
resources:
  domain:
    type: azure-native:communication:Domain
    properties:
      domainManagement: CustomerManaged
      domainName: mydomain.com
      emailServiceName: MyEmailServiceResource
      location: Global
      resourceGroupName: MyResourceGroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:communication:Domain mydomain.com /subscriptions/11112222-3333-4444-5555-666677778888/resourceGroups/MyResourceGroup/providers/Microsoft.Communication/EmailServices/MyEmailServiceResource/Domains/mydomain.com 
```
