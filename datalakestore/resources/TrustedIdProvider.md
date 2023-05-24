Data Lake Store trusted identity provider information.
API Version: 2016-11-01.
Previous API Version: 2016-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Creates or updates the specified trusted identity provider. During update, the trusted identity provider with the specified name will be replaced with this new provider
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var trustedIdProvider = new AzureNative.DataLakeStore.TrustedIdProvider("trustedIdProvider", new()
    {
        AccountName = "contosoadla",
        IdProvider = "https://sts.windows.net/ea9ec534-a3e3-4e45-ad36-3afc5bb291c1",
        ResourceGroupName = "contosorg",
        TrustedIdProviderName = "test_trusted_id_provider_name",
    });

});


```

```go
package main

import (
	datalakestore "github.com/pulumi/pulumi-azure-native-sdk/datalakestore"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := datalakestore.NewTrustedIdProvider(ctx, "trustedIdProvider", &datalakestore.TrustedIdProviderArgs{
			AccountName:           pulumi.String("contosoadla"),
			IdProvider:            pulumi.String("https://sts.windows.net/ea9ec534-a3e3-4e45-ad36-3afc5bb291c1"),
			ResourceGroupName:     pulumi.String("contosorg"),
			TrustedIdProviderName: pulumi.String("test_trusted_id_provider_name"),
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
import com.pulumi.azurenative.datalakestore.TrustedIdProvider;
import com.pulumi.azurenative.datalakestore.TrustedIdProviderArgs;
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
        var trustedIdProvider = new TrustedIdProvider("trustedIdProvider", TrustedIdProviderArgs.builder()        
            .accountName("contosoadla")
            .idProvider("https://sts.windows.net/ea9ec534-a3e3-4e45-ad36-3afc5bb291c1")
            .resourceGroupName("contosorg")
            .trustedIdProviderName("test_trusted_id_provider_name")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const trustedIdProvider = new azure_native.datalakestore.TrustedIdProvider("trustedIdProvider", {
    accountName: "contosoadla",
    idProvider: "https://sts.windows.net/ea9ec534-a3e3-4e45-ad36-3afc5bb291c1",
    resourceGroupName: "contosorg",
    trustedIdProviderName: "test_trusted_id_provider_name",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

trusted_id_provider = azure_native.datalakestore.TrustedIdProvider("trustedIdProvider",
    account_name="contosoadla",
    id_provider="https://sts.windows.net/ea9ec534-a3e3-4e45-ad36-3afc5bb291c1",
    resource_group_name="contosorg",
    trusted_id_provider_name="test_trusted_id_provider_name")

```

```yaml
resources:
  trustedIdProvider:
    type: azure-native:datalakestore:TrustedIdProvider
    properties:
      accountName: contosoadla
      idProvider: https://sts.windows.net/ea9ec534-a3e3-4e45-ad36-3afc5bb291c1
      resourceGroupName: contosorg
      trustedIdProviderName: test_trusted_id_provider_name

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:datalakestore:TrustedIdProvider test_trusted_id_provider_name 34adfa4f-cedf-4dc0-ba29-b6d1a69ab345 
```
