Gateway certificate authority details.
API Version: 2022-08-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ApiManagementCreateGatewayCertificateAuthority
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var gatewayCertificateAuthority = new AzureNative.ApiManagement.GatewayCertificateAuthority("gatewayCertificateAuthority", new()
    {
        CertificateId = "cert1",
        GatewayId = "gw1",
        IsTrusted = false,
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
    });

});


```

```go
package main

import (
	apimanagement "github.com/pulumi/pulumi-azure-native-sdk/apimanagement"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := apimanagement.NewGatewayCertificateAuthority(ctx, "gatewayCertificateAuthority", &apimanagement.GatewayCertificateAuthorityArgs{
			CertificateId:     pulumi.String("cert1"),
			GatewayId:         pulumi.String("gw1"),
			IsTrusted:         pulumi.Bool(false),
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("apimService1"),
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
import com.pulumi.azurenative.apimanagement.GatewayCertificateAuthority;
import com.pulumi.azurenative.apimanagement.GatewayCertificateAuthorityArgs;
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
        var gatewayCertificateAuthority = new GatewayCertificateAuthority("gatewayCertificateAuthority", GatewayCertificateAuthorityArgs.builder()        
            .certificateId("cert1")
            .gatewayId("gw1")
            .isTrusted(false)
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const gatewayCertificateAuthority = new azure_native.apimanagement.GatewayCertificateAuthority("gatewayCertificateAuthority", {
    certificateId: "cert1",
    gatewayId: "gw1",
    isTrusted: false,
    resourceGroupName: "rg1",
    serviceName: "apimService1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

gateway_certificate_authority = azure_native.apimanagement.GatewayCertificateAuthority("gatewayCertificateAuthority",
    certificate_id="cert1",
    gateway_id="gw1",
    is_trusted=False,
    resource_group_name="rg1",
    service_name="apimService1")

```

```yaml
resources:
  gatewayCertificateAuthority:
    type: azure-native:apimanagement:GatewayCertificateAuthority
    properties:
      certificateId: cert1
      gatewayId: gw1
      isTrusted: false
      resourceGroupName: rg1
      serviceName: apimService1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:apimanagement:GatewayCertificateAuthority cert1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/gateways/gw1/certificateAuthorities/cert1 
```
