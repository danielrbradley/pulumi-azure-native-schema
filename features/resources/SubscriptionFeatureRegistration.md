Subscription feature registration details
API Version: 2021-07-01.
Previous API Version: 2021-07-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Creates a feature registration
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var subscriptionFeatureRegistration = new AzureNative.Features.SubscriptionFeatureRegistration("subscriptionFeatureRegistration", new()
    {
        FeatureName = "testFeature",
        Properties = null,
        ProviderNamespace = "subscriptionFeatureRegistrationGroupTestRG",
    });

});


```

```go
package main

import (
	features "github.com/pulumi/pulumi-azure-native-sdk/features"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := features.NewSubscriptionFeatureRegistration(ctx, "subscriptionFeatureRegistration", &features.SubscriptionFeatureRegistrationArgs{
			FeatureName:       pulumi.String("testFeature"),
			Properties:        nil,
			ProviderNamespace: pulumi.String("subscriptionFeatureRegistrationGroupTestRG"),
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
import com.pulumi.azurenative.features.SubscriptionFeatureRegistration;
import com.pulumi.azurenative.features.SubscriptionFeatureRegistrationArgs;
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
        var subscriptionFeatureRegistration = new SubscriptionFeatureRegistration("subscriptionFeatureRegistration", SubscriptionFeatureRegistrationArgs.builder()        
            .featureName("testFeature")
            .properties()
            .providerNamespace("subscriptionFeatureRegistrationGroupTestRG")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const subscriptionFeatureRegistration = new azure_native.features.SubscriptionFeatureRegistration("subscriptionFeatureRegistration", {
    featureName: "testFeature",
    properties: {},
    providerNamespace: "subscriptionFeatureRegistrationGroupTestRG",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

subscription_feature_registration = azure_native.features.SubscriptionFeatureRegistration("subscriptionFeatureRegistration",
    feature_name="testFeature",
    properties=azure_native.features.SubscriptionFeatureRegistrationPropertiesArgs(),
    provider_namespace="subscriptionFeatureRegistrationGroupTestRG")

```

```yaml
resources:
  subscriptionFeatureRegistration:
    type: azure-native:features:SubscriptionFeatureRegistration
    properties:
      featureName: testFeature
      properties: {}
      providerNamespace: subscriptionFeatureRegistrationGroupTestRG

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:features:SubscriptionFeatureRegistration testFeature /subscriptions/00000000-1111-2222-3333-444444444444/providers/Microsoft.Features/featureProviders/Microsoft.TestRP/subscriptionFeatureRegistrations/testFeature 
```
