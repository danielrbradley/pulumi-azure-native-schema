Single item in List or Get Alias(Disaster Recovery configuration) operation
API Version: 2021-11-01.
Previous API Version: 2017-04-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### EHAliasCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var disasterRecoveryConfig = new AzureNative.EventHub.DisasterRecoveryConfig("disasterRecoveryConfig", new()
    {
        Alias = "sdk-DisasterRecovery-3814",
        NamespaceName = "sdk-Namespace-8859",
        PartnerNamespace = "sdk-Namespace-37",
        ResourceGroupName = "exampleResourceGroup",
    });

});


```

```go
package main

import (
	eventhub "github.com/pulumi/pulumi-azure-native-sdk/eventhub"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := eventhub.NewDisasterRecoveryConfig(ctx, "disasterRecoveryConfig", &eventhub.DisasterRecoveryConfigArgs{
			Alias:             pulumi.String("sdk-DisasterRecovery-3814"),
			NamespaceName:     pulumi.String("sdk-Namespace-8859"),
			PartnerNamespace:  pulumi.String("sdk-Namespace-37"),
			ResourceGroupName: pulumi.String("exampleResourceGroup"),
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
import com.pulumi.azurenative.eventhub.DisasterRecoveryConfig;
import com.pulumi.azurenative.eventhub.DisasterRecoveryConfigArgs;
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
        var disasterRecoveryConfig = new DisasterRecoveryConfig("disasterRecoveryConfig", DisasterRecoveryConfigArgs.builder()        
            .alias("sdk-DisasterRecovery-3814")
            .namespaceName("sdk-Namespace-8859")
            .partnerNamespace("sdk-Namespace-37")
            .resourceGroupName("exampleResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const disasterRecoveryConfig = new azure_native.eventhub.DisasterRecoveryConfig("disasterRecoveryConfig", {
    alias: "sdk-DisasterRecovery-3814",
    namespaceName: "sdk-Namespace-8859",
    partnerNamespace: "sdk-Namespace-37",
    resourceGroupName: "exampleResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

disaster_recovery_config = azure_native.eventhub.DisasterRecoveryConfig("disasterRecoveryConfig",
    alias="sdk-DisasterRecovery-3814",
    namespace_name="sdk-Namespace-8859",
    partner_namespace="sdk-Namespace-37",
    resource_group_name="exampleResourceGroup")

```

```yaml
resources:
  disasterRecoveryConfig:
    type: azure-native:eventhub:DisasterRecoveryConfig
    properties:
      alias: sdk-DisasterRecovery-3814
      namespaceName: sdk-Namespace-8859
      partnerNamespace: sdk-Namespace-37
      resourceGroupName: exampleResourceGroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:eventhub:DisasterRecoveryConfig sdk-DisasterRecovery-3814 /subscriptions/exampleResourceGroup/resourceGroups/exampleResourceGroup/providers/Microsoft.EventHub/namespaces/sdk-Namespace-8859/disasterRecoveryConfig/sdk-DisasterRecovery-3814 
```
