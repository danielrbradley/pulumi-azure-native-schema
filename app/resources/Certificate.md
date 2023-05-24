Certificate used for Custom Domain bindings of Container Apps in a Managed Environment
API Version: 2022-10-01.
Previous API Version: 2022-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or Update Certificate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var certificate = new AzureNative.App.Certificate("certificate", new()
    {
        CertificateName = "certificate-firendly-name",
        EnvironmentName = "testcontainerenv",
        Location = "East US",
        Properties = new AzureNative.App.Inputs.CertificatePropertiesArgs
        {
            Password = "private key password",
            Value = "Y2VydA==",
        },
        ResourceGroupName = "examplerg",
    });

});


```

```go
package main

import (
	app "github.com/pulumi/pulumi-azure-native-sdk/app"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := app.NewCertificate(ctx, "certificate", &app.CertificateArgs{
			CertificateName: pulumi.String("certificate-firendly-name"),
			EnvironmentName: pulumi.String("testcontainerenv"),
			Location:        pulumi.String("East US"),
			Properties: &app.CertificatePropertiesArgs{
				Password: pulumi.String("private key password"),
				Value:    pulumi.String("Y2VydA=="),
			},
			ResourceGroupName: pulumi.String("examplerg"),
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
import com.pulumi.azurenative.app.Certificate;
import com.pulumi.azurenative.app.CertificateArgs;
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
            .certificateName("certificate-firendly-name")
            .environmentName("testcontainerenv")
            .location("East US")
            .properties(Map.ofEntries(
                Map.entry("password", "private key password"),
                Map.entry("value", "Y2VydA==")
            ))
            .resourceGroupName("examplerg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const certificate = new azure_native.app.Certificate("certificate", {
    certificateName: "certificate-firendly-name",
    environmentName: "testcontainerenv",
    location: "East US",
    properties: {
        password: "private key password",
        value: "Y2VydA==",
    },
    resourceGroupName: "examplerg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

certificate = azure_native.app.Certificate("certificate",
    certificate_name="certificate-firendly-name",
    environment_name="testcontainerenv",
    location="East US",
    properties=azure_native.app.CertificatePropertiesArgs(
        password="private key password",
        value="Y2VydA==",
    ),
    resource_group_name="examplerg")

```

```yaml
resources:
  certificate:
    type: azure-native:app:Certificate
    properties:
      certificateName: certificate-firendly-name
      environmentName: testcontainerenv
      location: East US
      properties:
        password: private key password
        value: Y2VydA==
      resourceGroupName: examplerg

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:app:Certificate myresource1 /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/examplerg/providers/Microsoft.App/managedEnvironments/testcontainerenv/certificate-firendly-name 
```
