SSL certificate for an app.
API Version: 2022-09-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create Or Update Certificate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var certificate = new AzureNative.Web.Certificate("certificate", new()
    {
        HostNames = new[]
        {
            "ServerCert",
        },
        Location = "East US",
        Name = "testc6282",
        Password = "<password>",
        ResourceGroupName = "testrg123",
    });

});


```

```go
package main

import (
	web "github.com/pulumi/pulumi-azure-native-sdk/web"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := web.NewCertificate(ctx, "certificate", &web.CertificateArgs{
			HostNames: pulumi.StringArray{
				pulumi.String("ServerCert"),
			},
			Location:          pulumi.String("East US"),
			Name:              pulumi.String("testc6282"),
			Password:          pulumi.String("<password>"),
			ResourceGroupName: pulumi.String("testrg123"),
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
import com.pulumi.azurenative.web.Certificate;
import com.pulumi.azurenative.web.CertificateArgs;
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
            .hostNames("ServerCert")
            .location("East US")
            .name("testc6282")
            .password("<password>")
            .resourceGroupName("testrg123")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const certificate = new azure_native.web.Certificate("certificate", {
    hostNames: ["ServerCert"],
    location: "East US",
    name: "testc6282",
    password: "<password>",
    resourceGroupName: "testrg123",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

certificate = azure_native.web.Certificate("certificate",
    host_names=["ServerCert"],
    location="East US",
    name="testc6282",
    password="<password>",
    resource_group_name="testrg123")

```

```yaml
resources:
  certificate:
    type: azure-native:web:Certificate
    properties:
      hostNames:
        - ServerCert
      location: East US
      name: testc6282
      password: <password>
      resourceGroupName: testrg123

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:web:Certificate testc6282 /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.Web/certificates/testc6282 
```
