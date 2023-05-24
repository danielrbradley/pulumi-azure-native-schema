
API Version: 2022-09-01-preview.
Previous API Version: 2022-09-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### AzureDevOpsConnector_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var azureDevOpsConnector = new AzureNative.SecurityDevOps.AzureDevOpsConnector("azureDevOpsConnector", new()
    {
        AzureDevOpsConnectorName = "testconnector",
        Location = "West US",
        Properties = new AzureNative.SecurityDevOps.Inputs.AzureDevOpsConnectorPropertiesArgs
        {
            Authorization = new AzureNative.SecurityDevOps.Inputs.AuthorizationInfoArgs
            {
                Code = "00000000000000000000",
            },
            Orgs = new[]
            {
                new AzureNative.SecurityDevOps.Inputs.AzureDevOpsOrgMetadataArgs
                {
                    Name = "testOrg",
                    Projects = new[]
                    {
                        new AzureNative.SecurityDevOps.Inputs.AzureDevOpsProjectMetadataArgs
                        {
                            Name = "testProject",
                            Repos = new[]
                            {
                                "testRepo",
                            },
                        },
                    },
                },
            },
        },
        ResourceGroupName = "westusrg",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.securitydevops.AzureDevOpsConnector;
import com.pulumi.azurenative.securitydevops.AzureDevOpsConnectorArgs;
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
        var azureDevOpsConnector = new AzureDevOpsConnector("azureDevOpsConnector", AzureDevOpsConnectorArgs.builder()        
            .azureDevOpsConnectorName("testconnector")
            .location("West US")
            .properties(Map.ofEntries(
                Map.entry("authorization", Map.of("code", "00000000000000000000")),
                Map.entry("orgs", Map.ofEntries(
                    Map.entry("name", "testOrg"),
                    Map.entry("projects", Map.ofEntries(
                        Map.entry("name", "testProject"),
                        Map.entry("repos", "testRepo")
                    ))
                ))
            ))
            .resourceGroupName("westusrg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const azureDevOpsConnector = new azure_native.securitydevops.AzureDevOpsConnector("azureDevOpsConnector", {
    azureDevOpsConnectorName: "testconnector",
    location: "West US",
    properties: {
        authorization: {
            code: "00000000000000000000",
        },
        orgs: [{
            name: "testOrg",
            projects: [{
                name: "testProject",
                repos: ["testRepo"],
            }],
        }],
    },
    resourceGroupName: "westusrg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

azure_dev_ops_connector = azure_native.securitydevops.AzureDevOpsConnector("azureDevOpsConnector",
    azure_dev_ops_connector_name="testconnector",
    location="West US",
    properties=azure_native.securitydevops.AzureDevOpsConnectorPropertiesResponseArgs(
        authorization=azure_native.securitydevops.AuthorizationInfoArgs(
            code="00000000000000000000",
        ),
        orgs=[{
            "name": "testOrg",
            "projects": [azure_native.securitydevops.AzureDevOpsProjectMetadataArgs(
                name="testProject",
                repos=["testRepo"],
            )],
        }],
    ),
    resource_group_name="westusrg")

```

```yaml
resources:
  azureDevOpsConnector:
    type: azure-native:securitydevops:AzureDevOpsConnector
    properties:
      azureDevOpsConnectorName: testconnector
      location: West US
      properties:
        authorization:
          code: '00000000000000000000'
        orgs:
          - name: testOrg
            projects:
              - name: testProject
                repos:
                  - testRepo
      resourceGroupName: westusrg

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:securitydevops:AzureDevOpsConnector testconnector /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/westusrg/providers/Microsoft.SecurityDevOps/azureDevOpsConnectors/testconnector 
```
