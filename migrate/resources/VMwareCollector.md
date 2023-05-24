
API Version: 2019-10-01.
Previous API Version: 2019-10-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### VMwareCollectors_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var vMwareCollector = new AzureNative.Migrate.VMwareCollector("vMwareCollector", new()
    {
        ETag = "\"01003d32-0000-0d00-0000-5d74d2e50000\"",
        ProjectName = "abgoyalWEselfhostb72bproject",
        Properties = new AzureNative.Migrate.Inputs.CollectorPropertiesArgs
        {
            AgentProperties = new AzureNative.Migrate.Inputs.CollectorAgentPropertiesArgs
            {
                SpnDetails = new AzureNative.Migrate.Inputs.CollectorBodyAgentSpnPropertiesArgs
                {
                    ApplicationId = "fc717575-8173-4b21-92a5-658b655e613e",
                    Audience = "https://72f988bf-86f1-41af-91ab-2d7cd011db47/PortalvCenterbc2fagentauthaadapp",
                    Authority = "https://login.windows.net/72f988bf-86f1-41af-91ab-2d7cd011db47",
                    ObjectId = "29d94f38-db94-4980-aec0-0cfd55ab1cd0",
                    TenantId = "72f988bf-86f1-41af-91ab-2d7cd011db47",
                },
            },
            DiscoverySiteId = "/subscriptions/6393a73f-8d55-47ef-b6dd-179b3e0c7910/resourceGroups/abgoyal-westEurope/providers/Microsoft.OffAzure/VMwareSites/PortalvCenterbc2fsite",
        },
        ResourceGroupName = "abgoyal-westEurope",
        VmWareCollectorName = "PortalvCenterbc2fcollector",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.migrate.VMwareCollector;
import com.pulumi.azurenative.migrate.VMwareCollectorArgs;
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
        var vMwareCollector = new VMwareCollector("vMwareCollector", VMwareCollectorArgs.builder()        
            .eTag("\"01003d32-0000-0d00-0000-5d74d2e50000\"")
            .projectName("abgoyalWEselfhostb72bproject")
            .properties(Map.ofEntries(
                Map.entry("agentProperties", Map.of("spnDetails", Map.ofEntries(
                    Map.entry("applicationId", "fc717575-8173-4b21-92a5-658b655e613e"),
                    Map.entry("audience", "https://72f988bf-86f1-41af-91ab-2d7cd011db47/PortalvCenterbc2fagentauthaadapp"),
                    Map.entry("authority", "https://login.windows.net/72f988bf-86f1-41af-91ab-2d7cd011db47"),
                    Map.entry("objectId", "29d94f38-db94-4980-aec0-0cfd55ab1cd0"),
                    Map.entry("tenantId", "72f988bf-86f1-41af-91ab-2d7cd011db47")
                ))),
                Map.entry("discoverySiteId", "/subscriptions/6393a73f-8d55-47ef-b6dd-179b3e0c7910/resourceGroups/abgoyal-westEurope/providers/Microsoft.OffAzure/VMwareSites/PortalvCenterbc2fsite")
            ))
            .resourceGroupName("abgoyal-westEurope")
            .vmWareCollectorName("PortalvCenterbc2fcollector")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const vMwareCollector = new azure_native.migrate.VMwareCollector("vMwareCollector", {
    eTag: "\"01003d32-0000-0d00-0000-5d74d2e50000\"",
    projectName: "abgoyalWEselfhostb72bproject",
    properties: {
        agentProperties: {
            spnDetails: {
                applicationId: "fc717575-8173-4b21-92a5-658b655e613e",
                audience: "https://72f988bf-86f1-41af-91ab-2d7cd011db47/PortalvCenterbc2fagentauthaadapp",
                authority: "https://login.windows.net/72f988bf-86f1-41af-91ab-2d7cd011db47",
                objectId: "29d94f38-db94-4980-aec0-0cfd55ab1cd0",
                tenantId: "72f988bf-86f1-41af-91ab-2d7cd011db47",
            },
        },
        discoverySiteId: "/subscriptions/6393a73f-8d55-47ef-b6dd-179b3e0c7910/resourceGroups/abgoyal-westEurope/providers/Microsoft.OffAzure/VMwareSites/PortalvCenterbc2fsite",
    },
    resourceGroupName: "abgoyal-westEurope",
    vmWareCollectorName: "PortalvCenterbc2fcollector",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

v_mware_collector = azure_native.migrate.VMwareCollector("vMwareCollector",
    e_tag="\"01003d32-0000-0d00-0000-5d74d2e50000\"",
    project_name="abgoyalWEselfhostb72bproject",
    properties=azure_native.migrate.CollectorPropertiesResponseArgs(
        agent_properties={
            "spnDetails": azure_native.migrate.CollectorBodyAgentSpnPropertiesArgs(
                application_id="fc717575-8173-4b21-92a5-658b655e613e",
                audience="https://72f988bf-86f1-41af-91ab-2d7cd011db47/PortalvCenterbc2fagentauthaadapp",
                authority="https://login.windows.net/72f988bf-86f1-41af-91ab-2d7cd011db47",
                object_id="29d94f38-db94-4980-aec0-0cfd55ab1cd0",
                tenant_id="72f988bf-86f1-41af-91ab-2d7cd011db47",
            ),
        },
        discovery_site_id="/subscriptions/6393a73f-8d55-47ef-b6dd-179b3e0c7910/resourceGroups/abgoyal-westEurope/providers/Microsoft.OffAzure/VMwareSites/PortalvCenterbc2fsite",
    ),
    resource_group_name="abgoyal-westEurope",
    vm_ware_collector_name="PortalvCenterbc2fcollector")

```

```yaml
resources:
  vMwareCollector:
    type: azure-native:migrate:VMwareCollector
    properties:
      eTag: '"01003d32-0000-0d00-0000-5d74d2e50000"'
      projectName: abgoyalWEselfhostb72bproject
      properties:
        agentProperties:
          spnDetails:
            applicationId: fc717575-8173-4b21-92a5-658b655e613e
            audience: https://72f988bf-86f1-41af-91ab-2d7cd011db47/PortalvCenterbc2fagentauthaadapp
            authority: https://login.windows.net/72f988bf-86f1-41af-91ab-2d7cd011db47
            objectId: 29d94f38-db94-4980-aec0-0cfd55ab1cd0
            tenantId: 72f988bf-86f1-41af-91ab-2d7cd011db47
        discoverySiteId: /subscriptions/6393a73f-8d55-47ef-b6dd-179b3e0c7910/resourceGroups/abgoyal-westEurope/providers/Microsoft.OffAzure/VMwareSites/PortalvCenterbc2fsite
      resourceGroupName: abgoyal-westEurope
      vmWareCollectorName: PortalvCenterbc2fcollector

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:migrate:VMwareCollector PortalvCenterbc2fcollector /subscriptions/6393a73f-8d55-47ef-b6dd-179b3e0c7910/resourceGroups/abgoyal-westeurope/providers/Microsoft.Migrate/assessmentprojects/abgoyalWEselfhostb72bproject/vmwarecollectors/PortalvCenterbc2fcollector 
```
