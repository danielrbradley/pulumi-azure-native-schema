Represents a devcenter resource.
API Version: 2022-11-11-preview.
Previous API Version: 2022-09-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### DevCenters_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var devCenter = new AzureNative.DevCenter.DevCenter("devCenter", new()
    {
        DevCenterName = "Contoso",
        Location = "centralus",
        ResourceGroupName = "rg1",
        Tags = 
        {
            { "CostCode", "12345" },
        },
    });

});


```

```go
package main

import (
	devcenter "github.com/pulumi/pulumi-azure-native-sdk/devcenter"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := devcenter.NewDevCenter(ctx, "devCenter", &devcenter.DevCenterArgs{
			DevCenterName:     pulumi.String("Contoso"),
			Location:          pulumi.String("centralus"),
			ResourceGroupName: pulumi.String("rg1"),
			Tags: pulumi.StringMap{
				"CostCode": pulumi.String("12345"),
			},
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
import com.pulumi.azurenative.devcenter.DevCenter;
import com.pulumi.azurenative.devcenter.DevCenterArgs;
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
        var devCenter = new DevCenter("devCenter", DevCenterArgs.builder()        
            .devCenterName("Contoso")
            .location("centralus")
            .resourceGroupName("rg1")
            .tags(Map.of("CostCode", "12345"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const devCenter = new azure_native.devcenter.DevCenter("devCenter", {
    devCenterName: "Contoso",
    location: "centralus",
    resourceGroupName: "rg1",
    tags: {
        CostCode: "12345",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

dev_center = azure_native.devcenter.DevCenter("devCenter",
    dev_center_name="Contoso",
    location="centralus",
    resource_group_name="rg1",
    tags={
        "CostCode": "12345",
    })

```

```yaml
resources:
  devCenter:
    type: azure-native:devcenter:DevCenter
    properties:
      devCenterName: Contoso
      location: centralus
      resourceGroupName: rg1
      tags:
        CostCode: '12345'

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:devcenter:DevCenter Contoso /subscriptions/0ac520ee-14c0-480f-b6c9-0a90c58ffff/resourceGroups/rg1/providers/Microsoft.DevCenter/devcenters/Contoso 
```
