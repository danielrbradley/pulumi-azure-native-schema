An environment for Kubernetes cluster specialized for web workloads by Azure App Service
API Version: 2022-10-01.

{{% examples %}}
## Example Usage
{{% example %}}
### Create kube environments
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var connectedEnvironment = new AzureNative.App.ConnectedEnvironment("connectedEnvironment", new()
    {
        ConnectedEnvironmentName = "testenv",
        CustomDomainConfiguration = new AzureNative.App.Inputs.CustomDomainConfigurationArgs
        {
            CertificatePassword = "private key password",
            CertificateValue = "Y2VydA==",
            DnsSuffix = "www.my-name.com",
        },
        DaprAIConnectionString = "InstrumentationKey=00000000-0000-0000-0000-000000000000;IngestionEndpoint=https://northcentralus-0.in.applicationinsights.azure.com/",
        ExtendedLocation = new AzureNative.App.Inputs.ExtendedLocationArgs
        {
            Name = "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/examplerg/providers/Microsoft.ExtendedLocation/customLocations/testcustomlocation",
            Type = "CustomLocation",
        },
        Location = "East US",
        ResourceGroupName = "examplerg",
        StaticIp = "1.2.3.4",
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
		_, err := app.NewConnectedEnvironment(ctx, "connectedEnvironment", &app.ConnectedEnvironmentArgs{
			ConnectedEnvironmentName: pulumi.String("testenv"),
			CustomDomainConfiguration: &app.CustomDomainConfigurationArgs{
				CertificatePassword: pulumi.String("private key password"),
				CertificateValue:    pulumi.String("Y2VydA=="),
				DnsSuffix:           pulumi.String("www.my-name.com"),
			},
			DaprAIConnectionString: pulumi.String("InstrumentationKey=00000000-0000-0000-0000-000000000000;IngestionEndpoint=https://northcentralus-0.in.applicationinsights.azure.com/"),
			ExtendedLocation: &app.ExtendedLocationArgs{
				Name: pulumi.String("/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/examplerg/providers/Microsoft.ExtendedLocation/customLocations/testcustomlocation"),
				Type: pulumi.String("CustomLocation"),
			},
			Location:          pulumi.String("East US"),
			ResourceGroupName: pulumi.String("examplerg"),
			StaticIp:          pulumi.String("1.2.3.4"),
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
import com.pulumi.azurenative.app.ConnectedEnvironment;
import com.pulumi.azurenative.app.ConnectedEnvironmentArgs;
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
        var connectedEnvironment = new ConnectedEnvironment("connectedEnvironment", ConnectedEnvironmentArgs.builder()        
            .connectedEnvironmentName("testenv")
            .customDomainConfiguration(Map.ofEntries(
                Map.entry("certificatePassword", "private key password"),
                Map.entry("certificateValue", "Y2VydA=="),
                Map.entry("dnsSuffix", "www.my-name.com")
            ))
            .daprAIConnectionString("InstrumentationKey=00000000-0000-0000-0000-000000000000;IngestionEndpoint=https://northcentralus-0.in.applicationinsights.azure.com/")
            .extendedLocation(Map.ofEntries(
                Map.entry("name", "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/examplerg/providers/Microsoft.ExtendedLocation/customLocations/testcustomlocation"),
                Map.entry("type", "CustomLocation")
            ))
            .location("East US")
            .resourceGroupName("examplerg")
            .staticIp("1.2.3.4")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const connectedEnvironment = new azure_native.app.ConnectedEnvironment("connectedEnvironment", {
    connectedEnvironmentName: "testenv",
    customDomainConfiguration: {
        certificatePassword: "private key password",
        certificateValue: "Y2VydA==",
        dnsSuffix: "www.my-name.com",
    },
    daprAIConnectionString: "InstrumentationKey=00000000-0000-0000-0000-000000000000;IngestionEndpoint=https://northcentralus-0.in.applicationinsights.azure.com/",
    extendedLocation: {
        name: "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/examplerg/providers/Microsoft.ExtendedLocation/customLocations/testcustomlocation",
        type: "CustomLocation",
    },
    location: "East US",
    resourceGroupName: "examplerg",
    staticIp: "1.2.3.4",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

connected_environment = azure_native.app.ConnectedEnvironment("connectedEnvironment",
    connected_environment_name="testenv",
    custom_domain_configuration=azure_native.app.CustomDomainConfigurationArgs(
        certificate_password="private key password",
        certificate_value="Y2VydA==",
        dns_suffix="www.my-name.com",
    ),
    dapr_ai_connection_string="InstrumentationKey=00000000-0000-0000-0000-000000000000;IngestionEndpoint=https://northcentralus-0.in.applicationinsights.azure.com/",
    extended_location=azure_native.app.ExtendedLocationArgs(
        name="/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/examplerg/providers/Microsoft.ExtendedLocation/customLocations/testcustomlocation",
        type="CustomLocation",
    ),
    location="East US",
    resource_group_name="examplerg",
    static_ip="1.2.3.4")

```

```yaml
resources:
  connectedEnvironment:
    type: azure-native:app:ConnectedEnvironment
    properties:
      connectedEnvironmentName: testenv
      customDomainConfiguration:
        certificatePassword: private key password
        certificateValue: Y2VydA==
        dnsSuffix: www.my-name.com
      daprAIConnectionString: InstrumentationKey=00000000-0000-0000-0000-000000000000;IngestionEndpoint=https://northcentralus-0.in.applicationinsights.azure.com/
      extendedLocation:
        name: /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/examplerg/providers/Microsoft.ExtendedLocation/customLocations/testcustomlocation
        type: CustomLocation
      location: East US
      resourceGroupName: examplerg
      staticIp: 1.2.3.4

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:app:ConnectedEnvironment testenv /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/examplerg/providers/Microsoft.App/connectedEnvironments/testenv 
```
