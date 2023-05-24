this is the management partner operations response
API Version: 2018-02-01.
Previous API Version: 2018-02-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### PutPartnerDetails
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var partner = new AzureNative.ManagementPartner.Partner("partner", new()
    {
        PartnerId = "123456",
    });

});


```

```go
package main

import (
	managementpartner "github.com/pulumi/pulumi-azure-native-sdk/managementpartner"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := managementpartner.NewPartner(ctx, "partner", &managementpartner.PartnerArgs{
			PartnerId: pulumi.String("123456"),
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
import com.pulumi.azurenative.managementpartner.Partner;
import com.pulumi.azurenative.managementpartner.PartnerArgs;
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
        var partner = new Partner("partner", PartnerArgs.builder()        
            .partnerId("123456")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const partner = new azure_native.managementpartner.Partner("partner", {partnerId: "123456"});

```

```python
import pulumi
import pulumi_azure_native as azure_native

partner = azure_native.managementpartner.Partner("partner", partner_id="123456")

```

```yaml
resources:
  partner:
    type: azure-native:managementpartner:Partner
    properties:
      partnerId: '123456'

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:managementpartner:Partner 123456 /providers/microsoft.managementpartner/partners/123456 
```
