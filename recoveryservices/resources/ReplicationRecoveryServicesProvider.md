Provider details.
API Version: 2023-02-01.
Previous API Version: 2018-07-10. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Adds a recovery services provider.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var replicationRecoveryServicesProvider = new AzureNative.RecoveryServices.ReplicationRecoveryServicesProvider("replicationRecoveryServicesProvider", new()
    {
        FabricName = "vmwarefabric1",
        Properties = new AzureNative.RecoveryServices.Inputs.AddRecoveryServicesProviderInputPropertiesArgs
        {
            AuthenticationIdentityInput = new AzureNative.RecoveryServices.Inputs.IdentityProviderInputArgs
            {
                AadAuthority = "https://login.microsoftonline.com",
                ApplicationId = "f66fce08-c0c6-47a1-beeb-0ede5ea94f90",
                Audience = "https://microsoft.onmicrosoft.com/cf19e349-644c-4c6a-bcae-9c8f35357874",
                ObjectId = "141360b8-5686-4240-a027-5e24e6affeba",
                TenantId = "72f988bf-86f1-41af-91ab-2d7cd011db47",
            },
            MachineName = "vmwareprovider1",
            ResourceAccessIdentityInput = new AzureNative.RecoveryServices.Inputs.IdentityProviderInputArgs
            {
                AadAuthority = "https://login.microsoftonline.com",
                ApplicationId = "f66fce08-c0c6-47a1-beeb-0ede5ea94f90",
                Audience = "https://microsoft.onmicrosoft.com/cf19e349-644c-4c6a-bcae-9c8f35357874",
                ObjectId = "141360b8-5686-4240-a027-5e24e6affeba",
                TenantId = "72f988bf-86f1-41af-91ab-2d7cd011db47",
            },
        },
        ProviderName = "vmwareprovider1",
        ResourceGroupName = "resourcegroup1",
        ResourceName = "migrationvault",
    });

});


```

```go
package main

