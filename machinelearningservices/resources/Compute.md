Machine Learning compute object wrapped into ARM resource envelope.
API Version: 2022-10-01.

{{% examples %}}
## Example Usage
{{% example %}}
### Attach a Kubernetes Compute
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var compute = new AzureNative.MachineLearningServices.Compute("compute", new()
    {
        ComputeName = "compute123",
        Location = "eastus",
        Properties = new AzureNative.MachineLearningServices.Inputs.KubernetesArgs
        {
            ComputeType = "Kubernetes",
            Description = "some compute",
            Properties = new AzureNative.MachineLearningServices.Inputs.KubernetesPropertiesArgs
            {
                DefaultInstanceType = "defaultInstanceType",
                InstanceTypes = 
                {
                    { "defaultInstanceType", new AzureNative.MachineLearningServices.Inputs.InstanceTypeSchemaArgs
                    {
                        Resources = new AzureNative.MachineLearningServices.Inputs.InstanceTypeSchemaResourcesArgs
                        {
                            Limits = 
                            {
                                { "cpu", "1" },
                                { "memory", "4Gi" },
                                { "nvidia.com/gpu", null },
                            },
                            Requests = 
                            {
                                { "cpu", "1" },
                                { "memory", "4Gi" },
                                { "nvidia.com/gpu", null },
                            },
                        },
                    } },
                },
                Namespace = "default",
            },
            ResourceId = "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourcegroups/testrg123/providers/Microsoft.ContainerService/managedClusters/compute123-56826-c9b00420020b2",
        },
        ResourceGroupName = "testrg123",
        WorkspaceName = "workspaces123",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.machinelearningservices.Compute;
import com.pulumi.azurenative.machinelearningservices.ComputeArgs;
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
        var compute = new Compute("compute", ComputeArgs.builder()        
            .computeName("compute123")
            .location("eastus")
            .properties(Map.ofEntries(
                Map.entry("computeType", "Kubernetes"),
                Map.entry("description", "some compute"),
                Map.entry("properties", Map.ofEntries(
                    Map.entry("defaultInstanceType", "defaultInstanceType"),
                    Map.entry("instanceTypes", Map.of("defaultInstanceType", Map.of("resources", Map.ofEntries(
                        Map.entry("limits", Map.ofEntries(
                            Map.entry("cpu", "1"),
                            Map.entry("memory", "4Gi"),
                            Map.entry("nvidia.com/gpu", null)
                        )),
                        Map.entry("requests", Map.ofEntries(
                            Map.entry("cpu", "1"),
                            Map.entry("memory", "4Gi"),
                            Map.entry("nvidia.com/gpu", null)
                        ))
                    )))),
                    Map.entry("namespace", "default")
                )),
                Map.entry("resourceId", "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourcegroups/testrg123/providers/Microsoft.ContainerService/managedClusters/compute123-56826-c9b00420020b2")
            ))
            .resourceGroupName("testrg123")
            .workspaceName("workspaces123")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const compute = new azure_native.machinelearningservices.Compute("compute", {
    computeName: "compute123",
    location: "eastus",
    properties: {
        computeType: "Kubernetes",
        description: "some compute",
        properties: {
            defaultInstanceType: "defaultInstanceType",
            instanceTypes: {
                defaultInstanceType: {
                    resources: {
                        limits: {
                            cpu: "1",
                            memory: "4Gi",
                            "nvidia.com/gpu": undefined,
                        },
                        requests: {
                            cpu: "1",
                            memory: "4Gi",
                            "nvidia.com/gpu": undefined,
                        },
                    },
                },
            },
            namespace: "default",
        },
        resourceId: "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourcegroups/testrg123/providers/Microsoft.ContainerService/managedClusters/compute123-56826-c9b00420020b2",
    },
    resourceGroupName: "testrg123",
    workspaceName: "workspaces123",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

compute = azure_native.machinelearningservices.Compute("compute",
    compute_name="compute123",
    location="eastus",
    properties=azure_native.machinelearningservices.KubernetesArgs(
        compute_type="Kubernetes",
        description="some compute",
        properties=azure_native.machinelearningservices.KubernetesPropertiesArgs(
            default_instance_type="defaultInstanceType",
            instance_types={
                "defaultInstanceType": azure_native.machinelearningservices.InstanceTypeSchemaArgs(
                    resources=azure_native.machinelearningservices.InstanceTypeSchemaResourcesArgs(
                        limits={
                            "cpu": "1",
                            "memory": "4Gi",
                            "nvidia.com/gpu": None,
                        },
                        requests={
                            "cpu": "1",
                            "memory": "4Gi",
                            "nvidia.com/gpu": None,
                        },
                    ),
                ),
            },
            namespace="default",
        ),
        resource_id="/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourcegroups/testrg123/providers/Microsoft.ContainerService/managedClusters/compute123-56826-c9b00420020b2",
    ),
    resource_group_name="testrg123",
    workspace_name="workspaces123")

```

```yaml
resources:
  compute:
    type: azure-native:machinelearningservices:Compute
    properties:
      computeName: compute123
      location: eastus
      properties:
        computeType: Kubernetes
        description: some compute
        properties:
          defaultInstanceType: defaultInstanceType
          instanceTypes:
            defaultInstanceType:
              resources:
                limits:
                  cpu: '1'
                  memory: 4Gi
                  nvidia.com/gpu: null
                requests:
                  cpu: '1'
                  memory: 4Gi
                  nvidia.com/gpu: null
          namespace: default
        resourceId: /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourcegroups/testrg123/providers/Microsoft.ContainerService/managedClusters/compute123-56826-c9b00420020b2
      resourceGroupName: testrg123
      workspaceName: workspaces123

```

{{% /example %}}
{{% example %}}
### Create a AML Compute
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var compute = new AzureNative.MachineLearningServices.Compute("compute", new()
    {
        ComputeName = "compute123",
        Location = "eastus",
        Properties = new AzureNative.MachineLearningServices.Inputs.AmlComputeArgs
        {
            ComputeType = "AmlCompute",
            Properties = new AzureNative.MachineLearningServices.Inputs.AmlComputePropertiesArgs
            {
                EnableNodePublicIp = true,
                IsolatedNetwork = false,
                OsType = "Windows",
                RemoteLoginPortPublicAccess = "NotSpecified",
                ScaleSettings = new AzureNative.MachineLearningServices.Inputs.ScaleSettingsArgs
                {
                    MaxNodeCount = 1,
                    MinNodeCount = 0,
                    NodeIdleTimeBeforeScaleDown = "PT5M",
                },
                VirtualMachineImage = new AzureNative.MachineLearningServices.Inputs.VirtualMachineImageArgs
                {
                    Id = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Compute/galleries/myImageGallery/images/myImageDefinition/versions/0.0.1",
                },
                VmPriority = "Dedicated",
                VmSize = "STANDARD_NC6",
            },
        },
        ResourceGroupName = "testrg123",
        WorkspaceName = "workspaces123",
    });

});


```

```go
package main

import (
	machinelearningservices "github.com/pulumi/pulumi-azure-native-sdk/machinelearningservices"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := machinelearningservices.NewCompute(ctx, "compute", &machinelearningservices.ComputeArgs{
			ComputeName: pulumi.String("compute123"),
			Location:    pulumi.String("eastus"),
			Properties: machinelearningservices.AmlCompute{
				ComputeType: "AmlCompute",
				Properties: machinelearningservices.AmlComputeProperties{
					EnableNodePublicIp:          true,
					IsolatedNetwork:             false,
					OsType:                      "Windows",
					RemoteLoginPortPublicAccess: "NotSpecified",
					ScaleSettings: machinelearningservices.ScaleSettings{
						MaxNodeCount:                1,
						MinNodeCount:                0,
						NodeIdleTimeBeforeScaleDown: "PT5M",
					},
					VirtualMachineImage: machinelearningservices.VirtualMachineImage{
						Id: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Compute/galleries/myImageGallery/images/myImageDefinition/versions/0.0.1",
					},
					VmPriority: "Dedicated",
					VmSize:     "STANDARD_NC6",
				},
			},
			ResourceGroupName: pulumi.String("testrg123"),
			WorkspaceName:     pulumi.String("workspaces123"),
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
import com.pulumi.azurenative.machinelearningservices.Compute;
import com.pulumi.azurenative.machinelearningservices.ComputeArgs;
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
        var compute = new Compute("compute", ComputeArgs.builder()        
            .computeName("compute123")
            .location("eastus")
            .properties(Map.ofEntries(
                Map.entry("computeType", "AmlCompute"),
                Map.entry("properties", Map.ofEntries(
                    Map.entry("enableNodePublicIp", true),
                    Map.entry("isolatedNetwork", false),
                    Map.entry("osType", "Windows"),
                    Map.entry("remoteLoginPortPublicAccess", "NotSpecified"),
                    Map.entry("scaleSettings", Map.ofEntries(
                        Map.entry("maxNodeCount", 1),
                        Map.entry("minNodeCount", 0),
                        Map.entry("nodeIdleTimeBeforeScaleDown", "PT5M")
                    )),
                    Map.entry("virtualMachineImage", Map.of("id", "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Compute/galleries/myImageGallery/images/myImageDefinition/versions/0.0.1")),
                    Map.entry("vmPriority", "Dedicated"),
                    Map.entry("vmSize", "STANDARD_NC6")
                ))
            ))
            .resourceGroupName("testrg123")
            .workspaceName("workspaces123")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const compute = new azure_native.machinelearningservices.Compute("compute", {
    computeName: "compute123",
    location: "eastus",
    properties: {
        computeType: "AmlCompute",
        properties: {
            enableNodePublicIp: true,
            isolatedNetwork: false,
            osType: "Windows",
            remoteLoginPortPublicAccess: "NotSpecified",
            scaleSettings: {
                maxNodeCount: 1,
                minNodeCount: 0,
                nodeIdleTimeBeforeScaleDown: "PT5M",
            },
            virtualMachineImage: {
                id: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Compute/galleries/myImageGallery/images/myImageDefinition/versions/0.0.1",
            },
            vmPriority: "Dedicated",
            vmSize: "STANDARD_NC6",
        },
    },
    resourceGroupName: "testrg123",
    workspaceName: "workspaces123",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

compute = azure_native.machinelearningservices.Compute("compute",
    compute_name="compute123",
    location="eastus",
    properties=azure_native.machinelearningservices.AmlComputeArgs(
        compute_type="AmlCompute",
        properties=azure_native.machinelearningservices.AmlComputePropertiesArgs(
            enable_node_public_ip=True,
            isolated_network=False,
            os_type="Windows",
            remote_login_port_public_access="NotSpecified",
            scale_settings=azure_native.machinelearningservices.ScaleSettingsArgs(
                max_node_count=1,
                min_node_count=0,
                node_idle_time_before_scale_down="PT5M",
            ),
            virtual_machine_image=azure_native.machinelearningservices.VirtualMachineImageArgs(
                id="/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Compute/galleries/myImageGallery/images/myImageDefinition/versions/0.0.1",
            ),
            vm_priority="Dedicated",
            vm_size="STANDARD_NC6",
        ),
    ),
    resource_group_name="testrg123",
    workspace_name="workspaces123")

```

```yaml
resources:
  compute:
    type: azure-native:machinelearningservices:Compute
    properties:
      computeName: compute123
      location: eastus
      properties:
        computeType: AmlCompute
        properties:
          enableNodePublicIp: true
          isolatedNetwork: false
          osType: Windows
          remoteLoginPortPublicAccess: NotSpecified
          scaleSettings:
            maxNodeCount: 1
            minNodeCount: 0
            nodeIdleTimeBeforeScaleDown: PT5M
          virtualMachineImage:
            id: /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Compute/galleries/myImageGallery/images/myImageDefinition/versions/0.0.1
          vmPriority: Dedicated
          vmSize: STANDARD_NC6
      resourceGroupName: testrg123
      workspaceName: workspaces123

```

{{% /example %}}
{{% example %}}
### Create a DataFactory Compute
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var compute = new AzureNative.MachineLearningServices.Compute("compute", new()
    {
        ComputeName = "compute123",
        Location = "eastus",
        Properties = new AzureNative.MachineLearningServices.Inputs.DataFactoryArgs
        {
            ComputeType = "DataFactory",
        },
        ResourceGroupName = "testrg123",
        WorkspaceName = "workspaces123",
    });

});


```

```go
package main

import (
	machinelearningservices "github.com/pulumi/pulumi-azure-native-sdk/machinelearningservices"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := machinelearningservices.NewCompute(ctx, "compute", &machinelearningservices.ComputeArgs{
			ComputeName: pulumi.String("compute123"),
			Location:    pulumi.String("eastus"),
			Properties: machinelearningservices.DataFactory{
				ComputeType: "DataFactory",
			},
			ResourceGroupName: pulumi.String("testrg123"),
			WorkspaceName:     pulumi.String("workspaces123"),
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
import com.pulumi.azurenative.machinelearningservices.Compute;
import com.pulumi.azurenative.machinelearningservices.ComputeArgs;
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
        var compute = new Compute("compute", ComputeArgs.builder()        
            .computeName("compute123")
            .location("eastus")
            .properties(Map.of("computeType", "DataFactory"))
            .resourceGroupName("testrg123")
            .workspaceName("workspaces123")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const compute = new azure_native.machinelearningservices.Compute("compute", {
    computeName: "compute123",
    location: "eastus",
    properties: {
        computeType: "DataFactory",
    },
    resourceGroupName: "testrg123",
    workspaceName: "workspaces123",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

compute = azure_native.machinelearningservices.Compute("compute",
    compute_name="compute123",
    location="eastus",
    properties=azure_native.machinelearningservices.DataFactoryArgs(
        compute_type="DataFactory",
    ),
    resource_group_name="testrg123",
    workspace_name="workspaces123")

```

```yaml
resources:
  compute:
    type: azure-native:machinelearningservices:Compute
    properties:
      computeName: compute123
      location: eastus
      properties:
        computeType: DataFactory
      resourceGroupName: testrg123
      workspaceName: workspaces123

```

{{% /example %}}
{{% example %}}
### Create an AKS Compute
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var compute = new AzureNative.MachineLearningServices.Compute("compute", new()
    {
        ComputeName = "compute123",
        Location = "eastus",
        Properties = new AzureNative.MachineLearningServices.Inputs.AKSArgs
        {
            ComputeType = "AKS",
        },
        ResourceGroupName = "testrg123",
        WorkspaceName = "workspaces123",
    });

});


```

```go
package main

import (
	machinelearningservices "github.com/pulumi/pulumi-azure-native-sdk/machinelearningservices"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := machinelearningservices.NewCompute(ctx, "compute", &machinelearningservices.ComputeArgs{
			ComputeName: pulumi.String("compute123"),
			Location:    pulumi.String("eastus"),
			Properties: machinelearningservices.AKS{
				ComputeType: "AKS",
			},
			ResourceGroupName: pulumi.String("testrg123"),
			WorkspaceName:     pulumi.String("workspaces123"),
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
import com.pulumi.azurenative.machinelearningservices.Compute;
import com.pulumi.azurenative.machinelearningservices.ComputeArgs;
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
        var compute = new Compute("compute", ComputeArgs.builder()        
            .computeName("compute123")
            .location("eastus")
            .properties(Map.of("computeType", "AKS"))
            .resourceGroupName("testrg123")
            .workspaceName("workspaces123")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const compute = new azure_native.machinelearningservices.Compute("compute", {
    computeName: "compute123",
    location: "eastus",
    properties: {
        computeType: "AKS",
    },
    resourceGroupName: "testrg123",
    workspaceName: "workspaces123",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

compute = azure_native.machinelearningservices.Compute("compute",
    compute_name="compute123",
    location="eastus",
    properties=azure_native.machinelearningservices.AKSArgs(
        compute_type="AKS",
    ),
    resource_group_name="testrg123",
    workspace_name="workspaces123")

```

```yaml
resources:
  compute:
    type: azure-native:machinelearningservices:Compute
    properties:
      computeName: compute123
      location: eastus
      properties:
        computeType: AKS
      resourceGroupName: testrg123
      workspaceName: workspaces123

```

{{% /example %}}
{{% example %}}
### Create an ComputeInstance Compute
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var compute = new AzureNative.MachineLearningServices.Compute("compute", new()
    {
        ComputeName = "compute123",
        Location = "eastus",
        Properties = new AzureNative.MachineLearningServices.Inputs.ComputeInstanceArgs
        {
            ComputeType = "ComputeInstance",
            Properties = new AzureNative.MachineLearningServices.Inputs.ComputeInstancePropertiesArgs
            {
                ApplicationSharingPolicy = "Personal",
                ComputeInstanceAuthorizationType = "personal",
                PersonalComputeInstanceSettings = new AzureNative.MachineLearningServices.Inputs.PersonalComputeInstanceSettingsArgs
                {
                    AssignedUser = new AzureNative.MachineLearningServices.Inputs.AssignedUserArgs
                    {
                        ObjectId = "00000000-0000-0000-0000-000000000000",
                        TenantId = "00000000-0000-0000-0000-000000000000",
                    },
                },
                SshSettings = new AzureNative.MachineLearningServices.Inputs.ComputeInstanceSshSettingsArgs
                {
                    SshPublicAccess = "Disabled",
                },
                Subnet = new AzureNative.MachineLearningServices.Inputs.ResourceIdArgs
                {
                    Id = "test-subnet-resource-id",
                },
                VmSize = "STANDARD_NC6",
            },
        },
        ResourceGroupName = "testrg123",
        WorkspaceName = "workspaces123",
    });

});


```

```go
package main

import (
	machinelearningservices "github.com/pulumi/pulumi-azure-native-sdk/machinelearningservices"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := machinelearningservices.NewCompute(ctx, "compute", &machinelearningservices.ComputeArgs{
			ComputeName: pulumi.String("compute123"),
			Location:    pulumi.String("eastus"),
			Properties: machinelearningservices.ComputeInstance{
				ComputeType: "ComputeInstance",
				Properties: machinelearningservices.ComputeInstanceProperties{
					ApplicationSharingPolicy:         "Personal",
					ComputeInstanceAuthorizationType: "personal",
					PersonalComputeInstanceSettings: machinelearningservices.PersonalComputeInstanceSettings{
						AssignedUser: machinelearningservices.AssignedUser{
							ObjectId: "00000000-0000-0000-0000-000000000000",
							TenantId: "00000000-0000-0000-0000-000000000000",
						},
					},
					SshSettings: machinelearningservices.ComputeInstanceSshSettings{
						SshPublicAccess: "Disabled",
					},
					Subnet: machinelearningservices.ResourceId{
						Id: "test-subnet-resource-id",
					},
					VmSize: "STANDARD_NC6",
				},
			},
			ResourceGroupName: pulumi.String("testrg123"),
			WorkspaceName:     pulumi.String("workspaces123"),
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
import com.pulumi.azurenative.machinelearningservices.Compute;
import com.pulumi.azurenative.machinelearningservices.ComputeArgs;
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
        var compute = new Compute("compute", ComputeArgs.builder()        
            .computeName("compute123")
            .location("eastus")
            .properties(Map.ofEntries(
                Map.entry("computeType", "ComputeInstance"),
                Map.entry("properties", Map.ofEntries(
                    Map.entry("applicationSharingPolicy", "Personal"),
                    Map.entry("computeInstanceAuthorizationType", "personal"),
                    Map.entry("personalComputeInstanceSettings", Map.of("assignedUser", Map.ofEntries(
                        Map.entry("objectId", "00000000-0000-0000-0000-000000000000"),
                        Map.entry("tenantId", "00000000-0000-0000-0000-000000000000")
                    ))),
                    Map.entry("sshSettings", Map.of("sshPublicAccess", "Disabled")),
                    Map.entry("subnet", Map.of("id", "test-subnet-resource-id")),
                    Map.entry("vmSize", "STANDARD_NC6")
                ))
            ))
            .resourceGroupName("testrg123")
            .workspaceName("workspaces123")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const compute = new azure_native.machinelearningservices.Compute("compute", {
    computeName: "compute123",
    location: "eastus",
    properties: {
        computeType: "ComputeInstance",
        properties: {
            applicationSharingPolicy: "Personal",
            computeInstanceAuthorizationType: "personal",
            personalComputeInstanceSettings: {
                assignedUser: {
                    objectId: "00000000-0000-0000-0000-000000000000",
                    tenantId: "00000000-0000-0000-0000-000000000000",
                },
            },
            sshSettings: {
                sshPublicAccess: "Disabled",
            },
            subnet: {
                id: "test-subnet-resource-id",
            },
            vmSize: "STANDARD_NC6",
        },
    },
    resourceGroupName: "testrg123",
    workspaceName: "workspaces123",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

compute = azure_native.machinelearningservices.Compute("compute",
    compute_name="compute123",
    location="eastus",
    properties=azure_native.machinelearningservices.ComputeInstanceArgs(
        compute_type="ComputeInstance",
        properties=azure_native.machinelearningservices.ComputeInstancePropertiesArgs(
            application_sharing_policy="Personal",
            compute_instance_authorization_type="personal",
            personal_compute_instance_settings=azure_native.machinelearningservices.PersonalComputeInstanceSettingsArgs(
                assigned_user=azure_native.machinelearningservices.AssignedUserArgs(
                    object_id="00000000-0000-0000-0000-000000000000",
                    tenant_id="00000000-0000-0000-0000-000000000000",
                ),
            ),
            ssh_settings=azure_native.machinelearningservices.ComputeInstanceSshSettingsArgs(
                ssh_public_access="Disabled",
            ),
            subnet=azure_native.machinelearningservices.ResourceIdArgs(
                id="test-subnet-resource-id",
            ),
            vm_size="STANDARD_NC6",
        ),
    ),
    resource_group_name="testrg123",
    workspace_name="workspaces123")

```

```yaml
resources:
  compute:
    type: azure-native:machinelearningservices:Compute
    properties:
      computeName: compute123
      location: eastus
      properties:
        computeType: ComputeInstance
        properties:
          applicationSharingPolicy: Personal
          computeInstanceAuthorizationType: personal
          personalComputeInstanceSettings:
            assignedUser:
              objectId: 00000000-0000-0000-0000-000000000000
              tenantId: 00000000-0000-0000-0000-000000000000
          sshSettings:
            sshPublicAccess: Disabled
          subnet:
            id: test-subnet-resource-id
          vmSize: STANDARD_NC6
      resourceGroupName: testrg123
      workspaceName: workspaces123

```

{{% /example %}}
{{% example %}}
### Create an ComputeInstance Compute with Schedules
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var compute = new AzureNative.MachineLearningServices.Compute("compute", new()
    {
        ComputeName = "compute123",
        Location = "eastus",
        Properties = new AzureNative.MachineLearningServices.Inputs.ComputeInstanceArgs
        {
            ComputeType = "ComputeInstance",
            Properties = new AzureNative.MachineLearningServices.Inputs.ComputeInstancePropertiesArgs
            {
                ApplicationSharingPolicy = "Personal",
                ComputeInstanceAuthorizationType = "personal",
                PersonalComputeInstanceSettings = new AzureNative.MachineLearningServices.Inputs.PersonalComputeInstanceSettingsArgs
                {
                    AssignedUser = new AzureNative.MachineLearningServices.Inputs.AssignedUserArgs
                    {
                        ObjectId = "00000000-0000-0000-0000-000000000000",
                        TenantId = "00000000-0000-0000-0000-000000000000",
                    },
                },
                Schedules = new AzureNative.MachineLearningServices.Inputs.ComputeSchedulesArgs
                {
                    ComputeStartStop = new[]
                    {
                        new AzureNative.MachineLearningServices.Inputs.ComputeStartStopScheduleArgs
                        {
                            Action = "Stop",
                            Cron = new AzureNative.MachineLearningServices.Inputs.CronArgs
                            {
                                Expression = "0 18 * * *",
                                StartTime = "2021-04-23T01:30:00",
                                TimeZone = "Pacific Standard Time",
                            },
                            Status = "Enabled",
                            TriggerType = "Cron",
                        },
                    },
                },
                SshSettings = new AzureNative.MachineLearningServices.Inputs.ComputeInstanceSshSettingsArgs
                {
                    SshPublicAccess = "Disabled",
                },
                VmSize = "STANDARD_NC6",
            },
        },
        ResourceGroupName = "testrg123",
        WorkspaceName = "workspaces123",
    });

});


```

```go
package main

import (
	machinelearningservices "github.com/pulumi/pulumi-azure-native-sdk/machinelearningservices"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := machinelearningservices.NewCompute(ctx, "compute", &machinelearningservices.ComputeArgs{
			ComputeName: pulumi.String("compute123"),
			Location:    pulumi.String("eastus"),
			Properties: machinelearningservices.ComputeInstance{
				ComputeType: "ComputeInstance",
				Properties: machinelearningservices.ComputeInstanceProperties{
					ApplicationSharingPolicy:         "Personal",
					ComputeInstanceAuthorizationType: "personal",
					PersonalComputeInstanceSettings: machinelearningservices.PersonalComputeInstanceSettings{
						AssignedUser: machinelearningservices.AssignedUser{
							ObjectId: "00000000-0000-0000-0000-000000000000",
							TenantId: "00000000-0000-0000-0000-000000000000",
						},
					},
					Schedules: machinelearningservices.ComputeSchedules{
						ComputeStartStop: []machinelearningservices.ComputeStartStopSchedule{
							{
								Action: "Stop",
								Cron: {
									Expression: "0 18 * * *",
									StartTime:  "2021-04-23T01:30:00",
									TimeZone:   "Pacific Standard Time",
								},
								Status:      "Enabled",
								TriggerType: "Cron",
							},
						},
					},
					SshSettings: machinelearningservices.ComputeInstanceSshSettings{
						SshPublicAccess: "Disabled",
					},
					VmSize: "STANDARD_NC6",
				},
			},
			ResourceGroupName: pulumi.String("testrg123"),
			WorkspaceName:     pulumi.String("workspaces123"),
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
import com.pulumi.azurenative.machinelearningservices.Compute;
import com.pulumi.azurenative.machinelearningservices.ComputeArgs;
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
        var compute = new Compute("compute", ComputeArgs.builder()        
            .computeName("compute123")
            .location("eastus")
            .properties(Map.ofEntries(
                Map.entry("computeType", "ComputeInstance"),
                Map.entry("properties", Map.ofEntries(
                    Map.entry("applicationSharingPolicy", "Personal"),
                    Map.entry("computeInstanceAuthorizationType", "personal"),
                    Map.entry("personalComputeInstanceSettings", Map.of("assignedUser", Map.ofEntries(
                        Map.entry("objectId", "00000000-0000-0000-0000-000000000000"),
                        Map.entry("tenantId", "00000000-0000-0000-0000-000000000000")
                    ))),
                    Map.entry("schedules", Map.of("computeStartStop", Map.ofEntries(
                        Map.entry("action", "Stop"),
                        Map.entry("cron", Map.ofEntries(
                            Map.entry("expression", "0 18 * * *"),
                            Map.entry("startTime", "2021-04-23T01:30:00"),
                            Map.entry("timeZone", "Pacific Standard Time")
                        )),
                        Map.entry("status", "Enabled"),
                        Map.entry("triggerType", "Cron")
                    ))),
                    Map.entry("sshSettings", Map.of("sshPublicAccess", "Disabled")),
                    Map.entry("vmSize", "STANDARD_NC6")
                ))
            ))
            .resourceGroupName("testrg123")
            .workspaceName("workspaces123")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const compute = new azure_native.machinelearningservices.Compute("compute", {
    computeName: "compute123",
    location: "eastus",
    properties: {
        computeType: "ComputeInstance",
        properties: {
            applicationSharingPolicy: "Personal",
            computeInstanceAuthorizationType: "personal",
            personalComputeInstanceSettings: {
                assignedUser: {
                    objectId: "00000000-0000-0000-0000-000000000000",
                    tenantId: "00000000-0000-0000-0000-000000000000",
                },
            },
            schedules: {
                computeStartStop: [{
                    action: "Stop",
                    cron: {
                        expression: "0 18 * * *",
                        startTime: "2021-04-23T01:30:00",
                        timeZone: "Pacific Standard Time",
                    },
                    status: "Enabled",
                    triggerType: "Cron",
                }],
            },
            sshSettings: {
                sshPublicAccess: "Disabled",
            },
            vmSize: "STANDARD_NC6",
        },
    },
    resourceGroupName: "testrg123",
    workspaceName: "workspaces123",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

compute = azure_native.machinelearningservices.Compute("compute",
    compute_name="compute123",
    location="eastus",
    properties=azure_native.machinelearningservices.ComputeInstanceArgs(
        compute_type="ComputeInstance",
        properties=azure_native.machinelearningservices.ComputeInstancePropertiesArgs(
            application_sharing_policy="Personal",
            compute_instance_authorization_type="personal",
            personal_compute_instance_settings=azure_native.machinelearningservices.PersonalComputeInstanceSettingsArgs(
                assigned_user=azure_native.machinelearningservices.AssignedUserArgs(
                    object_id="00000000-0000-0000-0000-000000000000",
                    tenant_id="00000000-0000-0000-0000-000000000000",
                ),
            ),
            schedules=azure_native.machinelearningservices.ComputeSchedulesArgs(
                compute_start_stop=[azure_native.machinelearningservices.ComputeStartStopScheduleArgs(
                    action="Stop",
                    cron=azure_native.machinelearningservices.CronArgs(
                        expression="0 18 * * *",
                        start_time="2021-04-23T01:30:00",
                        time_zone="Pacific Standard Time",
                    ),
                    status="Enabled",
                    trigger_type="Cron",
                )],
            ),
            ssh_settings=azure_native.machinelearningservices.ComputeInstanceSshSettingsArgs(
                ssh_public_access="Disabled",
            ),
            vm_size="STANDARD_NC6",
        ),
    ),
    resource_group_name="testrg123",
    workspace_name="workspaces123")

```

```yaml
resources:
  compute:
    type: azure-native:machinelearningservices:Compute
    properties:
      computeName: compute123
      location: eastus
      properties:
        computeType: ComputeInstance
        properties:
          applicationSharingPolicy: Personal
          computeInstanceAuthorizationType: personal
          personalComputeInstanceSettings:
            assignedUser:
              objectId: 00000000-0000-0000-0000-000000000000
              tenantId: 00000000-0000-0000-0000-000000000000
          schedules:
            computeStartStop:
              - action: Stop
                cron:
                  expression: 0 18 * * *
                  startTime: 2021-04-23T01:30:00
                  timeZone: Pacific Standard Time
                status: Enabled
                triggerType: Cron
          sshSettings:
            sshPublicAccess: Disabled
          vmSize: STANDARD_NC6
      resourceGroupName: testrg123
      workspaceName: workspaces123

```

{{% /example %}}
{{% example %}}
### Create an ComputeInstance Compute with minimal inputs
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var compute = new AzureNative.MachineLearningServices.Compute("compute", new()
    {
        ComputeName = "compute123",
        Location = "eastus",
        Properties = new AzureNative.MachineLearningServices.Inputs.ComputeInstanceArgs
        {
            ComputeType = "ComputeInstance",
            Properties = new AzureNative.MachineLearningServices.Inputs.ComputeInstancePropertiesArgs
            {
                VmSize = "STANDARD_NC6",
            },
        },
        ResourceGroupName = "testrg123",
        WorkspaceName = "workspaces123",
    });

});


```

```go
package main

import (
	machinelearningservices "github.com/pulumi/pulumi-azure-native-sdk/machinelearningservices"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := machinelearningservices.NewCompute(ctx, "compute", &machinelearningservices.ComputeArgs{
			ComputeName: pulumi.String("compute123"),
			Location:    pulumi.String("eastus"),
			Properties: machinelearningservices.ComputeInstance{
				ComputeType: "ComputeInstance",
				Properties: machinelearningservices.ComputeInstanceProperties{
					VmSize: "STANDARD_NC6",
				},
			},
			ResourceGroupName: pulumi.String("testrg123"),
			WorkspaceName:     pulumi.String("workspaces123"),
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
import com.pulumi.azurenative.machinelearningservices.Compute;
import com.pulumi.azurenative.machinelearningservices.ComputeArgs;
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
        var compute = new Compute("compute", ComputeArgs.builder()        
            .computeName("compute123")
            .location("eastus")
            .properties(Map.ofEntries(
                Map.entry("computeType", "ComputeInstance"),
                Map.entry("properties", Map.of("vmSize", "STANDARD_NC6"))
            ))
            .resourceGroupName("testrg123")
            .workspaceName("workspaces123")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const compute = new azure_native.machinelearningservices.Compute("compute", {
    computeName: "compute123",
    location: "eastus",
    properties: {
        computeType: "ComputeInstance",
        properties: {
            vmSize: "STANDARD_NC6",
        },
    },
    resourceGroupName: "testrg123",
    workspaceName: "workspaces123",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

compute = azure_native.machinelearningservices.Compute("compute",
    compute_name="compute123",
    location="eastus",
    properties=azure_native.machinelearningservices.ComputeInstanceArgs(
        compute_type="ComputeInstance",
        properties=azure_native.machinelearningservices.ComputeInstancePropertiesArgs(
            vm_size="STANDARD_NC6",
        ),
    ),
    resource_group_name="testrg123",
    workspace_name="workspaces123")

```

```yaml
resources:
  compute:
    type: azure-native:machinelearningservices:Compute
    properties:
      computeName: compute123
      location: eastus
      properties:
        computeType: ComputeInstance
        properties:
          vmSize: STANDARD_NC6
      resourceGroupName: testrg123
      workspaceName: workspaces123

```

{{% /example %}}
{{% example %}}
### Update a AML Compute
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var compute = new AzureNative.MachineLearningServices.Compute("compute", new()
    {
        ComputeName = "compute123",
        Location = "eastus",
        Properties = new AzureNative.MachineLearningServices.Inputs.AmlComputeArgs
        {
            ComputeType = "AmlCompute",
            Description = "some compute",
            Properties = new AzureNative.MachineLearningServices.Inputs.AmlComputePropertiesArgs
            {
                ScaleSettings = new AzureNative.MachineLearningServices.Inputs.ScaleSettingsArgs
                {
                    MaxNodeCount = 4,
                    MinNodeCount = 4,
                    NodeIdleTimeBeforeScaleDown = "PT5M",
                },
            },
        },
        ResourceGroupName = "testrg123",
        WorkspaceName = "workspaces123",
    });

});


```

```go
package main

import (
	machinelearningservices "github.com/pulumi/pulumi-azure-native-sdk/machinelearningservices"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := machinelearningservices.NewCompute(ctx, "compute", &machinelearningservices.ComputeArgs{
			ComputeName: pulumi.String("compute123"),
			Location:    pulumi.String("eastus"),
			Properties: machinelearningservices.AmlCompute{
				ComputeType: "AmlCompute",
				Description: "some compute",
				Properties: machinelearningservices.AmlComputeProperties{
					ScaleSettings: machinelearningservices.ScaleSettings{
						MaxNodeCount:                4,
						MinNodeCount:                4,
						NodeIdleTimeBeforeScaleDown: "PT5M",
					},
				},
			},
			ResourceGroupName: pulumi.String("testrg123"),
			WorkspaceName:     pulumi.String("workspaces123"),
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
import com.pulumi.azurenative.machinelearningservices.Compute;
import com.pulumi.azurenative.machinelearningservices.ComputeArgs;
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
        var compute = new Compute("compute", ComputeArgs.builder()        
            .computeName("compute123")
            .location("eastus")
            .properties(Map.ofEntries(
                Map.entry("computeType", "AmlCompute"),
                Map.entry("description", "some compute"),
                Map.entry("properties", Map.of("scaleSettings", Map.ofEntries(
                    Map.entry("maxNodeCount", 4),
                    Map.entry("minNodeCount", 4),
                    Map.entry("nodeIdleTimeBeforeScaleDown", "PT5M")
                )))
            ))
            .resourceGroupName("testrg123")
            .workspaceName("workspaces123")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const compute = new azure_native.machinelearningservices.Compute("compute", {
    computeName: "compute123",
    location: "eastus",
    properties: {
        computeType: "AmlCompute",
        description: "some compute",
        properties: {
            scaleSettings: {
                maxNodeCount: 4,
                minNodeCount: 4,
                nodeIdleTimeBeforeScaleDown: "PT5M",
            },
        },
    },
    resourceGroupName: "testrg123",
    workspaceName: "workspaces123",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

compute = azure_native.machinelearningservices.Compute("compute",
    compute_name="compute123",
    location="eastus",
    properties=azure_native.machinelearningservices.AmlComputeArgs(
        compute_type="AmlCompute",
        description="some compute",
        properties=azure_native.machinelearningservices.AmlComputePropertiesArgs(
            scale_settings=azure_native.machinelearningservices.ScaleSettingsArgs(
                max_node_count=4,
                min_node_count=4,
                node_idle_time_before_scale_down="PT5M",
            ),
        ),
    ),
    resource_group_name="testrg123",
    workspace_name="workspaces123")

```

```yaml
resources:
  compute:
    type: azure-native:machinelearningservices:Compute
    properties:
      computeName: compute123
      location: eastus
      properties:
        computeType: AmlCompute
        description: some compute
        properties:
          scaleSettings:
            maxNodeCount: 4
            minNodeCount: 4
            nodeIdleTimeBeforeScaleDown: PT5M
      resourceGroupName: testrg123
      workspaceName: workspaces123

```

{{% /example %}}
{{% example %}}
### Update an AKS Compute
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var compute = new AzureNative.MachineLearningServices.Compute("compute", new()
    {
        ComputeName = "compute123",
        Location = "eastus",
        Properties = new AzureNative.MachineLearningServices.Inputs.AKSArgs
        {
            ComputeType = "AKS",
            Description = "some compute",
            Properties = new AzureNative.MachineLearningServices.Inputs.AKSSchemaPropertiesArgs
            {
                AgentCount = 4,
            },
            ResourceId = "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourcegroups/testrg123/providers/Microsoft.ContainerService/managedClusters/compute123-56826-c9b00420020b2",
        },
        ResourceGroupName = "testrg123",
        WorkspaceName = "workspaces123",
    });

});


```

```go
package main

import (
	machinelearningservices "github.com/pulumi/pulumi-azure-native-sdk/machinelearningservices"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := machinelearningservices.NewCompute(ctx, "compute", &machinelearningservices.ComputeArgs{
			ComputeName: pulumi.String("compute123"),
			Location:    pulumi.String("eastus"),
			Properties: machinelearningservices.AKS{
				ComputeType: "AKS",
				Description: "some compute",
				Properties: machinelearningservices.AKSSchemaProperties{
					AgentCount: 4,
				},
				ResourceId: "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourcegroups/testrg123/providers/Microsoft.ContainerService/managedClusters/compute123-56826-c9b00420020b2",
			},
			ResourceGroupName: pulumi.String("testrg123"),
			WorkspaceName:     pulumi.String("workspaces123"),
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
import com.pulumi.azurenative.machinelearningservices.Compute;
import com.pulumi.azurenative.machinelearningservices.ComputeArgs;
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
        var compute = new Compute("compute", ComputeArgs.builder()        
            .computeName("compute123")
            .location("eastus")
            .properties(Map.ofEntries(
                Map.entry("computeType", "AKS"),
                Map.entry("description", "some compute"),
                Map.entry("properties", Map.of("agentCount", 4)),
                Map.entry("resourceId", "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourcegroups/testrg123/providers/Microsoft.ContainerService/managedClusters/compute123-56826-c9b00420020b2")
            ))
            .resourceGroupName("testrg123")
            .workspaceName("workspaces123")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const compute = new azure_native.machinelearningservices.Compute("compute", {
    computeName: "compute123",
    location: "eastus",
    properties: {
        computeType: "AKS",
        description: "some compute",
        properties: {
            agentCount: 4,
        },
        resourceId: "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourcegroups/testrg123/providers/Microsoft.ContainerService/managedClusters/compute123-56826-c9b00420020b2",
    },
    resourceGroupName: "testrg123",
    workspaceName: "workspaces123",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

compute = azure_native.machinelearningservices.Compute("compute",
    compute_name="compute123",
    location="eastus",
    properties=azure_native.machinelearningservices.AKSArgs(
        compute_type="AKS",
        description="some compute",
        properties=azure_native.machinelearningservices.AKSSchemaPropertiesArgs(
            agent_count=4,
        ),
        resource_id="/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourcegroups/testrg123/providers/Microsoft.ContainerService/managedClusters/compute123-56826-c9b00420020b2",
    ),
    resource_group_name="testrg123",
    workspace_name="workspaces123")

```

```yaml
resources:
  compute:
    type: azure-native:machinelearningservices:Compute
    properties:
      computeName: compute123
      location: eastus
      properties:
        computeType: AKS
        description: some compute
        properties:
          agentCount: 4
        resourceId: /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourcegroups/testrg123/providers/Microsoft.ContainerService/managedClusters/compute123-56826-c9b00420020b2
      resourceGroupName: testrg123
      workspaceName: workspaces123

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:machinelearningservices:Compute compute123 /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.MachineLearningServices/workspaces/workspaces123/computes/compute123 
```
