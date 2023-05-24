Agent Pool.
API Version: 2023-01-01.
Previous API Version: 2021-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create Agent Pool using an agent pool snapshot
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var agentPool = new AzureNative.ContainerService.AgentPool("agentPool", new()
    {
        AgentPoolName = "agentpool1",
        Count = 3,
        CreationData = new AzureNative.ContainerService.Inputs.CreationDataArgs
        {
            SourceResourceId = "/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.ContainerService/snapshots/snapshot1",
        },
        EnableFIPS = true,
        OrchestratorVersion = "",
        OsType = "Linux",
        ResourceGroupName = "rg1",
        ResourceName = "clustername1",
        VmSize = "Standard_DS2_v2",
    });

});


```

```go
package main

import (
	containerservice "github.com/pulumi/pulumi-azure-native-sdk/containerservice"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := containerservice.NewAgentPool(ctx, "agentPool", &containerservice.AgentPoolArgs{
			AgentPoolName: pulumi.String("agentpool1"),
			Count:         pulumi.Int(3),
			CreationData: &containerservice.CreationDataArgs{
				SourceResourceId: pulumi.String("/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.ContainerService/snapshots/snapshot1"),
			},
			EnableFIPS:          pulumi.Bool(true),
			OrchestratorVersion: pulumi.String(""),
			OsType:              pulumi.String("Linux"),
			ResourceGroupName:   pulumi.String("rg1"),
			ResourceName:        pulumi.String("clustername1"),
			VmSize:              pulumi.String("Standard_DS2_v2"),
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
import com.pulumi.azurenative.containerservice.AgentPool;
import com.pulumi.azurenative.containerservice.AgentPoolArgs;
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
        var agentPool = new AgentPool("agentPool", AgentPoolArgs.builder()        
            .agentPoolName("agentpool1")
            .count(3)
            .creationData(Map.of("sourceResourceId", "/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.ContainerService/snapshots/snapshot1"))
            .enableFIPS(true)
            .orchestratorVersion("")
            .osType("Linux")
            .resourceGroupName("rg1")
            .resourceName("clustername1")
            .vmSize("Standard_DS2_v2")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const agentPool = new azure_native.containerservice.AgentPool("agentPool", {
    agentPoolName: "agentpool1",
    count: 3,
    creationData: {
        sourceResourceId: "/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.ContainerService/snapshots/snapshot1",
    },
    enableFIPS: true,
    orchestratorVersion: "",
    osType: "Linux",
    resourceGroupName: "rg1",
    resourceName: "clustername1",
    vmSize: "Standard_DS2_v2",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

agent_pool = azure_native.containerservice.AgentPool("agentPool",
    agent_pool_name="agentpool1",
    count=3,
    creation_data=azure_native.containerservice.CreationDataArgs(
        source_resource_id="/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.ContainerService/snapshots/snapshot1",
    ),
    enable_fips=True,
    orchestrator_version="",
    os_type="Linux",
    resource_group_name="rg1",
    resource_name_="clustername1",
    vm_size="Standard_DS2_v2")

```

```yaml
resources:
  agentPool:
    type: azure-native:containerservice:AgentPool
    properties:
      agentPoolName: agentpool1
      count: 3
      creationData:
        sourceResourceId: /subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.ContainerService/snapshots/snapshot1
      enableFIPS: true
      orchestratorVersion:
      osType: Linux
      resourceGroupName: rg1
      resourceName: clustername1
      vmSize: Standard_DS2_v2

```

{{% /example %}}
{{% example %}}
### Create Agent Pool with Dedicated Host Group
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var agentPool = new AzureNative.ContainerService.AgentPool("agentPool", new()
    {
        AgentPoolName = "agentpool1",
        Count = 3,
        HostGroupID = "/subscriptions/subid1/resourcegroups/rg/providers/Microsoft.Compute/hostGroups/hostgroup1",
        OrchestratorVersion = "",
        OsType = "Linux",
        ResourceGroupName = "rg1",
        ResourceName = "clustername1",
        VmSize = "Standard_DS2_v2",
    });

});


```

```go
package main

import (
	containerservice "github.com/pulumi/pulumi-azure-native-sdk/containerservice"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := containerservice.NewAgentPool(ctx, "agentPool", &containerservice.AgentPoolArgs{
			AgentPoolName:       pulumi.String("agentpool1"),
			Count:               pulumi.Int(3),
			HostGroupID:         pulumi.String("/subscriptions/subid1/resourcegroups/rg/providers/Microsoft.Compute/hostGroups/hostgroup1"),
			OrchestratorVersion: pulumi.String(""),
			OsType:              pulumi.String("Linux"),
			ResourceGroupName:   pulumi.String("rg1"),
			ResourceName:        pulumi.String("clustername1"),
			VmSize:              pulumi.String("Standard_DS2_v2"),
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
import com.pulumi.azurenative.containerservice.AgentPool;
import com.pulumi.azurenative.containerservice.AgentPoolArgs;
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
        var agentPool = new AgentPool("agentPool", AgentPoolArgs.builder()        
            .agentPoolName("agentpool1")
            .count(3)
            .hostGroupID("/subscriptions/subid1/resourcegroups/rg/providers/Microsoft.Compute/hostGroups/hostgroup1")
            .orchestratorVersion("")
            .osType("Linux")
            .resourceGroupName("rg1")
            .resourceName("clustername1")
            .vmSize("Standard_DS2_v2")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const agentPool = new azure_native.containerservice.AgentPool("agentPool", {
    agentPoolName: "agentpool1",
    count: 3,
    hostGroupID: "/subscriptions/subid1/resourcegroups/rg/providers/Microsoft.Compute/hostGroups/hostgroup1",
    orchestratorVersion: "",
    osType: "Linux",
    resourceGroupName: "rg1",
    resourceName: "clustername1",
    vmSize: "Standard_DS2_v2",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

agent_pool = azure_native.containerservice.AgentPool("agentPool",
    agent_pool_name="agentpool1",
    count=3,
    host_group_id="/subscriptions/subid1/resourcegroups/rg/providers/Microsoft.Compute/hostGroups/hostgroup1",
    orchestrator_version="",
    os_type="Linux",
    resource_group_name="rg1",
    resource_name_="clustername1",
    vm_size="Standard_DS2_v2")

```

```yaml
resources:
  agentPool:
    type: azure-native:containerservice:AgentPool
    properties:
      agentPoolName: agentpool1
      count: 3
      hostGroupID: /subscriptions/subid1/resourcegroups/rg/providers/Microsoft.Compute/hostGroups/hostgroup1
      orchestratorVersion:
      osType: Linux
      resourceGroupName: rg1
      resourceName: clustername1
      vmSize: Standard_DS2_v2

```

{{% /example %}}
{{% example %}}
### Create Agent Pool with EncryptionAtHost enabled
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var agentPool = new AzureNative.ContainerService.AgentPool("agentPool", new()
    {
        AgentPoolName = "agentpool1",
        Count = 3,
        EnableEncryptionAtHost = true,
        OrchestratorVersion = "",
        OsType = "Linux",
        ResourceGroupName = "rg1",
        ResourceName = "clustername1",
        VmSize = "Standard_DS2_v2",
    });

});


```

```go
package main

import (
	containerservice "github.com/pulumi/pulumi-azure-native-sdk/containerservice"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := containerservice.NewAgentPool(ctx, "agentPool", &containerservice.AgentPoolArgs{
			AgentPoolName:          pulumi.String("agentpool1"),
			Count:                  pulumi.Int(3),
			EnableEncryptionAtHost: pulumi.Bool(true),
			OrchestratorVersion:    pulumi.String(""),
			OsType:                 pulumi.String("Linux"),
			ResourceGroupName:      pulumi.String("rg1"),
			ResourceName:           pulumi.String("clustername1"),
			VmSize:                 pulumi.String("Standard_DS2_v2"),
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
import com.pulumi.azurenative.containerservice.AgentPool;
import com.pulumi.azurenative.containerservice.AgentPoolArgs;
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
        var agentPool = new AgentPool("agentPool", AgentPoolArgs.builder()        
            .agentPoolName("agentpool1")
            .count(3)
            .enableEncryptionAtHost(true)
            .orchestratorVersion("")
            .osType("Linux")
            .resourceGroupName("rg1")
            .resourceName("clustername1")
            .vmSize("Standard_DS2_v2")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const agentPool = new azure_native.containerservice.AgentPool("agentPool", {
    agentPoolName: "agentpool1",
    count: 3,
    enableEncryptionAtHost: true,
    orchestratorVersion: "",
    osType: "Linux",
    resourceGroupName: "rg1",
    resourceName: "clustername1",
    vmSize: "Standard_DS2_v2",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

agent_pool = azure_native.containerservice.AgentPool("agentPool",
    agent_pool_name="agentpool1",
    count=3,
    enable_encryption_at_host=True,
    orchestrator_version="",
    os_type="Linux",
    resource_group_name="rg1",
    resource_name_="clustername1",
    vm_size="Standard_DS2_v2")

```

```yaml
resources:
  agentPool:
    type: azure-native:containerservice:AgentPool
    properties:
      agentPoolName: agentpool1
      count: 3
      enableEncryptionAtHost: true
      orchestratorVersion:
      osType: Linux
      resourceGroupName: rg1
      resourceName: clustername1
      vmSize: Standard_DS2_v2

```

{{% /example %}}
{{% example %}}
### Create Agent Pool with Ephemeral OS Disk
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var agentPool = new AzureNative.ContainerService.AgentPool("agentPool", new()
    {
        AgentPoolName = "agentpool1",
        Count = 3,
        OrchestratorVersion = "",
        OsDiskSizeGB = 64,
        OsDiskType = "Ephemeral",
        OsType = "Linux",
        ResourceGroupName = "rg1",
        ResourceName = "clustername1",
        VmSize = "Standard_DS2_v2",
    });

});


```

```go
package main

import (
	containerservice "github.com/pulumi/pulumi-azure-native-sdk/containerservice"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := containerservice.NewAgentPool(ctx, "agentPool", &containerservice.AgentPoolArgs{
			AgentPoolName:       pulumi.String("agentpool1"),
			Count:               pulumi.Int(3),
			OrchestratorVersion: pulumi.String(""),
			OsDiskSizeGB:        pulumi.Int(64),
			OsDiskType:          pulumi.String("Ephemeral"),
			OsType:              pulumi.String("Linux"),
			ResourceGroupName:   pulumi.String("rg1"),
			ResourceName:        pulumi.String("clustername1"),
			VmSize:              pulumi.String("Standard_DS2_v2"),
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
import com.pulumi.azurenative.containerservice.AgentPool;
import com.pulumi.azurenative.containerservice.AgentPoolArgs;
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
        var agentPool = new AgentPool("agentPool", AgentPoolArgs.builder()        
            .agentPoolName("agentpool1")
            .count(3)
            .orchestratorVersion("")
            .osDiskSizeGB(64)
            .osDiskType("Ephemeral")
            .osType("Linux")
            .resourceGroupName("rg1")
            .resourceName("clustername1")
            .vmSize("Standard_DS2_v2")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const agentPool = new azure_native.containerservice.AgentPool("agentPool", {
    agentPoolName: "agentpool1",
    count: 3,
    orchestratorVersion: "",
    osDiskSizeGB: 64,
    osDiskType: "Ephemeral",
    osType: "Linux",
    resourceGroupName: "rg1",
    resourceName: "clustername1",
    vmSize: "Standard_DS2_v2",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

agent_pool = azure_native.containerservice.AgentPool("agentPool",
    agent_pool_name="agentpool1",
    count=3,
    orchestrator_version="",
    os_disk_size_gb=64,
    os_disk_type="Ephemeral",
    os_type="Linux",
    resource_group_name="rg1",
    resource_name_="clustername1",
    vm_size="Standard_DS2_v2")

```

```yaml
resources:
  agentPool:
    type: azure-native:containerservice:AgentPool
    properties:
      agentPoolName: agentpool1
      count: 3
      orchestratorVersion:
      osDiskSizeGB: 64
      osDiskType: Ephemeral
      osType: Linux
      resourceGroupName: rg1
      resourceName: clustername1
      vmSize: Standard_DS2_v2

```

{{% /example %}}
{{% example %}}
### Create Agent Pool with FIPS enabled OS
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var agentPool = new AzureNative.ContainerService.AgentPool("agentPool", new()
    {
        AgentPoolName = "agentpool1",
        Count = 3,
        EnableFIPS = true,
        OrchestratorVersion = "",
        OsType = "Linux",
        ResourceGroupName = "rg1",
        ResourceName = "clustername1",
        VmSize = "Standard_DS2_v2",
    });

});


```

```go
package main

import (
	containerservice "github.com/pulumi/pulumi-azure-native-sdk/containerservice"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := containerservice.NewAgentPool(ctx, "agentPool", &containerservice.AgentPoolArgs{
			AgentPoolName:       pulumi.String("agentpool1"),
			Count:               pulumi.Int(3),
			EnableFIPS:          pulumi.Bool(true),
			OrchestratorVersion: pulumi.String(""),
			OsType:              pulumi.String("Linux"),
			ResourceGroupName:   pulumi.String("rg1"),
			ResourceName:        pulumi.String("clustername1"),
			VmSize:              pulumi.String("Standard_DS2_v2"),
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
import com.pulumi.azurenative.containerservice.AgentPool;
import com.pulumi.azurenative.containerservice.AgentPoolArgs;
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
        var agentPool = new AgentPool("agentPool", AgentPoolArgs.builder()        
            .agentPoolName("agentpool1")
            .count(3)
            .enableFIPS(true)
            .orchestratorVersion("")
            .osType("Linux")
            .resourceGroupName("rg1")
            .resourceName("clustername1")
            .vmSize("Standard_DS2_v2")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const agentPool = new azure_native.containerservice.AgentPool("agentPool", {
    agentPoolName: "agentpool1",
    count: 3,
    enableFIPS: true,
    orchestratorVersion: "",
    osType: "Linux",
    resourceGroupName: "rg1",
    resourceName: "clustername1",
    vmSize: "Standard_DS2_v2",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

agent_pool = azure_native.containerservice.AgentPool("agentPool",
    agent_pool_name="agentpool1",
    count=3,
    enable_fips=True,
    orchestrator_version="",
    os_type="Linux",
    resource_group_name="rg1",
    resource_name_="clustername1",
    vm_size="Standard_DS2_v2")

```

```yaml
resources:
  agentPool:
    type: azure-native:containerservice:AgentPool
    properties:
      agentPoolName: agentpool1
      count: 3
      enableFIPS: true
      orchestratorVersion:
      osType: Linux
      resourceGroupName: rg1
      resourceName: clustername1
      vmSize: Standard_DS2_v2

```

{{% /example %}}
{{% example %}}
### Create Agent Pool with GPUMIG
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var agentPool = new AzureNative.ContainerService.AgentPool("agentPool", new()
    {
        AgentPoolName = "agentpool1",
        Count = 3,
        GpuInstanceProfile = "MIG2g",
        KubeletConfig = new AzureNative.ContainerService.Inputs.KubeletConfigArgs
        {
            AllowedUnsafeSysctls = new[]
            {
                "kernel.msg*",
                "net.core.somaxconn",
            },
            CpuCfsQuota = true,
            CpuCfsQuotaPeriod = "200ms",
            CpuManagerPolicy = "static",
            FailSwapOn = false,
            ImageGcHighThreshold = 90,
            ImageGcLowThreshold = 70,
            TopologyManagerPolicy = "best-effort",
        },
        LinuxOSConfig = new AzureNative.ContainerService.Inputs.LinuxOSConfigArgs
        {
            SwapFileSizeMB = 1500,
            Sysctls = new AzureNative.ContainerService.Inputs.SysctlConfigArgs
            {
                KernelThreadsMax = 99999,
                NetCoreWmemDefault = 12345,
                NetIpv4IpLocalPortRange = "20000 60000",
                NetIpv4TcpTwReuse = true,
            },
            TransparentHugePageDefrag = "madvise",
            TransparentHugePageEnabled = "always",
        },
        OrchestratorVersion = "",
        OsType = "Linux",
        ResourceGroupName = "rg1",
        ResourceName = "clustername1",
        VmSize = "Standard_ND96asr_v4",
    });

});


```

```go
package main

import (
	containerservice "github.com/pulumi/pulumi-azure-native-sdk/containerservice"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := containerservice.NewAgentPool(ctx, "agentPool", &containerservice.AgentPoolArgs{
			AgentPoolName:      pulumi.String("agentpool1"),
			Count:              pulumi.Int(3),
			GpuInstanceProfile: pulumi.String("MIG2g"),
			KubeletConfig: &containerservice.KubeletConfigArgs{
				AllowedUnsafeSysctls: pulumi.StringArray{
					pulumi.String("kernel.msg*"),
					pulumi.String("net.core.somaxconn"),
				},
				CpuCfsQuota:           pulumi.Bool(true),
				CpuCfsQuotaPeriod:     pulumi.String("200ms"),
				CpuManagerPolicy:      pulumi.String("static"),
				FailSwapOn:            pulumi.Bool(false),
				ImageGcHighThreshold:  pulumi.Int(90),
				ImageGcLowThreshold:   pulumi.Int(70),
				TopologyManagerPolicy: pulumi.String("best-effort"),
			},
			LinuxOSConfig: containerservice.LinuxOSConfigResponse{
				SwapFileSizeMB: pulumi.Int(1500),
				Sysctls: &containerservice.SysctlConfigArgs{
					KernelThreadsMax:        pulumi.Int(99999),
					NetCoreWmemDefault:      pulumi.Int(12345),
					NetIpv4IpLocalPortRange: pulumi.String("20000 60000"),
					NetIpv4TcpTwReuse:       pulumi.Bool(true),
				},
				TransparentHugePageDefrag:  pulumi.String("madvise"),
				TransparentHugePageEnabled: pulumi.String("always"),
			},
			OrchestratorVersion: pulumi.String(""),
			OsType:              pulumi.String("Linux"),
			ResourceGroupName:   pulumi.String("rg1"),
			ResourceName:        pulumi.String("clustername1"),
			VmSize:              pulumi.String("Standard_ND96asr_v4"),
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
import com.pulumi.azurenative.containerservice.AgentPool;
import com.pulumi.azurenative.containerservice.AgentPoolArgs;
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
        var agentPool = new AgentPool("agentPool", AgentPoolArgs.builder()        
            .agentPoolName("agentpool1")
            .count(3)
            .gpuInstanceProfile("MIG2g")
            .kubeletConfig(Map.ofEntries(
                Map.entry("allowedUnsafeSysctls",                 
                    "kernel.msg*",
                    "net.core.somaxconn"),
                Map.entry("cpuCfsQuota", true),
                Map.entry("cpuCfsQuotaPeriod", "200ms"),
                Map.entry("cpuManagerPolicy", "static"),
                Map.entry("failSwapOn", false),
                Map.entry("imageGcHighThreshold", 90),
                Map.entry("imageGcLowThreshold", 70),
                Map.entry("topologyManagerPolicy", "best-effort")
            ))
            .linuxOSConfig(Map.ofEntries(
                Map.entry("swapFileSizeMB", 1500),
                Map.entry("sysctls", Map.ofEntries(
                    Map.entry("kernelThreadsMax", 99999),
                    Map.entry("netCoreWmemDefault", 12345),
                    Map.entry("netIpv4IpLocalPortRange", "20000 60000"),
                    Map.entry("netIpv4TcpTwReuse", true)
                )),
                Map.entry("transparentHugePageDefrag", "madvise"),
                Map.entry("transparentHugePageEnabled", "always")
            ))
            .orchestratorVersion("")
            .osType("Linux")
            .resourceGroupName("rg1")
            .resourceName("clustername1")
            .vmSize("Standard_ND96asr_v4")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const agentPool = new azure_native.containerservice.AgentPool("agentPool", {
    agentPoolName: "agentpool1",
    count: 3,
    gpuInstanceProfile: "MIG2g",
    kubeletConfig: {
        allowedUnsafeSysctls: [
            "kernel.msg*",
            "net.core.somaxconn",
        ],
        cpuCfsQuota: true,
        cpuCfsQuotaPeriod: "200ms",
        cpuManagerPolicy: "static",
        failSwapOn: false,
        imageGcHighThreshold: 90,
        imageGcLowThreshold: 70,
        topologyManagerPolicy: "best-effort",
    },
    linuxOSConfig: {
        swapFileSizeMB: 1500,
        sysctls: {
            kernelThreadsMax: 99999,
            netCoreWmemDefault: 12345,
            netIpv4IpLocalPortRange: "20000 60000",
            netIpv4TcpTwReuse: true,
        },
        transparentHugePageDefrag: "madvise",
        transparentHugePageEnabled: "always",
    },
    orchestratorVersion: "",
    osType: "Linux",
    resourceGroupName: "rg1",
    resourceName: "clustername1",
    vmSize: "Standard_ND96asr_v4",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

agent_pool = azure_native.containerservice.AgentPool("agentPool",
    agent_pool_name="agentpool1",
    count=3,
    gpu_instance_profile="MIG2g",
    kubelet_config=azure_native.containerservice.KubeletConfigArgs(
        allowed_unsafe_sysctls=[
            "kernel.msg*",
            "net.core.somaxconn",
        ],
        cpu_cfs_quota=True,
        cpu_cfs_quota_period="200ms",
        cpu_manager_policy="static",
        fail_swap_on=False,
        image_gc_high_threshold=90,
        image_gc_low_threshold=70,
        topology_manager_policy="best-effort",
    ),
    linux_os_config=azure_native.containerservice.LinuxOSConfigResponseArgs(
        swap_file_size_mb=1500,
        sysctls=azure_native.containerservice.SysctlConfigArgs(
            kernel_threads_max=99999,
            net_core_wmem_default=12345,
            net_ipv4_ip_local_port_range="20000 60000",
            net_ipv4_tcp_tw_reuse=True,
        ),
        transparent_huge_page_defrag="madvise",
        transparent_huge_page_enabled="always",
    ),
    orchestrator_version="",
    os_type="Linux",
    resource_group_name="rg1",
    resource_name_="clustername1",
    vm_size="Standard_ND96asr_v4")

```

```yaml
resources:
  agentPool:
    type: azure-native:containerservice:AgentPool
    properties:
      agentPoolName: agentpool1
      count: 3
      gpuInstanceProfile: MIG2g
      kubeletConfig:
        allowedUnsafeSysctls:
          - kernel.msg*
          - net.core.somaxconn
        cpuCfsQuota: true
        cpuCfsQuotaPeriod: 200ms
        cpuManagerPolicy: static
        failSwapOn: false
        imageGcHighThreshold: 90
        imageGcLowThreshold: 70
        topologyManagerPolicy: best-effort
      linuxOSConfig:
        swapFileSizeMB: 1500
        sysctls:
          kernelThreadsMax: 99999
          netCoreWmemDefault: 12345
          netIpv4IpLocalPortRange: 20000 60000
          netIpv4TcpTwReuse: true
        transparentHugePageDefrag: madvise
        transparentHugePageEnabled: always
      orchestratorVersion:
      osType: Linux
      resourceGroupName: rg1
      resourceName: clustername1
      vmSize: Standard_ND96asr_v4

```

{{% /example %}}
{{% example %}}
### Create Agent Pool with Krustlet and the WASI runtime
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var agentPool = new AzureNative.ContainerService.AgentPool("agentPool", new()
    {
        AgentPoolName = "agentpool1",
        Count = 3,
        Mode = "User",
        OrchestratorVersion = "",
        OsDiskSizeGB = 64,
        OsType = "Linux",
        ResourceGroupName = "rg1",
        ResourceName = "clustername1",
        VmSize = "Standard_DS2_v2",
        WorkloadRuntime = "WasmWasi",
    });

});


```

```go
package main

import (
	containerservice "github.com/pulumi/pulumi-azure-native-sdk/containerservice"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := containerservice.NewAgentPool(ctx, "agentPool", &containerservice.AgentPoolArgs{
			AgentPoolName:       pulumi.String("agentpool1"),
			Count:               pulumi.Int(3),
			Mode:                pulumi.String("User"),
			OrchestratorVersion: pulumi.String(""),
			OsDiskSizeGB:        pulumi.Int(64),
			OsType:              pulumi.String("Linux"),
			ResourceGroupName:   pulumi.String("rg1"),
			ResourceName:        pulumi.String("clustername1"),
			VmSize:              pulumi.String("Standard_DS2_v2"),
			WorkloadRuntime:     pulumi.String("WasmWasi"),
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
import com.pulumi.azurenative.containerservice.AgentPool;
import com.pulumi.azurenative.containerservice.AgentPoolArgs;
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
        var agentPool = new AgentPool("agentPool", AgentPoolArgs.builder()        
            .agentPoolName("agentpool1")
            .count(3)
            .mode("User")
            .orchestratorVersion("")
            .osDiskSizeGB(64)
            .osType("Linux")
            .resourceGroupName("rg1")
            .resourceName("clustername1")
            .vmSize("Standard_DS2_v2")
            .workloadRuntime("WasmWasi")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const agentPool = new azure_native.containerservice.AgentPool("agentPool", {
    agentPoolName: "agentpool1",
    count: 3,
    mode: "User",
    orchestratorVersion: "",
    osDiskSizeGB: 64,
    osType: "Linux",
    resourceGroupName: "rg1",
    resourceName: "clustername1",
    vmSize: "Standard_DS2_v2",
    workloadRuntime: "WasmWasi",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

agent_pool = azure_native.containerservice.AgentPool("agentPool",
    agent_pool_name="agentpool1",
    count=3,
    mode="User",
    orchestrator_version="",
    os_disk_size_gb=64,
    os_type="Linux",
    resource_group_name="rg1",
    resource_name_="clustername1",
    vm_size="Standard_DS2_v2",
    workload_runtime="WasmWasi")

```

```yaml
resources:
  agentPool:
    type: azure-native:containerservice:AgentPool
    properties:
      agentPoolName: agentpool1
      count: 3
      mode: User
      orchestratorVersion:
      osDiskSizeGB: 64
      osType: Linux
      resourceGroupName: rg1
      resourceName: clustername1
      vmSize: Standard_DS2_v2
      workloadRuntime: WasmWasi

```

{{% /example %}}
{{% example %}}
### Create Agent Pool with KubeletConfig and LinuxOSConfig
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var agentPool = new AzureNative.ContainerService.AgentPool("agentPool", new()
    {
        AgentPoolName = "agentpool1",
        Count = 3,
        KubeletConfig = new AzureNative.ContainerService.Inputs.KubeletConfigArgs
        {
            AllowedUnsafeSysctls = new[]
            {
                "kernel.msg*",
                "net.core.somaxconn",
            },
            CpuCfsQuota = true,
            CpuCfsQuotaPeriod = "200ms",
            CpuManagerPolicy = "static",
            FailSwapOn = false,
            ImageGcHighThreshold = 90,
            ImageGcLowThreshold = 70,
            TopologyManagerPolicy = "best-effort",
        },
        LinuxOSConfig = new AzureNative.ContainerService.Inputs.LinuxOSConfigArgs
        {
            SwapFileSizeMB = 1500,
            Sysctls = new AzureNative.ContainerService.Inputs.SysctlConfigArgs
            {
                KernelThreadsMax = 99999,
                NetCoreWmemDefault = 12345,
                NetIpv4IpLocalPortRange = "20000 60000",
                NetIpv4TcpTwReuse = true,
            },
            TransparentHugePageDefrag = "madvise",
            TransparentHugePageEnabled = "always",
        },
        OrchestratorVersion = "",
        OsType = "Linux",
        ResourceGroupName = "rg1",
        ResourceName = "clustername1",
        VmSize = "Standard_DS2_v2",
    });

});


```

```go
package main

import (
	containerservice "github.com/pulumi/pulumi-azure-native-sdk/containerservice"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := containerservice.NewAgentPool(ctx, "agentPool", &containerservice.AgentPoolArgs{
			AgentPoolName: pulumi.String("agentpool1"),
			Count:         pulumi.Int(3),
			KubeletConfig: &containerservice.KubeletConfigArgs{
				AllowedUnsafeSysctls: pulumi.StringArray{
					pulumi.String("kernel.msg*"),
					pulumi.String("net.core.somaxconn"),
				},
				CpuCfsQuota:           pulumi.Bool(true),
				CpuCfsQuotaPeriod:     pulumi.String("200ms"),
				CpuManagerPolicy:      pulumi.String("static"),
				FailSwapOn:            pulumi.Bool(false),
				ImageGcHighThreshold:  pulumi.Int(90),
				ImageGcLowThreshold:   pulumi.Int(70),
				TopologyManagerPolicy: pulumi.String("best-effort"),
			},
			LinuxOSConfig: containerservice.LinuxOSConfigResponse{
				SwapFileSizeMB: pulumi.Int(1500),
				Sysctls: &containerservice.SysctlConfigArgs{
					KernelThreadsMax:        pulumi.Int(99999),
					NetCoreWmemDefault:      pulumi.Int(12345),
					NetIpv4IpLocalPortRange: pulumi.String("20000 60000"),
					NetIpv4TcpTwReuse:       pulumi.Bool(true),
				},
				TransparentHugePageDefrag:  pulumi.String("madvise"),
				TransparentHugePageEnabled: pulumi.String("always"),
			},
			OrchestratorVersion: pulumi.String(""),
			OsType:              pulumi.String("Linux"),
			ResourceGroupName:   pulumi.String("rg1"),
			ResourceName:        pulumi.String("clustername1"),
			VmSize:              pulumi.String("Standard_DS2_v2"),
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
import com.pulumi.azurenative.containerservice.AgentPool;
import com.pulumi.azurenative.containerservice.AgentPoolArgs;
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
        var agentPool = new AgentPool("agentPool", AgentPoolArgs.builder()        
            .agentPoolName("agentpool1")
            .count(3)
            .kubeletConfig(Map.ofEntries(
                Map.entry("allowedUnsafeSysctls",                 
                    "kernel.msg*",
                    "net.core.somaxconn"),
                Map.entry("cpuCfsQuota", true),
                Map.entry("cpuCfsQuotaPeriod", "200ms"),
                Map.entry("cpuManagerPolicy", "static"),
                Map.entry("failSwapOn", false),
                Map.entry("imageGcHighThreshold", 90),
                Map.entry("imageGcLowThreshold", 70),
                Map.entry("topologyManagerPolicy", "best-effort")
            ))
            .linuxOSConfig(Map.ofEntries(
                Map.entry("swapFileSizeMB", 1500),
                Map.entry("sysctls", Map.ofEntries(
                    Map.entry("kernelThreadsMax", 99999),
                    Map.entry("netCoreWmemDefault", 12345),
                    Map.entry("netIpv4IpLocalPortRange", "20000 60000"),
                    Map.entry("netIpv4TcpTwReuse", true)
                )),
                Map.entry("transparentHugePageDefrag", "madvise"),
                Map.entry("transparentHugePageEnabled", "always")
            ))
            .orchestratorVersion("")
            .osType("Linux")
            .resourceGroupName("rg1")
            .resourceName("clustername1")
            .vmSize("Standard_DS2_v2")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const agentPool = new azure_native.containerservice.AgentPool("agentPool", {
    agentPoolName: "agentpool1",
    count: 3,
    kubeletConfig: {
        allowedUnsafeSysctls: [
            "kernel.msg*",
            "net.core.somaxconn",
        ],
        cpuCfsQuota: true,
        cpuCfsQuotaPeriod: "200ms",
        cpuManagerPolicy: "static",
        failSwapOn: false,
        imageGcHighThreshold: 90,
        imageGcLowThreshold: 70,
        topologyManagerPolicy: "best-effort",
    },
    linuxOSConfig: {
        swapFileSizeMB: 1500,
        sysctls: {
            kernelThreadsMax: 99999,
            netCoreWmemDefault: 12345,
            netIpv4IpLocalPortRange: "20000 60000",
            netIpv4TcpTwReuse: true,
        },
        transparentHugePageDefrag: "madvise",
        transparentHugePageEnabled: "always",
    },
    orchestratorVersion: "",
    osType: "Linux",
    resourceGroupName: "rg1",
    resourceName: "clustername1",
    vmSize: "Standard_DS2_v2",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

agent_pool = azure_native.containerservice.AgentPool("agentPool",
    agent_pool_name="agentpool1",
    count=3,
    kubelet_config=azure_native.containerservice.KubeletConfigArgs(
        allowed_unsafe_sysctls=[
            "kernel.msg*",
            "net.core.somaxconn",
        ],
        cpu_cfs_quota=True,
        cpu_cfs_quota_period="200ms",
        cpu_manager_policy="static",
        fail_swap_on=False,
        image_gc_high_threshold=90,
        image_gc_low_threshold=70,
        topology_manager_policy="best-effort",
    ),
    linux_os_config=azure_native.containerservice.LinuxOSConfigResponseArgs(
        swap_file_size_mb=1500,
        sysctls=azure_native.containerservice.SysctlConfigArgs(
            kernel_threads_max=99999,
            net_core_wmem_default=12345,
            net_ipv4_ip_local_port_range="20000 60000",
            net_ipv4_tcp_tw_reuse=True,
        ),
        transparent_huge_page_defrag="madvise",
        transparent_huge_page_enabled="always",
    ),
    orchestrator_version="",
    os_type="Linux",
    resource_group_name="rg1",
    resource_name_="clustername1",
    vm_size="Standard_DS2_v2")

```

```yaml
resources:
  agentPool:
    type: azure-native:containerservice:AgentPool
    properties:
      agentPoolName: agentpool1
      count: 3
      kubeletConfig:
        allowedUnsafeSysctls:
          - kernel.msg*
          - net.core.somaxconn
        cpuCfsQuota: true
        cpuCfsQuotaPeriod: 200ms
        cpuManagerPolicy: static
        failSwapOn: false
        imageGcHighThreshold: 90
        imageGcLowThreshold: 70
        topologyManagerPolicy: best-effort
      linuxOSConfig:
        swapFileSizeMB: 1500
        sysctls:
          kernelThreadsMax: 99999
          netCoreWmemDefault: 12345
          netIpv4IpLocalPortRange: 20000 60000
          netIpv4TcpTwReuse: true
        transparentHugePageDefrag: madvise
        transparentHugePageEnabled: always
      orchestratorVersion:
      osType: Linux
      resourceGroupName: rg1
      resourceName: clustername1
      vmSize: Standard_DS2_v2

```

{{% /example %}}
{{% example %}}
### Create Agent Pool with OSSKU
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var agentPool = new AzureNative.ContainerService.AgentPool("agentPool", new()
    {
        AgentPoolName = "agentpool1",
        Count = 3,
        KubeletConfig = new AzureNative.ContainerService.Inputs.KubeletConfigArgs
        {
            AllowedUnsafeSysctls = new[]
            {
                "kernel.msg*",
                "net.core.somaxconn",
            },
            CpuCfsQuota = true,
            CpuCfsQuotaPeriod = "200ms",
            CpuManagerPolicy = "static",
            FailSwapOn = false,
            ImageGcHighThreshold = 90,
            ImageGcLowThreshold = 70,
            TopologyManagerPolicy = "best-effort",
        },
        LinuxOSConfig = new AzureNative.ContainerService.Inputs.LinuxOSConfigArgs
        {
            SwapFileSizeMB = 1500,
            Sysctls = new AzureNative.ContainerService.Inputs.SysctlConfigArgs
            {
                KernelThreadsMax = 99999,
                NetCoreWmemDefault = 12345,
                NetIpv4IpLocalPortRange = "20000 60000",
                NetIpv4TcpTwReuse = true,
            },
            TransparentHugePageDefrag = "madvise",
            TransparentHugePageEnabled = "always",
        },
        OrchestratorVersion = "",
        OsSKU = "CBLMariner",
        OsType = "Linux",
        ResourceGroupName = "rg1",
        ResourceName = "clustername1",
        VmSize = "Standard_DS2_v2",
    });

});


```

```go
package main

import (
	containerservice "github.com/pulumi/pulumi-azure-native-sdk/containerservice"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := containerservice.NewAgentPool(ctx, "agentPool", &containerservice.AgentPoolArgs{
			AgentPoolName: pulumi.String("agentpool1"),
			Count:         pulumi.Int(3),
			KubeletConfig: &containerservice.KubeletConfigArgs{
				AllowedUnsafeSysctls: pulumi.StringArray{
					pulumi.String("kernel.msg*"),
					pulumi.String("net.core.somaxconn"),
				},
				CpuCfsQuota:           pulumi.Bool(true),
				CpuCfsQuotaPeriod:     pulumi.String("200ms"),
				CpuManagerPolicy:      pulumi.String("static"),
				FailSwapOn:            pulumi.Bool(false),
				ImageGcHighThreshold:  pulumi.Int(90),
				ImageGcLowThreshold:   pulumi.Int(70),
				TopologyManagerPolicy: pulumi.String("best-effort"),
			},
			LinuxOSConfig: containerservice.LinuxOSConfigResponse{
				SwapFileSizeMB: pulumi.Int(1500),
				Sysctls: &containerservice.SysctlConfigArgs{
					KernelThreadsMax:        pulumi.Int(99999),
					NetCoreWmemDefault:      pulumi.Int(12345),
					NetIpv4IpLocalPortRange: pulumi.String("20000 60000"),
					NetIpv4TcpTwReuse:       pulumi.Bool(true),
				},
				TransparentHugePageDefrag:  pulumi.String("madvise"),
				TransparentHugePageEnabled: pulumi.String("always"),
			},
			OrchestratorVersion: pulumi.String(""),
			OsSKU:               pulumi.String("CBLMariner"),
			OsType:              pulumi.String("Linux"),
			ResourceGroupName:   pulumi.String("rg1"),
			ResourceName:        pulumi.String("clustername1"),
			VmSize:              pulumi.String("Standard_DS2_v2"),
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
import com.pulumi.azurenative.containerservice.AgentPool;
import com.pulumi.azurenative.containerservice.AgentPoolArgs;
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
        var agentPool = new AgentPool("agentPool", AgentPoolArgs.builder()        
            .agentPoolName("agentpool1")
            .count(3)
            .kubeletConfig(Map.ofEntries(
                Map.entry("allowedUnsafeSysctls",                 
                    "kernel.msg*",
                    "net.core.somaxconn"),
                Map.entry("cpuCfsQuota", true),
                Map.entry("cpuCfsQuotaPeriod", "200ms"),
                Map.entry("cpuManagerPolicy", "static"),
                Map.entry("failSwapOn", false),
                Map.entry("imageGcHighThreshold", 90),
                Map.entry("imageGcLowThreshold", 70),
                Map.entry("topologyManagerPolicy", "best-effort")
            ))
            .linuxOSConfig(Map.ofEntries(
                Map.entry("swapFileSizeMB", 1500),
                Map.entry("sysctls", Map.ofEntries(
                    Map.entry("kernelThreadsMax", 99999),
                    Map.entry("netCoreWmemDefault", 12345),
                    Map.entry("netIpv4IpLocalPortRange", "20000 60000"),
                    Map.entry("netIpv4TcpTwReuse", true)
                )),
                Map.entry("transparentHugePageDefrag", "madvise"),
                Map.entry("transparentHugePageEnabled", "always")
            ))
            .orchestratorVersion("")
            .osSKU("CBLMariner")
            .osType("Linux")
            .resourceGroupName("rg1")
            .resourceName("clustername1")
            .vmSize("Standard_DS2_v2")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const agentPool = new azure_native.containerservice.AgentPool("agentPool", {
    agentPoolName: "agentpool1",
    count: 3,
    kubeletConfig: {
        allowedUnsafeSysctls: [
            "kernel.msg*",
            "net.core.somaxconn",
        ],
        cpuCfsQuota: true,
        cpuCfsQuotaPeriod: "200ms",
        cpuManagerPolicy: "static",
        failSwapOn: false,
        imageGcHighThreshold: 90,
        imageGcLowThreshold: 70,
        topologyManagerPolicy: "best-effort",
    },
    linuxOSConfig: {
        swapFileSizeMB: 1500,
        sysctls: {
            kernelThreadsMax: 99999,
            netCoreWmemDefault: 12345,
            netIpv4IpLocalPortRange: "20000 60000",
            netIpv4TcpTwReuse: true,
        },
        transparentHugePageDefrag: "madvise",
        transparentHugePageEnabled: "always",
    },
    orchestratorVersion: "",
    osSKU: "CBLMariner",
    osType: "Linux",
    resourceGroupName: "rg1",
    resourceName: "clustername1",
    vmSize: "Standard_DS2_v2",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

agent_pool = azure_native.containerservice.AgentPool("agentPool",
    agent_pool_name="agentpool1",
    count=3,
    kubelet_config=azure_native.containerservice.KubeletConfigArgs(
        allowed_unsafe_sysctls=[
            "kernel.msg*",
            "net.core.somaxconn",
        ],
        cpu_cfs_quota=True,
        cpu_cfs_quota_period="200ms",
        cpu_manager_policy="static",
        fail_swap_on=False,
        image_gc_high_threshold=90,
        image_gc_low_threshold=70,
        topology_manager_policy="best-effort",
    ),
    linux_os_config=azure_native.containerservice.LinuxOSConfigResponseArgs(
        swap_file_size_mb=1500,
        sysctls=azure_native.containerservice.SysctlConfigArgs(
            kernel_threads_max=99999,
            net_core_wmem_default=12345,
            net_ipv4_ip_local_port_range="20000 60000",
            net_ipv4_tcp_tw_reuse=True,
        ),
        transparent_huge_page_defrag="madvise",
        transparent_huge_page_enabled="always",
    ),
    orchestrator_version="",
    os_sku="CBLMariner",
    os_type="Linux",
    resource_group_name="rg1",
    resource_name_="clustername1",
    vm_size="Standard_DS2_v2")

```

```yaml
resources:
  agentPool:
    type: azure-native:containerservice:AgentPool
    properties:
      agentPoolName: agentpool1
      count: 3
      kubeletConfig:
        allowedUnsafeSysctls:
          - kernel.msg*
          - net.core.somaxconn
        cpuCfsQuota: true
        cpuCfsQuotaPeriod: 200ms
        cpuManagerPolicy: static
        failSwapOn: false
        imageGcHighThreshold: 90
        imageGcLowThreshold: 70
        topologyManagerPolicy: best-effort
      linuxOSConfig:
        swapFileSizeMB: 1500
        sysctls:
          kernelThreadsMax: 99999
          netCoreWmemDefault: 12345
          netIpv4IpLocalPortRange: 20000 60000
          netIpv4TcpTwReuse: true
        transparentHugePageDefrag: madvise
        transparentHugePageEnabled: always
      orchestratorVersion:
      osSKU: CBLMariner
      osType: Linux
      resourceGroupName: rg1
      resourceName: clustername1
      vmSize: Standard_DS2_v2

```

{{% /example %}}
{{% example %}}
### Create Agent Pool with PPG
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var agentPool = new AzureNative.ContainerService.AgentPool("agentPool", new()
    {
        AgentPoolName = "agentpool1",
        Count = 3,
        OrchestratorVersion = "",
        OsType = "Linux",
        ProximityPlacementGroupID = "/subscriptions/subid1/resourcegroups/rg1/providers/Microsoft.Compute/proximityPlacementGroups/ppg1",
        ResourceGroupName = "rg1",
        ResourceName = "clustername1",
        VmSize = "Standard_DS2_v2",
    });

});


```

```go
package main

import (
	containerservice "github.com/pulumi/pulumi-azure-native-sdk/containerservice"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := containerservice.NewAgentPool(ctx, "agentPool", &containerservice.AgentPoolArgs{
			AgentPoolName:             pulumi.String("agentpool1"),
			Count:                     pulumi.Int(3),
			OrchestratorVersion:       pulumi.String(""),
			OsType:                    pulumi.String("Linux"),
			ProximityPlacementGroupID: pulumi.String("/subscriptions/subid1/resourcegroups/rg1/providers/Microsoft.Compute/proximityPlacementGroups/ppg1"),
			ResourceGroupName:         pulumi.String("rg1"),
			ResourceName:              pulumi.String("clustername1"),
			VmSize:                    pulumi.String("Standard_DS2_v2"),
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
import com.pulumi.azurenative.containerservice.AgentPool;
import com.pulumi.azurenative.containerservice.AgentPoolArgs;
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
        var agentPool = new AgentPool("agentPool", AgentPoolArgs.builder()        
            .agentPoolName("agentpool1")
            .count(3)
            .orchestratorVersion("")
            .osType("Linux")
            .proximityPlacementGroupID("/subscriptions/subid1/resourcegroups/rg1/providers/Microsoft.Compute/proximityPlacementGroups/ppg1")
            .resourceGroupName("rg1")
            .resourceName("clustername1")
            .vmSize("Standard_DS2_v2")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const agentPool = new azure_native.containerservice.AgentPool("agentPool", {
    agentPoolName: "agentpool1",
    count: 3,
    orchestratorVersion: "",
    osType: "Linux",
    proximityPlacementGroupID: "/subscriptions/subid1/resourcegroups/rg1/providers/Microsoft.Compute/proximityPlacementGroups/ppg1",
    resourceGroupName: "rg1",
    resourceName: "clustername1",
    vmSize: "Standard_DS2_v2",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

agent_pool = azure_native.containerservice.AgentPool("agentPool",
    agent_pool_name="agentpool1",
    count=3,
    orchestrator_version="",
    os_type="Linux",
    proximity_placement_group_id="/subscriptions/subid1/resourcegroups/rg1/providers/Microsoft.Compute/proximityPlacementGroups/ppg1",
    resource_group_name="rg1",
    resource_name_="clustername1",
    vm_size="Standard_DS2_v2")

```

```yaml
resources:
  agentPool:
    type: azure-native:containerservice:AgentPool
    properties:
      agentPoolName: agentpool1
      count: 3
      orchestratorVersion:
      osType: Linux
      proximityPlacementGroupID: /subscriptions/subid1/resourcegroups/rg1/providers/Microsoft.Compute/proximityPlacementGroups/ppg1
      resourceGroupName: rg1
      resourceName: clustername1
      vmSize: Standard_DS2_v2

```

{{% /example %}}
{{% example %}}
### Create Agent Pool with UltraSSD enabled
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var agentPool = new AzureNative.ContainerService.AgentPool("agentPool", new()
    {
        AgentPoolName = "agentpool1",
        Count = 3,
        EnableUltraSSD = true,
        OrchestratorVersion = "",
        OsType = "Linux",
        ResourceGroupName = "rg1",
        ResourceName = "clustername1",
        VmSize = "Standard_DS2_v2",
    });

});


```

```go
package main

import (
	containerservice "github.com/pulumi/pulumi-azure-native-sdk/containerservice"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := containerservice.NewAgentPool(ctx, "agentPool", &containerservice.AgentPoolArgs{
			AgentPoolName:       pulumi.String("agentpool1"),
			Count:               pulumi.Int(3),
			EnableUltraSSD:      pulumi.Bool(true),
			OrchestratorVersion: pulumi.String(""),
			OsType:              pulumi.String("Linux"),
			ResourceGroupName:   pulumi.String("rg1"),
			ResourceName:        pulumi.String("clustername1"),
			VmSize:              pulumi.String("Standard_DS2_v2"),
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
import com.pulumi.azurenative.containerservice.AgentPool;
import com.pulumi.azurenative.containerservice.AgentPoolArgs;
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
        var agentPool = new AgentPool("agentPool", AgentPoolArgs.builder()        
            .agentPoolName("agentpool1")
            .count(3)
            .enableUltraSSD(true)
            .orchestratorVersion("")
            .osType("Linux")
            .resourceGroupName("rg1")
            .resourceName("clustername1")
            .vmSize("Standard_DS2_v2")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const agentPool = new azure_native.containerservice.AgentPool("agentPool", {
    agentPoolName: "agentpool1",
    count: 3,
    enableUltraSSD: true,
    orchestratorVersion: "",
    osType: "Linux",
    resourceGroupName: "rg1",
    resourceName: "clustername1",
    vmSize: "Standard_DS2_v2",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

agent_pool = azure_native.containerservice.AgentPool("agentPool",
    agent_pool_name="agentpool1",
    count=3,
    enable_ultra_ssd=True,
    orchestrator_version="",
    os_type="Linux",
    resource_group_name="rg1",
    resource_name_="clustername1",
    vm_size="Standard_DS2_v2")

```

```yaml
resources:
  agentPool:
    type: azure-native:containerservice:AgentPool
    properties:
      agentPoolName: agentpool1
      count: 3
      enableUltraSSD: true
      orchestratorVersion:
      osType: Linux
      resourceGroupName: rg1
      resourceName: clustername1
      vmSize: Standard_DS2_v2

```

{{% /example %}}
{{% example %}}
### Create Agent Pool with Windows OSSKU
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var agentPool = new AzureNative.ContainerService.AgentPool("agentPool", new()
    {
        AgentPoolName = "wnp2",
        Count = 3,
        OrchestratorVersion = "1.23.3",
        OsSKU = "Windows2022",
        OsType = "Windows",
        ResourceGroupName = "rg1",
        ResourceName = "clustername1",
        VmSize = "Standard_D4s_v3",
    });

});


```

```go
package main

import (
	containerservice "github.com/pulumi/pulumi-azure-native-sdk/containerservice"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := containerservice.NewAgentPool(ctx, "agentPool", &containerservice.AgentPoolArgs{
			AgentPoolName:       pulumi.String("wnp2"),
			Count:               pulumi.Int(3),
			OrchestratorVersion: pulumi.String("1.23.3"),
			OsSKU:               pulumi.String("Windows2022"),
			OsType:              pulumi.String("Windows"),
			ResourceGroupName:   pulumi.String("rg1"),
			ResourceName:        pulumi.String("clustername1"),
			VmSize:              pulumi.String("Standard_D4s_v3"),
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
import com.pulumi.azurenative.containerservice.AgentPool;
import com.pulumi.azurenative.containerservice.AgentPoolArgs;
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
        var agentPool = new AgentPool("agentPool", AgentPoolArgs.builder()        
            .agentPoolName("wnp2")
            .count(3)
            .orchestratorVersion("1.23.3")
            .osSKU("Windows2022")
            .osType("Windows")
            .resourceGroupName("rg1")
            .resourceName("clustername1")
            .vmSize("Standard_D4s_v3")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const agentPool = new azure_native.containerservice.AgentPool("agentPool", {
    agentPoolName: "wnp2",
    count: 3,
    orchestratorVersion: "1.23.3",
    osSKU: "Windows2022",
    osType: "Windows",
    resourceGroupName: "rg1",
    resourceName: "clustername1",
    vmSize: "Standard_D4s_v3",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

agent_pool = azure_native.containerservice.AgentPool("agentPool",
    agent_pool_name="wnp2",
    count=3,
    orchestrator_version="1.23.3",
    os_sku="Windows2022",
    os_type="Windows",
    resource_group_name="rg1",
    resource_name_="clustername1",
    vm_size="Standard_D4s_v3")

```

```yaml
resources:
  agentPool:
    type: azure-native:containerservice:AgentPool
    properties:
      agentPoolName: wnp2
      count: 3
      orchestratorVersion: 1.23.3
      osSKU: Windows2022
      osType: Windows
      resourceGroupName: rg1
      resourceName: clustername1
      vmSize: Standard_D4s_v3

```

{{% /example %}}
{{% example %}}
### Create Spot Agent Pool
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var agentPool = new AzureNative.ContainerService.AgentPool("agentPool", new()
    {
        AgentPoolName = "agentpool1",
        Count = 3,
        NodeLabels = 
        {
            { "key1", "val1" },
        },
        NodeTaints = new[]
        {
            "Key1=Value1:NoSchedule",
        },
        OrchestratorVersion = "",
        OsType = "Linux",
        ResourceGroupName = "rg1",
        ResourceName = "clustername1",
        ScaleSetEvictionPolicy = "Delete",
        ScaleSetPriority = "Spot",
        Tags = 
        {
            { "name1", "val1" },
        },
        VmSize = "Standard_DS1_v2",
    });

});


```

```go
package main

import (
	containerservice "github.com/pulumi/pulumi-azure-native-sdk/containerservice"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := containerservice.NewAgentPool(ctx, "agentPool", &containerservice.AgentPoolArgs{
			AgentPoolName: pulumi.String("agentpool1"),
			Count:         pulumi.Int(3),
			NodeLabels: pulumi.StringMap{
				"key1": pulumi.String("val1"),
			},
			NodeTaints: pulumi.StringArray{
				pulumi.String("Key1=Value1:NoSchedule"),
			},
			OrchestratorVersion:    pulumi.String(""),
			OsType:                 pulumi.String("Linux"),
			ResourceGroupName:      pulumi.String("rg1"),
			ResourceName:           pulumi.String("clustername1"),
			ScaleSetEvictionPolicy: pulumi.String("Delete"),
			ScaleSetPriority:       pulumi.String("Spot"),
			Tags: pulumi.StringMap{
				"name1": pulumi.String("val1"),
			},
			VmSize: pulumi.String("Standard_DS1_v2"),
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
import com.pulumi.azurenative.containerservice.AgentPool;
import com.pulumi.azurenative.containerservice.AgentPoolArgs;
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
        var agentPool = new AgentPool("agentPool", AgentPoolArgs.builder()        
            .agentPoolName("agentpool1")
            .count(3)
            .nodeLabels(Map.of("key1", "val1"))
            .nodeTaints("Key1=Value1:NoSchedule")
            .orchestratorVersion("")
            .osType("Linux")
            .resourceGroupName("rg1")
            .resourceName("clustername1")
            .scaleSetEvictionPolicy("Delete")
            .scaleSetPriority("Spot")
            .tags(Map.of("name1", "val1"))
            .vmSize("Standard_DS1_v2")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const agentPool = new azure_native.containerservice.AgentPool("agentPool", {
    agentPoolName: "agentpool1",
    count: 3,
    nodeLabels: {
        key1: "val1",
    },
    nodeTaints: ["Key1=Value1:NoSchedule"],
    orchestratorVersion: "",
    osType: "Linux",
    resourceGroupName: "rg1",
    resourceName: "clustername1",
    scaleSetEvictionPolicy: "Delete",
    scaleSetPriority: "Spot",
    tags: {
        name1: "val1",
    },
    vmSize: "Standard_DS1_v2",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

agent_pool = azure_native.containerservice.AgentPool("agentPool",
    agent_pool_name="agentpool1",
    count=3,
    node_labels={
        "key1": "val1",
    },
    node_taints=["Key1=Value1:NoSchedule"],
    orchestrator_version="",
    os_type="Linux",
    resource_group_name="rg1",
    resource_name_="clustername1",
    scale_set_eviction_policy="Delete",
    scale_set_priority="Spot",
    tags={
        "name1": "val1",
    },
    vm_size="Standard_DS1_v2")

```

```yaml
resources:
  agentPool:
    type: azure-native:containerservice:AgentPool
    properties:
      agentPoolName: agentpool1
      count: 3
      nodeLabels:
        key1: val1
      nodeTaints:
        - Key1=Value1:NoSchedule
      orchestratorVersion:
      osType: Linux
      resourceGroupName: rg1
      resourceName: clustername1
      scaleSetEvictionPolicy: Delete
      scaleSetPriority: Spot
      tags:
        name1: val1
      vmSize: Standard_DS1_v2

```

{{% /example %}}
{{% example %}}
### Create/Update Agent Pool
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var agentPool = new AzureNative.ContainerService.AgentPool("agentPool", new()
    {
        AgentPoolName = "agentpool1",
        Count = 3,
        Mode = "User",
        NodeLabels = 
        {
            { "key1", "val1" },
        },
        NodeTaints = new[]
        {
            "Key1=Value1:NoSchedule",
        },
        OrchestratorVersion = "",
        OsType = "Linux",
        ResourceGroupName = "rg1",
        ResourceName = "clustername1",
        ScaleSetEvictionPolicy = "Delete",
        ScaleSetPriority = "Spot",
        Tags = 
        {
            { "name1", "val1" },
        },
        VmSize = "Standard_DS1_v2",
    });

});


```

```go
package main

import (
	containerservice "github.com/pulumi/pulumi-azure-native-sdk/containerservice"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := containerservice.NewAgentPool(ctx, "agentPool", &containerservice.AgentPoolArgs{
			AgentPoolName: pulumi.String("agentpool1"),
			Count:         pulumi.Int(3),
			Mode:          pulumi.String("User"),
			NodeLabels: pulumi.StringMap{
				"key1": pulumi.String("val1"),
			},
			NodeTaints: pulumi.StringArray{
				pulumi.String("Key1=Value1:NoSchedule"),
			},
			OrchestratorVersion:    pulumi.String(""),
			OsType:                 pulumi.String("Linux"),
			ResourceGroupName:      pulumi.String("rg1"),
			ResourceName:           pulumi.String("clustername1"),
			ScaleSetEvictionPolicy: pulumi.String("Delete"),
			ScaleSetPriority:       pulumi.String("Spot"),
			Tags: pulumi.StringMap{
				"name1": pulumi.String("val1"),
			},
			VmSize: pulumi.String("Standard_DS1_v2"),
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
import com.pulumi.azurenative.containerservice.AgentPool;
import com.pulumi.azurenative.containerservice.AgentPoolArgs;
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
        var agentPool = new AgentPool("agentPool", AgentPoolArgs.builder()        
            .agentPoolName("agentpool1")
            .count(3)
            .mode("User")
            .nodeLabels(Map.of("key1", "val1"))
            .nodeTaints("Key1=Value1:NoSchedule")
            .orchestratorVersion("")
            .osType("Linux")
            .resourceGroupName("rg1")
            .resourceName("clustername1")
            .scaleSetEvictionPolicy("Delete")
            .scaleSetPriority("Spot")
            .tags(Map.of("name1", "val1"))
            .vmSize("Standard_DS1_v2")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const agentPool = new azure_native.containerservice.AgentPool("agentPool", {
    agentPoolName: "agentpool1",
    count: 3,
    mode: "User",
    nodeLabels: {
        key1: "val1",
    },
    nodeTaints: ["Key1=Value1:NoSchedule"],
    orchestratorVersion: "",
    osType: "Linux",
    resourceGroupName: "rg1",
    resourceName: "clustername1",
    scaleSetEvictionPolicy: "Delete",
    scaleSetPriority: "Spot",
    tags: {
        name1: "val1",
    },
    vmSize: "Standard_DS1_v2",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

agent_pool = azure_native.containerservice.AgentPool("agentPool",
    agent_pool_name="agentpool1",
    count=3,
    mode="User",
    node_labels={
        "key1": "val1",
    },
    node_taints=["Key1=Value1:NoSchedule"],
    orchestrator_version="",
    os_type="Linux",
    resource_group_name="rg1",
    resource_name_="clustername1",
    scale_set_eviction_policy="Delete",
    scale_set_priority="Spot",
    tags={
        "name1": "val1",
    },
    vm_size="Standard_DS1_v2")

```

```yaml
resources:
  agentPool:
    type: azure-native:containerservice:AgentPool
    properties:
      agentPoolName: agentpool1
      count: 3
      mode: User
      nodeLabels:
        key1: val1
      nodeTaints:
        - Key1=Value1:NoSchedule
      orchestratorVersion:
      osType: Linux
      resourceGroupName: rg1
      resourceName: clustername1
      scaleSetEvictionPolicy: Delete
      scaleSetPriority: Spot
      tags:
        name1: val1
      vmSize: Standard_DS1_v2

```

{{% /example %}}
{{% example %}}
### Start Agent Pool
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var agentPool = new AzureNative.ContainerService.AgentPool("agentPool", new()
    {
        AgentPoolName = "agentpool1",
        PowerState = new AzureNative.ContainerService.Inputs.PowerStateArgs
        {
            Code = "Running",
        },
        ResourceGroupName = "rg1",
        ResourceName = "clustername1",
    });

});


```

```go
package main

import (
	containerservice "github.com/pulumi/pulumi-azure-native-sdk/containerservice"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := containerservice.NewAgentPool(ctx, "agentPool", &containerservice.AgentPoolArgs{
			AgentPoolName: pulumi.String("agentpool1"),
			PowerState: &containerservice.PowerStateArgs{
				Code: pulumi.String("Running"),
			},
			ResourceGroupName: pulumi.String("rg1"),
			ResourceName:      pulumi.String("clustername1"),
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
import com.pulumi.azurenative.containerservice.AgentPool;
import com.pulumi.azurenative.containerservice.AgentPoolArgs;
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
        var agentPool = new AgentPool("agentPool", AgentPoolArgs.builder()        
            .agentPoolName("agentpool1")
            .powerState(Map.of("code", "Running"))
            .resourceGroupName("rg1")
            .resourceName("clustername1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const agentPool = new azure_native.containerservice.AgentPool("agentPool", {
    agentPoolName: "agentpool1",
    powerState: {
        code: "Running",
    },
    resourceGroupName: "rg1",
    resourceName: "clustername1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

agent_pool = azure_native.containerservice.AgentPool("agentPool",
    agent_pool_name="agentpool1",
    power_state=azure_native.containerservice.PowerStateArgs(
        code="Running",
    ),
    resource_group_name="rg1",
    resource_name_="clustername1")

```

```yaml
resources:
  agentPool:
    type: azure-native:containerservice:AgentPool
    properties:
      agentPoolName: agentpool1
      powerState:
        code: Running
      resourceGroupName: rg1
      resourceName: clustername1

```

{{% /example %}}
{{% example %}}
### Stop Agent Pool
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var agentPool = new AzureNative.ContainerService.AgentPool("agentPool", new()
    {
        AgentPoolName = "agentpool1",
        PowerState = new AzureNative.ContainerService.Inputs.PowerStateArgs
        {
            Code = "Stopped",
        },
        ResourceGroupName = "rg1",
        ResourceName = "clustername1",
    });

});


```

```go
package main

import (
	containerservice "github.com/pulumi/pulumi-azure-native-sdk/containerservice"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := containerservice.NewAgentPool(ctx, "agentPool", &containerservice.AgentPoolArgs{
			AgentPoolName: pulumi.String("agentpool1"),
			PowerState: &containerservice.PowerStateArgs{
				Code: pulumi.String("Stopped"),
			},
			ResourceGroupName: pulumi.String("rg1"),
			ResourceName:      pulumi.String("clustername1"),
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
import com.pulumi.azurenative.containerservice.AgentPool;
import com.pulumi.azurenative.containerservice.AgentPoolArgs;
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
        var agentPool = new AgentPool("agentPool", AgentPoolArgs.builder()        
            .agentPoolName("agentpool1")
            .powerState(Map.of("code", "Stopped"))
            .resourceGroupName("rg1")
            .resourceName("clustername1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const agentPool = new azure_native.containerservice.AgentPool("agentPool", {
    agentPoolName: "agentpool1",
    powerState: {
        code: "Stopped",
    },
    resourceGroupName: "rg1",
    resourceName: "clustername1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

agent_pool = azure_native.containerservice.AgentPool("agentPool",
    agent_pool_name="agentpool1",
    power_state=azure_native.containerservice.PowerStateArgs(
        code="Stopped",
    ),
    resource_group_name="rg1",
    resource_name_="clustername1")

```

```yaml
resources:
  agentPool:
    type: azure-native:containerservice:AgentPool
    properties:
      agentPoolName: agentpool1
      powerState:
        code: Stopped
      resourceGroupName: rg1
      resourceName: clustername1

```

{{% /example %}}
{{% example %}}
### Update Agent Pool
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var agentPool = new AzureNative.ContainerService.AgentPool("agentPool", new()
    {
        AgentPoolName = "agentpool1",
        Count = 3,
        EnableAutoScaling = true,
        MaxCount = 2,
        MinCount = 2,
        NodeTaints = new[]
        {
            "Key1=Value1:NoSchedule",
        },
        OrchestratorVersion = "",
        OsType = "Linux",
        ResourceGroupName = "rg1",
        ResourceName = "clustername1",
        ScaleSetEvictionPolicy = "Delete",
        ScaleSetPriority = "Spot",
        VmSize = "Standard_DS1_v2",
    });

});


```

```go
package main

import (
	containerservice "github.com/pulumi/pulumi-azure-native-sdk/containerservice"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := containerservice.NewAgentPool(ctx, "agentPool", &containerservice.AgentPoolArgs{
			AgentPoolName:     pulumi.String("agentpool1"),
			Count:             pulumi.Int(3),
			EnableAutoScaling: pulumi.Bool(true),
			MaxCount:          pulumi.Int(2),
			MinCount:          pulumi.Int(2),
			NodeTaints: pulumi.StringArray{
				pulumi.String("Key1=Value1:NoSchedule"),
			},
			OrchestratorVersion:    pulumi.String(""),
			OsType:                 pulumi.String("Linux"),
			ResourceGroupName:      pulumi.String("rg1"),
			ResourceName:           pulumi.String("clustername1"),
			ScaleSetEvictionPolicy: pulumi.String("Delete"),
			ScaleSetPriority:       pulumi.String("Spot"),
			VmSize:                 pulumi.String("Standard_DS1_v2"),
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
import com.pulumi.azurenative.containerservice.AgentPool;
import com.pulumi.azurenative.containerservice.AgentPoolArgs;
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
        var agentPool = new AgentPool("agentPool", AgentPoolArgs.builder()        
            .agentPoolName("agentpool1")
            .count(3)
            .enableAutoScaling(true)
            .maxCount(2)
            .minCount(2)
            .nodeTaints("Key1=Value1:NoSchedule")
            .orchestratorVersion("")
            .osType("Linux")
            .resourceGroupName("rg1")
            .resourceName("clustername1")
            .scaleSetEvictionPolicy("Delete")
            .scaleSetPriority("Spot")
            .vmSize("Standard_DS1_v2")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const agentPool = new azure_native.containerservice.AgentPool("agentPool", {
    agentPoolName: "agentpool1",
    count: 3,
    enableAutoScaling: true,
    maxCount: 2,
    minCount: 2,
    nodeTaints: ["Key1=Value1:NoSchedule"],
    orchestratorVersion: "",
    osType: "Linux",
    resourceGroupName: "rg1",
    resourceName: "clustername1",
    scaleSetEvictionPolicy: "Delete",
    scaleSetPriority: "Spot",
    vmSize: "Standard_DS1_v2",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

agent_pool = azure_native.containerservice.AgentPool("agentPool",
    agent_pool_name="agentpool1",
    count=3,
    enable_auto_scaling=True,
    max_count=2,
    min_count=2,
    node_taints=["Key1=Value1:NoSchedule"],
    orchestrator_version="",
    os_type="Linux",
    resource_group_name="rg1",
    resource_name_="clustername1",
    scale_set_eviction_policy="Delete",
    scale_set_priority="Spot",
    vm_size="Standard_DS1_v2")

```

```yaml
resources:
  agentPool:
    type: azure-native:containerservice:AgentPool
    properties:
      agentPoolName: agentpool1
      count: 3
      enableAutoScaling: true
      maxCount: 2
      minCount: 2
      nodeTaints:
        - Key1=Value1:NoSchedule
      orchestratorVersion:
      osType: Linux
      resourceGroupName: rg1
      resourceName: clustername1
      scaleSetEvictionPolicy: Delete
      scaleSetPriority: Spot
      vmSize: Standard_DS1_v2

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:containerservice:AgentPool agentpool1 /subscriptions/subid1/resourcegroups/rg1/providers/Microsoft.ContainerService/managedClusters/clustername1/agentPools/agentpool1 
```
