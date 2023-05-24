Definition of the certificate.
API Version: 2022-08-08.
Previous API Version: 2019-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a certificate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var certificate = new AzureNative.Automation.Certificate("certificate", new()
    {
        AutomationAccountName = "myAutomationAccount18",
        Base64Value = "base 64 value of cert",
        CertificateName = "testCert",
        Description = "Sample Cert",
        IsExportable = false,
        Name = "testCert",
        ResourceGroupName = "rg",
        Thumbprint = "thumbprint of cert",
    });

});


```

```go
package main

import (
	automation "github.com/pulumi/pulumi-azure-native-sdk/automation"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := automation.NewCertificate(ctx, "certificate", &automation.CertificateArgs{
			AutomationAccountName: pulumi.String("myAutomationAccount18"),
			Base64Value:           pulumi.String("base 64 value of cert"),
			CertificateName:       pulumi.String("testCert"),
			Description:           pulumi.String("Sample Cert"),
			IsExportable:          pulumi.Bool(false),
			Name:                  pulumi.String("testCert"),
			ResourceGroupName:     pulumi.String("rg"),
			Thumbprint:            pulumi.String("thumbprint of cert"),
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
import com.pulumi.azurenative.automation.Certificate;
import com.pulumi.azurenative.automation.CertificateArgs;
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
            .automationAccountName("myAutomationAccount18")
            .base64Value("base 64 value of cert")
            .certificateName("testCert")
            .description("Sample Cert")
            .isExportable(false)
            .name("testCert")
            .resourceGroupName("rg")
            .thumbprint("thumbprint of cert")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const certificate = new azure_native.automation.Certificate("certificate", {
    automationAccountName: "myAutomationAccount18",
    base64Value: "base 64 value of cert",
    certificateName: "testCert",
    description: "Sample Cert",
    isExportable: false,
    name: "testCert",
    resourceGroupName: "rg",
    thumbprint: "thumbprint of cert",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

certificate = azure_native.automation.Certificate("certificate",
    automation_account_name="myAutomationAccount18",
    base64_value="base 64 value of cert",
    certificate_name="testCert",
    description="Sample Cert",
    is_exportable=False,
    name="testCert",
    resource_group_name="rg",
    thumbprint="thumbprint of cert")

```

```yaml
resources:
  certificate:
    type: azure-native:automation:Certificate
    properties:
      automationAccountName: myAutomationAccount18
      base64Value: base 64 value of cert
      certificateName: testCert
      description: Sample Cert
      isExportable: false
      name: testCert
      resourceGroupName: rg
      thumbprint: thumbprint of cert

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:automation:Certificate testCert /subscriptions/subid/resourceGroups/rg/providers/Microsoft.Automation/automationAccounts/myAutomationAccount33/certificates/testCert 
```
