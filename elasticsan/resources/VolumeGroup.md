Response for Volume Group request.
API Version: 2021-11-20-preview.
Previous API Version: 2021-11-20-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### VolumeGroups_Create_MaximumSet_Gen
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var volumeGroup = new AzureNative.ElasticSan.VolumeGroup("volumeGroup", new()
    {
        ElasticSanName = "ti7q-k952-1qB3J_5",
        Encryption = "EncryptionAtRestWithPlatformKey",
        NetworkAcls = new AzureNative.ElasticSan.Inputs.NetworkRuleSetArgs
        {
            VirtualNetworkRules = new[]
            {
                new AzureNative.ElasticSan.Inputs.VirtualNetworkRuleArgs
                {
                    Action = AzureNative.ElasticSan.Action.Allow,
                    VirtualNetworkResourceId = "aaaaaaaaaaaaaaaa",
                },
            },
        },
        ProtocolType = "Iscsi",
        ResourceGroupName = "rgelasticsan",
        Tags = 
        {
            { "key5933", "aaaaaaaaaaaaaaaaaaaaaaaaaaaaa" },
        },
        VolumeGroupName = "u_5I_1j4t3",
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
		_, err := elasticsan.NewVolumeGroup(ctx, "volumeGroup", &elasticsan.VolumeGroupArgs{
			ElasticSanName: pulumi.String("ti7q-k952-1qB3J_5"),
			Encryption:     pulumi.String("EncryptionAtRestWithPlatformKey"),
			NetworkAcls: elasticsan.NetworkRuleSetResponse{
				VirtualNetworkRules: elasticsan.VirtualNetworkRuleArray{
					&elasticsan.VirtualNetworkRuleArgs{
						Action:                   elasticsan.ActionAllow,
						VirtualNetworkResourceId: pulumi.String("aaaaaaaaaaaaaaaa"),
					},
				},
			},
			ProtocolType:      pulumi.String("Iscsi"),
			ResourceGroupName: pulumi.String("rgelasticsan"),
			Tags: pulumi.StringMap{
				"key5933": pulumi.String("aaaaaaaaaaaaaaaaaaaaaaaaaaaaa"),
			},
			VolumeGroupName: pulumi.String("u_5I_1j4t3"),
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
import com.pulumi.azurenative.elasticsan.VolumeGroup;
import com.pulumi.azurenative.elasticsan.VolumeGroupArgs;
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
        var volumeGroup = new VolumeGroup("volumeGroup", VolumeGroupArgs.builder()        
            .elasticSanName("ti7q-k952-1qB3J_5")
            .encryption("EncryptionAtRestWithPlatformKey")
            .networkAcls(Map.of("virtualNetworkRules", Map.ofEntries(
                Map.entry("action", "Allow"),
                Map.entry("virtualNetworkResourceId", "aaaaaaaaaaaaaaaa")
            )))
            .protocolType("Iscsi")
            .resourceGroupName("rgelasticsan")
            .tags(Map.of("key5933", "aaaaaaaaaaaaaaaaaaaaaaaaaaaaa"))
            .volumeGroupName("u_5I_1j4t3")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const volumeGroup = new azure_native.elasticsan.VolumeGroup("volumeGroup", {
    elasticSanName: "ti7q-k952-1qB3J_5",
    encryption: "EncryptionAtRestWithPlatformKey",
    networkAcls: {
        virtualNetworkRules: [{
            action: azure_native.elasticsan.Action.Allow,
            virtualNetworkResourceId: "aaaaaaaaaaaaaaaa",
        }],
    },
    protocolType: "Iscsi",
    resourceGroupName: "rgelasticsan",
    tags: {
        key5933: "aaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
    },
    volumeGroupName: "u_5I_1j4t3",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

volume_group = azure_native.elasticsan.VolumeGroup("volumeGroup",
    elastic_san_name="ti7q-k952-1qB3J_5",
    encryption="EncryptionAtRestWithPlatformKey",
    network_acls=azure_native.elasticsan.NetworkRuleSetResponseArgs(
        virtual_network_rules=[azure_native.elasticsan.VirtualNetworkRuleArgs(
            action=azure_native.elasticsan.Action.ALLOW,
            virtual_network_resource_id="aaaaaaaaaaaaaaaa",
        )],
    ),
    protocol_type="Iscsi",
    resource_group_name="rgelasticsan",
    tags={
        "key5933": "aaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
    },
    volume_group_name="u_5I_1j4t3")

```

```yaml
resources:
  volumeGroup:
    type: azure-native:elasticsan:VolumeGroup
    properties:
      elasticSanName: ti7q-k952-1qB3J_5
      encryption: EncryptionAtRestWithPlatformKey
      networkAcls:
        virtualNetworkRules:
          - action: Allow
            virtualNetworkResourceId: aaaaaaaaaaaaaaaa
      protocolType: Iscsi
      resourceGroupName: rgelasticsan
      tags:
        key5933: aaaaaaaaaaaaaaaaaaaaaaaaaaaaa
      volumeGroupName: u_5I_1j4t3

```

{{% /example %}}
{{% example %}}
### VolumeGroups_Create_MinimumSet_Gen
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var volumeGroup = new AzureNative.ElasticSan.VolumeGroup("volumeGroup", new()
    {
        ElasticSanName = "ti7q-k952-1qB3J_5",
        ResourceGroupName = "rgelasticsan",
        VolumeGroupName = "u_5I_1j4t3",
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
		_, err := elasticsan.NewVolumeGroup(ctx, "volumeGroup", &elasticsan.VolumeGroupArgs{
			ElasticSanName:    pulumi.String("ti7q-k952-1qB3J_5"),
			ResourceGroupName: pulumi.String("rgelasticsan"),
			VolumeGroupName:   pulumi.String("u_5I_1j4t3"),
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
import com.pulumi.azurenative.elasticsan.VolumeGroup;
import com.pulumi.azurenative.elasticsan.VolumeGroupArgs;
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
        var volumeGroup = new VolumeGroup("volumeGroup", VolumeGroupArgs.builder()        
            .elasticSanName("ti7q-k952-1qB3J_5")
            .resourceGroupName("rgelasticsan")
            .volumeGroupName("u_5I_1j4t3")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const volumeGroup = new azure_native.elasticsan.VolumeGroup("volumeGroup", {
    elasticSanName: "ti7q-k952-1qB3J_5",
    resourceGroupName: "rgelasticsan",
    volumeGroupName: "u_5I_1j4t3",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

volume_group = azure_native.elasticsan.VolumeGroup("volumeGroup",
    elastic_san_name="ti7q-k952-1qB3J_5",
    resource_group_name="rgelasticsan",
    volume_group_name="u_5I_1j4t3")

```

```yaml
resources:
  volumeGroup:
    type: azure-native:elasticsan:VolumeGroup
    properties:
      elasticSanName: ti7q-k952-1qB3J_5
      resourceGroupName: rgelasticsan
      volumeGroupName: u_5I_1j4t3

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:elasticsan:VolumeGroup aaaaaaaaaaaaaaaaaaaaaa aaaaaaaaaaaaaaaaaaaaaaaaaaa 
```
