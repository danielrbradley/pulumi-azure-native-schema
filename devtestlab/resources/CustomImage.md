A custom image.
API Version: 2018-09-15.
Previous API Version: 2018-09-15. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CustomImages_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var customImage = new AzureNative.DevTestLab.CustomImage("customImage", new()
    {
        Description = "My Custom Image",
        LabName = "{labName}",
        Name = "{customImageName}",
        ResourceGroupName = "resourceGroupName",
        Tags = 
        {
            { "tagName1", "tagValue1" },
        },
        Vm = new AzureNative.DevTestLab.Inputs.CustomImagePropertiesFromVmArgs
        {
            LinuxOsInfo = new AzureNative.DevTestLab.Inputs.LinuxOsInfoArgs
            {
                LinuxOsState = "NonDeprovisioned",
            },
            SourceVmId = "/subscriptions/{subscriptionId}/resourcegroups/resourceGroupName/providers/microsoft.devtestlab/labs/{labName}/virtualmachines/{vmName}",
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
		_, err := devtestlab.NewCustomImage(ctx, "customImage", &devtestlab.CustomImageArgs{
			Description:       pulumi.String("My Custom Image"),
			LabName:           pulumi.String("{labName}"),
			Name:              pulumi.String("{customImageName}"),
			ResourceGroupName: pulumi.String("resourceGroupName"),
			Tags: pulumi.StringMap{
				"tagName1": pulumi.String("tagValue1"),
			},
			Vm: devtestlab.CustomImagePropertiesFromVmResponse{
				LinuxOsInfo: &devtestlab.LinuxOsInfoArgs{
					LinuxOsState: pulumi.String("NonDeprovisioned"),
				},
				SourceVmId: pulumi.String("/subscriptions/{subscriptionId}/resourcegroups/resourceGroupName/providers/microsoft.devtestlab/labs/{labName}/virtualmachines/{vmName}"),
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
import com.pulumi.azurenative.devtestlab.CustomImage;
import com.pulumi.azurenative.devtestlab.CustomImageArgs;
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
        var customImage = new CustomImage("customImage", CustomImageArgs.builder()        
            .description("My Custom Image")
            .labName("{labName}")
            .name("{customImageName}")
            .resourceGroupName("resourceGroupName")
            .tags(Map.of("tagName1", "tagValue1"))
            .vm(Map.ofEntries(
                Map.entry("linuxOsInfo", Map.of("linuxOsState", "NonDeprovisioned")),
                Map.entry("sourceVmId", "/subscriptions/{subscriptionId}/resourcegroups/resourceGroupName/providers/microsoft.devtestlab/labs/{labName}/virtualmachines/{vmName}")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const customImage = new azure_native.devtestlab.CustomImage("customImage", {
    description: "My Custom Image",
    labName: "{labName}",
    name: "{customImageName}",
    resourceGroupName: "resourceGroupName",
    tags: {
        tagName1: "tagValue1",
    },
    vm: {
        linuxOsInfo: {
            linuxOsState: "NonDeprovisioned",
        },
        sourceVmId: "/subscriptions/{subscriptionId}/resourcegroups/resourceGroupName/providers/microsoft.devtestlab/labs/{labName}/virtualmachines/{vmName}",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

custom_image = azure_native.devtestlab.CustomImage("customImage",
    description="My Custom Image",
    lab_name="{labName}",
    name="{customImageName}",
    resource_group_name="resourceGroupName",
    tags={
        "tagName1": "tagValue1",
    },
    vm=azure_native.devtestlab.CustomImagePropertiesFromVmResponseArgs(
        linux_os_info=azure_native.devtestlab.LinuxOsInfoArgs(
            linux_os_state="NonDeprovisioned",
        ),
        source_vm_id="/subscriptions/{subscriptionId}/resourcegroups/resourceGroupName/providers/microsoft.devtestlab/labs/{labName}/virtualmachines/{vmName}",
    ))

```

```yaml
resources:
  customImage:
    type: azure-native:devtestlab:CustomImage
    properties:
      description: My Custom Image
      labName: '{labName}'
      name: '{customImageName}'
      resourceGroupName: resourceGroupName
      tags:
        tagName1: tagValue1
      vm:
        linuxOsInfo:
          linuxOsState: NonDeprovisioned
        sourceVmId: /subscriptions/{subscriptionId}/resourcegroups/resourceGroupName/providers/microsoft.devtestlab/labs/{labName}/virtualmachines/{vmName}

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:devtestlab:CustomImage {customImageName} /subscriptions/{subscriptionId}/resourcegroups/resourceGroupName/providers/microsoft.devtestlab/labs/{labName}/customimages/{customImageName} 
```
