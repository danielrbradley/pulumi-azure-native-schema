The X509 Certificate.
API Version: 2022-12-12.
Previous API Version: 2020-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### DPSCreateOrUpdateCertificate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var dpsCertificate = new AzureNative.Devices.DpsCertificate("dpsCertificate", new()
    {
        CertificateName = "cert",
        Properties = new AzureNative.Devices.Inputs.CertificatePropertiesArgs
        {
            Certificate = "MA==",
        },
        ProvisioningServiceName = "myFirstProvisioningService",
        ResourceGroupName = "myResourceGroup",
    });

});


```

```go
package main

import (
	devices "github.com/pulumi/pulumi-azure-native-sdk/devices"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := devices.NewDpsCertificate(ctx, "dpsCertificate", &devices.DpsCertificateArgs{
			CertificateName: pulumi.String("cert"),
			Properties: &devices.CertificatePropertiesArgs{
				Certificate: pulumi.String("MA=="),
			},
			ProvisioningServiceName: pulumi.String("myFirstProvisioningService"),
			ResourceGroupName:       pulumi.String("myResourceGroup"),
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
import com.pulumi.azurenative.devices.DpsCertificate;
import com.pulumi.azurenative.devices.DpsCertificateArgs;
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
        var dpsCertificate = new DpsCertificate("dpsCertificate", DpsCertificateArgs.builder()        
            .certificateName("cert")
            .properties(Map.of("certificate", "MA=="))
            .provisioningServiceName("myFirstProvisioningService")
            .resourceGroupName("myResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const dpsCertificate = new azure_native.devices.DpsCertificate("dpsCertificate", {
    certificateName: "cert",
    properties: {
        certificate: "MA==",
    },
    provisioningServiceName: "myFirstProvisioningService",
    resourceGroupName: "myResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

dps_certificate = azure_native.devices.DpsCertificate("dpsCertificate",
    certificate_name="cert",
    properties=azure_native.devices.CertificatePropertiesArgs(
        certificate="MA==",
    ),
    provisioning_service_name="myFirstProvisioningService",
    resource_group_name="myResourceGroup")

```

```yaml
resources:
  dpsCertificate:
    type: azure-native:devices:DpsCertificate
    properties:
      certificateName: cert
      properties:
        certificate: MA==
      provisioningServiceName: myFirstProvisioningService
      resourceGroupName: myResourceGroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:devices:DpsCertificate cert /subscriptions/91d12660-3dec-467a-be2a-213b5544ddc0/resourceGroups/myResourceGroup/providers/Microsoft.Devices/ProvisioningServives/myFirstProvisioningService/certificates/cert 
```
