A container for a managed identity to execute DevTest lab services.
API Version: 2018-09-15.
Previous API Version: 2018-09-15. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ServiceRunners_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var serviceRunner = new AzureNative.DevTestLab.ServiceRunner("serviceRunner", new()
    {
        Identity = new AzureNative.DevTestLab.Inputs.IdentityPropertiesArgs
        {
            ClientSecretUrl = "{identityClientSecretUrl}",
            PrincipalId = "{identityPrincipalId}",
            TenantId = "{identityTenantId}",
            Type = "{identityType}",
        },
        LabName = "{devtestlabName}",
        Location = "{location}",
        Name = "{servicerunnerName}",
        ResourceGroupName = "resourceGroupName",
        Tags = 
        {
            { "tagName1", "tagValue1" },
        },
    });

});


```

```go
package main

import (
	devtestlab "github.com/pulumi/pulumi-azure-native-sdk/devtestlab"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := devtestlab.NewServiceRunner(ctx, "serviceRunner", &devtestlab.ServiceRunnerArgs{
			Identity: &devtestlab.IdentityPropertiesArgs{
				ClientSecretUrl: pulumi.String("{identityClientSecretUrl}"),
				PrincipalId:     pulumi.String("{identityPrincipalId}"),
				TenantId:        pulumi.String("{identityTenantId}"),
				Type:            pulumi.String("{identityType}"),
			},
			LabName:           pulumi.String("{devtestlabName}"),
			Location:          pulumi.String("{location}"),
			Name:              pulumi.String("{servicerunnerName}"),
			ResourceGroupName: pulumi.String("resourceGroupName"),
			Tags: pulumi.StringMap{
				"tagName1": pulumi.String("tagValue1"),
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
import com.pulumi.azurenative.devtestlab.ServiceRunner;
import com.pulumi.azurenative.devtestlab.ServiceRunnerArgs;
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
        var serviceRunner = new ServiceRunner("serviceRunner", ServiceRunnerArgs.builder()        
            .identity(Map.ofEntries(
                Map.entry("clientSecretUrl", "{identityClientSecretUrl}"),
                Map.entry("principalId", "{identityPrincipalId}"),
                Map.entry("tenantId", "{identityTenantId}"),
                Map.entry("type", "{identityType}")
            ))
            .labName("{devtestlabName}")
            .location("{location}")
            .name("{servicerunnerName}")
            .resourceGroupName("resourceGroupName")
            .tags(Map.of("tagName1", "tagValue1"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const serviceRunner = new azure_native.devtestlab.ServiceRunner("serviceRunner", {
    identity: {
        clientSecretUrl: "{identityClientSecretUrl}",
        principalId: "{identityPrincipalId}",
        tenantId: "{identityTenantId}",
        type: "{identityType}",
    },
    labName: "{devtestlabName}",
    location: "{location}",
    name: "{servicerunnerName}",
    resourceGroupName: "resourceGroupName",
    tags: {
        tagName1: "tagValue1",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

service_runner = azure_native.devtestlab.ServiceRunner("serviceRunner",
    identity=azure_native.devtestlab.IdentityPropertiesArgs(
        client_secret_url="{identityClientSecretUrl}",
        principal_id="{identityPrincipalId}",
        tenant_id="{identityTenantId}",
        type="{identityType}",
    ),
    lab_name="{devtestlabName}",
    location="{location}",
    name="{servicerunnerName}",
    resource_group_name="resourceGroupName",
    tags={
        "tagName1": "tagValue1",
    })

```

```yaml
resources:
  serviceRunner:
    type: azure-native:devtestlab:ServiceRunner
    properties:
      identity:
        clientSecretUrl: '{identityClientSecretUrl}'
        principalId: '{identityPrincipalId}'
        tenantId: '{identityTenantId}'
        type: '{identityType}'
      labName: '{devtestlabName}'
      location: '{location}'
      name: '{servicerunnerName}'
      resourceGroupName: resourceGroupName
      tags:
        tagName1: tagValue1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:devtestlab:ServiceRunner myresource1 /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.DevTestLab/labs/{labName}/servicerunners/{name} 
```
