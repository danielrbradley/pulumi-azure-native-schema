Certificate details.
API Version: 2022-08-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ApiManagementCreateCertificate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var certificate = new AzureNative.ApiManagement.Certificate("certificate", new()
    {
        CertificateId = "tempcert",
        Data = "****************Base 64 Encoded Certificate *******************************",
        Password = "****Certificate Password******",
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
		_, err := apimanagement.NewCertificate(ctx, "certificate", &apimanagement.CertificateArgs{
			CertificateId:     pulumi.String("tempcert"),
			Data:              pulumi.String("****************Base 64 Encoded Certificate *******************************"),
			Password:          pulumi.String("****Certificate Password******"),
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
import com.pulumi.azurenative.apimanagement.Certificate;
import com.pulumi.azurenative.apimanagement.CertificateArgs;
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
            .certificateId("tempcert")
            .data("****************Base 64 Encoded Certificate *******************************")
            .password("****Certificate Password******")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const certificate = new azure_native.apimanagement.Certificate("certificate", {
    certificateId: "tempcert",
    data: "****************Base 64 Encoded Certificate *******************************",
    password: "****Certificate Password******",
    resourceGroupName: "rg1",
    serviceName: "apimService1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

certificate = azure_native.apimanagement.Certificate("certificate",
    certificate_id="tempcert",
    data="****************Base 64 Encoded Certificate *******************************",
    password="****Certificate Password******",
    resource_group_name="rg1",
    service_name="apimService1")

```

```yaml
resources:
  certificate:
    type: azure-native:apimanagement:Certificate
    properties:
      certificateId: tempcert
      data: '****************Base 64 Encoded Certificate *******************************'
      password: '****Certificate Password******'
      resourceGroupName: rg1
      serviceName: apimService1

```

{{% /example %}}
{{% example %}}
### ApiManagementCreateCertificateWithKeyVault
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var certificate = new AzureNative.ApiManagement.Certificate("certificate", new()
    {
        CertificateId = "templateCertkv",
        KeyVault = new AzureNative.ApiManagement.Inputs.KeyVaultContractCreatePropertiesArgs
        {
            IdentityClientId = "ceaa6b06-c00f-43ef-99ac-f53d1fe876a0",
            SecretIdentifier = "https://rpbvtkeyvaultintegration.vault-int.azure-int.net/secrets/msitestingCert",
        },
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
		_, err := apimanagement.NewCertificate(ctx, "certificate", &apimanagement.CertificateArgs{
			CertificateId: pulumi.String("templateCertkv"),
			KeyVault: &apimanagement.KeyVaultContractCreatePropertiesArgs{
				IdentityClientId: pulumi.String("ceaa6b06-c00f-43ef-99ac-f53d1fe876a0"),
				SecretIdentifier: pulumi.String("https://rpbvtkeyvaultintegration.vault-int.azure-int.net/secrets/msitestingCert"),
			},
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
import com.pulumi.azurenative.apimanagement.Certificate;
import com.pulumi.azurenative.apimanagement.CertificateArgs;
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
            .certificateId("templateCertkv")
            .keyVault(Map.ofEntries(
                Map.entry("identityClientId", "ceaa6b06-c00f-43ef-99ac-f53d1fe876a0"),
                Map.entry("secretIdentifier", "https://rpbvtkeyvaultintegration.vault-int.azure-int.net/secrets/msitestingCert")
            ))
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const certificate = new azure_native.apimanagement.Certificate("certificate", {
    certificateId: "templateCertkv",
    keyVault: {
        identityClientId: "ceaa6b06-c00f-43ef-99ac-f53d1fe876a0",
        secretIdentifier: "https://rpbvtkeyvaultintegration.vault-int.azure-int.net/secrets/msitestingCert",
    },
    resourceGroupName: "rg1",
    serviceName: "apimService1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

certificate = azure_native.apimanagement.Certificate("certificate",
    certificate_id="templateCertkv",
    key_vault=azure_native.apimanagement.KeyVaultContractCreatePropertiesArgs(
        identity_client_id="ceaa6b06-c00f-43ef-99ac-f53d1fe876a0",
        secret_identifier="https://rpbvtkeyvaultintegration.vault-int.azure-int.net/secrets/msitestingCert",
    ),
    resource_group_name="rg1",
    service_name="apimService1")

```

```yaml
resources:
  certificate:
    type: azure-native:apimanagement:Certificate
    properties:
      certificateId: templateCertkv
      keyVault:
        identityClientId: ceaa6b06-c00f-43ef-99ac-f53d1fe876a0
        secretIdentifier: https://rpbvtkeyvaultintegration.vault-int.azure-int.net/secrets/msitestingCert
      resourceGroupName: rg1
      serviceName: apimService1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:apimanagement:Certificate templateCertkv /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/certificates/templateCertkv 
```
