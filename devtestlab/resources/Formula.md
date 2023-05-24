A formula for creating a VM, specifying an image base and other parameters
API Version: 2018-09-15.
Previous API Version: 2018-09-15. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Formulas_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var formula = new AzureNative.DevTestLab.Formula("formula", new()
    {
        Description = "Formula using a Linux base",
        FormulaContent = new AzureNative.DevTestLab.Inputs.LabVirtualMachineCreationParameterArgs
        {
            AllowClaim = false,
            Artifacts = new[]
            {
                new AzureNative.DevTestLab.Inputs.ArtifactInstallPropertiesArgs
                {
                    ArtifactId = "/artifactsources/{artifactSourceName}/artifacts/linux-install-nodejs",
                    Parameters = new[] {},
                },
            },
            DisallowPublicIpAddress = true,
            GalleryImageReference = new AzureNative.DevTestLab.Inputs.GalleryImageReferenceArgs
            {
                Offer = "0001-com-ubuntu-server-groovy",
                OsType = "Linux",
                Publisher = "canonical",
                Sku = "20_10",
                Version = "latest",
            },
            IsAuthenticationWithSshKey = false,
            LabSubnetName = "Dtl{labName}Subnet",
            LabVirtualNetworkId = "/virtualnetworks/dtl{labName}",
            Location = "{location}",
            NetworkInterface = new AzureNative.DevTestLab.Inputs.NetworkInterfacePropertiesArgs
            {
                SharedPublicIpAddressConfiguration = new AzureNative.DevTestLab.Inputs.SharedPublicIpAddressConfigurationArgs
                {
                    InboundNatRules = new[]
                    {
                        new AzureNative.DevTestLab.Inputs.InboundNatRuleArgs
                        {
                            BackendPort = 22,
                            TransportProtocol = "Tcp",
                        },
                    },
                },
            },
            Notes = "Ubuntu Server 20.10",
            Size = "Standard_B1ms",
            StorageType = "Standard",
            UserName = "user",
        },
        LabName = "{labName}",
        Location = "{location}",
        Name = "{formulaName}",
        ResourceGroupName = "resourceGroupName",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.devtestlab.Formula;
import com.pulumi.azurenative.devtestlab.FormulaArgs;
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
        var formula = new Formula("formula", FormulaArgs.builder()        
            .description("Formula using a Linux base")
            .formulaContent(Map.ofEntries(
                Map.entry("allowClaim", false),
                Map.entry("artifacts", Map.ofEntries(
                    Map.entry("artifactId", "/artifactsources/{artifactSourceName}/artifacts/linux-install-nodejs"),
                    Map.entry("parameters", )
                )),
                Map.entry("disallowPublicIpAddress", true),
                Map.entry("galleryImageReference", Map.ofEntries(
                    Map.entry("offer", "0001-com-ubuntu-server-groovy"),
                    Map.entry("osType", "Linux"),
                    Map.entry("publisher", "canonical"),
                    Map.entry("sku", "20_10"),
                    Map.entry("version", "latest")
                )),
                Map.entry("isAuthenticationWithSshKey", false),
                Map.entry("labSubnetName", "Dtl{labName}Subnet"),
                Map.entry("labVirtualNetworkId", "/virtualnetworks/dtl{labName}"),
                Map.entry("location", "{location}"),
                Map.entry("networkInterface", Map.of("sharedPublicIpAddressConfiguration", Map.of("inboundNatRules", Map.ofEntries(
                    Map.entry("backendPort", 22),
                    Map.entry("transportProtocol", "Tcp")
                )))),
                Map.entry("notes", "Ubuntu Server 20.10"),
                Map.entry("size", "Standard_B1ms"),
                Map.entry("storageType", "Standard"),
                Map.entry("userName", "user")
            ))
            .labName("{labName}")
            .location("{location}")
            .name("{formulaName}")
            .resourceGroupName("resourceGroupName")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const formula = new azure_native.devtestlab.Formula("formula", {
    description: "Formula using a Linux base",
    formulaContent: {
        allowClaim: false,
        artifacts: [{
            artifactId: "/artifactsources/{artifactSourceName}/artifacts/linux-install-nodejs",
            parameters: [],
        }],
        disallowPublicIpAddress: true,
        galleryImageReference: {
            offer: "0001-com-ubuntu-server-groovy",
            osType: "Linux",
            publisher: "canonical",
            sku: "20_10",
            version: "latest",
        },
        isAuthenticationWithSshKey: false,
        labSubnetName: "Dtl{labName}Subnet",
        labVirtualNetworkId: "/virtualnetworks/dtl{labName}",
        location: "{location}",
        networkInterface: {
            sharedPublicIpAddressConfiguration: {
                inboundNatRules: [{
                    backendPort: 22,
                    transportProtocol: "Tcp",
                }],
            },
        },
        notes: "Ubuntu Server 20.10",
        size: "Standard_B1ms",
        storageType: "Standard",
        userName: "user",
    },
    labName: "{labName}",
    location: "{location}",
    name: "{formulaName}",
    resourceGroupName: "resourceGroupName",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

formula = azure_native.devtestlab.Formula("formula",
    description="Formula using a Linux base",
    formula_content=azure_native.devtestlab.LabVirtualMachineCreationParameterResponseArgs(
        allow_claim=False,
        artifacts=[{
            "artifactId": "/artifactsources/{artifactSourceName}/artifacts/linux-install-nodejs",
            "parameters": [],
        }],
        disallow_public_ip_address=True,
        gallery_image_reference=azure_native.devtestlab.GalleryImageReferenceArgs(
            offer="0001-com-ubuntu-server-groovy",
            os_type="Linux",
            publisher="canonical",
            sku="20_10",
            version="latest",
        ),
        is_authentication_with_ssh_key=False,
        lab_subnet_name="Dtl{labName}Subnet",
        lab_virtual_network_id="/virtualnetworks/dtl{labName}",
        location="{location}",
        network_interface={
            "sharedPublicIpAddressConfiguration": {
                "inboundNatRules": [azure_native.devtestlab.InboundNatRuleArgs(
                    backend_port=22,
                    transport_protocol="Tcp",
                )],
            },
        },
        notes="Ubuntu Server 20.10",
        size="Standard_B1ms",
        storage_type="Standard",
        user_name="user",
    ),
    lab_name="{labName}",
    location="{location}",
    name="{formulaName}",
    resource_group_name="resourceGroupName")

```

```yaml
resources:
  formula:
    type: azure-native:devtestlab:Formula
    properties:
      description: Formula using a Linux base
      formulaContent:
        allowClaim: false
        artifacts:
          - artifactId: /artifactsources/{artifactSourceName}/artifacts/linux-install-nodejs
            parameters: []
        disallowPublicIpAddress: true
        galleryImageReference:
          offer: 0001-com-ubuntu-server-groovy
          osType: Linux
          publisher: canonical
          sku: '20_10'
          version: latest
        isAuthenticationWithSshKey: false
        labSubnetName: Dtl{labName}Subnet
        labVirtualNetworkId: /virtualnetworks/dtl{labName}
        location: '{location}'
        networkInterface:
          sharedPublicIpAddressConfiguration:
            inboundNatRules:
              - backendPort: 22
                transportProtocol: Tcp
        notes: Ubuntu Server 20.10
        size: Standard_B1ms
        storageType: Standard
        userName: user
      labName: '{labName}'
      location: '{location}'
      name: '{formulaName}'
      resourceGroupName: resourceGroupName

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:devtestlab:Formula {formulaName} /subscriptions/{subscriptionId}/resourcegroups/resourceGroupName/providers/microsoft.devtestlab/labs/{labName}/formulas/{formulaName} 
```
