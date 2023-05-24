The security connector resource.
API Version: 2022-08-01-preview.
Previous API Version: 2021-07-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a security connector
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var securityConnector = new AzureNative.Security.SecurityConnector("securityConnector", new()
    {
        EnvironmentData = new AzureNative.Security.Inputs.AwsEnvironmentDataArgs
        {
            EnvironmentType = "AwsAccount",
        },
        EnvironmentName = "AWS",
        HierarchyIdentifier = "exampleHierarchyId",
        Location = "Central US",
        Offerings = new[]
        {
            new AzureNative.Security.Inputs.CspmMonitorAwsOfferingArgs
            {
                NativeCloudConnection = new AzureNative.Security.Inputs.CspmMonitorAwsOfferingNativeCloudConnectionArgs
                {
                    CloudRoleArn = "arn:aws:iam::00000000:role/ASCMonitor",
                },
                OfferingType = "CspmMonitorAws",
            },
        },
        ResourceGroupName = "exampleResourceGroup",
        SecurityConnectorName = "exampleSecurityConnectorName",
        Tags = null,
    });

});


```

```go
package main

import (
	security "github.com/pulumi/pulumi-azure-native-sdk/security"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := security.NewSecurityConnector(ctx, "securityConnector", &security.SecurityConnectorArgs{
			EnvironmentData: security.AwsEnvironmentData{
				EnvironmentType: "AwsAccount",
			},
			EnvironmentName:     pulumi.String("AWS"),
			HierarchyIdentifier: pulumi.String("exampleHierarchyId"),
			Location:            pulumi.String("Central US"),
			Offerings: pulumi.AnyArray{
				security.CspmMonitorAwsOffering{
					NativeCloudConnection: security.CspmMonitorAwsOfferingNativeCloudConnection{
						CloudRoleArn: "arn:aws:iam::00000000:role/ASCMonitor",
					},
					OfferingType: "CspmMonitorAws",
				},
			},
			ResourceGroupName:     pulumi.String("exampleResourceGroup"),
			SecurityConnectorName: pulumi.String("exampleSecurityConnectorName"),
			Tags:                  nil,
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
import com.pulumi.azurenative.security.SecurityConnector;
import com.pulumi.azurenative.security.SecurityConnectorArgs;
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
        var securityConnector = new SecurityConnector("securityConnector", SecurityConnectorArgs.builder()        
            .environmentData(Map.of("environmentType", "AwsAccount"))
            .environmentName("AWS")
            .hierarchyIdentifier("exampleHierarchyId")
            .location("Central US")
            .offerings(Map.ofEntries(
                Map.entry("nativeCloudConnection", Map.of("cloudRoleArn", "arn:aws:iam::00000000:role/ASCMonitor")),
                Map.entry("offeringType", "CspmMonitorAws")
            ))
            .resourceGroupName("exampleResourceGroup")
            .securityConnectorName("exampleSecurityConnectorName")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const securityConnector = new azure_native.security.SecurityConnector("securityConnector", {
    environmentData: {
        environmentType: "AwsAccount",
    },
    environmentName: "AWS",
    hierarchyIdentifier: "exampleHierarchyId",
    location: "Central US",
    offerings: [{
        nativeCloudConnection: {
            cloudRoleArn: "arn:aws:iam::00000000:role/ASCMonitor",
        },
        offeringType: "CspmMonitorAws",
    }],
    resourceGroupName: "exampleResourceGroup",
    securityConnectorName: "exampleSecurityConnectorName",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

security_connector = azure_native.security.SecurityConnector("securityConnector",
    environment_data=azure_native.security.AwsEnvironmentDataArgs(
        environment_type="AwsAccount",
    ),
    environment_name="AWS",
    hierarchy_identifier="exampleHierarchyId",
    location="Central US",
    offerings=[azure_native.security.CspmMonitorAwsOfferingArgs(
        native_cloud_connection=azure_native.security.CspmMonitorAwsOfferingNativeCloudConnectionArgs(
            cloud_role_arn="arn:aws:iam::00000000:role/ASCMonitor",
        ),
        offering_type="CspmMonitorAws",
    )],
    resource_group_name="exampleResourceGroup",
    security_connector_name="exampleSecurityConnectorName",
    tags={})

```

```yaml
resources:
  securityConnector:
    type: azure-native:security:SecurityConnector
    properties:
      environmentData:
        environmentType: AwsAccount
      environmentName: AWS
      hierarchyIdentifier: exampleHierarchyId
      location: Central US
      offerings:
        - nativeCloudConnection:
            cloudRoleArn: arn:aws:iam::00000000:role/ASCMonitor
          offeringType: CspmMonitorAws
      resourceGroupName: exampleResourceGroup
      securityConnectorName: exampleSecurityConnectorName
      tags: {}

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:security:SecurityConnector exampleSecurityConnectorName /subscriptions/a5caac9c-5c04-49af-b3d0-e204f40345d5/resourceGroups/exampleResourceGroup/providers/Microsoft.Security/securityConnectors/exampleSecurityConnectorName 
```
