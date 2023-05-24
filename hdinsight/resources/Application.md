The HDInsight cluster application
API Version: 2021-06-01.
Previous API Version: 2018-06-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create Application
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var application = new AzureNative.HDInsight.Application("application", new()
    {
        ApplicationName = "hue",
        ClusterName = "cluster1",
        Properties = new AzureNative.HDInsight.Inputs.ApplicationPropertiesArgs
        {
            ApplicationType = "CustomApplication",
            ComputeProfile = new AzureNative.HDInsight.Inputs.ComputeProfileArgs
            {
                Roles = new[]
                {
                    new AzureNative.HDInsight.Inputs.RoleArgs
                    {
                        HardwareProfile = new AzureNative.HDInsight.Inputs.HardwareProfileArgs
                        {
                            VmSize = "Standard_D12_v2",
                        },
                        Name = "edgenode",
                        TargetInstanceCount = 1,
                    },
                },
            },
            Errors = new[] {},
            HttpsEndpoints = new[]
            {
                new AzureNative.HDInsight.Inputs.ApplicationGetHttpsEndpointArgs
                {
                    AccessModes = new[]
                    {
                        "WebPage",
                    },
                    DestinationPort = 20000,
                    SubDomainSuffix = "dss",
                },
            },
            InstallScriptActions = new[]
            {
                new AzureNative.HDInsight.Inputs.RuntimeScriptActionArgs
                {
                    Name = "app-install-app1",
                    Parameters = "-version latest -port 20000",
                    Roles = new[]
                    {
                        "edgenode",
                    },
                    Uri = "https://.../install.sh",
                },
            },
            UninstallScriptActions = new[] {},
        },
        ResourceGroupName = "rg1",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.hdinsight.Application;
import com.pulumi.azurenative.hdinsight.ApplicationArgs;
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
        var application = new Application("application", ApplicationArgs.builder()        
            .applicationName("hue")
            .clusterName("cluster1")
            .properties(Map.ofEntries(
                Map.entry("applicationType", "CustomApplication"),
                Map.entry("computeProfile", Map.of("roles", Map.ofEntries(
                    Map.entry("hardwareProfile", Map.of("vmSize", "Standard_D12_v2")),
                    Map.entry("name", "edgenode"),
                    Map.entry("targetInstanceCount", 1)
                ))),
                Map.entry("errors", ),
                Map.entry("httpsEndpoints", Map.ofEntries(
                    Map.entry("accessModes", "WebPage"),
                    Map.entry("destinationPort", 20000),
                    Map.entry("subDomainSuffix", "dss")
                )),
                Map.entry("installScriptActions", Map.ofEntries(
                    Map.entry("name", "app-install-app1"),
                    Map.entry("parameters", "-version latest -port 20000"),
                    Map.entry("roles", "edgenode"),
                    Map.entry("uri", "https://.../install.sh")
                )),
                Map.entry("uninstallScriptActions", )
            ))
            .resourceGroupName("rg1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const application = new azure_native.hdinsight.Application("application", {
    applicationName: "hue",
    clusterName: "cluster1",
    properties: {
        applicationType: "CustomApplication",
        computeProfile: {
            roles: [{
                hardwareProfile: {
                    vmSize: "Standard_D12_v2",
                },
                name: "edgenode",
                targetInstanceCount: 1,
            }],
        },
        errors: [],
        httpsEndpoints: [{
            accessModes: ["WebPage"],
            destinationPort: 20000,
            subDomainSuffix: "dss",
        }],
        installScriptActions: [{
            name: "app-install-app1",
            parameters: "-version latest -port 20000",
            roles: ["edgenode"],
            uri: "https://.../install.sh",
        }],
        uninstallScriptActions: [],
    },
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

application = azure_native.hdinsight.Application("application",
    application_name="hue",
    cluster_name="cluster1",
    properties=azure_native.hdinsight.ApplicationPropertiesResponseArgs(
        application_type="CustomApplication",
        compute_profile={
            "roles": [{
                "hardwareProfile": azure_native.hdinsight.HardwareProfileArgs(
                    vm_size="Standard_D12_v2",
                ),
                "name": "edgenode",
                "targetInstanceCount": 1,
            }],
        },
        errors=[],
        https_endpoints=[azure_native.hdinsight.ApplicationGetHttpsEndpointArgs(
            access_modes=["WebPage"],
            destination_port=20000,
            sub_domain_suffix="dss",
        )],
        install_script_actions=[azure_native.hdinsight.RuntimeScriptActionArgs(
            name="app-install-app1",
            parameters="-version latest -port 20000",
            roles=["edgenode"],
            uri="https://.../install.sh",
        )],
        uninstall_script_actions=[],
    ),
    resource_group_name="rg1")

```

```yaml
resources:
  application:
    type: azure-native:hdinsight:Application
    properties:
      applicationName: hue
      clusterName: cluster1
      properties:
        applicationType: CustomApplication
        computeProfile:
          roles:
            - hardwareProfile:
                vmSize: Standard_D12_v2
              name: edgenode
              targetInstanceCount: 1
        errors: []
        httpsEndpoints:
          - accessModes:
              - WebPage
            destinationPort: 20000
            subDomainSuffix: dss
        installScriptActions:
          - name: app-install-app1
            parameters: -version latest -port 20000
            roles:
              - edgenode
            uri: https://.../install.sh
        uninstallScriptActions: []
      resourceGroupName: rg1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:hdinsight:Application hue /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.HDInsight/clusters/cluster1/applications/hue 
```
