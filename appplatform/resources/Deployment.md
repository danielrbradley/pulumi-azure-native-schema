Deployment resource payload
API Version: 2022-12-01.
Previous API Version: 2020-07-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Deployments_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var deployment = new AzureNative.AppPlatform.Deployment("deployment", new()
    {
        AppName = "myapp",
        DeploymentName = "mydeployment",
        Properties = new AzureNative.AppPlatform.Inputs.DeploymentResourcePropertiesArgs
        {
            DeploymentSettings = new AzureNative.AppPlatform.Inputs.DeploymentSettingsArgs
            {
                AddonConfigs = 
                {
                    { "ApplicationConfigurationService", 
                    {
                        { "patterns", new[]
                        {
                            "mypattern",
                        } },
                    } },
                },
                EnvironmentVariables = 
                {
                    { "env", "test" },
                },
                LivenessProbe = new AzureNative.AppPlatform.Inputs.ProbeArgs
                {
                    DisableProbe = false,
                    FailureThreshold = 3,
                    InitialDelaySeconds = 30,
                    PeriodSeconds = 10,
                    ProbeAction = new AzureNative.AppPlatform.Inputs.HTTPGetActionArgs
                    {
                        Path = "/health",
                        Scheme = "HTTP",
                        Type = "HTTPGetAction",
                    },
                },
                ReadinessProbe = new AzureNative.AppPlatform.Inputs.ProbeArgs
                {
                    DisableProbe = false,
                    FailureThreshold = 3,
                    InitialDelaySeconds = 30,
                    PeriodSeconds = 10,
                    ProbeAction = new AzureNative.AppPlatform.Inputs.HTTPGetActionArgs
                    {
                        Path = "/health",
                        Scheme = "HTTP",
                        Type = "HTTPGetAction",
                    },
                },
                ResourceRequests = new AzureNative.AppPlatform.Inputs.ResourceRequestsArgs
                {
                    Cpu = "1000m",
                    Memory = "3Gi",
                },
                TerminationGracePeriodSeconds = 30,
            },
            Source = new AzureNative.AppPlatform.Inputs.SourceUploadedUserSourceInfoArgs
            {
                ArtifactSelector = "sub-module-1",
                RelativePath = "resources/a172cedcae47474b615c54d510a5d84a8dea3032e958587430b413538be3f333-2019082605-e3095339-1723-44b7-8b5e-31b1003978bc",
                Type = "Source",
                Version = "1.0",
            },
        },
        ResourceGroupName = "myResourceGroup",
        ServiceName = "myservice",
        Sku = new AzureNative.AppPlatform.Inputs.SkuArgs
        {
            Capacity = 1,
            Name = "S0",
            Tier = "Standard",
        },
    });

});


```

```go
package main

