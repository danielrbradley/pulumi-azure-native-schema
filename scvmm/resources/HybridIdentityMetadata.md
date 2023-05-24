Defines the HybridIdentityMetadata.
API Version: 2022-05-21-preview.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateHybridIdentityMetadata
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var hybridIdentityMetadata = new AzureNative.ScVmm.HybridIdentityMetadata("hybridIdentityMetadata", new()
    {
        MetadataName = "default",
        PublicKey = "8ec7d60c-9700-40b1-8e6e-e5b2f6f477f2",
        ResourceGroupName = "testrg",
        ResourceUid = "f8b82dff-38ef-4220-99ef-d3a3f86ddc6c",
        VirtualMachineName = "ContosoVm",
    });

});


```

```go
package main

import (
	scvmm "github.com/pulumi/pulumi-azure-native-sdk/scvmm"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := scvmm.NewHybridIdentityMetadata(ctx, "hybridIdentityMetadata", &scvmm.HybridIdentityMetadataArgs{
			MetadataName:       pulumi.String("default"),
			PublicKey:          pulumi.String("8ec7d60c-9700-40b1-8e6e-e5b2f6f477f2"),
			ResourceGroupName:  pulumi.String("testrg"),
			ResourceUid:        pulumi.String("f8b82dff-38ef-4220-99ef-d3a3f86ddc6c"),
			VirtualMachineName: pulumi.String("ContosoVm"),
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
import com.pulumi.azurenative.scvmm.HybridIdentityMetadata;
import com.pulumi.azurenative.scvmm.HybridIdentityMetadataArgs;
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
        var hybridIdentityMetadata = new HybridIdentityMetadata("hybridIdentityMetadata", HybridIdentityMetadataArgs.builder()        
            .metadataName("default")
            .publicKey("8ec7d60c-9700-40b1-8e6e-e5b2f6f477f2")
            .resourceGroupName("testrg")
            .resourceUid("f8b82dff-38ef-4220-99ef-d3a3f86ddc6c")
            .virtualMachineName("ContosoVm")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const hybridIdentityMetadata = new azure_native.scvmm.HybridIdentityMetadata("hybridIdentityMetadata", {
    metadataName: "default",
    publicKey: "8ec7d60c-9700-40b1-8e6e-e5b2f6f477f2",
    resourceGroupName: "testrg",
    resourceUid: "f8b82dff-38ef-4220-99ef-d3a3f86ddc6c",
    virtualMachineName: "ContosoVm",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

hybrid_identity_metadata = azure_native.scvmm.HybridIdentityMetadata("hybridIdentityMetadata",
    metadata_name="default",
    public_key="8ec7d60c-9700-40b1-8e6e-e5b2f6f477f2",
    resource_group_name="testrg",
    resource_uid="f8b82dff-38ef-4220-99ef-d3a3f86ddc6c",
    virtual_machine_name="ContosoVm")

```

```yaml
resources:
  hybridIdentityMetadata:
    type: azure-native:scvmm:HybridIdentityMetadata
    properties:
      metadataName: default
      publicKey: 8ec7d60c-9700-40b1-8e6e-e5b2f6f477f2
      resourceGroupName: testrg
      resourceUid: f8b82dff-38ef-4220-99ef-d3a3f86ddc6c
      virtualMachineName: ContosoVm

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:scvmm:HybridIdentityMetadata default /subscriptions/fd3c3665-1729-4b7b-9a38-238e83b0f98b/resourceGroups/testrg/providers/Microsoft.ScVmm/VitualMachines/ContosoVm/hybridIdentityMetadatas/default 
```
