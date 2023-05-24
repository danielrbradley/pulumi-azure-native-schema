A container group.
API Version: 2022-09-01.
Previous API Version: 2021-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ContainerGroupCreateWithExtensions
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var containerGroup = new AzureNative.ContainerInstance.ContainerGroup("containerGroup", new()
    {
        ContainerGroupName = "demo1",
        Containers = new[]
        {
            new AzureNative.ContainerInstance.Inputs.ContainerArgs
            {
                Command = new[] {},
                EnvironmentVariables = new[] {},
                Image = "nginx",
                Name = "demo1",
                Ports = new[]
                {
                    new AzureNative.ContainerInstance.Inputs.ContainerPortArgs
                    {
                        Port = 80,
                    },
                },
                Resources = new AzureNative.ContainerInstance.Inputs.ResourceRequirementsArgs
                {
                    Requests = new AzureNative.ContainerInstance.Inputs.ResourceRequestsArgs
                    {
                        Cpu = 1,
                        MemoryInGB = 1.5,
                    },
                },
            },
        },
        Extensions = new[]
        {
            new AzureNative.ContainerInstance.Inputs.DeploymentExtensionSpecArgs
            {
                ExtensionType = "kube-proxy",
                Name = "kube-proxy",
                ProtectedSettings = 
                {
                    { "kubeConfig", "<kubeconfig encoded string>" },
                },
                Settings = 
                {
                    { "clusterCidr", "10.240.0.0/16" },
                    { "kubeVersion", "v1.9.10" },
                },
                Version = "1.0",
            },
            new AzureNative.ContainerInstance.Inputs.DeploymentExtensionSpecArgs
            {
                ExtensionType = "realtime-metrics",
                Name = "vk-realtime-metrics",
                Version = "1.0",
            },
        },
        ImageRegistryCredentials = new[] {},
        IpAddress = new AzureNative.ContainerInstance.Inputs.IpAddressArgs
        {
            Ports = new[]
            {
                new AzureNative.ContainerInstance.Inputs.PortArgs
                {
                    Port = 80,
                    Protocol = "TCP",
                },
            },
            Type = "Private",
        },
        Location = "eastus2",
        OsType = "Linux",
        ResourceGroupName = "demo",
        SubnetIds = new[]
        {
            new AzureNative.ContainerInstance.Inputs.ContainerGroupSubnetIdArgs
            {
                Id = "/subscriptions/00000000-0000-0000-0000-00000000/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-rg-vnet/subnets/test-subnet",
            },
        },
    });

});


```

```go
package main

