The Job Definition resource.
API Version: 2023-03-01.
Previous API Version: 2022-07-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### JobDefinitions_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var jobDefinition = new AzureNative.StorageMover.JobDefinition("jobDefinition", new()
    {
        AgentName = "migration-agent",
        CopyMode = "Additive",
        Description = "Example Job Definition Description",
        JobDefinitionName = "examples-jobDefinitionName",
        ProjectName = "examples-projectName",
        ResourceGroupName = "examples-rg",
        SourceName = "examples-sourceEndpointName",
        SourceSubpath = "/",
        StorageMoverName = "examples-storageMoverName",
        TargetName = "examples-targetEndpointName",
        TargetSubpath = "/",
    });

});


```

```go
package main

import (
	storagemover "github.com/pulumi/pulumi-azure-native-sdk/storagemover"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := storagemover.NewJobDefinition(ctx, "jobDefinition", &storagemover.JobDefinitionArgs{
			AgentName:         pulumi.String("migration-agent"),
			CopyMode:          pulumi.String("Additive"),
			Description:       pulumi.String("Example Job Definition Description"),
			JobDefinitionName: pulumi.String("examples-jobDefinitionName"),
			ProjectName:       pulumi.String("examples-projectName"),
			ResourceGroupName: pulumi.String("examples-rg"),
			SourceName:        pulumi.String("examples-sourceEndpointName"),
			SourceSubpath:     pulumi.String("/"),
			StorageMoverName:  pulumi.String("examples-storageMoverName"),
			TargetName:        pulumi.String("examples-targetEndpointName"),
			TargetSubpath:     pulumi.String("/"),
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
import com.pulumi.azurenative.storagemover.JobDefinition;
import com.pulumi.azurenative.storagemover.JobDefinitionArgs;
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
        var jobDefinition = new JobDefinition("jobDefinition", JobDefinitionArgs.builder()        
            .agentName("migration-agent")
            .copyMode("Additive")
            .description("Example Job Definition Description")
            .jobDefinitionName("examples-jobDefinitionName")
            .projectName("examples-projectName")
            .resourceGroupName("examples-rg")
            .sourceName("examples-sourceEndpointName")
            .sourceSubpath("/")
            .storageMoverName("examples-storageMoverName")
            .targetName("examples-targetEndpointName")
            .targetSubpath("/")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const jobDefinition = new azure_native.storagemover.JobDefinition("jobDefinition", {
    agentName: "migration-agent",
    copyMode: "Additive",
    description: "Example Job Definition Description",
    jobDefinitionName: "examples-jobDefinitionName",
    projectName: "examples-projectName",
    resourceGroupName: "examples-rg",
    sourceName: "examples-sourceEndpointName",
    sourceSubpath: "/",
    storageMoverName: "examples-storageMoverName",
    targetName: "examples-targetEndpointName",
    targetSubpath: "/",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

job_definition = azure_native.storagemover.JobDefinition("jobDefinition",
    agent_name="migration-agent",
    copy_mode="Additive",
    description="Example Job Definition Description",
    job_definition_name="examples-jobDefinitionName",
    project_name="examples-projectName",
    resource_group_name="examples-rg",
    source_name="examples-sourceEndpointName",
    source_subpath="/",
    storage_mover_name="examples-storageMoverName",
    target_name="examples-targetEndpointName",
    target_subpath="/")

```

```yaml
resources:
  jobDefinition:
    type: azure-native:storagemover:JobDefinition
    properties:
      agentName: migration-agent
      copyMode: Additive
      description: Example Job Definition Description
      jobDefinitionName: examples-jobDefinitionName
      projectName: examples-projectName
      resourceGroupName: examples-rg
      sourceName: examples-sourceEndpointName
      sourceSubpath: /
      storageMoverName: examples-storageMoverName
      targetName: examples-targetEndpointName
      targetSubpath: /

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:storagemover:JobDefinition examples-jobDefinitionName /subscriptions/11111111-2222-3333-4444-555555555555/resourceGroups/examples-rg/providers/Microsoft.StorageMover/storageMovers/examples-storageMoverName/projects/examples-projectName/jobDefinitions/examples-jobDefinitionName 
```
