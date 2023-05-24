A lab.
API Version: 2018-09-15.
Previous API Version: 2018-09-15. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Labs_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var lab = new AzureNative.DevTestLab.Lab("lab", new()
    {
        LabStorageType = "{Standard|Premium}",
        Location = "{location}",
        Name = "{labName}",
        ResourceGroupName = "resourceGroupName",
        Tags = 
        {
            { "tagName1", "tagValue1" },
        },
    });

});


```

```go
package main

import (
	devtestlab "github.com/pulumi/pulumi-azure-native-sdk/devtestlab"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := devtestlab.NewLab(ctx, "lab", &devtestlab.LabArgs{
			LabStorageType:    pulumi.String("{Standard|Premium}"),
			Location:          pulumi.String("{location}"),
			Name:              pulumi.String("{labName}"),
			ResourceGroupName: pulumi.String("resourceGroupName"),
			Tags: pulumi.StringMap{
				"tagName1": pulumi.String("tagValue1"),
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
import com.pulumi.azurenative.devtestlab.Lab;
import com.pulumi.azurenative.devtestlab.LabArgs;
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
        var lab = new Lab("lab", LabArgs.builder()        
            .labStorageType("{Standard|Premium}")
            .location("{location}")
            .name("{labName}")
            .resourceGroupName("resourceGroupName")
            .tags(Map.of("tagName1", "tagValue1"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const lab = new azure_native.devtestlab.Lab("lab", {
    labStorageType: "{Standard|Premium}",
    location: "{location}",
    name: "{labName}",
    resourceGroupName: "resourceGroupName",
    tags: {
        tagName1: "tagValue1",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

lab = azure_native.devtestlab.Lab("lab",
    lab_storage_type="{Standard|Premium}",
    location="{location}",
    name="{labName}",
    resource_group_name="resourceGroupName",
    tags={
        "tagName1": "tagValue1",
    })

```

```yaml
resources:
  lab:
    type: azure-native:devtestlab:Lab
    properties:
      labStorageType: '{Standard|Premium}'
      location: '{location}'
      name: '{labName}'
      resourceGroupName: resourceGroupName
      tags:
        tagName1: tagValue1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:devtestlab:Lab {labName} /subscriptions/{subscriptionId}/resourcegroups/resourceGroupName/providers/microsoft.devtestlab/labs/{labName} 
```
