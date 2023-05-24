Domain ownership Identifier.
API Version: 2022-09-01.
Previous API Version: 2020-10-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create App Service Domain OwnershipIdentifier
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var domainOwnershipIdentifier = new AzureNative.DomainRegistration.DomainOwnershipIdentifier("domainOwnershipIdentifier", new()
    {
        DomainName = "example.com",
        Name = "SampleOwnershipId",
        OwnershipId = "SampleOwnershipId",
        ResourceGroupName = "testrg123",
    });

});


```

```go
package main

import (
	domainregistration "github.com/pulumi/pulumi-azure-native-sdk/domainregistration"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := domainregistration.NewDomainOwnershipIdentifier(ctx, "domainOwnershipIdentifier", &domainregistration.DomainOwnershipIdentifierArgs{
			DomainName:        pulumi.String("example.com"),
			Name:              pulumi.String("SampleOwnershipId"),
			OwnershipId:       pulumi.String("SampleOwnershipId"),
			ResourceGroupName: pulumi.String("testrg123"),
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
import com.pulumi.azurenative.domainregistration.DomainOwnershipIdentifier;
import com.pulumi.azurenative.domainregistration.DomainOwnershipIdentifierArgs;
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
        var domainOwnershipIdentifier = new DomainOwnershipIdentifier("domainOwnershipIdentifier", DomainOwnershipIdentifierArgs.builder()        
            .domainName("example.com")
            .name("SampleOwnershipId")
            .ownershipId("SampleOwnershipId")
            .resourceGroupName("testrg123")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const domainOwnershipIdentifier = new azure_native.domainregistration.DomainOwnershipIdentifier("domainOwnershipIdentifier", {
    domainName: "example.com",
    name: "SampleOwnershipId",
    ownershipId: "SampleOwnershipId",
    resourceGroupName: "testrg123",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

domain_ownership_identifier = azure_native.domainregistration.DomainOwnershipIdentifier("domainOwnershipIdentifier",
    domain_name="example.com",
    name="SampleOwnershipId",
    ownership_id="SampleOwnershipId",
    resource_group_name="testrg123")

```

```yaml
resources:
  domainOwnershipIdentifier:
    type: azure-native:domainregistration:DomainOwnershipIdentifier
    properties:
      domainName: example.com
      name: SampleOwnershipId
      ownershipId: SampleOwnershipId
      resourceGroupName: testrg123

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:domainregistration:DomainOwnershipIdentifier SampleOwnershipId /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.DomainRegistration/domains/example.com/domainownershipidentifiers/SampleOwnershipId 
```
