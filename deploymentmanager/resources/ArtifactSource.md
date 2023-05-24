The resource that defines the source location where the artifacts are located.
API Version: 2019-11-01-preview.
Previous API Version: 2019-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create artifact source
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var artifactSource = new AzureNative.DeploymentManager.ArtifactSource("artifactSource", new()
    {
        ArtifactSourceName = "myArtifactSource",
        Authentication = new AzureNative.DeploymentManager.Inputs.SasAuthenticationArgs
        {
            SasUri = "https://mystorageaccount.blob.core.windows.net/myartifactsource?st=2018-07-07T14%3A10%3A00Z&se=2019-12-31T15%3A10%3A00Z&sp=rl&sv=2017-04-17&sr=c&sig=Yh2SoJ1NhhLRwCLln7de%2Fkabcdefghijklmno5sWEIk%3D",
            Type = "Sas",
        },
        Location = "centralus",
        ResourceGroupName = "myResourceGroup",
        SourceType = "AzureStorage",
        Tags = null,
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.deploymentmanager.ArtifactSource;
import com.pulumi.azurenative.deploymentmanager.ArtifactSourceArgs;
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
        var artifactSource = new ArtifactSource("artifactSource", ArtifactSourceArgs.builder()        
            .artifactSourceName("myArtifactSource")
            .authentication(Map.ofEntries(
                Map.entry("sasUri", "https://mystorageaccount.blob.core.windows.net/myartifactsource?st=2018-07-07T14%3A10%3A00Z&se=2019-12-31T15%3A10%3A00Z&sp=rl&sv=2017-04-17&sr=c&sig=Yh2SoJ1NhhLRwCLln7de%2Fkabcdefghijklmno5sWEIk%3D"),
                Map.entry("type", "Sas")
            ))
            .location("centralus")
            .resourceGroupName("myResourceGroup")
            .sourceType("AzureStorage")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const artifactSource = new azure_native.deploymentmanager.ArtifactSource("artifactSource", {
    artifactSourceName: "myArtifactSource",
    authentication: {
        sasUri: "https://mystorageaccount.blob.core.windows.net/myartifactsource?st=2018-07-07T14%3A10%3A00Z&se=2019-12-31T15%3A10%3A00Z&sp=rl&sv=2017-04-17&sr=c&sig=Yh2SoJ1NhhLRwCLln7de%2Fkabcdefghijklmno5sWEIk%3D",
        type: "Sas",
    },
    location: "centralus",
    resourceGroupName: "myResourceGroup",
    sourceType: "AzureStorage",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

artifact_source = azure_native.deploymentmanager.ArtifactSource("artifactSource",
    artifact_source_name="myArtifactSource",
    authentication=azure_native.deploymentmanager.SasAuthenticationResponseArgs(
        sas_uri="https://mystorageaccount.blob.core.windows.net/myartifactsource?st=2018-07-07T14%3A10%3A00Z&se=2019-12-31T15%3A10%3A00Z&sp=rl&sv=2017-04-17&sr=c&sig=Yh2SoJ1NhhLRwCLln7de%2Fkabcdefghijklmno5sWEIk%3D",
        type="Sas",
    ),
    location="centralus",
    resource_group_name="myResourceGroup",
    source_type="AzureStorage",
    tags={})

```

```yaml
resources:
  artifactSource:
    type: azure-native:deploymentmanager:ArtifactSource
    properties:
      artifactSourceName: myArtifactSource
      authentication:
        sasUri: https://mystorageaccount.blob.core.windows.net/myartifactsource?st=2018-07-07T14%3A10%3A00Z&se=2019-12-31T15%3A10%3A00Z&sp=rl&sv=2017-04-17&sr=c&sig=Yh2SoJ1NhhLRwCLln7de%2Fkabcdefghijklmno5sWEIk%3D
        type: Sas
      location: centralus
      resourceGroupName: myResourceGroup
      sourceType: AzureStorage
      tags: {}

```

{{% /example %}}
{{% example %}}
### Create artifact source with artifact root, an offset into the storage container
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var artifactSource = new AzureNative.DeploymentManager.ArtifactSource("artifactSource", new()
    {
        ArtifactRoot = "1.0.0.0",
        ArtifactSourceName = "myArtifactSource",
        Authentication = new AzureNative.DeploymentManager.Inputs.SasAuthenticationArgs
        {
            SasUri = "https://mystorageaccount.blob.core.windows.net/myartifactsource?st=2018-07-07T14%3A10%3A00Z&se=2019-12-31T15%3A10%3A00Z&sp=rl&sv=2017-04-17&sr=c&sig=Yh2SoJ1NhhLRwCLln7de%2Fkabcdefghijklmno5sWEIk%3D",
            Type = "Sas",
        },
        Location = "centralus",
        ResourceGroupName = "myResourceGroup",
        SourceType = "AzureStorage",
        Tags = null,
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.deploymentmanager.ArtifactSource;
import com.pulumi.azurenative.deploymentmanager.ArtifactSourceArgs;
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
        var artifactSource = new ArtifactSource("artifactSource", ArtifactSourceArgs.builder()        
            .artifactRoot("1.0.0.0")
            .artifactSourceName("myArtifactSource")
            .authentication(Map.ofEntries(
                Map.entry("sasUri", "https://mystorageaccount.blob.core.windows.net/myartifactsource?st=2018-07-07T14%3A10%3A00Z&se=2019-12-31T15%3A10%3A00Z&sp=rl&sv=2017-04-17&sr=c&sig=Yh2SoJ1NhhLRwCLln7de%2Fkabcdefghijklmno5sWEIk%3D"),
                Map.entry("type", "Sas")
            ))
            .location("centralus")
            .resourceGroupName("myResourceGroup")
            .sourceType("AzureStorage")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const artifactSource = new azure_native.deploymentmanager.ArtifactSource("artifactSource", {
    artifactRoot: "1.0.0.0",
    artifactSourceName: "myArtifactSource",
    authentication: {
        sasUri: "https://mystorageaccount.blob.core.windows.net/myartifactsource?st=2018-07-07T14%3A10%3A00Z&se=2019-12-31T15%3A10%3A00Z&sp=rl&sv=2017-04-17&sr=c&sig=Yh2SoJ1NhhLRwCLln7de%2Fkabcdefghijklmno5sWEIk%3D",
        type: "Sas",
    },
    location: "centralus",
    resourceGroupName: "myResourceGroup",
    sourceType: "AzureStorage",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

artifact_source = azure_native.deploymentmanager.ArtifactSource("artifactSource",
    artifact_root="1.0.0.0",
    artifact_source_name="myArtifactSource",
    authentication=azure_native.deploymentmanager.SasAuthenticationResponseArgs(
        sas_uri="https://mystorageaccount.blob.core.windows.net/myartifactsource?st=2018-07-07T14%3A10%3A00Z&se=2019-12-31T15%3A10%3A00Z&sp=rl&sv=2017-04-17&sr=c&sig=Yh2SoJ1NhhLRwCLln7de%2Fkabcdefghijklmno5sWEIk%3D",
        type="Sas",
    ),
    location="centralus",
    resource_group_name="myResourceGroup",
    source_type="AzureStorage",
    tags={})

```

```yaml
resources:
  artifactSource:
    type: azure-native:deploymentmanager:ArtifactSource
    properties:
      artifactRoot: 1.0.0.0
      artifactSourceName: myArtifactSource
      authentication:
        sasUri: https://mystorageaccount.blob.core.windows.net/myartifactsource?st=2018-07-07T14%3A10%3A00Z&se=2019-12-31T15%3A10%3A00Z&sp=rl&sv=2017-04-17&sr=c&sig=Yh2SoJ1NhhLRwCLln7de%2Fkabcdefghijklmno5sWEIk%3D
        type: Sas
      location: centralus
      resourceGroupName: myResourceGroup
      sourceType: AzureStorage
      tags: {}

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:deploymentmanager:ArtifactSource myArtifactSource /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.DeploymentManager/artifactSources/{artifactSourceName} 
```
