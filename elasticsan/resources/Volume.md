Response for Volume request.
API Version: 2021-11-20-preview.
Previous API Version: 2021-11-20-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Volumes_Create_MaximumSet_Gen
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var volume = new AzureNative.ElasticSan.Volume("volume", new()
    {
        CreationData = new AzureNative.ElasticSan.Inputs.SourceCreationDataArgs
        {
            CreateSource = AzureNative.ElasticSan.VolumeCreateOption.None,
            SourceUri = "aaaaaa",
        },
        ElasticSanName = "ti7q-k952-1qB3J_5",
        ResourceGroupName = "rgelasticsan",
        SizeGiB = 22,
        Tags = 
        {
            { "key7423", "aaaa" },
        },
        VolumeGroupName = "u_5I_1j4t3",
        VolumeName = "9132y",
    });

});


```

```go
package main

import (
	elasticsan "github.com/pulumi/pulumi-azure-native-sdk/elasticsan"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := elasticsan.NewVolume(ctx, "volume", &elasticsan.VolumeArgs{
			CreationData: &elasticsan.SourceCreationDataArgs{
				CreateSource: elasticsan.VolumeCreateOptionNone,
				SourceUri:    pulumi.String("aaaaaa"),
			},
			ElasticSanName:    pulumi.String("ti7q-k952-1qB3J_5"),
			ResourceGroupName: pulumi.String("rgelasticsan"),
			SizeGiB:           pulumi.Float64(22),
			Tags: pulumi.StringMap{
				"key7423": pulumi.String("aaaa"),
			},
			VolumeGroupName: pulumi.String("u_5I_1j4t3"),
			VolumeName:      pulumi.String("9132y"),
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
import com.pulumi.azurenative.elasticsan.Volume;
import com.pulumi.azurenative.elasticsan.VolumeArgs;
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
            .creationData(Map.ofEntries(
                Map.entry("createSource", "None"),
                Map.entry("sourceUri", "aaaaaa")
            ))
            .elasticSanName("ti7q-k952-1qB3J_5")
            .resourceGroupName("rgelasticsan")
            .sizeGiB(22)
            .tags(Map.of("key7423", "aaaa"))
            .volumeGroupName("u_5I_1j4t3")
            .volumeName("9132y")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const volume = new azure_native.elasticsan.Volume("volume", {
    creationData: {
        createSource: azure_native.elasticsan.VolumeCreateOption.None,
        sourceUri: "aaaaaa",
    },
    elasticSanName: "ti7q-k952-1qB3J_5",
    resourceGroupName: "rgelasticsan",
    sizeGiB: 22,
    tags: {
        key7423: "aaaa",
    },
    volumeGroupName: "u_5I_1j4t3",
    volumeName: "9132y",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

volume = azure_native.elasticsan.Volume("volume",
    creation_data=azure_native.elasticsan.SourceCreationDataArgs(
        create_source=azure_native.elasticsan.VolumeCreateOption.NONE,
        source_uri="aaaaaa",
    ),
    elastic_san_name="ti7q-k952-1qB3J_5",
    resource_group_name="rgelasticsan",
    size_gi_b=22,
    tags={
        "key7423": "aaaa",
    },
    volume_group_name="u_5I_1j4t3",
    volume_name="9132y")

```

```yaml
resources:
  volume:
    type: azure-native:elasticsan:Volume
    properties:
      creationData:
        createSource: None
        sourceUri: aaaaaa
      elasticSanName: ti7q-k952-1qB3J_5
      resourceGroupName: rgelasticsan
      sizeGiB: 22
      tags:
        key7423: aaaa
      volumeGroupName: u_5I_1j4t3
      volumeName: 9132y

```

{{% /example %}}
{{% example %}}
### Volumes_Create_MinimumSet_Gen
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var volume = new AzureNative.ElasticSan.Volume("volume", new()
    {
        ElasticSanName = "ti7q-k952-1qB3J_5",
        ResourceGroupName = "rgelasticsan",
        VolumeGroupName = "u_5I_1j4t3",
        VolumeName = "9132y",
    });

});


```

```go
package main

import (
	elasticsan "github.com/pulumi/pulumi-azure-native-sdk/elasticsan"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := elasticsan.NewVolume(ctx, "volume", &elasticsan.VolumeArgs{
			ElasticSanName:    pulumi.String("ti7q-k952-1qB3J_5"),
			ResourceGroupName: pulumi.String("rgelasticsan"),
			VolumeGroupName:   pulumi.String("u_5I_1j4t3"),
			VolumeName:        pulumi.String("9132y"),
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
import com.pulumi.azurenative.elasticsan.Volume;
import com.pulumi.azurenative.elasticsan.VolumeArgs;
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
            .elasticSanName("ti7q-k952-1qB3J_5")
            .resourceGroupName("rgelasticsan")
            .volumeGroupName("u_5I_1j4t3")
            .volumeName("9132y")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const volume = new azure_native.elasticsan.Volume("volume", {
    elasticSanName: "ti7q-k952-1qB3J_5",
    resourceGroupName: "rgelasticsan",
    volumeGroupName: "u_5I_1j4t3",
    volumeName: "9132y",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

volume = azure_native.elasticsan.Volume("volume",
    elastic_san_name="ti7q-k952-1qB3J_5",
    resource_group_name="rgelasticsan",
    volume_group_name="u_5I_1j4t3",
    volume_name="9132y")

```

```yaml
resources:
  volume:
    type: azure-native:elasticsan:Volume
    properties:
      elasticSanName: ti7q-k952-1qB3J_5
      resourceGroupName: rgelasticsan
      volumeGroupName: u_5I_1j4t3
      volumeName: 9132y

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:elasticsan:Volume aaaaaaaaaaaa aaaaaaaa 
```
