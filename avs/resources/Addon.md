An addon resource
API Version: 2022-05-01.
Previous API Version: 2020-07-17-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Addons_CreateOrUpdate_Arc
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var addon = new AzureNative.AVS.Addon("addon", new()
    {
        AddonName = "arc",
        PrivateCloudName = "cloud1",
        Properties = new AzureNative.AVS.Inputs.AddonArcPropertiesArgs
        {
            AddonType = "Arc",
            VCenter = "subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/rg_test/providers/Microsoft.ConnectedVMwarevSphere/VCenters/test-vcenter",
        },
        ResourceGroupName = "group1",
    });

});


```

```go
package main

import (
	avs "github.com/pulumi/pulumi-azure-native-sdk/avs"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := avs.NewAddon(ctx, "addon", &avs.AddonArgs{
			AddonName:        pulumi.String("arc"),
			PrivateCloudName: pulumi.String("cloud1"),
			Properties: avs.AddonArcProperties{
				AddonType: "Arc",
				VCenter:   "subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/rg_test/providers/Microsoft.ConnectedVMwarevSphere/VCenters/test-vcenter",
			},
			ResourceGroupName: pulumi.String("group1"),
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
import com.pulumi.azurenative.avs.Addon;
import com.pulumi.azurenative.avs.AddonArgs;
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
        var addon = new Addon("addon", AddonArgs.builder()        
            .addonName("arc")
            .privateCloudName("cloud1")
            .properties(Map.ofEntries(
                Map.entry("addonType", "Arc"),
                Map.entry("vCenter", "subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/rg_test/providers/Microsoft.ConnectedVMwarevSphere/VCenters/test-vcenter")
            ))
            .resourceGroupName("group1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const addon = new azure_native.avs.Addon("addon", {
    addonName: "arc",
    privateCloudName: "cloud1",
    properties: {
        addonType: "Arc",
        vCenter: "subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/rg_test/providers/Microsoft.ConnectedVMwarevSphere/VCenters/test-vcenter",
    },
    resourceGroupName: "group1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

addon = azure_native.avs.Addon("addon",
    addon_name="arc",
    private_cloud_name="cloud1",
    properties=azure_native.avs.AddonArcPropertiesArgs(
        addon_type="Arc",
        v_center="subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/rg_test/providers/Microsoft.ConnectedVMwarevSphere/VCenters/test-vcenter",
    ),
    resource_group_name="group1")

```

```yaml
resources:
  addon:
    type: azure-native:avs:Addon
    properties:
      addonName: arc
      privateCloudName: cloud1
      properties:
        addonType: Arc
        vCenter: subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/rg_test/providers/Microsoft.ConnectedVMwarevSphere/VCenters/test-vcenter
      resourceGroupName: group1

```

{{% /example %}}
{{% example %}}
### Addons_CreateOrUpdate_HCX
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var addon = new AzureNative.AVS.Addon("addon", new()
    {
        AddonName = "hcx",
        PrivateCloudName = "cloud1",
        Properties = new AzureNative.AVS.Inputs.AddonHcxPropertiesArgs
        {
            AddonType = "HCX",
            Offer = "VMware MaaS Cloud Provider (Enterprise)",
        },
        ResourceGroupName = "group1",
    });

});


```

```go
package main

import (
	avs "github.com/pulumi/pulumi-azure-native-sdk/avs"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := avs.NewAddon(ctx, "addon", &avs.AddonArgs{
			AddonName:        pulumi.String("hcx"),
			PrivateCloudName: pulumi.String("cloud1"),
			Properties: avs.AddonHcxProperties{
				AddonType: "HCX",
				Offer:     "VMware MaaS Cloud Provider (Enterprise)",
			},
			ResourceGroupName: pulumi.String("group1"),
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
import com.pulumi.azurenative.avs.Addon;
import com.pulumi.azurenative.avs.AddonArgs;
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
        var addon = new Addon("addon", AddonArgs.builder()        
            .addonName("hcx")
            .privateCloudName("cloud1")
            .properties(Map.ofEntries(
                Map.entry("addonType", "HCX"),
                Map.entry("offer", "VMware MaaS Cloud Provider (Enterprise)")
            ))
            .resourceGroupName("group1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const addon = new azure_native.avs.Addon("addon", {
    addonName: "hcx",
    privateCloudName: "cloud1",
    properties: {
        addonType: "HCX",
        offer: "VMware MaaS Cloud Provider (Enterprise)",
    },
    resourceGroupName: "group1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

addon = azure_native.avs.Addon("addon",
    addon_name="hcx",
    private_cloud_name="cloud1",
    properties=azure_native.avs.AddonHcxPropertiesArgs(
        addon_type="HCX",
        offer="VMware MaaS Cloud Provider (Enterprise)",
    ),
    resource_group_name="group1")

```

```yaml
resources:
  addon:
    type: azure-native:avs:Addon
    properties:
      addonName: hcx
      privateCloudName: cloud1
      properties:
        addonType: HCX
        offer: VMware MaaS Cloud Provider (Enterprise)
      resourceGroupName: group1

```

{{% /example %}}
{{% example %}}
### Addons_CreateOrUpdate_SRM
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var addon = new AzureNative.AVS.Addon("addon", new()
    {
        AddonName = "srm",
        PrivateCloudName = "cloud1",
        Properties = new AzureNative.AVS.Inputs.AddonSrmPropertiesArgs
        {
            AddonType = "SRM",
            LicenseKey = "41915178-A8FF-4A4D-B683-6D735AF5E3F5",
        },
        ResourceGroupName = "group1",
    });

});


```

```go
package main

import (
	avs "github.com/pulumi/pulumi-azure-native-sdk/avs"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := avs.NewAddon(ctx, "addon", &avs.AddonArgs{
			AddonName:        pulumi.String("srm"),
			PrivateCloudName: pulumi.String("cloud1"),
			Properties: avs.AddonSrmProperties{
				AddonType:  "SRM",
				LicenseKey: "41915178-A8FF-4A4D-B683-6D735AF5E3F5",
			},
			ResourceGroupName: pulumi.String("group1"),
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
import com.pulumi.azurenative.avs.Addon;
import com.pulumi.azurenative.avs.AddonArgs;
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
        var addon = new Addon("addon", AddonArgs.builder()        
            .addonName("srm")
            .privateCloudName("cloud1")
            .properties(Map.ofEntries(
                Map.entry("addonType", "SRM"),
                Map.entry("licenseKey", "41915178-A8FF-4A4D-B683-6D735AF5E3F5")
            ))
            .resourceGroupName("group1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const addon = new azure_native.avs.Addon("addon", {
    addonName: "srm",
    privateCloudName: "cloud1",
    properties: {
        addonType: "SRM",
        licenseKey: "41915178-A8FF-4A4D-B683-6D735AF5E3F5",
    },
    resourceGroupName: "group1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

addon = azure_native.avs.Addon("addon",
    addon_name="srm",
    private_cloud_name="cloud1",
    properties=azure_native.avs.AddonSrmPropertiesArgs(
        addon_type="SRM",
        license_key="41915178-A8FF-4A4D-B683-6D735AF5E3F5",
    ),
    resource_group_name="group1")

```

```yaml
resources:
  addon:
    type: azure-native:avs:Addon
    properties:
      addonName: srm
      privateCloudName: cloud1
      properties:
        addonType: SRM
        licenseKey: 41915178-A8FF-4A4D-B683-6D735AF5E3F5
      resourceGroupName: group1

```

{{% /example %}}
{{% example %}}
### Addons_CreateOrUpdate_VR
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var addon = new AzureNative.AVS.Addon("addon", new()
    {
        AddonName = "vr",
        PrivateCloudName = "cloud1",
        Properties = new AzureNative.AVS.Inputs.AddonVrPropertiesArgs
        {
            AddonType = "VR",
            VrsCount = 1,
        },
        ResourceGroupName = "group1",
    });

});


```

```go
package main

import (
	avs "github.com/pulumi/pulumi-azure-native-sdk/avs"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := avs.NewAddon(ctx, "addon", &avs.AddonArgs{
			AddonName:        pulumi.String("vr"),
			PrivateCloudName: pulumi.String("cloud1"),
			Properties: avs.AddonVrProperties{
				AddonType: "VR",
				VrsCount:  1,
			},
			ResourceGroupName: pulumi.String("group1"),
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
import com.pulumi.azurenative.avs.Addon;
import com.pulumi.azurenative.avs.AddonArgs;
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
        var addon = new Addon("addon", AddonArgs.builder()        
            .addonName("vr")
            .privateCloudName("cloud1")
            .properties(Map.ofEntries(
                Map.entry("addonType", "VR"),
                Map.entry("vrsCount", 1)
            ))
            .resourceGroupName("group1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const addon = new azure_native.avs.Addon("addon", {
    addonName: "vr",
    privateCloudName: "cloud1",
    properties: {
        addonType: "VR",
        vrsCount: 1,
    },
    resourceGroupName: "group1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

addon = azure_native.avs.Addon("addon",
    addon_name="vr",
    private_cloud_name="cloud1",
    properties=azure_native.avs.AddonVrPropertiesArgs(
        addon_type="VR",
        vrs_count=1,
    ),
    resource_group_name="group1")

```

```yaml
resources:
  addon:
    type: azure-native:avs:Addon
    properties:
      addonName: vr
      privateCloudName: cloud1
      properties:
        addonType: VR
        vrsCount: 1
      resourceGroupName: group1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:avs:Addon vr /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/group1/providers/Microsoft.AVS/privateClouds/cloud1/addons/vr 
```
