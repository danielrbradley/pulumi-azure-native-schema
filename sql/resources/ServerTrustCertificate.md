Server trust certificate imported from box to enable connection between box and Sql Managed Instance.
API Version: 2021-11-01.
Previous API Version: 2021-05-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create server trust certificate.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var serverTrustCertificate = new AzureNative.Sql.ServerTrustCertificate("serverTrustCertificate", new()
    {
        CertificateName = "customerCertificateName",
        ManagedInstanceName = "testcl",
        PublicBlob = "308203AE30820296A0030201020210",
        ResourceGroupName = "testrg",
    });

});


```

```go
package main

import (
	sql "github.com/pulumi/pulumi-azure-native-sdk/sql"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := sql.NewServerTrustCertificate(ctx, "serverTrustCertificate", &sql.ServerTrustCertificateArgs{
			CertificateName:     pulumi.String("customerCertificateName"),
			ManagedInstanceName: pulumi.String("testcl"),
			PublicBlob:          pulumi.String("308203AE30820296A0030201020210"),
			ResourceGroupName:   pulumi.String("testrg"),
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
import com.pulumi.azurenative.sql.ServerTrustCertificate;
import com.pulumi.azurenative.sql.ServerTrustCertificateArgs;
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
        var serverTrustCertificate = new ServerTrustCertificate("serverTrustCertificate", ServerTrustCertificateArgs.builder()        
            .certificateName("customerCertificateName")
            .managedInstanceName("testcl")
            .publicBlob("308203AE30820296A0030201020210")
            .resourceGroupName("testrg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const serverTrustCertificate = new azure_native.sql.ServerTrustCertificate("serverTrustCertificate", {
    certificateName: "customerCertificateName",
    managedInstanceName: "testcl",
    publicBlob: "308203AE30820296A0030201020210",
    resourceGroupName: "testrg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

server_trust_certificate = azure_native.sql.ServerTrustCertificate("serverTrustCertificate",
    certificate_name="customerCertificateName",
    managed_instance_name="testcl",
    public_blob="308203AE30820296A0030201020210",
    resource_group_name="testrg")

```

```yaml
resources:
  serverTrustCertificate:
    type: azure-native:sql:ServerTrustCertificate
    properties:
      certificateName: customerCertificateName
      managedInstanceName: testcl
      publicBlob: 308203AE30820296A0030201020210
      resourceGroupName: testrg

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:sql:ServerTrustCertificate customerCertificateName /subscriptions/0574222d-5c7f-489c-a172-b3013eafab53/resourceGroups/testrg/providers/Microsoft.Sql/managedInstances/testcl/serverTrustCertificates/customerCertificateName 
```
