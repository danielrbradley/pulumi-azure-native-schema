Defines the HybridIdentityMetadata.
API Version: 2022-07-15-preview.
Previous API Version: 2020-10-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

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
    var hybridIdentityMetadatum = new AzureNative.ConnectedVMwarevSphere.HybridIdentityMetadatum("hybridIdentityMetadatum", new()
    {
        MetadataName = "default",
        PublicKey = "8ec7d60c-9700-40b1-8e6e-e5b2f6f477f2",
        ResourceGroupName = "testrg",
        VirtualMachineName = "ContosoVm",
        VmId = "f8b82dff-38ef-4220-99ef-d3a3f86ddc6c",
    });

});


```

```go
package main

import (
	connectedvmwarevsphere "github.com/pulumi/pulumi-azure-native-sdk/connectedvmwarevsphere"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := connectedvmwarevsphere.NewHybridIdentityMetadatum(ctx, "hybridIdentityMetadatum", &connectedvmwarevsphere.HybridIdentityMetadatumArgs{
			MetadataName:       pulumi.String("default"),
			PublicKey:          pulumi.String("8ec7d60c-9700-40b1-8e6e-e5b2f6f477f2"),
			ResourceGroupName:  pulumi.String("testrg"),
			VirtualMachineName: pulumi.String("ContosoVm"),
			VmId:               pulumi.String("f8b82dff-38ef-4220-99ef-d3a3f86ddc6c"),
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
import com.pulumi.azurenative.connectedvmwarevsphere.HybridIdentityMetadatum;
import com.pulumi.azurenative.connectedvmwarevsphere.HybridIdentityMetadatumArgs;
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
        var hybridIdentityMetadatum = new HybridIdentityMetadatum("hybridIdentityMetadatum", HybridIdentityMetadatumArgs.builder()        
            .metadataName("default")
            .publicKey("8ec7d60c-9700-40b1-8e6e-e5b2f6f477f2")
            .resourceGroupName("testrg")
            .virtualMachineName("ContosoVm")
            .vmId("f8b82dff-38ef-4220-99ef-d3a3f86ddc6c")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const hybridIdentityMetadatum = new azure_native.connectedvmwarevsphere.HybridIdentityMetadatum("hybridIdentityMetadatum", {
    metadataName: "default",
    publicKey: "8ec7d60c-9700-40b1-8e6e-e5b2f6f477f2",
    resourceGroupName: "testrg",
    virtualMachineName: "ContosoVm",
    vmId: "f8b82dff-38ef-4220-99ef-d3a3f86ddc6c",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

hybrid_identity_metadatum = azure_native.connectedvmwarevsphere.HybridIdentityMetadatum("hybridIdentityMetadatum",
    metadata_name="default",
    public_key="8ec7d60c-9700-40b1-8e6e-e5b2f6f477f2",
    resource_group_name="testrg",
    virtual_machine_name="ContosoVm",
    vm_id="f8b82dff-38ef-4220-99ef-d3a3f86ddc6c")

```

```yaml
resources:
  hybridIdentityMetadatum:
    type: azure-native:connectedvmwarevsphere:HybridIdentityMetadatum
    properties:
      metadataName: default
      publicKey: 8ec7d60c-9700-40b1-8e6e-e5b2f6f477f2
      resourceGroupName: testrg
      virtualMachineName: ContosoVm
      vmId: f8b82dff-38ef-4220-99ef-d3a3f86ddc6c

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:connectedvmwarevsphere:HybridIdentityMetadatum testItem /subscriptions/fd3c3665-1729-4b7b-9a38-238e83b0f98b/resourceGroups/testrg/providers/Microsoft.ConnectedVMwarevSphere/VitualMachines/ContosoVm/hybridIdentityMetadatas/default 
```
