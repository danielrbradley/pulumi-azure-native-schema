
API Version: 2019-10-01.
Previous API Version: 2019-10-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ServerCollectors_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var serverCollector = new AzureNative.Migrate.ServerCollector("serverCollector", new()
    {
        ETag = "\"00000606-0000-0d00-0000-605999bf0000\"",
        ProjectName = "app11141project",
        Properties = new AzureNative.Migrate.Inputs.CollectorPropertiesArgs
        {
            AgentProperties = new AzureNative.Migrate.Inputs.CollectorAgentPropertiesArgs
            {
                SpnDetails = new AzureNative.Migrate.Inputs.CollectorBodyAgentSpnPropertiesArgs
                {
                    ApplicationId = "ad9f701a-cc08-4421-b51f-b5762d58e9ba",
                    Audience = "https://72f988bf-86f1-41af-91ab-2d7cd011db47/app23df4authandaccessaadapp",
                    Authority = "https://login.windows.net/72f988bf-86f1-41af-91ab-2d7cd011db47",
                    ObjectId = "b4975e42-9248-4a36-b99f-37eca377ea00",
                    TenantId = "72f988bf-86f1-41af-91ab-2d7cd011db47",
                },
            },
            DiscoverySiteId = "/subscriptions/4bd2aa0f-2bd2-4d67-91a8-5a4533d58600/resourceGroups/pajindTest/providers/Microsoft.OffAzure/ServerSites/app21141site",
        },
        ResourceGroupName = "pajindtest",
        ServerCollectorName = "app23df4collector",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.migrate.ServerCollector;
import com.pulumi.azurenative.migrate.ServerCollectorArgs;
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
        var serverCollector = new ServerCollector("serverCollector", ServerCollectorArgs.builder()        
            .eTag("\"00000606-0000-0d00-0000-605999bf0000\"")
            .projectName("app11141project")
            .properties(Map.ofEntries(
                Map.entry("agentProperties", Map.of("spnDetails", Map.ofEntries(
                    Map.entry("applicationId", "ad9f701a-cc08-4421-b51f-b5762d58e9ba"),
                    Map.entry("audience", "https://72f988bf-86f1-41af-91ab-2d7cd011db47/app23df4authandaccessaadapp"),
                    Map.entry("authority", "https://login.windows.net/72f988bf-86f1-41af-91ab-2d7cd011db47"),
                    Map.entry("objectId", "b4975e42-9248-4a36-b99f-37eca377ea00"),
                    Map.entry("tenantId", "72f988bf-86f1-41af-91ab-2d7cd011db47")
                ))),
                Map.entry("discoverySiteId", "/subscriptions/4bd2aa0f-2bd2-4d67-91a8-5a4533d58600/resourceGroups/pajindTest/providers/Microsoft.OffAzure/ServerSites/app21141site")
            ))
            .resourceGroupName("pajindtest")
            .serverCollectorName("app23df4collector")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const serverCollector = new azure_native.migrate.ServerCollector("serverCollector", {
    eTag: "\"00000606-0000-0d00-0000-605999bf0000\"",
    projectName: "app11141project",
    properties: {
        agentProperties: {
            spnDetails: {
                applicationId: "ad9f701a-cc08-4421-b51f-b5762d58e9ba",
                audience: "https://72f988bf-86f1-41af-91ab-2d7cd011db47/app23df4authandaccessaadapp",
                authority: "https://login.windows.net/72f988bf-86f1-41af-91ab-2d7cd011db47",
                objectId: "b4975e42-9248-4a36-b99f-37eca377ea00",
                tenantId: "72f988bf-86f1-41af-91ab-2d7cd011db47",
            },
        },
        discoverySiteId: "/subscriptions/4bd2aa0f-2bd2-4d67-91a8-5a4533d58600/resourceGroups/pajindTest/providers/Microsoft.OffAzure/ServerSites/app21141site",
    },
    resourceGroupName: "pajindtest",
    serverCollectorName: "app23df4collector",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

server_collector = azure_native.migrate.ServerCollector("serverCollector",
    e_tag="\"00000606-0000-0d00-0000-605999bf0000\"",
    project_name="app11141project",
    properties=azure_native.migrate.CollectorPropertiesResponseArgs(
        agent_properties={
            "spnDetails": azure_native.migrate.CollectorBodyAgentSpnPropertiesArgs(
                application_id="ad9f701a-cc08-4421-b51f-b5762d58e9ba",
                audience="https://72f988bf-86f1-41af-91ab-2d7cd011db47/app23df4authandaccessaadapp",
                authority="https://login.windows.net/72f988bf-86f1-41af-91ab-2d7cd011db47",
                object_id="b4975e42-9248-4a36-b99f-37eca377ea00",
                tenant_id="72f988bf-86f1-41af-91ab-2d7cd011db47",
            ),
        },
        discovery_site_id="/subscriptions/4bd2aa0f-2bd2-4d67-91a8-5a4533d58600/resourceGroups/pajindTest/providers/Microsoft.OffAzure/ServerSites/app21141site",
    ),
    resource_group_name="pajindtest",
    server_collector_name="app23df4collector")

```

```yaml
resources:
  serverCollector:
    type: azure-native:migrate:ServerCollector
    properties:
      eTag: '"00000606-0000-0d00-0000-605999bf0000"'
      projectName: app11141project
      properties:
        agentProperties:
          spnDetails:
            applicationId: ad9f701a-cc08-4421-b51f-b5762d58e9ba
            audience: https://72f988bf-86f1-41af-91ab-2d7cd011db47/app23df4authandaccessaadapp
            authority: https://login.windows.net/72f988bf-86f1-41af-91ab-2d7cd011db47
            objectId: b4975e42-9248-4a36-b99f-37eca377ea00
            tenantId: 72f988bf-86f1-41af-91ab-2d7cd011db47
        discoverySiteId: /subscriptions/4bd2aa0f-2bd2-4d67-91a8-5a4533d58600/resourceGroups/pajindTest/providers/Microsoft.OffAzure/ServerSites/app21141site
      resourceGroupName: pajindtest
      serverCollectorName: app23df4collector

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:migrate:ServerCollector app23df4collector /subscriptions/4bd2aa0f-2bd2-4d67-91a8-5a4533d58600/resourceGroups/pajindtest/providers/Microsoft.Migrate/assessmentprojects/app11141project/servercollectors/app23df4collector 
```
