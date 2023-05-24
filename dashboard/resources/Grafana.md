The grafana resource type.
API Version: 2022-08-01.
Previous API Version: 2022-05-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Grafana_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var grafana = new AzureNative.Dashboard.Grafana("grafana", new()
    {
        Identity = new AzureNative.Dashboard.Inputs.ManagedServiceIdentityArgs
        {
            Type = "SystemAssigned",
        },
        Location = "West US",
        Properties = new AzureNative.Dashboard.Inputs.ManagedGrafanaPropertiesArgs
        {
            ApiKey = "Enabled",
            DeterministicOutboundIP = "Enabled",
            GrafanaIntegrations = new AzureNative.Dashboard.Inputs.GrafanaIntegrationsArgs
            {
                AzureMonitorWorkspaceIntegrations = new[]
                {
                    new AzureNative.Dashboard.Inputs.AzureMonitorWorkspaceIntegrationArgs
                    {
                        AzureMonitorWorkspaceResourceId = "/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/microsoft.monitor/accounts/myAzureMonitorWorkspace",
                    },
                },
            },
            PublicNetworkAccess = "Enabled",
            ZoneRedundancy = "Enabled",
        },
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.Dashboard.Inputs.ResourceSkuArgs
        {
            Name = "Standard",
        },
        Tags = 
        {
            { "Environment", "Dev" },
        },
        WorkspaceName = "myWorkspace",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.dashboard.Grafana;
import com.pulumi.azurenative.dashboard.GrafanaArgs;
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
        var grafana = new Grafana("grafana", GrafanaArgs.builder()        
            .identity(Map.of("type", "SystemAssigned"))
            .location("West US")
            .properties(Map.ofEntries(
                Map.entry("apiKey", "Enabled"),
                Map.entry("deterministicOutboundIP", "Enabled"),
                Map.entry("grafanaIntegrations", Map.of("azureMonitorWorkspaceIntegrations", Map.of("azureMonitorWorkspaceResourceId", "/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/microsoft.monitor/accounts/myAzureMonitorWorkspace"))),
                Map.entry("publicNetworkAccess", "Enabled"),
                Map.entry("zoneRedundancy", "Enabled")
            ))
            .resourceGroupName("myResourceGroup")
            .sku(Map.of("name", "Standard"))
            .tags(Map.of("Environment", "Dev"))
            .workspaceName("myWorkspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const grafana = new azure_native.dashboard.Grafana("grafana", {
    identity: {
        type: "SystemAssigned",
    },
    location: "West US",
    properties: {
        apiKey: "Enabled",
        deterministicOutboundIP: "Enabled",
        grafanaIntegrations: {
            azureMonitorWorkspaceIntegrations: [{
                azureMonitorWorkspaceResourceId: "/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/microsoft.monitor/accounts/myAzureMonitorWorkspace",
            }],
        },
        publicNetworkAccess: "Enabled",
        zoneRedundancy: "Enabled",
    },
    resourceGroupName: "myResourceGroup",
    sku: {
        name: "Standard",
    },
    tags: {
        Environment: "Dev",
    },
    workspaceName: "myWorkspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

grafana = azure_native.dashboard.Grafana("grafana",
    identity=azure_native.dashboard.ManagedServiceIdentityArgs(
        type="SystemAssigned",
    ),
    location="West US",
    properties=azure_native.dashboard.ManagedGrafanaPropertiesResponseArgs(
        api_key="Enabled",
        deterministic_outbound_ip="Enabled",
        grafana_integrations={
            "azureMonitorWorkspaceIntegrations": [azure_native.dashboard.AzureMonitorWorkspaceIntegrationArgs(
                azure_monitor_workspace_resource_id="/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/microsoft.monitor/accounts/myAzureMonitorWorkspace",
            )],
        },
        public_network_access="Enabled",
        zone_redundancy="Enabled",
    ),
    resource_group_name="myResourceGroup",
    sku=azure_native.dashboard.ResourceSkuArgs(
        name="Standard",
    ),
    tags={
        "Environment": "Dev",
    },
    workspace_name="myWorkspace")

```

```yaml
resources:
  grafana:
    type: azure-native:dashboard:Grafana
    properties:
      identity:
        type: SystemAssigned
      location: West US
      properties:
        apiKey: Enabled
        deterministicOutboundIP: Enabled
        grafanaIntegrations:
          azureMonitorWorkspaceIntegrations:
            - azureMonitorWorkspaceResourceId: /subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/microsoft.monitor/accounts/myAzureMonitorWorkspace
        publicNetworkAccess: Enabled
        zoneRedundancy: Enabled
      resourceGroupName: myResourceGroup
      sku:
        name: Standard
      tags:
        Environment: Dev
      workspaceName: myWorkspace

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:dashboard:Grafana myWorkspace /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/grafana/myWorkspace 
```