import (
	recoveryservices "github.com/pulumi/pulumi-azure-native-sdk/recoveryservices"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := recoveryservices.NewReplicationRecoveryServicesProvider(ctx, "replicationRecoveryServicesProvider", &recoveryservices.ReplicationRecoveryServicesProviderArgs{
			FabricName: pulumi.String("vmwarefabric1"),
			Properties: recoveryservices.RecoveryServicesProviderPropertiesResponse{
				AuthenticationIdentityInput: &recoveryservices.IdentityProviderInputArgs{
					AadAuthority:  pulumi.String("https://login.microsoftonline.com"),
					ApplicationId: pulumi.String("f66fce08-c0c6-47a1-beeb-0ede5ea94f90"),
					Audience:      pulumi.String("https://microsoft.onmicrosoft.com/cf19e349-644c-4c6a-bcae-9c8f35357874"),
					ObjectId:      pulumi.String("141360b8-5686-4240-a027-5e24e6affeba"),
					TenantId:      pulumi.String("72f988bf-86f1-41af-91ab-2d7cd011db47"),
				},
				MachineName: pulumi.String("vmwareprovider1"),
				ResourceAccessIdentityInput: &recoveryservices.IdentityProviderInputArgs{
					AadAuthority:  pulumi.String("https://login.microsoftonline.com"),
					ApplicationId: pulumi.String("f66fce08-c0c6-47a1-beeb-0ede5ea94f90"),
					Audience:      pulumi.String("https://microsoft.onmicrosoft.com/cf19e349-644c-4c6a-bcae-9c8f35357874"),
					ObjectId:      pulumi.String("141360b8-5686-4240-a027-5e24e6affeba"),
					TenantId:      pulumi.String("72f988bf-86f1-41af-91ab-2d7cd011db47"),
				},
			},
			ProviderName:      pulumi.String("vmwareprovider1"),
			ResourceGroupName: pulumi.String("resourcegroup1"),
			ResourceName:      pulumi.String("migrationvault"),
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
import com.pulumi.azurenative.recoveryservices.ReplicationRecoveryServicesProvider;
import com.pulumi.azurenative.recoveryservices.ReplicationRecoveryServicesProviderArgs;
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
        var replicationRecoveryServicesProvider = new ReplicationRecoveryServicesProvider("replicationRecoveryServicesProvider", ReplicationRecoveryServicesProviderArgs.builder()        
            .fabricName("vmwarefabric1")
            .properties(Map.ofEntries(
                Map.entry("authenticationIdentityInput", Map.ofEntries(
                    Map.entry("aadAuthority", "https://login.microsoftonline.com"),
                    Map.entry("applicationId", "f66fce08-c0c6-47a1-beeb-0ede5ea94f90"),
                    Map.entry("audience", "https://microsoft.onmicrosoft.com/cf19e349-644c-4c6a-bcae-9c8f35357874"),
                    Map.entry("objectId", "141360b8-5686-4240-a027-5e24e6affeba"),
                    Map.entry("tenantId", "72f988bf-86f1-41af-91ab-2d7cd011db47")
                )),
                Map.entry("machineName", "vmwareprovider1"),
                Map.entry("resourceAccessIdentityInput", Map.ofEntries(
                    Map.entry("aadAuthority", "https://login.microsoftonline.com"),
                    Map.entry("applicationId", "f66fce08-c0c6-47a1-beeb-0ede5ea94f90"),
                    Map.entry("audience", "https://microsoft.onmicrosoft.com/cf19e349-644c-4c6a-bcae-9c8f35357874"),
                    Map.entry("objectId", "141360b8-5686-4240-a027-5e24e6affeba"),
                    Map.entry("tenantId", "72f988bf-86f1-41af-91ab-2d7cd011db47")
                ))
            ))
            .providerName("vmwareprovider1")
            .resourceGroupName("resourcegroup1")
            .resourceName("migrationvault")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const replicationRecoveryServicesProvider = new azure_native.recoveryservices.ReplicationRecoveryServicesProvider("replicationRecoveryServicesProvider", {
    fabricName: "vmwarefabric1",
    properties: {
        authenticationIdentityInput: {
            aadAuthority: "https://login.microsoftonline.com",
            applicationId: "f66fce08-c0c6-47a1-beeb-0ede5ea94f90",
            audience: "https://microsoft.onmicrosoft.com/cf19e349-644c-4c6a-bcae-9c8f35357874",
            objectId: "141360b8-5686-4240-a027-5e24e6affeba",
            tenantId: "72f988bf-86f1-41af-91ab-2d7cd011db47",
        },
        machineName: "vmwareprovider1",
        resourceAccessIdentityInput: {
            aadAuthority: "https://login.microsoftonline.com",
            applicationId: "f66fce08-c0c6-47a1-beeb-0ede5ea94f90",
            audience: "https://microsoft.onmicrosoft.com/cf19e349-644c-4c6a-bcae-9c8f35357874",
            objectId: "141360b8-5686-4240-a027-5e24e6affeba",
            tenantId: "72f988bf-86f1-41af-91ab-2d7cd011db47",
        },
    },
    providerName: "vmwareprovider1",
    resourceGroupName: "resourcegroup1",
    resourceName: "migrationvault",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

replication_recovery_services_provider = azure_native.recoveryservices.ReplicationRecoveryServicesProvider("replicationRecoveryServicesProvider",
    fabric_name="vmwarefabric1",
    properties=azure_native.recoveryservices.RecoveryServicesProviderPropertiesResponseArgs(
        authentication_identity_input=azure_native.recoveryservices.IdentityProviderInputArgs(
            aad_authority="https://login.microsoftonline.com",
            application_id="f66fce08-c0c6-47a1-beeb-0ede5ea94f90",
            audience="https://microsoft.onmicrosoft.com/cf19e349-644c-4c6a-bcae-9c8f35357874",
            object_id="141360b8-5686-4240-a027-5e24e6affeba",
            tenant_id="72f988bf-86f1-41af-91ab-2d7cd011db47",
        ),
        machine_name="vmwareprovider1",
        resource_access_identity_input=azure_native.recoveryservices.IdentityProviderInputArgs(
            aad_authority="https://login.microsoftonline.com",
            application_id="f66fce08-c0c6-47a1-beeb-0ede5ea94f90",
            audience="https://microsoft.onmicrosoft.com/cf19e349-644c-4c6a-bcae-9c8f35357874",
            object_id="141360b8-5686-4240-a027-5e24e6affeba",
            tenant_id="72f988bf-86f1-41af-91ab-2d7cd011db47",
        ),
    ),
    provider_name="vmwareprovider1",
    resource_group_name="resourcegroup1",
    resource_name_="migrationvault")

```

```yaml
resources:
  replicationRecoveryServicesProvider:
    type: azure-native:recoveryservices:ReplicationRecoveryServicesProvider
    properties:
      fabricName: vmwarefabric1
      properties:
        authenticationIdentityInput:
          aadAuthority: https://login.microsoftonline.com
          applicationId: f66fce08-c0c6-47a1-beeb-0ede5ea94f90
          audience: https://microsoft.onmicrosoft.com/cf19e349-644c-4c6a-bcae-9c8f35357874
          objectId: 141360b8-5686-4240-a027-5e24e6affeba
          tenantId: 72f988bf-86f1-41af-91ab-2d7cd011db47
        machineName: vmwareprovider1
        resourceAccessIdentityInput:
          aadAuthority: https://login.microsoftonline.com
          applicationId: f66fce08-c0c6-47a1-beeb-0ede5ea94f90
          audience: https://microsoft.onmicrosoft.com/cf19e349-644c-4c6a-bcae-9c8f35357874
          objectId: 141360b8-5686-4240-a027-5e24e6affeba
          tenantId: 72f988bf-86f1-41af-91ab-2d7cd011db47
      providerName: vmwareprovider1
      resourceGroupName: resourcegroup1
      resourceName: migrationvault

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:recoveryservices:ReplicationRecoveryServicesProvider vmwareprovider1 /Subscriptions/cb53d0c3-bd59-4721-89bc-06916a9147ef/resourceGroups/resourcegroup1/providers/Microsoft.RecoveryServices/vaults/migrationvault/replicationFabrics/vmwarefabric1/replicationRecoveryServicesProviders/vmwareprovider1 
```
