Gateway hostname configuration details.
API Version: 2022-08-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ApiManagementCreateGatewayHostnameConfiguration
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var gatewayHostnameConfiguration = new AzureNative.ApiManagement.GatewayHostnameConfiguration("gatewayHostnameConfiguration", new()
    {
        CertificateId = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/certificates/cert1",
        GatewayId = "gw1",
        HcId = "default",
        Hostname = "*",
        Http2Enabled = true,
        NegotiateClientCertificate = false,
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
        Tls10Enabled = false,
        Tls11Enabled = false,
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
		_, err := apimanagement.NewGatewayHostnameConfiguration(ctx, "gatewayHostnameConfiguration", &apimanagement.GatewayHostnameConfigurationArgs{
			CertificateId:              pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/certificates/cert1"),
			GatewayId:                  pulumi.String("gw1"),
			HcId:                       pulumi.String("default"),
			Hostname:                   pulumi.String("*"),
			Http2Enabled:               pulumi.Bool(true),
			NegotiateClientCertificate: pulumi.Bool(false),
			ResourceGroupName:          pulumi.String("rg1"),
			ServiceName:                pulumi.String("apimService1"),
			Tls10Enabled:               pulumi.Bool(false),
			Tls11Enabled:               pulumi.Bool(false),
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
import com.pulumi.azurenative.apimanagement.GatewayHostnameConfiguration;
import com.pulumi.azurenative.apimanagement.GatewayHostnameConfigurationArgs;
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
        var gatewayHostnameConfiguration = new GatewayHostnameConfiguration("gatewayHostnameConfiguration", GatewayHostnameConfigurationArgs.builder()        
            .certificateId("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/certificates/cert1")
            .gatewayId("gw1")
            .hcId("default")
            .hostname("*")
            .http2Enabled(true)
            .negotiateClientCertificate(false)
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .tls10Enabled(false)
            .tls11Enabled(false)
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const gatewayHostnameConfiguration = new azure_native.apimanagement.GatewayHostnameConfiguration("gatewayHostnameConfiguration", {
    certificateId: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/certificates/cert1",
    gatewayId: "gw1",
    hcId: "default",
    hostname: "*",
    http2Enabled: true,
    negotiateClientCertificate: false,
    resourceGroupName: "rg1",
    serviceName: "apimService1",
    tls10Enabled: false,
    tls11Enabled: false,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

gateway_hostname_configuration = azure_native.apimanagement.GatewayHostnameConfiguration("gatewayHostnameConfiguration",
    certificate_id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/certificates/cert1",
    gateway_id="gw1",
    hc_id="default",
    hostname="*",
    http2_enabled=True,
    negotiate_client_certificate=False,
    resource_group_name="rg1",
    service_name="apimService1",
    tls10_enabled=False,
    tls11_enabled=False)

```

```yaml
resources:
  gatewayHostnameConfiguration:
    type: azure-native:apimanagement:GatewayHostnameConfiguration
    properties:
      certificateId: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/certificates/cert1
      gatewayId: gw1
      hcId: default
      hostname: '*'
      http2Enabled: true
      negotiateClientCertificate: false
      resourceGroupName: rg1
      serviceName: apimService1
      tls10Enabled: false
      tls11Enabled: false

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:apimanagement:GatewayHostnameConfiguration default /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/gateways/gw1/hostnameConfigurations/default 
```
