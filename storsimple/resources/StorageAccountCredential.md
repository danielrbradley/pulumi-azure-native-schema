The storage account credential.
API Version: 2017-06-01.
Previous API Version: 2017-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### StorageAccountCredentialsCreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var storageAccountCredential = new AzureNative.StorSimple.StorageAccountCredential("storageAccountCredential", new()
    {
        AccessKey = new AzureNative.StorSimple.Inputs.AsymmetricEncryptedSecretArgs
        {
            EncryptionAlgorithm = AzureNative.StorSimple.EncryptionAlgorithm.RSAES_PKCS1_v_1_5,
            EncryptionCertThumbprint = "A872A2DF196AC7682EE24791E7DE2E2A360F5926",
            Value = "ATuJSkmrFk4h8r1jrZ4nd3nthLSddcguEO5QLO/NECUtTuB9kL4dNv3/jC4WOvFkeVr3x1UvfhlIeMmJBF1SMr6hR1JzD0xNU/TtQqUeXN7V3jk7I+2l67P9StuHWR6OMd3XOLwvznxOEQtEWpweDiobZU1ZiY03WafcGZFpV5j6tEoHeopoZ1J/GhPtkYmx+TqxzUN6qnir5rP3NSYiZciImP/qu8U9yUV/xpVRv39KvFc2Yr5SpKpMMRUj55XW10UnPer63M6KovF8X9Wi/fNnrZAs1Esl5XddZETGrW/e5B++VMJ6w0Q/uvPR+UBwrOU0804l0SzwdIe3qVVd0Q==",
        },
        EndPoint = "blob.core.windows.net",
        ManagerName = "ManagerForSDKTest1",
        ResourceGroupName = "ResourceGroupForSDKTest",
        SslStatus = AzureNative.StorSimple.SslStatus.Enabled,
        StorageAccountCredentialName = "SACForTest",
    });

});


```

```go
package main