import (
	containerinstance "github.com/pulumi/pulumi-azure-native-sdk/containerinstance"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := containerinstance.NewContainerGroup(ctx, "containerGroup", &containerinstance.ContainerGroupArgs{
			ContainerGroupName: pulumi.String("demo1"),
			Containers: []containerinstance.ContainerArgs{
				{
					Command:              pulumi.StringArray{},
					EnvironmentVariables: containerinstance.EnvironmentVariableArray{},
					Image:                pulumi.String("nginx"),
					Name:                 pulumi.String("demo1"),
					Ports: containerinstance.ContainerPortArray{
						{
							Port: pulumi.Int(80),
						},
					},
					Resources: {
						Requests: {
							Cpu:        pulumi.Float64(1),
							MemoryInGB: pulumi.Float64(1.5),
						},
					},
				},
			},
			Extensions: []containerinstance.DeploymentExtensionSpecArgs{
				{
					ExtensionType: pulumi.String("kube-proxy"),
					Name:          pulumi.String("kube-proxy"),
					ProtectedSettings: {
						KubeConfig: "<kubeconfig encoded string>",
					},
					Settings: {
						ClusterCidr: "10.240.0.0/16",
						KubeVersion: "v1.9.10",
					},
					Version: pulumi.String("1.0"),
				},
				{
					ExtensionType: pulumi.String("realtime-metrics"),
					Name:          pulumi.String("vk-realtime-metrics"),
					Version:       pulumi.String("1.0"),
				},
			},
			ImageRegistryCredentials: containerinstance.ImageRegistryCredentialArray{},
			IpAddress: containerinstance.IpAddressResponse{
				Ports: containerinstance.PortArray{
					&containerinstance.PortArgs{
						Port:     pulumi.Int(80),
						Protocol: pulumi.String("TCP"),
					},
				},
				Type: pulumi.String("Private"),
			},
			Location:          pulumi.String("eastus2"),
			OsType:            pulumi.String("Linux"),
			ResourceGroupName: pulumi.String("demo"),
			SubnetIds: []containerinstance.ContainerGroupSubnetIdArgs{
				{
					Id: pulumi.String("/subscriptions/00000000-0000-0000-0000-00000000/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-rg-vnet/subnets/test-subnet"),
				},
			},
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
import com.pulumi.azurenative.containerinstance.ContainerGroup;
import com.pulumi.azurenative.containerinstance.ContainerGroupArgs;
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
        var containerGroup = new ContainerGroup("containerGroup", ContainerGroupArgs.builder()        
            .containerGroupName("demo1")
            .containers(Map.ofEntries(
                Map.entry("command", ),
                Map.entry("environmentVariables", ),
                Map.entry("image", "nginx"),
                Map.entry("name", "demo1"),
                Map.entry("ports", Map.of("port", 80)),
                Map.entry("resources", Map.of("requests", Map.ofEntries(
                    Map.entry("cpu", 1),
                    Map.entry("memoryInGB", 1.5)
                )))
            ))
            .extensions(            
                Map.ofEntries(
                    Map.entry("extensionType", "kube-proxy"),
                    Map.entry("name", "kube-proxy"),
                    Map.entry("protectedSettings", Map.of("kubeConfig", "<kubeconfig encoded string>")),
                    Map.entry("settings", Map.ofEntries(
                        Map.entry("clusterCidr", "10.240.0.0/16"),
                        Map.entry("kubeVersion", "v1.9.10")
                    )),
                    Map.entry("version", "1.0")
                ),
                Map.ofEntries(
                    Map.entry("extensionType", "realtime-metrics"),
                    Map.entry("name", "vk-realtime-metrics"),
                    Map.entry("version", "1.0")
                ))
            .imageRegistryCredentials()
            .ipAddress(Map.ofEntries(
                Map.entry("ports", Map.ofEntries(
                    Map.entry("port", 80),
                    Map.entry("protocol", "TCP")
                )),
                Map.entry("type", "Private")
            ))
            .location("eastus2")
            .osType("Linux")
            .resourceGroupName("demo")
            .subnetIds(Map.of("id", "/subscriptions/00000000-0000-0000-0000-00000000/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-rg-vnet/subnets/test-subnet"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const containerGroup = new azure_native.containerinstance.ContainerGroup("containerGroup", {
    containerGroupName: "demo1",
    containers: [{
        command: [],
        environmentVariables: [],
        image: "nginx",
        name: "demo1",
        ports: [{
            port: 80,
        }],
        resources: {
            requests: {
                cpu: 1,
                memoryInGB: 1.5,
            },
        },
    }],
    extensions: [
        {
            extensionType: "kube-proxy",
            name: "kube-proxy",
            protectedSettings: {
                kubeConfig: "<kubeconfig encoded string>",
            },
            settings: {
                clusterCidr: "10.240.0.0/16",
                kubeVersion: "v1.9.10",
            },
            version: "1.0",
        },
        {
            extensionType: "realtime-metrics",
            name: "vk-realtime-metrics",
            version: "1.0",
        },
    ],
    imageRegistryCredentials: [],
    ipAddress: {
        ports: [{
            port: 80,
            protocol: "TCP",
        }],
        type: "Private",
    },
    location: "eastus2",
    osType: "Linux",
    resourceGroupName: "demo",
    subnetIds: [{
        id: "/subscriptions/00000000-0000-0000-0000-00000000/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-rg-vnet/subnets/test-subnet",
    }],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

container_group = azure_native.containerinstance.ContainerGroup("containerGroup",
    container_group_name="demo1",
    containers=[{
        "command": [],
        "environmentVariables": [],
        "image": "nginx",
        "name": "demo1",
        "ports": [azure_native.containerinstance.ContainerPortArgs(
            port=80,
        )],
        "resources": {
            "requests": azure_native.containerinstance.ResourceRequestsArgs(
                cpu=1,
                memory_in_gb=1.5,
            ),
        },
    }],
    extensions=[
        azure_native.containerinstance.DeploymentExtensionSpecArgs(
            extension_type="kube-proxy",
            name="kube-proxy",
            protected_settings={
                "kubeConfig": "<kubeconfig encoded string>",
            },
            settings={
                "clusterCidr": "10.240.0.0/16",
                "kubeVersion": "v1.9.10",
            },
            version="1.0",
        ),
        azure_native.containerinstance.DeploymentExtensionSpecArgs(
            extension_type="realtime-metrics",
            name="vk-realtime-metrics",
            version="1.0",
        ),
    ],
    image_registry_credentials=[],
    ip_address=azure_native.containerinstance.IpAddressResponseArgs(
        ports=[azure_native.containerinstance.PortArgs(
            port=80,
            protocol="TCP",
        )],
        type="Private",
    ),
    location="eastus2",
    os_type="Linux",
    resource_group_name="demo",
    subnet_ids=[azure_native.containerinstance.ContainerGroupSubnetIdArgs(
        id="/subscriptions/00000000-0000-0000-0000-00000000/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-rg-vnet/subnets/test-subnet",
    )])

```

```yaml
resources:
  containerGroup:
    type: azure-native:containerinstance:ContainerGroup
    properties:
      containerGroupName: demo1
      containers:
        - command: []
          environmentVariables: []
          image: nginx
          name: demo1
          ports:
            - port: 80
          resources:
            requests:
              cpu: 1
              memoryInGB: 1.5
      extensions:
        - extensionType: kube-proxy
          name: kube-proxy
          protectedSettings:
            kubeConfig: <kubeconfig encoded string>
          settings:
            clusterCidr: 10.240.0.0/16
            kubeVersion: v1.9.10
          version: '1.0'
        - extensionType: realtime-metrics
          name: vk-realtime-metrics
          version: '1.0'
      imageRegistryCredentials: []
      ipAddress:
        ports:
          - port: 80
            protocol: TCP
        type: Private
      location: eastus2
      osType: Linux
      resourceGroupName: demo
      subnetIds:
        - id: /subscriptions/00000000-0000-0000-0000-00000000/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-rg-vnet/subnets/test-subnet

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:containerinstance:ContainerGroup demo1 /subscriptions/subid/resourceGroups/demo/providers/Microsoft.ContainerInstance/containerGroups/demo1 
```
