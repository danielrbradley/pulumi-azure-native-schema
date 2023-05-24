REST model used to encapsulate the user visible state of a PrivateEndpoint.
API Version: 2020-07-07.
Previous API Version: 2020-07-07. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Put privateEndpointConnection
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateEndpointConnection = new AzureNative.OffAzure.PrivateEndpointConnection("privateEndpointConnection", new()
    {
        PeConnectionName = "privateendpt1938mastersit9007pe.4f2f2970-0bfa-45d4-9ee1-d9f79502fc6f",
        ResourceGroupName = "ayagrawrg",
        SiteName = "privateendpt1938mastersite",
    });

});


```

```go
package main

import (
	offazure "github.com/pulumi/pulumi-azure-native-sdk/offazure"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := offazure.NewPrivateEndpointConnection(ctx, "privateEndpointConnection", &offazure.PrivateEndpointConnectionArgs{
			PeConnectionName:  pulumi.String("privateendpt1938mastersit9007pe.4f2f2970-0bfa-45d4-9ee1-d9f79502fc6f"),
			ResourceGroupName: pulumi.String("ayagrawrg"),
			SiteName:          pulumi.String("privateendpt1938mastersite"),
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
import com.pulumi.azurenative.offazure.PrivateEndpointConnection;
import com.pulumi.azurenative.offazure.PrivateEndpointConnectionArgs;
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
        var privateEndpointConnection = new PrivateEndpointConnection("privateEndpointConnection", PrivateEndpointConnectionArgs.builder()        
            .peConnectionName("privateendpt1938mastersit9007pe.4f2f2970-0bfa-45d4-9ee1-d9f79502fc6f")
            .resourceGroupName("ayagrawrg")
            .siteName("privateendpt1938mastersite")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateEndpointConnection = new azure_native.offazure.PrivateEndpointConnection("privateEndpointConnection", {
    peConnectionName: "privateendpt1938mastersit9007pe.4f2f2970-0bfa-45d4-9ee1-d9f79502fc6f",
    resourceGroupName: "ayagrawrg",
    siteName: "privateendpt1938mastersite",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_endpoint_connection = azure_native.offazure.PrivateEndpointConnection("privateEndpointConnection",
    pe_connection_name="privateendpt1938mastersit9007pe.4f2f2970-0bfa-45d4-9ee1-d9f79502fc6f",
    resource_group_name="ayagrawrg",
    site_name="privateendpt1938mastersite")

```

```yaml
resources:
  privateEndpointConnection:
    type: azure-native:offazure:PrivateEndpointConnection
    properties:
      peConnectionName: privateendpt1938mastersit9007pe.4f2f2970-0bfa-45d4-9ee1-d9f79502fc6f
      resourceGroupName: ayagrawrg
      siteName: privateendpt1938mastersite

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:offazure:PrivateEndpointConnection privateendpt1938mastersit9007pe.4f2f2970-0bfa-45d4-9ee1-d9f79502fc6f /subscriptions/4bd2aa0f-2bd2-4d67-91a8-5a4533d58600/resourceGroups/ayagrawrg/providers/Microsoft.OffAzure/MasterSites/privateendpt1938mastersite/privateEndpointConnections/privateendpt1938mastersit9007pe.4f2f2970-0bfa-45d4-9ee1-d9f79502fc6f 
```
