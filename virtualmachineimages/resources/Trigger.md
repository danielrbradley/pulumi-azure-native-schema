Represents a trigger that can invoke an image template build.
API Version: 2022-07-01.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a source image type trigger
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var trigger = new AzureNative.VirtualMachineImages.Trigger("trigger", new()
    {
        ImageTemplateName = "myImageTemplate",
        Kind = "SourceImage",
        ResourceGroupName = "myResourceGroup",
        TriggerName = "source",
    });

});


```

```go
package main

import (
	virtualmachineimages "github.com/pulumi/pulumi-azure-native-sdk/virtualmachineimages"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := virtualmachineimages.NewTrigger(ctx, "trigger", &virtualmachineimages.TriggerArgs{
			ImageTemplateName: pulumi.String("myImageTemplate"),
			Kind:              pulumi.String("SourceImage"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
			TriggerName:       pulumi.String("source"),
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
import com.pulumi.azurenative.virtualmachineimages.Trigger;
import com.pulumi.azurenative.virtualmachineimages.TriggerArgs;
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
        var trigger = new Trigger("trigger", TriggerArgs.builder()        
            .imageTemplateName("myImageTemplate")
            .kind("SourceImage")
            .resourceGroupName("myResourceGroup")
            .triggerName("source")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const trigger = new azure_native.virtualmachineimages.Trigger("trigger", {
    imageTemplateName: "myImageTemplate",
    kind: "SourceImage",
    resourceGroupName: "myResourceGroup",
    triggerName: "source",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

trigger = azure_native.virtualmachineimages.Trigger("trigger",
    image_template_name="myImageTemplate",
    kind="SourceImage",
    resource_group_name="myResourceGroup",
    trigger_name="source")

```

```yaml
resources:
  trigger:
    type: azure-native:virtualmachineimages:Trigger
    properties:
      imageTemplateName: myImageTemplate
      kind: SourceImage
      resourceGroupName: myResourceGroup
      triggerName: source

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:virtualmachineimages:Trigger source /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.VirtualMachineImages/imageTemplates/myImageTemplate/triggers/source 
```
