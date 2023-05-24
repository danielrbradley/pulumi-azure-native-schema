This type describes a volume resource.
API Version: 2018-09-01-preview.
Previous API Version: 2018-09-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateOrUpdateVolume
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var volume = new AzureNative.ServiceFabricMesh.Volume("volume", new()
    {
        AzureFileParameters = new AzureNative.ServiceFabricMesh.Inputs.VolumeProviderParametersAzureFileArgs
        {
            AccountKey = "provide-account-key-here",
            AccountName = "sbzdemoaccount",
            ShareName = "sharel",
        },
        Description = "Service Fabric Mesh sample volume.",
        Location = "EastUS",
        Provider = "SFAzureFile",
        ResourceGroupName = "sbz_demo",
        Tags = null,
        VolumeResourceName = "sampleVolume",
    });

});


```

```go
package main

import (
	servicefabricmesh "github.com/pulumi/pulumi-azure-native-sdk/servicefabricmesh"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := servicefabricmesh.NewVolume(ctx, "volume", &servicefabricmesh.VolumeArgs{
			AzureFileParameters: &servicefabricmesh.VolumeProviderParametersAzureFileArgs{
				AccountKey:  pulumi.String("provide-account-key-here"),
				AccountName: pulumi.String("sbzdemoaccount"),
				ShareName:   pulumi.String("sharel"),
			},
			Description:        pulumi.String("Service Fabric Mesh sample volume."),
			Location:           pulumi.String("EastUS"),
			Provider:           pulumi.String("SFAzureFile"),
			ResourceGroupName:  pulumi.String("sbz_demo"),
			Tags:               nil,
			VolumeResourceName: pulumi.String("sampleVolume"),
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
import com.pulumi.azurenative.servicefabricmesh.Volume;
import com.pulumi.azurenative.servicefabricmesh.VolumeArgs;
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
        var volume = new Volume("volume", VolumeArgs.builder()        
            .azureFileParameters(Map.ofEntries(
                Map.entry("accountKey", "provide-account-key-here"),
                Map.entry("accountName", "sbzdemoaccount"),
                Map.entry("shareName", "sharel")
            ))
            .description("Service Fabric Mesh sample volume.")
            .location("EastUS")
            .provider("SFAzureFile")
            .resourceGroupName("sbz_demo")
            .tags()
            .volumeResourceName("sampleVolume")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const volume = new azure_native.servicefabricmesh.Volume("volume", {
    azureFileParameters: {
        accountKey: "provide-account-key-here",
        accountName: "sbzdemoaccount",
        shareName: "sharel",
    },
    description: "Service Fabric Mesh sample volume.",
    location: "EastUS",
    provider: "SFAzureFile",
    resourceGroupName: "sbz_demo",
    tags: {},
    volumeResourceName: "sampleVolume",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

volume = azure_native.servicefabricmesh.Volume("volume",
    azure_file_parameters=azure_native.servicefabricmesh.VolumeProviderParametersAzureFileArgs(
        account_key="provide-account-key-here",
        account_name="sbzdemoaccount",
        share_name="sharel",
    ),
    description="Service Fabric Mesh sample volume.",
    location="EastUS",
    provider="SFAzureFile",
    resource_group_name="sbz_demo",
    tags={},
    volume_resource_name="sampleVolume")

```

```yaml
resources:
  volume:
    type: azure-native:servicefabricmesh:Volume
    properties:
      azureFileParameters:
        accountKey: provide-account-key-here
        accountName: sbzdemoaccount
        shareName: sharel
      description: Service Fabric Mesh sample volume.
      location: EastUS
      provider: SFAzureFile
      resourceGroupName: sbz_demo
      tags: {}
      volumeResourceName: sampleVolume

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:servicefabricmesh:Volume sampleVolume /subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/sbz_demo/providers/Microsoft.ServiceFabricMesh/volumes/sampleVolume 
```
