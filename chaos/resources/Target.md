Model that represents a Target resource.
API Version: 2022-10-01-preview.
Previous API Version: 2021-09-15-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create/update a Target that extends a virtual machine resource.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var target = new AzureNative.Chaos.Target("target", new()
    {
        ParentProviderNamespace = "Microsoft.Compute",
        ParentResourceName = "exampleVM",
        ParentResourceType = "virtualMachines",
        Properties = 
        {
            { "identities", new[]
            {
                
                {
                    { "subject", "CN=example.subject" },
                    { "type", "CertificateSubjectIssuer" },
                },
            } },
        },
        ResourceGroupName = "exampleRG",
        TargetName = "Microsoft-Agent",
    });

});


```

```go
package main

import (
	chaos "github.com/pulumi/pulumi-azure-native-sdk/chaos"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := chaos.NewTarget(ctx, "target", &chaos.TargetArgs{
			ParentProviderNamespace: pulumi.String("Microsoft.Compute"),
			ParentResourceName:      pulumi.String("exampleVM"),
			ParentResourceType:      pulumi.String("virtualMachines"),
			Properties: pulumi.Any{
				Identities: []map[string]interface{}{
					map[string]interface{}{
						"subject": "CN=example.subject",
						"type":    "CertificateSubjectIssuer",
					},
				},
			},
			ResourceGroupName: pulumi.String("exampleRG"),
			TargetName:        pulumi.String("Microsoft-Agent"),
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
import com.pulumi.azurenative.chaos.Target;
import com.pulumi.azurenative.chaos.TargetArgs;
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
        var target = new Target("target", TargetArgs.builder()        
            .parentProviderNamespace("Microsoft.Compute")
            .parentResourceName("exampleVM")
            .parentResourceType("virtualMachines")
            .properties(Map.of("identities", Map.ofEntries(
                Map.entry("subject", "CN=example.subject"),
                Map.entry("type", "CertificateSubjectIssuer")
            )))
            .resourceGroupName("exampleRG")
            .targetName("Microsoft-Agent")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const target = new azure_native.chaos.Target("target", {
    parentProviderNamespace: "Microsoft.Compute",
    parentResourceName: "exampleVM",
    parentResourceType: "virtualMachines",
    properties: {
        identities: [{
            subject: "CN=example.subject",
            type: "CertificateSubjectIssuer",
        }],
    },
    resourceGroupName: "exampleRG",
    targetName: "Microsoft-Agent",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

target = azure_native.chaos.Target("target",
    parent_provider_namespace="Microsoft.Compute",
    parent_resource_name="exampleVM",
    parent_resource_type="virtualMachines",
    properties={
        "identities": [{
            "subject": "CN=example.subject",
            "type": "CertificateSubjectIssuer",
        }],
    },
    resource_group_name="exampleRG",
    target_name="Microsoft-Agent")

```

```yaml
resources:
  target:
    type: azure-native:chaos:Target
    properties:
      parentProviderNamespace: Microsoft.Compute
      parentResourceName: exampleVM
      parentResourceType: virtualMachines
      properties:
        identities:
          - subject: CN=example.subject
            type: CertificateSubjectIssuer
      resourceGroupName: exampleRG
      targetName: Microsoft-Agent

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:chaos:Target Microsoft-Agent /subscriptions/6b052e15-03d3-4f17-b2e1-be7f07588291/resourceGroups/exampleRG/providers/Microsoft.Compute/virtualMachines/exampleVM/providers/Microsoft.Chaos/targets/Microsoft-Agent 
```
