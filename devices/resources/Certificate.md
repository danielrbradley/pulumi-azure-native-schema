The X509 Certificate.
API Version: 2021-07-02.
Previous API Version: 2020-08-31. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Certificates_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var certificate = new AzureNative.Devices.Certificate("certificate", new()
    {
        CertificateName = "cert",
        Properties = new AzureNative.Devices.Inputs.CertificatePropertiesArgs
        {
            Certificate = "############################################",
        },
        ResourceGroupName = "myResourceGroup",
        ResourceName = "iothub",
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
		_, err := devices.NewCertificate(ctx, "certificate", &devices.CertificateArgs{
			CertificateName: pulumi.String("cert"),
			Properties: &devices.CertificatePropertiesArgs{
				Certificate: pulumi.String("############################################"),
			},
			ResourceGroupName: pulumi.String("myResourceGroup"),
			ResourceName:      pulumi.String("iothub"),
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
import com.pulumi.azurenative.devices.Certificate;
import com.pulumi.azurenative.devices.CertificateArgs;
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
        var certificate = new Certificate("certificate", CertificateArgs.builder()        
            .certificateName("cert")
            .properties(Map.of("certificate", "############################################"))
            .resourceGroupName("myResourceGroup")
            .resourceName("iothub")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const certificate = new azure_native.devices.Certificate("certificate", {
    certificateName: "cert",
    properties: {
        certificate: "############################################",
    },
    resourceGroupName: "myResourceGroup",
    resourceName: "iothub",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

certificate = azure_native.devices.Certificate("certificate",
    certificate_name="cert",
    properties=azure_native.devices.CertificatePropertiesArgs(
        certificate="############################################",
    ),
    resource_group_name="myResourceGroup",
    resource_name_="iothub")

```

```yaml
resources:
  certificate:
    type: azure-native:devices:Certificate
    properties:
      certificateName: cert
      properties:
        certificate: '############################################'
      resourceGroupName: myResourceGroup
      resourceName: iothub

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:devices:Certificate cert /subscriptions/91d12660-3dec-467a-be2a-213b5544ddc0/resourceGroups/myResourceGroup/providers/Microsoft.Devices/ProvisioningServives/myFirstProvisioningService/certificates/cert 
```
