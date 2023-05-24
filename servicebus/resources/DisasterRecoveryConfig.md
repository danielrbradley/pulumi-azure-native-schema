Single item in List or Get Alias(Disaster Recovery configuration) operation
API Version: 2021-11-01.
Previous API Version: 2017-04-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### SBAliasCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var disasterRecoveryConfig = new AzureNative.ServiceBus.DisasterRecoveryConfig("disasterRecoveryConfig", new()
    {
        Alias = "sdk-Namespace-8860",
        AlternateName = "alternameforAlias-Namespace-8860",
        NamespaceName = "sdk-Namespace-8860",
        PartnerNamespace = "sdk-Namespace-37",
        ResourceGroupName = "ardsouzatestRG",
    });

});


```

```go
package main

import (
	servicebus "github.com/pulumi/pulumi-azure-native-sdk/servicebus"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := servicebus.NewDisasterRecoveryConfig(ctx, "disasterRecoveryConfig", &servicebus.DisasterRecoveryConfigArgs{
			Alias:             pulumi.String("sdk-Namespace-8860"),
			AlternateName:     pulumi.String("alternameforAlias-Namespace-8860"),
			NamespaceName:     pulumi.String("sdk-Namespace-8860"),
			PartnerNamespace:  pulumi.String("sdk-Namespace-37"),
			ResourceGroupName: pulumi.String("ardsouzatestRG"),
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
import com.pulumi.azurenative.servicebus.DisasterRecoveryConfig;
import com.pulumi.azurenative.servicebus.DisasterRecoveryConfigArgs;
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
            .alias("sdk-Namespace-8860")
            .alternateName("alternameforAlias-Namespace-8860")
            .namespaceName("sdk-Namespace-8860")
            .partnerNamespace("sdk-Namespace-37")
            .resourceGroupName("ardsouzatestRG")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const disasterRecoveryConfig = new azure_native.servicebus.DisasterRecoveryConfig("disasterRecoveryConfig", {
    alias: "sdk-Namespace-8860",
    alternateName: "alternameforAlias-Namespace-8860",
    namespaceName: "sdk-Namespace-8860",
    partnerNamespace: "sdk-Namespace-37",
    resourceGroupName: "ardsouzatestRG",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

disaster_recovery_config = azure_native.servicebus.DisasterRecoveryConfig("disasterRecoveryConfig",
    alias="sdk-Namespace-8860",
    alternate_name="alternameforAlias-Namespace-8860",
    namespace_name="sdk-Namespace-8860",
    partner_namespace="sdk-Namespace-37",
    resource_group_name="ardsouzatestRG")

```

```yaml
resources:
  disasterRecoveryConfig:
    type: azure-native:servicebus:DisasterRecoveryConfig
    properties:
      alias: sdk-Namespace-8860
      alternateName: alternameforAlias-Namespace-8860
      namespaceName: sdk-Namespace-8860
      partnerNamespace: sdk-Namespace-37
      resourceGroupName: ardsouzatestRG

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:servicebus:DisasterRecoveryConfig sdk-Namespace-8860 /subscriptions/5f750a97-50d9-4e36-8081-c9ee4c0210d4/resourceGroups/ardsouzatestRG/providers/Microsoft.ServiceBus/namespaces/sdk-Namespace-8860/disasterRecoveryConfig/sdk-Namespace-8860 
```