import (
	appplatform "github.com/pulumi/pulumi-azure-native-sdk/appplatform"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := appplatform.NewDeployment(ctx, "deployment", &appplatform.DeploymentArgs{
			AppName:        pulumi.String("myapp"),
			DeploymentName: pulumi.String("mydeployment"),
			Properties: appplatform.DeploymentResourcePropertiesResponse{
				DeploymentSettings: appplatform.DeploymentSettingsResponse{
					AddonConfigs: pulumi.AnyMap{
						"ApplicationConfigurationService": pulumi.Any{
							Patterns: []string{
								"mypattern",
							},
						},
					},
					EnvironmentVariables: pulumi.StringMap{
						"env": pulumi.String("test"),
					},
					LivenessProbe: &appplatform.ProbeArgs{
						DisableProbe:        pulumi.Bool(false),
						FailureThreshold:    pulumi.Int(3),
						InitialDelaySeconds: pulumi.Int(30),
						PeriodSeconds:       pulumi.Int(10),
						ProbeAction: appplatform.HTTPGetAction{
							Path:   "/health",
							Scheme: "HTTP",
							Type:   "HTTPGetAction",
						},
					},
					ReadinessProbe: &appplatform.ProbeArgs{
						DisableProbe:        pulumi.Bool(false),
						FailureThreshold:    pulumi.Int(3),
						InitialDelaySeconds: pulumi.Int(30),
						PeriodSeconds:       pulumi.Int(10),
						ProbeAction: appplatform.HTTPGetAction{
							Path:   "/health",
							Scheme: "HTTP",
							Type:   "HTTPGetAction",
						},
					},
					ResourceRequests: &appplatform.ResourceRequestsArgs{
						Cpu:    pulumi.String("1000m"),
						Memory: pulumi.String("3Gi"),
					},
					TerminationGracePeriodSeconds: pulumi.Int(30),
				},
				Source: appplatform.SourceUploadedUserSourceInfo{
					ArtifactSelector: "sub-module-1",
					RelativePath:     "resources/a172cedcae47474b615c54d510a5d84a8dea3032e958587430b413538be3f333-2019082605-e3095339-1723-44b7-8b5e-31b1003978bc",
					Type:             "Source",
					Version:          "1.0",
				},
			},
			ResourceGroupName: pulumi.String("myResourceGroup"),
			ServiceName:       pulumi.String("myservice"),
			Sku: &appplatform.SkuArgs{
				Capacity: pulumi.Int(1),
				Name:     pulumi.String("S0"),
				Tier:     pulumi.String("Standard"),
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
import com.pulumi.azurenative.appplatform.Deployment;
import com.pulumi.azurenative.appplatform.DeploymentArgs;
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
        var deployment = new Deployment("deployment", DeploymentArgs.builder()        
            .appName("myapp")
            .deploymentName("mydeployment")
            .properties(Map.ofEntries(
                Map.entry("deploymentSettings", Map.ofEntries(
                    Map.entry("addonConfigs", Map.of("ApplicationConfigurationService", Map.of("patterns", "mypattern"))),
                    Map.entry("environmentVariables", Map.of("env", "test")),
                    Map.entry("livenessProbe", Map.ofEntries(
                        Map.entry("disableProbe", false),
                        Map.entry("failureThreshold", 3),
                        Map.entry("initialDelaySeconds", 30),
                        Map.entry("periodSeconds", 10),
                        Map.entry("probeAction", Map.ofEntries(
                            Map.entry("path", "/health"),
                            Map.entry("scheme", "HTTP"),
                            Map.entry("type", "HTTPGetAction")
                        ))
                    )),
                    Map.entry("readinessProbe", Map.ofEntries(
                        Map.entry("disableProbe", false),
                        Map.entry("failureThreshold", 3),
                        Map.entry("initialDelaySeconds", 30),
                        Map.entry("periodSeconds", 10),
                        Map.entry("probeAction", Map.ofEntries(
                            Map.entry("path", "/health"),
                            Map.entry("scheme", "HTTP"),
                            Map.entry("type", "HTTPGetAction")
                        ))
                    )),
                    Map.entry("resourceRequests", Map.ofEntries(
                        Map.entry("cpu", "1000m"),
                        Map.entry("memory", "3Gi")
                    )),
                    Map.entry("terminationGracePeriodSeconds", 30)
                )),
                Map.entry("source", Map.ofEntries(
                    Map.entry("artifactSelector", "sub-module-1"),
                    Map.entry("relativePath", "resources/a172cedcae47474b615c54d510a5d84a8dea3032e958587430b413538be3f333-2019082605-e3095339-1723-44b7-8b5e-31b1003978bc"),
                    Map.entry("type", "Source"),
                    Map.entry("version", "1.0")
                ))
            ))
            .resourceGroupName("myResourceGroup")
            .serviceName("myservice")
            .sku(Map.ofEntries(
                Map.entry("capacity", 1),
                Map.entry("name", "S0"),
                Map.entry("tier", "Standard")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const deployment = new azure_native.appplatform.Deployment("deployment", {
    appName: "myapp",
    deploymentName: "mydeployment",
    properties: {
        deploymentSettings: {
            addonConfigs: {
                ApplicationConfigurationService: {
                    patterns: ["mypattern"],
                },
            },
            environmentVariables: {
                env: "test",
            },
            livenessProbe: {
                disableProbe: false,
                failureThreshold: 3,
                initialDelaySeconds: 30,
                periodSeconds: 10,
                probeAction: {
                    path: "/health",
                    scheme: "HTTP",
                    type: "HTTPGetAction",
                },
            },
            readinessProbe: {
                disableProbe: false,
                failureThreshold: 3,
                initialDelaySeconds: 30,
                periodSeconds: 10,
                probeAction: {
                    path: "/health",
                    scheme: "HTTP",
                    type: "HTTPGetAction",
                },
            },
            resourceRequests: {
                cpu: "1000m",
                memory: "3Gi",
            },
            terminationGracePeriodSeconds: 30,
        },
        source: {
            artifactSelector: "sub-module-1",
            relativePath: "resources/a172cedcae47474b615c54d510a5d84a8dea3032e958587430b413538be3f333-2019082605-e3095339-1723-44b7-8b5e-31b1003978bc",
            type: "Source",
            version: "1.0",
        },
    },
    resourceGroupName: "myResourceGroup",
    serviceName: "myservice",
    sku: {
        capacity: 1,
        name: "S0",
        tier: "Standard",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

deployment = azure_native.appplatform.Deployment("deployment",
    app_name="myapp",
    deployment_name="mydeployment",
    properties=azure_native.appplatform.DeploymentResourcePropertiesResponseArgs(
        deployment_settings={
            "addonConfigs": {
                "ApplicationConfigurationService": {
                    "patterns": ["mypattern"],
                },
            },
            "environmentVariables": {
                "env": "test",
            },
            "livenessProbe": azure_native.appplatform.ProbeArgs(
                disable_probe=False,
                failure_threshold=3,
                initial_delay_seconds=30,
                period_seconds=10,
                probe_action=azure_native.appplatform.HTTPGetActionArgs(
                    path="/health",
                    scheme="HTTP",
                    type="HTTPGetAction",
                ),
            ),
            "readinessProbe": azure_native.appplatform.ProbeArgs(
                disable_probe=False,
                failure_threshold=3,
                initial_delay_seconds=30,
                period_seconds=10,
                probe_action=azure_native.appplatform.HTTPGetActionArgs(
                    path="/health",
                    scheme="HTTP",
                    type="HTTPGetAction",
                ),
            ),
            "resourceRequests": azure_native.appplatform.ResourceRequestsArgs(
                cpu="1000m",
                memory="3Gi",
            ),
            "terminationGracePeriodSeconds": 30,
        },
        source=azure_native.appplatform.SourceUploadedUserSourceInfoArgs(
            artifact_selector="sub-module-1",
            relative_path="resources/a172cedcae47474b615c54d510a5d84a8dea3032e958587430b413538be3f333-2019082605-e3095339-1723-44b7-8b5e-31b1003978bc",
            type="Source",
            version="1.0",
        ),
    ),
    resource_group_name="myResourceGroup",
    service_name="myservice",
    sku=azure_native.appplatform.SkuArgs(
        capacity=1,
        name="S0",
        tier="Standard",
    ))

```

```yaml
resources:
  deployment:
    type: azure-native:appplatform:Deployment
    properties:
      appName: myapp
      deploymentName: mydeployment
      properties:
        deploymentSettings:
          addonConfigs:
            ApplicationConfigurationService:
              patterns:
                - mypattern
          environmentVariables:
            env: test
          livenessProbe:
            disableProbe: false
            failureThreshold: 3
            initialDelaySeconds: 30
            periodSeconds: 10
            probeAction:
              path: /health
              scheme: HTTP
              type: HTTPGetAction
          readinessProbe:
            disableProbe: false
            failureThreshold: 3
            initialDelaySeconds: 30
            periodSeconds: 10
            probeAction:
              path: /health
              scheme: HTTP
              type: HTTPGetAction
          resourceRequests:
            cpu: 1000m
            memory: 3Gi
          terminationGracePeriodSeconds: 30
        source:
          artifactSelector: sub-module-1
          relativePath: resources/a172cedcae47474b615c54d510a5d84a8dea3032e958587430b413538be3f333-2019082605-e3095339-1723-44b7-8b5e-31b1003978bc
          type: Source
          version: '1.0'
      resourceGroupName: myResourceGroup
      serviceName: myservice
      sku:
        capacity: 1
        name: S0
        tier: Standard

```

{{% /example %}}
{{% example %}}
### Deployments_CreateOrUpdate_CustomContainer
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var deployment = new AzureNative.AppPlatform.Deployment("deployment", new()
    {
        AppName = "myapp",
        DeploymentName = "mydeployment",
        Properties = new AzureNative.AppPlatform.Inputs.DeploymentResourcePropertiesArgs
        {
            DeploymentSettings = new AzureNative.AppPlatform.Inputs.DeploymentSettingsArgs
            {
                EnvironmentVariables = 
                {
                    { "env", "test" },
                },
                LivenessProbe = new AzureNative.AppPlatform.Inputs.ProbeArgs
                {
                    DisableProbe = false,
                    FailureThreshold = 3,
                    InitialDelaySeconds = 30,
                    PeriodSeconds = 10,
                    ProbeAction = new AzureNative.AppPlatform.Inputs.HTTPGetActionArgs
                    {
                        Path = "/health",
                        Scheme = "HTTP",
                        Type = "HTTPGetAction",
                    },
                },
                ReadinessProbe = new AzureNative.AppPlatform.Inputs.ProbeArgs
                {
                    DisableProbe = false,
                    FailureThreshold = 3,
                    InitialDelaySeconds = 30,
                    PeriodSeconds = 10,
                    ProbeAction = new AzureNative.AppPlatform.Inputs.HTTPGetActionArgs
                    {
                        Path = "/health",
                        Scheme = "HTTP",
                        Type = "HTTPGetAction",
                    },
                },
                ResourceRequests = new AzureNative.AppPlatform.Inputs.ResourceRequestsArgs
                {
                    Cpu = "1000m",
                    Memory = "3Gi",
                },
                TerminationGracePeriodSeconds = 30,
            },
            Source = new AzureNative.AppPlatform.Inputs.CustomContainerUserSourceInfoArgs
            {
                CustomContainer = new AzureNative.AppPlatform.Inputs.CustomContainerArgs
                {
                    Args = new[]
                    {
                        "-c",
                        "while true; do echo hello; sleep 10;done",
                    },
                    Command = new[]
                    {
                        "/bin/sh",
                    },
                    ContainerImage = "myContainerImage:v1",
                    ImageRegistryCredential = new AzureNative.AppPlatform.Inputs.ImageRegistryCredentialArgs
                    {
                        Password = "myPassword",
                        Username = "myUsername",
                    },
                    LanguageFramework = "springboot",
                    Server = "myacr.azurecr.io",
                },
                Type = "Container",
            },
        },
        ResourceGroupName = "myResourceGroup",
        ServiceName = "myservice",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.appplatform.Deployment;
import com.pulumi.azurenative.appplatform.DeploymentArgs;
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
        var deployment = new Deployment("deployment", DeploymentArgs.builder()        
            .appName("myapp")
            .deploymentName("mydeployment")
            .properties(Map.ofEntries(
                Map.entry("deploymentSettings", Map.ofEntries(
                    Map.entry("environmentVariables", Map.of("env", "test")),
                    Map.entry("livenessProbe", Map.ofEntries(
                        Map.entry("disableProbe", false),
                        Map.entry("failureThreshold", 3),
                        Map.entry("initialDelaySeconds", 30),
                        Map.entry("periodSeconds", 10),
                        Map.entry("probeAction", Map.ofEntries(
                            Map.entry("path", "/health"),
                            Map.entry("scheme", "HTTP"),
                            Map.entry("type", "HTTPGetAction")
                        ))
                    )),
                    Map.entry("readinessProbe", Map.ofEntries(
                        Map.entry("disableProbe", false),
                        Map.entry("failureThreshold", 3),
                        Map.entry("initialDelaySeconds", 30),
                        Map.entry("periodSeconds", 10),
                        Map.entry("probeAction", Map.ofEntries(
                            Map.entry("path", "/health"),
                            Map.entry("scheme", "HTTP"),
                            Map.entry("type", "HTTPGetAction")
                        ))
                    )),
                    Map.entry("resourceRequests", Map.ofEntries(
                        Map.entry("cpu", "1000m"),
                        Map.entry("memory", "3Gi")
                    )),
                    Map.entry("terminationGracePeriodSeconds", 30)
                )),
                Map.entry("source", Map.ofEntries(
                    Map.entry("customContainer", Map.ofEntries(
                        Map.entry("args",                         
                            "-c",
                            "while true; do echo hello; sleep 10;done"),
                        Map.entry("command", "/bin/sh"),
                        Map.entry("containerImage", "myContainerImage:v1"),
                        Map.entry("imageRegistryCredential", Map.ofEntries(
                            Map.entry("password", "myPassword"),
                            Map.entry("username", "myUsername")
                        )),
                        Map.entry("languageFramework", "springboot"),
                        Map.entry("server", "myacr.azurecr.io")
                    )),
                    Map.entry("type", "Container")
                ))
            ))
            .resourceGroupName("myResourceGroup")
            .serviceName("myservice")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const deployment = new azure_native.appplatform.Deployment("deployment", {
    appName: "myapp",
    deploymentName: "mydeployment",
    properties: {
        deploymentSettings: {
            environmentVariables: {
                env: "test",
            },
            livenessProbe: {
                disableProbe: false,
                failureThreshold: 3,
                initialDelaySeconds: 30,
                periodSeconds: 10,
                probeAction: {
                    path: "/health",
                    scheme: "HTTP",
                    type: "HTTPGetAction",
                },
            },
            readinessProbe: {
                disableProbe: false,
                failureThreshold: 3,
                initialDelaySeconds: 30,
                periodSeconds: 10,
                probeAction: {
                    path: "/health",
                    scheme: "HTTP",
                    type: "HTTPGetAction",
                },
            },
            resourceRequests: {
                cpu: "1000m",
                memory: "3Gi",
            },
            terminationGracePeriodSeconds: 30,
        },
        source: {
            customContainer: {
                args: [
                    "-c",
                    "while true; do echo hello; sleep 10;done",
                ],
                command: ["/bin/sh"],
                containerImage: "myContainerImage:v1",
                imageRegistryCredential: {
                    password: "myPassword",
                    username: "myUsername",
                },
                languageFramework: "springboot",
                server: "myacr.azurecr.io",
            },
            type: "Container",
        },
    },
    resourceGroupName: "myResourceGroup",
    serviceName: "myservice",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

deployment = azure_native.appplatform.Deployment("deployment",
    app_name="myapp",
    deployment_name="mydeployment",
    properties=azure_native.appplatform.DeploymentResourcePropertiesResponseArgs(
        deployment_settings={
            "environmentVariables": {
                "env": "test",
            },
            "livenessProbe": azure_native.appplatform.ProbeArgs(
                disable_probe=False,
                failure_threshold=3,
                initial_delay_seconds=30,
                period_seconds=10,
                probe_action=azure_native.appplatform.HTTPGetActionArgs(
                    path="/health",
                    scheme="HTTP",
                    type="HTTPGetAction",
                ),
            ),
            "readinessProbe": azure_native.appplatform.ProbeArgs(
                disable_probe=False,
                failure_threshold=3,
                initial_delay_seconds=30,
                period_seconds=10,
                probe_action=azure_native.appplatform.HTTPGetActionArgs(
                    path="/health",
                    scheme="HTTP",
                    type="HTTPGetAction",
                ),
            ),
            "resourceRequests": azure_native.appplatform.ResourceRequestsArgs(
                cpu="1000m",
                memory="3Gi",
            ),
            "terminationGracePeriodSeconds": 30,
        },
        source=azure_native.appplatform.CustomContainerUserSourceInfoArgs(
            custom_container=azure_native.appplatform.CustomContainerArgs(
                args=[
                    "-c",
                    "while true; do echo hello; sleep 10;done",
                ],
                command=["/bin/sh"],
                container_image="myContainerImage:v1",
                image_registry_credential=azure_native.appplatform.ImageRegistryCredentialArgs(
                    password="myPassword",
                    username="myUsername",
                ),
                language_framework="springboot",
                server="myacr.azurecr.io",
            ),
            type="Container",
        ),
    ),
    resource_group_name="myResourceGroup",
    service_name="myservice")

```

```yaml
resources:
  deployment:
    type: azure-native:appplatform:Deployment
    properties:
      appName: myapp
      deploymentName: mydeployment
      properties:
        deploymentSettings:
          environmentVariables:
            env: test
          livenessProbe:
            disableProbe: false
            failureThreshold: 3
            initialDelaySeconds: 30
            periodSeconds: 10
            probeAction:
              path: /health
              scheme: HTTP
              type: HTTPGetAction
          readinessProbe:
            disableProbe: false
            failureThreshold: 3
            initialDelaySeconds: 30
            periodSeconds: 10
            probeAction:
              path: /health
              scheme: HTTP
              type: HTTPGetAction
          resourceRequests:
            cpu: 1000m
            memory: 3Gi
          terminationGracePeriodSeconds: 30
        source:
          customContainer:
            args:
              - -c
              - while true; do echo hello; sleep 10;done
            command:
              - /bin/sh
            containerImage: myContainerImage:v1
            imageRegistryCredential:
              password: myPassword
              username: myUsername
            languageFramework: springboot
            server: myacr.azurecr.io
          type: Container
      resourceGroupName: myResourceGroup
      serviceName: myservice

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:appplatform:Deployment mydeployment /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.AppPlatform/Spring/myservice/apps/myapp/deployments/mydeployment 
```
