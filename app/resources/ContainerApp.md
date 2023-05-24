Container App.
API Version: 2022-10-01.
Previous API Version: 2022-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or Update Container App
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var containerApp = new AzureNative.App.ContainerApp("containerApp", new()
    {
        Configuration = new AzureNative.App.Inputs.ConfigurationArgs
        {
            Dapr = new AzureNative.App.Inputs.DaprArgs
            {
                AppPort = 3000,
                AppProtocol = "http",
                EnableApiLogging = true,
                Enabled = true,
                HttpMaxRequestSize = 10,
                HttpReadBufferSize = 30,
                LogLevel = "debug",
            },
            Ingress = new AzureNative.App.Inputs.IngressArgs
            {
                ClientCertificateMode = "accept",
                CorsPolicy = new AzureNative.App.Inputs.CorsPolicyArgs
                {
                    AllowCredentials = true,
                    AllowedHeaders = new[]
                    {
                        "HEADER1",
                        "HEADER2",
                    },
                    AllowedMethods = new[]
                    {
                        "GET",
                        "POST",
                    },
                    AllowedOrigins = new[]
                    {
                        "https://a.test.com",
                        "https://b.test.com",
                    },
                    ExposeHeaders = new[]
                    {
                        "HEADER3",
                        "HEADER4",
                    },
                    MaxAge = 1234,
                },
                CustomDomains = new[]
                {
                    new AzureNative.App.Inputs.CustomDomainArgs
                    {
                        BindingType = "SniEnabled",
                        CertificateId = "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/rg/providers/Microsoft.App/managedEnvironments/demokube/certificates/my-certificate-for-my-name-dot-com",
                        Name = "www.my-name.com",
                    },
                    new AzureNative.App.Inputs.CustomDomainArgs
                    {
                        BindingType = "SniEnabled",
                        CertificateId = "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/rg/providers/Microsoft.App/managedEnvironments/demokube/certificates/my-certificate-for-my-other-name-dot-com",
                        Name = "www.my-other-name.com",
                    },
                },
                External = true,
                IpSecurityRestrictions = new[]
                {
                    new AzureNative.App.Inputs.IpSecurityRestrictionRuleArgs
                    {
                        Action = "Allow",
                        Description = "Allowing all IP's within the subnet below to access containerapp",
                        IpAddressRange = "192.168.1.1/32",
                        Name = "Allow work IP A subnet",
                    },
                    new AzureNative.App.Inputs.IpSecurityRestrictionRuleArgs
                    {
                        Action = "Allow",
                        Description = "Allowing all IP's within the subnet below to access containerapp",
                        IpAddressRange = "192.168.1.1/8",
                        Name = "Allow work IP B subnet",
                    },
                },
                TargetPort = 3000,
                Traffic = new[]
                {
                    new AzureNative.App.Inputs.TrafficWeightArgs
                    {
                        Label = "production",
                        RevisionName = "testcontainerApp0-ab1234",
                        Weight = 100,
                    },
                },
            },
            MaxInactiveRevisions = 10,
        },
        ContainerAppName = "testcontainerApp0",
        EnvironmentId = "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/rg/providers/Microsoft.App/managedEnvironments/demokube",
        Location = "East US",
        ResourceGroupName = "rg",
        Template = new AzureNative.App.Inputs.TemplateArgs
        {
            Containers = new[]
            {
                new AzureNative.App.Inputs.ContainerArgs
                {
                    Image = "repo/testcontainerApp0:v1",
                    Name = "testcontainerApp0",
                    Probes = new[]
                    {
                        new AzureNative.App.Inputs.ContainerAppProbeArgs
                        {
                            HttpGet = new AzureNative.App.Inputs.ContainerAppProbeHttpGetArgs
                            {
                                HttpHeaders = new[]
                                {
                                    new AzureNative.App.Inputs.ContainerAppProbeHttpHeadersArgs
                                    {
                                        Name = "Custom-Header",
                                        Value = "Awesome",
                                    },
                                },
                                Path = "/health",
                                Port = 8080,
                            },
                            InitialDelaySeconds = 3,
                            PeriodSeconds = 3,
                            Type = "Liveness",
                        },
                    },
                },
            },
            InitContainers = new[]
            {
                new AzureNative.App.Inputs.InitContainerArgs
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
                    Image = "repo/testcontainerApp0:v4",
                    Name = "testinitcontainerApp0",
                    Resources = new AzureNative.App.Inputs.ContainerResourcesArgs
                    {
                        Cpu = 0.2,
                        Memory = "100Mi",
                    },
                },
            },
            Scale = new AzureNative.App.Inputs.ScaleArgs
            {
                MaxReplicas = 5,
                MinReplicas = 1,
                Rules = new[]
                {
                    new AzureNative.App.Inputs.ScaleRuleArgs
                    {
                        Custom = new AzureNative.App.Inputs.CustomScaleRuleArgs
                        {
                            Metadata = 
                            {
                                { "concurrentRequests", "50" },
                            },
                            Type = "http",
                        },
                        Name = "httpscalingrule",
                    },
                },
            },
        },
        WorkloadProfileType = "GeneralPurpose",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.app.ContainerApp;
import com.pulumi.azurenative.app.ContainerAppArgs;
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
        var containerApp = new ContainerApp("containerApp", ContainerAppArgs.builder()        
            .configuration(Map.ofEntries(
                Map.entry("dapr", Map.ofEntries(
                    Map.entry("appPort", 3000),
                    Map.entry("appProtocol", "http"),
                    Map.entry("enableApiLogging", true),
                    Map.entry("enabled", true),
                    Map.entry("httpMaxRequestSize", 10),
                    Map.entry("httpReadBufferSize", 30),
                    Map.entry("logLevel", "debug")
                )),
                Map.entry("ingress", Map.ofEntries(
                    Map.entry("clientCertificateMode", "accept"),
                    Map.entry("corsPolicy", Map.ofEntries(
                        Map.entry("allowCredentials", true),
                        Map.entry("allowedHeaders",                         
                            "HEADER1",
                            "HEADER2"),
                        Map.entry("allowedMethods",                         
                            "GET",
                            "POST"),
                        Map.entry("allowedOrigins",                         
                            "https://a.test.com",
                            "https://b.test.com"),
                        Map.entry("exposeHeaders",                         
                            "HEADER3",
                            "HEADER4"),
                        Map.entry("maxAge", 1234)
                    )),
                    Map.entry("customDomains",                     
                        Map.ofEntries(
                            Map.entry("bindingType", "SniEnabled"),
                            Map.entry("certificateId", "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/rg/providers/Microsoft.App/managedEnvironments/demokube/certificates/my-certificate-for-my-name-dot-com"),
                            Map.entry("name", "www.my-name.com")
                        ),
                        Map.ofEntries(
                            Map.entry("bindingType", "SniEnabled"),
                            Map.entry("certificateId", "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/rg/providers/Microsoft.App/managedEnvironments/demokube/certificates/my-certificate-for-my-other-name-dot-com"),
                            Map.entry("name", "www.my-other-name.com")
                        )),
                    Map.entry("external", true),
                    Map.entry("ipSecurityRestrictions",                     
                        Map.ofEntries(
                            Map.entry("action", "Allow"),
                            Map.entry("description", "Allowing all IP's within the subnet below to access containerapp"),
                            Map.entry("ipAddressRange", "192.168.1.1/32"),
                            Map.entry("name", "Allow work IP A subnet")
                        ),
                        Map.ofEntries(
                            Map.entry("action", "Allow"),
                            Map.entry("description", "Allowing all IP's within the subnet below to access containerapp"),
                            Map.entry("ipAddressRange", "192.168.1.1/8"),
                            Map.entry("name", "Allow work IP B subnet")
                        )),
                    Map.entry("targetPort", 3000),
                    Map.entry("traffic", Map.ofEntries(
                        Map.entry("label", "production"),
                        Map.entry("revisionName", "testcontainerApp0-ab1234"),
                        Map.entry("weight", 100)
                    ))
                )),
                Map.entry("maxInactiveRevisions", 10)
            ))
            .containerAppName("testcontainerApp0")
            .environmentId("/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/rg/providers/Microsoft.App/managedEnvironments/demokube")
            .location("East US")
            .resourceGroupName("rg")
            .template(Map.ofEntries(
                Map.entry("containers", Map.ofEntries(
                    Map.entry("image", "repo/testcontainerApp0:v1"),
                    Map.entry("name", "testcontainerApp0"),
                    Map.entry("probes", Map.ofEntries(
                        Map.entry("httpGet", Map.ofEntries(
                            Map.entry("httpHeaders", Map.ofEntries(
                                Map.entry("name", "Custom-Header"),
                                Map.entry("value", "Awesome")
                            )),
                            Map.entry("path", "/health"),
                            Map.entry("port", 8080)
                        )),
                        Map.entry("initialDelaySeconds", 3),
                        Map.entry("periodSeconds", 3),
                        Map.entry("type", "Liveness")
                    ))
                )),
                Map.entry("initContainers", Map.ofEntries(
                    Map.entry("args",                     
                        "-c",
                        "while true; do echo hello; sleep 10;done"),
                    Map.entry("command", "/bin/sh"),
                    Map.entry("image", "repo/testcontainerApp0:v4"),
                    Map.entry("name", "testinitcontainerApp0"),
                    Map.entry("resources", Map.ofEntries(
                        Map.entry("cpu", 0.2),
                        Map.entry("memory", "100Mi")
                    ))
                )),
                Map.entry("scale", Map.ofEntries(
                    Map.entry("maxReplicas", 5),
                    Map.entry("minReplicas", 1),
                    Map.entry("rules", Map.ofEntries(
                        Map.entry("custom", Map.ofEntries(
                            Map.entry("metadata", Map.of("concurrentRequests", "50")),
                            Map.entry("type", "http")
                        )),
                        Map.entry("name", "httpscalingrule")
                    ))
                ))
            ))
            .workloadProfileType("GeneralPurpose")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const containerApp = new azure_native.app.ContainerApp("containerApp", {
    configuration: {
        dapr: {
            appPort: 3000,
            appProtocol: "http",
            enableApiLogging: true,
            enabled: true,
            httpMaxRequestSize: 10,
            httpReadBufferSize: 30,
            logLevel: "debug",
        },
        ingress: {
            clientCertificateMode: "accept",
            corsPolicy: {
                allowCredentials: true,
                allowedHeaders: [
                    "HEADER1",
                    "HEADER2",
                ],
                allowedMethods: [
                    "GET",
                    "POST",
                ],
                allowedOrigins: [
                    "https://a.test.com",
                    "https://b.test.com",
                ],
                exposeHeaders: [
                    "HEADER3",
                    "HEADER4",
                ],
                maxAge: 1234,
            },
            customDomains: [
                {
                    bindingType: "SniEnabled",
                    certificateId: "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/rg/providers/Microsoft.App/managedEnvironments/demokube/certificates/my-certificate-for-my-name-dot-com",
                    name: "www.my-name.com",
                },
                {
                    bindingType: "SniEnabled",
                    certificateId: "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/rg/providers/Microsoft.App/managedEnvironments/demokube/certificates/my-certificate-for-my-other-name-dot-com",
                    name: "www.my-other-name.com",
                },
            ],
            external: true,
            ipSecurityRestrictions: [
                {
                    action: "Allow",
                    description: "Allowing all IP's within the subnet below to access containerapp",
                    ipAddressRange: "192.168.1.1/32",
                    name: "Allow work IP A subnet",
                },
                {
                    action: "Allow",
                    description: "Allowing all IP's within the subnet below to access containerapp",
                    ipAddressRange: "192.168.1.1/8",
                    name: "Allow work IP B subnet",
                },
            ],
            targetPort: 3000,
            traffic: [{
                label: "production",
                revisionName: "testcontainerApp0-ab1234",
                weight: 100,
            }],
        },
        maxInactiveRevisions: 10,
    },
    containerAppName: "testcontainerApp0",
    environmentId: "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/rg/providers/Microsoft.App/managedEnvironments/demokube",
    location: "East US",
    resourceGroupName: "rg",
    template: {
        containers: [{
            image: "repo/testcontainerApp0:v1",
            name: "testcontainerApp0",
            probes: [{
                httpGet: {
                    httpHeaders: [{
                        name: "Custom-Header",
                        value: "Awesome",
                    }],
                    path: "/health",
                    port: 8080,
                },
                initialDelaySeconds: 3,
                periodSeconds: 3,
                type: "Liveness",
            }],
        }],
        initContainers: [{
            args: [
                "-c",
                "while true; do echo hello; sleep 10;done",
            ],
            command: ["/bin/sh"],
            image: "repo/testcontainerApp0:v4",
            name: "testinitcontainerApp0",
            resources: {
                cpu: 0.2,
                memory: "100Mi",
            },
        }],
        scale: {
            maxReplicas: 5,
            minReplicas: 1,
            rules: [{
                custom: {
                    metadata: {
                        concurrentRequests: "50",
                    },
                    type: "http",
                },
                name: "httpscalingrule",
            }],
        },
    },
    workloadProfileType: "GeneralPurpose",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

container_app = azure_native.app.ContainerApp("containerApp",
    configuration=azure_native.app.ConfigurationResponseArgs(
        dapr=azure_native.app.DaprArgs(
            app_port=3000,
            app_protocol="http",
            enable_api_logging=True,
            enabled=True,
            http_max_request_size=10,
            http_read_buffer_size=30,
            log_level="debug",
        ),
        ingress={
            "clientCertificateMode": "accept",
            "corsPolicy": azure_native.app.CorsPolicyArgs(
                allow_credentials=True,
                allowed_headers=[
                    "HEADER1",
                    "HEADER2",
                ],
                allowed_methods=[
                    "GET",
                    "POST",
                ],
                allowed_origins=[
                    "https://a.test.com",
                    "https://b.test.com",
                ],
                expose_headers=[
                    "HEADER3",
                    "HEADER4",
                ],
                max_age=1234,
            ),
            "customDomains": [
                azure_native.app.CustomDomainArgs(
                    binding_type="SniEnabled",
                    certificate_id="/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/rg/providers/Microsoft.App/managedEnvironments/demokube/certificates/my-certificate-for-my-name-dot-com",
                    name="www.my-name.com",
                ),
                azure_native.app.CustomDomainArgs(
                    binding_type="SniEnabled",
                    certificate_id="/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/rg/providers/Microsoft.App/managedEnvironments/demokube/certificates/my-certificate-for-my-other-name-dot-com",
                    name="www.my-other-name.com",
                ),
            ],
            "external": True,
            "ipSecurityRestrictions": [
                azure_native.app.IpSecurityRestrictionRuleArgs(
                    action="Allow",
                    description="Allowing all IP's within the subnet below to access containerapp",
                    ip_address_range="192.168.1.1/32",
                    name="Allow work IP A subnet",
                ),
                azure_native.app.IpSecurityRestrictionRuleArgs(
                    action="Allow",
                    description="Allowing all IP's within the subnet below to access containerapp",
                    ip_address_range="192.168.1.1/8",
                    name="Allow work IP B subnet",
                ),
            ],
            "targetPort": 3000,
            "traffic": [azure_native.app.TrafficWeightArgs(
                label="production",
                revision_name="testcontainerApp0-ab1234",
                weight=100,
            )],
        },
        max_inactive_revisions=10,
    ),
    container_app_name="testcontainerApp0",
    environment_id="/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/rg/providers/Microsoft.App/managedEnvironments/demokube",
    location="East US",
    resource_group_name="rg",
    template=azure_native.app.TemplateResponseArgs(
        containers=[{
            "image": "repo/testcontainerApp0:v1",
            "name": "testcontainerApp0",
            "probes": [{
                "httpGet": {
                    "httpHeaders": [azure_native.app.ContainerAppProbeHttpHeadersArgs(
                        name="Custom-Header",
                        value="Awesome",
                    )],
                    "path": "/health",
                    "port": 8080,
                },
                "initialDelaySeconds": 3,
                "periodSeconds": 3,
                "type": "Liveness",
            }],
        }],
        init_containers=[{
            "args": [
                "-c",
                "while true; do echo hello; sleep 10;done",
            ],
            "command": ["/bin/sh"],
            "image": "repo/testcontainerApp0:v4",
            "name": "testinitcontainerApp0",
            "resources": azure_native.app.ContainerResourcesArgs(
                cpu=0.2,
                memory="100Mi",
            ),
        }],
        scale={
            "maxReplicas": 5,
            "minReplicas": 1,
            "rules": [{
                "custom": azure_native.app.CustomScaleRuleArgs(
                    metadata={
                        "concurrentRequests": "50",
                    },
                    type="http",
                ),
                "name": "httpscalingrule",
            }],
        },
    ),
    workload_profile_type="GeneralPurpose")

```

```yaml
resources:
  containerApp:
    type: azure-native:app:ContainerApp
    properties:
      configuration:
        dapr:
          appPort: 3000
          appProtocol: http
          enableApiLogging: true
          enabled: true
          httpMaxRequestSize: 10
          httpReadBufferSize: 30
          logLevel: debug
        ingress:
          clientCertificateMode: accept
          corsPolicy:
            allowCredentials: true
            allowedHeaders:
              - HEADER1
              - HEADER2
            allowedMethods:
              - GET
              - POST
            allowedOrigins:
              - https://a.test.com
              - https://b.test.com
            exposeHeaders:
              - HEADER3
              - HEADER4
            maxAge: 1234
          customDomains:
            - bindingType: SniEnabled
              certificateId: /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/rg/providers/Microsoft.App/managedEnvironments/demokube/certificates/my-certificate-for-my-name-dot-com
              name: www.my-name.com
            - bindingType: SniEnabled
              certificateId: /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/rg/providers/Microsoft.App/managedEnvironments/demokube/certificates/my-certificate-for-my-other-name-dot-com
              name: www.my-other-name.com
          external: true
          ipSecurityRestrictions:
            - action: Allow
              description: Allowing all IP's within the subnet below to access containerapp
              ipAddressRange: 192.168.1.1/32
              name: Allow work IP A subnet
            - action: Allow
              description: Allowing all IP's within the subnet below to access containerapp
              ipAddressRange: 192.168.1.1/8
              name: Allow work IP B subnet
          targetPort: 3000
          traffic:
            - label: production
              revisionName: testcontainerApp0-ab1234
              weight: 100
        maxInactiveRevisions: 10
      containerAppName: testcontainerApp0
      environmentId: /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/rg/providers/Microsoft.App/managedEnvironments/demokube
      location: East US
      resourceGroupName: rg
      template:
        containers:
          - image: repo/testcontainerApp0:v1
            name: testcontainerApp0
            probes:
              - httpGet:
                  httpHeaders:
                    - name: Custom-Header
                      value: Awesome
                  path: /health
                  port: 8080
                initialDelaySeconds: 3
                periodSeconds: 3
                type: Liveness
        initContainers:
          - args:
              - -c
              - while true; do echo hello; sleep 10;done
            command:
              - /bin/sh
            image: repo/testcontainerApp0:v4
            name: testinitcontainerApp0
            resources:
              cpu: 0.2
              memory: 100Mi
        scale:
          maxReplicas: 5
          minReplicas: 1
          rules:
            - custom:
                metadata:
                  concurrentRequests: '50'
                type: http
              name: httpscalingrule
      workloadProfileType: GeneralPurpose

```

{{% /example %}}
{{% example %}}
### Create or Update Tcp App
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var containerApp = new AzureNative.App.ContainerApp("containerApp", new()
    {
        Configuration = new AzureNative.App.Inputs.ConfigurationArgs
        {
            Ingress = new AzureNative.App.Inputs.IngressArgs
            {
                ExposedPort = 4000,
                External = true,
                TargetPort = 3000,
                Traffic = new[]
                {
                    new AzureNative.App.Inputs.TrafficWeightArgs
                    {
                        RevisionName = "testcontainerAppTcp-ab1234",
                        Weight = 100,
                    },
                },
                Transport = "tcp",
            },
        },
        ContainerAppName = "testcontainerAppTcp",
        EnvironmentId = "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/rg/providers/Microsoft.App/managedEnvironments/demokube",
        Location = "East US",
        ResourceGroupName = "rg",
        Template = new AzureNative.App.Inputs.TemplateArgs
        {
            Containers = new[]
            {
                new AzureNative.App.Inputs.ContainerArgs
                {
                    Image = "repo/testcontainerAppTcp:v1",
                    Name = "testcontainerAppTcp",
                    Probes = new[]
                    {
                        new AzureNative.App.Inputs.ContainerAppProbeArgs
                        {
                            InitialDelaySeconds = 3,
                            PeriodSeconds = 3,
                            TcpSocket = new AzureNative.App.Inputs.ContainerAppProbeTcpSocketArgs
                            {
                                Port = 8080,
                            },
                            Type = "Liveness",
                        },
                    },
                },
            },
            Scale = new AzureNative.App.Inputs.ScaleArgs
            {
                MaxReplicas = 5,
                MinReplicas = 1,
                Rules = new[]
                {
                    new AzureNative.App.Inputs.ScaleRuleArgs
                    {
                        Name = "tcpscalingrule",
                        Tcp = new AzureNative.App.Inputs.TcpScaleRuleArgs
                        {
                            Metadata = 
                            {
                                { "concurrentConnections", "50" },
                            },
                        },
                    },
                },
            },
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.app.ContainerApp;
import com.pulumi.azurenative.app.ContainerAppArgs;
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
        var containerApp = new ContainerApp("containerApp", ContainerAppArgs.builder()        
            .configuration(Map.of("ingress", Map.ofEntries(
                Map.entry("exposedPort", 4000),
                Map.entry("external", true),
                Map.entry("targetPort", 3000),
                Map.entry("traffic", Map.ofEntries(
                    Map.entry("revisionName", "testcontainerAppTcp-ab1234"),
                    Map.entry("weight", 100)
                )),
                Map.entry("transport", "tcp")
            )))
            .containerAppName("testcontainerAppTcp")
            .environmentId("/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/rg/providers/Microsoft.App/managedEnvironments/demokube")
            .location("East US")
            .resourceGroupName("rg")
            .template(Map.ofEntries(
                Map.entry("containers", Map.ofEntries(
                    Map.entry("image", "repo/testcontainerAppTcp:v1"),
                    Map.entry("name", "testcontainerAppTcp"),
                    Map.entry("probes", Map.ofEntries(
                        Map.entry("initialDelaySeconds", 3),
                        Map.entry("periodSeconds", 3),
                        Map.entry("tcpSocket", Map.of("port", 8080)),
                        Map.entry("type", "Liveness")
                    ))
                )),
                Map.entry("scale", Map.ofEntries(
                    Map.entry("maxReplicas", 5),
                    Map.entry("minReplicas", 1),
                    Map.entry("rules", Map.ofEntries(
                        Map.entry("name", "tcpscalingrule"),
                        Map.entry("tcp", Map.of("metadata", Map.of("concurrentConnections", "50")))
                    ))
                ))
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const containerApp = new azure_native.app.ContainerApp("containerApp", {
    configuration: {
        ingress: {
            exposedPort: 4000,
            external: true,
            targetPort: 3000,
            traffic: [{
                revisionName: "testcontainerAppTcp-ab1234",
                weight: 100,
            }],
            transport: "tcp",
        },
    },
    containerAppName: "testcontainerAppTcp",
    environmentId: "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/rg/providers/Microsoft.App/managedEnvironments/demokube",
    location: "East US",
    resourceGroupName: "rg",
    template: {
        containers: [{
            image: "repo/testcontainerAppTcp:v1",
            name: "testcontainerAppTcp",
            probes: [{
                initialDelaySeconds: 3,
                periodSeconds: 3,
                tcpSocket: {
                    port: 8080,
                },
                type: "Liveness",
            }],
        }],
        scale: {
            maxReplicas: 5,
            minReplicas: 1,
            rules: [{
                name: "tcpscalingrule",
                tcp: {
                    metadata: {
                        concurrentConnections: "50",
                    },
                },
            }],
        },
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

container_app = azure_native.app.ContainerApp("containerApp",
    configuration=azure_native.app.ConfigurationResponseArgs(
        ingress={
            "exposedPort": 4000,
            "external": True,
            "targetPort": 3000,
            "traffic": [azure_native.app.TrafficWeightArgs(
                revision_name="testcontainerAppTcp-ab1234",
                weight=100,
            )],
            "transport": "tcp",
        },
    ),
    container_app_name="testcontainerAppTcp",
    environment_id="/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/rg/providers/Microsoft.App/managedEnvironments/demokube",
    location="East US",
    resource_group_name="rg",
    template=azure_native.app.TemplateResponseArgs(
        containers=[{
            "image": "repo/testcontainerAppTcp:v1",
            "name": "testcontainerAppTcp",
            "probes": [{
                "initialDelaySeconds": 3,
                "periodSeconds": 3,
                "tcpSocket": azure_native.app.ContainerAppProbeTcpSocketArgs(
                    port=8080,
                ),
                "type": "Liveness",
            }],
        }],
        scale={
            "maxReplicas": 5,
            "minReplicas": 1,
            "rules": [{
                "name": "tcpscalingrule",
                "tcp": azure_native.app.TcpScaleRuleArgs(
                    metadata={
                        "concurrentConnections": "50",
                    },
                ),
            }],
        },
    ))

```

```yaml
resources:
  containerApp:
    type: azure-native:app:ContainerApp
    properties:
      configuration:
        ingress:
          exposedPort: 4000
          external: true
          targetPort: 3000
          traffic:
            - revisionName: testcontainerAppTcp-ab1234
              weight: 100
          transport: tcp
      containerAppName: testcontainerAppTcp
      environmentId: /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/rg/providers/Microsoft.App/managedEnvironments/demokube
      location: East US
      resourceGroupName: rg
      template:
        containers:
          - image: repo/testcontainerAppTcp:v1
            name: testcontainerAppTcp
            probes:
              - initialDelaySeconds: 3
                periodSeconds: 3
                tcpSocket:
                  port: 8080
                type: Liveness
        scale:
          maxReplicas: 5
          minReplicas: 1
          rules:
            - name: tcpscalingrule
              tcp:
                metadata:
                  concurrentConnections: '50'

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:app:ContainerApp testcontainerAppTcp /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/rg/providers/Microsoft.App/containerApps/testcontainerAppTcp 
```