import (
	storsimple "github.com/pulumi/pulumi-azure-native-sdk/storsimple"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := storsimple.NewStorageAccountCredential(ctx, "storageAccountCredential", &storsimple.StorageAccountCredentialArgs{
			AccessKey: &storsimple.AsymmetricEncryptedSecretArgs{
				EncryptionAlgorithm:      storsimple.EncryptionAlgorithm_RSAES_PKCS1_v_1_5,
				EncryptionCertThumbprint: pulumi.String("A872A2DF196AC7682EE24791E7DE2E2A360F5926"),
				Value:                    pulumi.String("ATuJSkmrFk4h8r1jrZ4nd3nthLSddcguEO5QLO/NECUtTuB9kL4dNv3/jC4WOvFkeVr3x1UvfhlIeMmJBF1SMr6hR1JzD0xNU/TtQqUeXN7V3jk7I+2l67P9StuHWR6OMd3XOLwvznxOEQtEWpweDiobZU1ZiY03WafcGZFpV5j6tEoHeopoZ1J/GhPtkYmx+TqxzUN6qnir5rP3NSYiZciImP/qu8U9yUV/xpVRv39KvFc2Yr5SpKpMMRUj55XW10UnPer63M6KovF8X9Wi/fNnrZAs1Esl5XddZETGrW/e5B++VMJ6w0Q/uvPR+UBwrOU0804l0SzwdIe3qVVd0Q=="),
			},
			EndPoint:                     pulumi.String("blob.core.windows.net"),
			ManagerName:                  pulumi.String("ManagerForSDKTest1"),
			ResourceGroupName:            pulumi.String("ResourceGroupForSDKTest"),
			SslStatus:                    storsimple.SslStatusEnabled,
			StorageAccountCredentialName: pulumi.String("SACForTest"),
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
import com.pulumi.azurenative.storsimple.StorageAccountCredential;
import com.pulumi.azurenative.storsimple.StorageAccountCredentialArgs;
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
        var storageAccountCredential = new StorageAccountCredential("storageAccountCredential", StorageAccountCredentialArgs.builder()        
            .accessKey(Map.ofEntries(
                Map.entry("encryptionAlgorithm", "RSAES_PKCS1_v_1_5"),
                Map.entry("encryptionCertThumbprint", "A872A2DF196AC7682EE24791E7DE2E2A360F5926"),
                Map.entry("value", "ATuJSkmrFk4h8r1jrZ4nd3nthLSddcguEO5QLO/NECUtTuB9kL4dNv3/jC4WOvFkeVr3x1UvfhlIeMmJBF1SMr6hR1JzD0xNU/TtQqUeXN7V3jk7I+2l67P9StuHWR6OMd3XOLwvznxOEQtEWpweDiobZU1ZiY03WafcGZFpV5j6tEoHeopoZ1J/GhPtkYmx+TqxzUN6qnir5rP3NSYiZciImP/qu8U9yUV/xpVRv39KvFc2Yr5SpKpMMRUj55XW10UnPer63M6KovF8X9Wi/fNnrZAs1Esl5XddZETGrW/e5B++VMJ6w0Q/uvPR+UBwrOU0804l0SzwdIe3qVVd0Q==")
            ))
            .endPoint("blob.core.windows.net")
            .managerName("ManagerForSDKTest1")
            .resourceGroupName("ResourceGroupForSDKTest")
            .sslStatus("Enabled")
            .storageAccountCredentialName("SACForTest")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const storageAccountCredential = new azure_native.storsimple.StorageAccountCredential("storageAccountCredential", {
    accessKey: {
        encryptionAlgorithm: azure_native.storsimple.EncryptionAlgorithm.RSAES_PKCS1_v_1_5,
        encryptionCertThumbprint: "A872A2DF196AC7682EE24791E7DE2E2A360F5926",
        value: "ATuJSkmrFk4h8r1jrZ4nd3nthLSddcguEO5QLO/NECUtTuB9kL4dNv3/jC4WOvFkeVr3x1UvfhlIeMmJBF1SMr6hR1JzD0xNU/TtQqUeXN7V3jk7I+2l67P9StuHWR6OMd3XOLwvznxOEQtEWpweDiobZU1ZiY03WafcGZFpV5j6tEoHeopoZ1J/GhPtkYmx+TqxzUN6qnir5rP3NSYiZciImP/qu8U9yUV/xpVRv39KvFc2Yr5SpKpMMRUj55XW10UnPer63M6KovF8X9Wi/fNnrZAs1Esl5XddZETGrW/e5B++VMJ6w0Q/uvPR+UBwrOU0804l0SzwdIe3qVVd0Q==",
    },
    endPoint: "blob.core.windows.net",
    managerName: "ManagerForSDKTest1",
    resourceGroupName: "ResourceGroupForSDKTest",
    sslStatus: azure_native.storsimple.SslStatus.Enabled,
    storageAccountCredentialName: "SACForTest",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

storage_account_credential = azure_native.storsimple.StorageAccountCredential("storageAccountCredential",
    access_key=azure_native.storsimple.AsymmetricEncryptedSecretArgs(
        encryption_algorithm=azure_native.storsimple.EncryptionAlgorithm.RSAE_S_PKCS1_V_1_5,
        encryption_cert_thumbprint="A872A2DF196AC7682EE24791E7DE2E2A360F5926",
        value="ATuJSkmrFk4h8r1jrZ4nd3nthLSddcguEO5QLO/NECUtTuB9kL4dNv3/jC4WOvFkeVr3x1UvfhlIeMmJBF1SMr6hR1JzD0xNU/TtQqUeXN7V3jk7I+2l67P9StuHWR6OMd3XOLwvznxOEQtEWpweDiobZU1ZiY03WafcGZFpV5j6tEoHeopoZ1J/GhPtkYmx+TqxzUN6qnir5rP3NSYiZciImP/qu8U9yUV/xpVRv39KvFc2Yr5SpKpMMRUj55XW10UnPer63M6KovF8X9Wi/fNnrZAs1Esl5XddZETGrW/e5B++VMJ6w0Q/uvPR+UBwrOU0804l0SzwdIe3qVVd0Q==",
    ),
    end_point="blob.core.windows.net",
    manager_name="ManagerForSDKTest1",
    resource_group_name="ResourceGroupForSDKTest",
    ssl_status=azure_native.storsimple.SslStatus.ENABLED,
    storage_account_credential_name="SACForTest")

```

```yaml
resources:
  storageAccountCredential:
    type: azure-native:storsimple:StorageAccountCredential
    properties:
      accessKey:
        encryptionAlgorithm: RSAES_PKCS1_v_1_5
        encryptionCertThumbprint: A872A2DF196AC7682EE24791E7DE2E2A360F5926
        value: ATuJSkmrFk4h8r1jrZ4nd3nthLSddcguEO5QLO/NECUtTuB9kL4dNv3/jC4WOvFkeVr3x1UvfhlIeMmJBF1SMr6hR1JzD0xNU/TtQqUeXN7V3jk7I+2l67P9StuHWR6OMd3XOLwvznxOEQtEWpweDiobZU1ZiY03WafcGZFpV5j6tEoHeopoZ1J/GhPtkYmx+TqxzUN6qnir5rP3NSYiZciImP/qu8U9yUV/xpVRv39KvFc2Yr5SpKpMMRUj55XW10UnPer63M6KovF8X9Wi/fNnrZAs1Esl5XddZETGrW/e5B++VMJ6w0Q/uvPR+UBwrOU0804l0SzwdIe3qVVd0Q==
      endPoint: blob.core.windows.net
      managerName: ManagerForSDKTest1
      resourceGroupName: ResourceGroupForSDKTest
      sslStatus: Enabled
      storageAccountCredentialName: SACForTest

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:storsimple:StorageAccountCredential SACForTest /subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/ResourceGroupForSDKTest/providers/Microsoft.StorSimple/managers/ManagerForSDKTest1/storageAccountCredentials/SACForTest 
```
