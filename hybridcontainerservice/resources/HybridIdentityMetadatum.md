Defines the hybridIdentityMetadata.
API Version: 2022-09-01-preview.
Previous API Version: 2022-05-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

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
    var hybridIdentityMetadatum = new AzureNative.HybridContainerService.HybridIdentityMetadatum("hybridIdentityMetadatum", new()
    {
        HybridIdentityMetadataResourceName = "default",
        PublicKey = "8ec7d60c-9700-40b1-8e6e-e5b2f6f477f2",
        ResourceGroupName = "testrg",
        ResourceName = "ContosoTargetCluster",
        ResourceUid = "f8b82dff-38ef-4220-99ef-d3a3f86ddc6c",
    });

});


```

```go
package main

import (
	hybridcontainerservice "github.com/pulumi/pulumi-azure-native-sdk/hybridcontainerservice"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := hybridcontainerservice.NewHybridIdentityMetadatum(ctx, "hybridIdentityMetadatum", &hybridcontainerservice.HybridIdentityMetadatumArgs{
			HybridIdentityMetadataResourceName: pulumi.String("default"),
			PublicKey:                          pulumi.String("8ec7d60c-9700-40b1-8e6e-e5b2f6f477f2"),
			ResourceGroupName:                  pulumi.String("testrg"),
			ResourceName:                       pulumi.String("ContosoTargetCluster"),
			ResourceUid:                        pulumi.String("f8b82dff-38ef-4220-99ef-d3a3f86ddc6c"),
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
import com.pulumi.azurenative.hybridcontainerservice.HybridIdentityMetadatum;
import com.pulumi.azurenative.hybridcontainerservice.HybridIdentityMetadatumArgs;
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
            .hybridIdentityMetadataResourceName("default")
            .publicKey("8ec7d60c-9700-40b1-8e6e-e5b2f6f477f2")
            .resourceGroupName("testrg")
            .resourceName("ContosoTargetCluster")
            .resourceUid("f8b82dff-38ef-4220-99ef-d3a3f86ddc6c")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const hybridIdentityMetadatum = new azure_native.hybridcontainerservice.HybridIdentityMetadatum("hybridIdentityMetadatum", {
    hybridIdentityMetadataResourceName: "default",
    publicKey: "8ec7d60c-9700-40b1-8e6e-e5b2f6f477f2",
    resourceGroupName: "testrg",
    resourceName: "ContosoTargetCluster",
    resourceUid: "f8b82dff-38ef-4220-99ef-d3a3f86ddc6c",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

hybrid_identity_metadatum = azure_native.hybridcontainerservice.HybridIdentityMetadatum("hybridIdentityMetadatum",
    hybrid_identity_metadata_resource_name="default",
    public_key="8ec7d60c-9700-40b1-8e6e-e5b2f6f477f2",
    resource_group_name="testrg",
    resource_name_="ContosoTargetCluster",
    resource_uid="f8b82dff-38ef-4220-99ef-d3a3f86ddc6c")

```

```yaml
resources:
  hybridIdentityMetadatum:
    type: azure-native:hybridcontainerservice:HybridIdentityMetadatum
    properties:
      hybridIdentityMetadataResourceName: default
      publicKey: 8ec7d60c-9700-40b1-8e6e-e5b2f6f477f2
      resourceGroupName: testrg
      resourceName: ContosoTargetCluster
      resourceUid: f8b82dff-38ef-4220-99ef-d3a3f86ddc6c

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:hybridcontainerservice:HybridIdentityMetadatum default /subscriptions/fd3c3665-1729-4b7b-9a38-238e83b0f98b/resourceGroups/testrg/providers/Microsoft.HybridContainerService/provisionedClusters/ContosoTargetCluster/hybridIdentityMetadata/default 
```
