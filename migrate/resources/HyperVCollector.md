
API Version: 2019-10-01.
Previous API Version: 2019-10-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### HyperVCollectors_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var hyperVCollector = new AzureNative.Migrate.HyperVCollector("hyperVCollector", new()
    {
        ETag = "\"00000981-0000-0300-0000-5d74cd5f0000\"",
        HyperVCollectorName = "migrateprojectce73collector",
        ProjectName = "migrateprojectce73project",
        Properties = new AzureNative.Migrate.Inputs.CollectorPropertiesArgs
        {
            AgentProperties = new AzureNative.Migrate.Inputs.CollectorAgentPropertiesArgs
            {
                SpnDetails = new AzureNative.Migrate.Inputs.CollectorBodyAgentSpnPropertiesArgs
                {
                    ApplicationId = "827f1053-44dc-439f-b832-05416dcce12b",
                    Audience = "https://72f988bf-86f1-41af-91ab-2d7cd011db47/migrateprojectce73agentauthaadapp",
                    Authority = "https://login.windows.net/72f988bf-86f1-41af-91ab-2d7cd011db47",
                    ObjectId = "be75098e-c0fc-4ac4-98c7-282ebbcf8370",
                    TenantId = "72f988bf-86f1-41af-91ab-2d7cd011db47",
                },
            },
            DiscoverySiteId = "/subscriptions/8c3c936a-c09b-4de3-830b-3f5f244d72e9/resourceGroups/ContosoITHyperV/providers/Microsoft.OffAzure/HyperVSites/migrateprojectce73site",
        },
        ResourceGroupName = "contosoithyperv",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.migrate.HyperVCollector;
import com.pulumi.azurenative.migrate.HyperVCollectorArgs;
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
        var hyperVCollector = new HyperVCollector("hyperVCollector", HyperVCollectorArgs.builder()        
            .eTag("\"00000981-0000-0300-0000-5d74cd5f0000\"")
            .hyperVCollectorName("migrateprojectce73collector")
            .projectName("migrateprojectce73project")
            .properties(Map.ofEntries(
                Map.entry("agentProperties", Map.of("spnDetails", Map.ofEntries(
                    Map.entry("applicationId", "827f1053-44dc-439f-b832-05416dcce12b"),
                    Map.entry("audience", "https://72f988bf-86f1-41af-91ab-2d7cd011db47/migrateprojectce73agentauthaadapp"),
                    Map.entry("authority", "https://login.windows.net/72f988bf-86f1-41af-91ab-2d7cd011db47"),
                    Map.entry("objectId", "be75098e-c0fc-4ac4-98c7-282ebbcf8370"),
                    Map.entry("tenantId", "72f988bf-86f1-41af-91ab-2d7cd011db47")
                ))),
                Map.entry("discoverySiteId", "/subscriptions/8c3c936a-c09b-4de3-830b-3f5f244d72e9/resourceGroups/ContosoITHyperV/providers/Microsoft.OffAzure/HyperVSites/migrateprojectce73site")
            ))
            .resourceGroupName("contosoithyperv")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const hyperVCollector = new azure_native.migrate.HyperVCollector("hyperVCollector", {
    eTag: "\"00000981-0000-0300-0000-5d74cd5f0000\"",
    hyperVCollectorName: "migrateprojectce73collector",
    projectName: "migrateprojectce73project",
    properties: {
        agentProperties: {
            spnDetails: {
                applicationId: "827f1053-44dc-439f-b832-05416dcce12b",
                audience: "https://72f988bf-86f1-41af-91ab-2d7cd011db47/migrateprojectce73agentauthaadapp",
                authority: "https://login.windows.net/72f988bf-86f1-41af-91ab-2d7cd011db47",
                objectId: "be75098e-c0fc-4ac4-98c7-282ebbcf8370",
                tenantId: "72f988bf-86f1-41af-91ab-2d7cd011db47",
            },
        },
        discoverySiteId: "/subscriptions/8c3c936a-c09b-4de3-830b-3f5f244d72e9/resourceGroups/ContosoITHyperV/providers/Microsoft.OffAzure/HyperVSites/migrateprojectce73site",
    },
    resourceGroupName: "contosoithyperv",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

hyper_v_collector = azure_native.migrate.HyperVCollector("hyperVCollector",
    e_tag="\"00000981-0000-0300-0000-5d74cd5f0000\"",
    hyper_v_collector_name="migrateprojectce73collector",
    project_name="migrateprojectce73project",
    properties=azure_native.migrate.CollectorPropertiesResponseArgs(
        agent_properties={
            "spnDetails": azure_native.migrate.CollectorBodyAgentSpnPropertiesArgs(
                application_id="827f1053-44dc-439f-b832-05416dcce12b",
                audience="https://72f988bf-86f1-41af-91ab-2d7cd011db47/migrateprojectce73agentauthaadapp",
                authority="https://login.windows.net/72f988bf-86f1-41af-91ab-2d7cd011db47",
                object_id="be75098e-c0fc-4ac4-98c7-282ebbcf8370",
                tenant_id="72f988bf-86f1-41af-91ab-2d7cd011db47",
            ),
        },
        discovery_site_id="/subscriptions/8c3c936a-c09b-4de3-830b-3f5f244d72e9/resourceGroups/ContosoITHyperV/providers/Microsoft.OffAzure/HyperVSites/migrateprojectce73site",
    ),
    resource_group_name="contosoithyperv")

```

```yaml
resources:
  hyperVCollector:
    type: azure-native:migrate:HyperVCollector
    properties:
      eTag: '"00000981-0000-0300-0000-5d74cd5f0000"'
      hyperVCollectorName: migrateprojectce73collector
      projectName: migrateprojectce73project
      properties:
        agentProperties:
          spnDetails:
            applicationId: 827f1053-44dc-439f-b832-05416dcce12b
            audience: https://72f988bf-86f1-41af-91ab-2d7cd011db47/migrateprojectce73agentauthaadapp
            authority: https://login.windows.net/72f988bf-86f1-41af-91ab-2d7cd011db47
            objectId: be75098e-c0fc-4ac4-98c7-282ebbcf8370
            tenantId: 72f988bf-86f1-41af-91ab-2d7cd011db47
        discoverySiteId: /subscriptions/8c3c936a-c09b-4de3-830b-3f5f244d72e9/resourceGroups/ContosoITHyperV/providers/Microsoft.OffAzure/HyperVSites/migrateprojectce73site
      resourceGroupName: contosoithyperv

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:migrate:HyperVCollector migrateprojectce73collector /subscriptions/8c3c936a-c09b-4de3-830b-3f5f244d72e9/resourceGroups/contosoithyperv/providers/Microsoft.Migrate/assessmentprojects/migrateprojectce73project/hypervcollectors/migrateprojectce73collector 
```
