Resource for OuContainer.
API Version: 2022-12-01.
Previous API Version: 2021-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create Domain Service
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var ouContainer = new AzureNative.Aad.OuContainer("ouContainer", new()
    {
        AccountName = "AccountName1",
        DomainServiceName = "OuContainer.com",
        OuContainerName = "OuContainer1",
        Password = "<password>",
        ResourceGroupName = "OuContainerResourceGroup",
        Spn = "Spn1",
    });

});


```

```go
package main

import (
	aad "github.com/pulumi/pulumi-azure-native-sdk/aad"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := aad.NewOuContainer(ctx, "ouContainer", &aad.OuContainerArgs{
			AccountName:       pulumi.String("AccountName1"),
			DomainServiceName: pulumi.String("OuContainer.com"),
			OuContainerName:   pulumi.String("OuContainer1"),
			Password:          pulumi.String("<password>"),
			ResourceGroupName: pulumi.String("OuContainerResourceGroup"),
			Spn:               pulumi.String("Spn1"),
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
import com.pulumi.azurenative.aad.OuContainer;
import com.pulumi.azurenative.aad.OuContainerArgs;
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
        var ouContainer = new OuContainer("ouContainer", OuContainerArgs.builder()        
            .accountName("AccountName1")
            .domainServiceName("OuContainer.com")
            .ouContainerName("OuContainer1")
            .password("<password>")
            .resourceGroupName("OuContainerResourceGroup")
            .spn("Spn1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const ouContainer = new azure_native.aad.OuContainer("ouContainer", {
    accountName: "AccountName1",
    domainServiceName: "OuContainer.com",
    ouContainerName: "OuContainer1",
    password: "<password>",
    resourceGroupName: "OuContainerResourceGroup",
    spn: "Spn1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

ou_container = azure_native.aad.OuContainer("ouContainer",
    account_name="AccountName1",
    domain_service_name="OuContainer.com",
    ou_container_name="OuContainer1",
    password="<password>",
    resource_group_name="OuContainerResourceGroup",
    spn="Spn1")

```

```yaml
resources:
  ouContainer:
    type: azure-native:aad:OuContainer
    properties:
      accountName: AccountName1
      domainServiceName: OuContainer.com
      ouContainerName: OuContainer1
      password: <password>
      resourceGroupName: OuContainerResourceGroup
      spn: Spn1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:aad:OuContainer OuContainer.com/OuContainer1 /subscriptions/1639790a-76a2-4ac4-98d9-8562f5dfcb4d/resourceGroups/ouContainerResourceGroup/providers/Microsoft.AAD/domainServices/ouContainer.com/ouContainer/ouContainer1 
```
