VpnServerConfiguration Resource.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### VpnServerConfigurationCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var vpnServerConfiguration = new AzureNative.Network.VpnServerConfiguration("vpnServerConfiguration", new()
    {
        ConfigurationPolicyGroups = new[]
        {
            new AzureNative.Network.Inputs.VpnServerConfigurationPolicyGroupArgs
            {
                Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/vpnServerConfigurations/vpnServerConfiguration1/vpnServerConfigurationPolicyGroups/policyGroup1",
                IsDefault = true,
                Name = "policyGroup1",
                PolicyMembers = new[]
                {
                    new AzureNative.Network.Inputs.VpnServerConfigurationPolicyGroupMemberArgs
                    {
                        AttributeType = "RadiusAzureGroupId",
                        AttributeValue = "6ad1bd08",
                        Name = "policy1",
                    },
                },
                Priority = 0,
            },
            new AzureNative.Network.Inputs.VpnServerConfigurationPolicyGroupArgs
            {
                Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/vpnServerConfigurations/vpnServerConfiguration1/vpnServerConfigurationPolicyGroups/policyGroup2",
                IsDefault = true,
                Name = "policyGroup2",
                PolicyMembers = new[]
                {
                    new AzureNative.Network.Inputs.VpnServerConfigurationPolicyGroupMemberArgs
                    {
                        AttributeType = "CertificateGroupId",
                        AttributeValue = "red.com",
                        Name = "policy2",
                    },
                },
                Priority = 0,
            },
        },
        Location = "West US",
        RadiusClientRootCertificates = new[]
        {
            new AzureNative.Network.Inputs.VpnServerConfigRadiusClientRootCertificateArgs
            {
                Name = "vpnServerConfigRadiusClientRootCert1",
                Thumbprint = "83FFBFC8848B5A5836C94D0112367E16148A286F",
            },
        },
        RadiusServerRootCertificates = new[]
        {
            new AzureNative.Network.Inputs.VpnServerConfigRadiusServerRootCertificateArgs
            {
                Name = "vpnServerConfigRadiusServerRootCer1",
                PublicCertData = "MIIC5zCCAc+gAwIBAgIQErQ0Hk4aDJxIA+Q5RagB+jANBgkqhkiG9w0BAQsFADAWMRQwEgYDVQQDDAtQMlNSb290Q2VydDAeFw0xNzEyMTQyMTA3MzhaFw0xODEyMTQyMTI3MzhaMBYxFDASBgNVBAMMC1AyU1Jvb3RDZXJ0MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEArP7/NQXmW7cQ/ZR1mv3Y3I29Lt7HTOqzo/1KUOoVH3NItbQIRAQbwKy3UWrOFz4eGNX2GWtNRMdCyWsKeqy9Ltsdfcm1IbKXkl84DFeU/ZacXu4Dl3xX3gV5du4TLZjEowJELyur11Ea2YcjPRQ/FzAF9/hGuboS1HZQEPLx4FdUs9OxCYOtc0MxBCwLfVTTRqarb0Ne+arNYd4kCzIhAke1nOyKAJBda5ZL+VHy3S5S8qGlD46jm8HXugmAkUygS4oIIXOmj/1O9sNAi3LN60zufSzCmP8Rm/iUGX+DHAGGiXxwZOKQLEDaZXKqoHjMPP0XudmSWwOIbyeQVrLhkwIDAQABozEwLzAOBgNVHQ8BAf8EBAMCAgQwHQYDVR0OBBYEFEfeNU2trYxNLF9ONmuJUsT13pKDMA0GCSqGSIb3DQEBCwUAA4IBAQBmM6RJzsGGipxyMhimHKN2xlkejhVsgBoTAhOU0llW9aUSwINJ9zFUGgI8IzUFy1VG776fchHp0LMRmPSIUYk5btEPxbsrPtumPuMH8EQGrS+Rt4pD+78c8H1fEPkq5CmDl/PKu4JoFGv+aFcE+Od0hlILstIF10Qysf++QXDolKfzJa/56bgMeYKFiju73loiRM57ns8ddXpfLl792UVpRkFU62LNns6Y1LKTwapmUF4IvIuAIzd6LZNOQng64LAKXtKnViJ1JQiXwf4CEzhgvAti3/ejpb3U90hsrUcyZi6wBv9bZLcAJRWpz61JNYliM1d1grSwQDKGXNQE4xuM",
            },
        },
        RadiusServers = new[]
        {
            new AzureNative.Network.Inputs.RadiusServerArgs
            {
                RadiusServerAddress = "10.0.0.0",
                RadiusServerScore = 25,
                RadiusServerSecret = "radiusServerSecret",
            },
        },
        ResourceGroupName = "rg1",
        Tags = 
        {
            { "key1", "value1" },
        },
        VpnClientIpsecPolicies = new[]
        {
            new AzureNative.Network.Inputs.IpsecPolicyArgs
            {
                DhGroup = "DHGroup14",
                IkeEncryption = "AES256",
                IkeIntegrity = "SHA384",
                IpsecEncryption = "AES256",
                IpsecIntegrity = "SHA256",
                PfsGroup = "PFS14",
                SaDataSizeKilobytes = 429497,
                SaLifeTimeSeconds = 86472,
            },
        },
        VpnClientRevokedCertificates = new[]
        {
            new AzureNative.Network.Inputs.VpnServerConfigVpnClientRevokedCertificateArgs
            {
                Name = "vpnServerConfigVpnClientRevokedCert1",
                Thumbprint = "83FFBFC8848B5A5836C94D0112367E16148A286F",
            },
        },
        VpnClientRootCertificates = new[]
        {
            new AzureNative.Network.Inputs.VpnServerConfigVpnClientRootCertificateArgs
            {
                Name = "vpnServerConfigVpnClientRootCert1",
                PublicCertData = "MIIC5zCCAc+gAwIBAgIQErQ0Hk4aDJxIA+Q5RagB+jANBgkqhkiG9w0BAQsFADAWMRQwEgYDVQQDDAtQMlNSb290Q2VydDAeFw0xNzEyMTQyMTA3MzhaFw0xODEyMTQyMTI3MzhaMBYxFDASBgNVBAMMC1AyU1Jvb3RDZXJ0MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEArP7/NQXmW7cQ/ZR1mv3Y3I29Lt7HTOqzo/1KUOoVH3NItbQIRAQbwKy3UWrOFz4eGNX2GWtNRMdCyWsKeqy9Ltsdfcm1IbKXkl84DFeU/ZacXu4Dl3xX3gV5du4TLZjEowJELyur11Ea2YcjPRQ/FzAF9/hGuboS1HZQEPLx4FdUs9OxCYOtc0MxBCwLfVTTRqarb0Ne+arNYd4kCzIhAke1nOyKAJBda5ZL+VHy3S5S8qGlD46jm8HXugmAkUygS4oIIXOmj/1O9sNAi3LN60zufSzCmP8Rm/iUGX+DHAGGiXxwZOKQLEDaZXKqoHjMPP0XudmSWwOIbyeQVrLhkwIDAQABozEwLzAOBgNVHQ8BAf8EBAMCAgQwHQYDVR0OBBYEFEfeNU2trYxNLF9ONmuJUsT13pKDMA0GCSqGSIb3DQEBCwUAA4IBAQBmM6RJzsGGipxyMhimHKN2xlkejhVsgBoTAhOU0llW9aUSwINJ9zFUGgI8IzUFy1VG776fchHp0LMRmPSIUYk5btEPxbsrPtumPuMH8EQGrS+Rt4pD+78c8H1fEPkq5CmDl/PKu4JoFGv+aFcE+Od0hlILstIF10Qysf++QXDolKfzJa/56bgMeYKFiju73loiRM57ns8ddXpfLl792UVpRkFU62LNns6Y1LKTwapmUF4IvIuAIzd6LZNOQng64LAKXtKnViJ1JQiXwf4CEzhgvAti3/ejpb3U90hsrUcyZi6wBv9bZLcAJRWpz61JNYliM1d1grSwQDKGXNQE4xuN",
            },
        },
        VpnProtocols = new[]
        {
            "IkeV2",
        },
        VpnServerConfigurationName = "vpnServerConfiguration1",
    });

});


```

```go
package main

import (
	network "github.com/pulumi/pulumi-azure-native-sdk/network"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := network.NewVpnServerConfiguration(ctx, "vpnServerConfiguration", &network.VpnServerConfigurationArgs{
			ConfigurationPolicyGroups: []network.VpnServerConfigurationPolicyGroupArgs{
				{
					Id:        pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/vpnServerConfigurations/vpnServerConfiguration1/vpnServerConfigurationPolicyGroups/policyGroup1"),
					IsDefault: pulumi.Bool(true),
					Name:      pulumi.String("policyGroup1"),
					PolicyMembers: network.VpnServerConfigurationPolicyGroupMemberArray{
						{
							AttributeType:  pulumi.String("RadiusAzureGroupId"),
							AttributeValue: pulumi.String("6ad1bd08"),
							Name:           pulumi.String("policy1"),
						},
					},
					Priority: pulumi.Int(0),
				},
				{
					Id:        pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/vpnServerConfigurations/vpnServerConfiguration1/vpnServerConfigurationPolicyGroups/policyGroup2"),
					IsDefault: pulumi.Bool(true),
					Name:      pulumi.String("policyGroup2"),
					PolicyMembers: network.VpnServerConfigurationPolicyGroupMemberArray{
						{
							AttributeType:  pulumi.String("CertificateGroupId"),
							AttributeValue: pulumi.String("red.com"),
							Name:           pulumi.String("policy2"),
						},
					},
					Priority: pulumi.Int(0),
				},
			},
			Location: pulumi.String("West US"),
			RadiusClientRootCertificates: []network.VpnServerConfigRadiusClientRootCertificateArgs{
				{
					Name:       pulumi.String("vpnServerConfigRadiusClientRootCert1"),
					Thumbprint: pulumi.String("83FFBFC8848B5A5836C94D0112367E16148A286F"),
				},
			},
			RadiusServerRootCertificates: []network.VpnServerConfigRadiusServerRootCertificateArgs{
				{
					Name:           pulumi.String("vpnServerConfigRadiusServerRootCer1"),
					PublicCertData: pulumi.String("MIIC5zCCAc+gAwIBAgIQErQ0Hk4aDJxIA+Q5RagB+jANBgkqhkiG9w0BAQsFADAWMRQwEgYDVQQDDAtQMlNSb290Q2VydDAeFw0xNzEyMTQyMTA3MzhaFw0xODEyMTQyMTI3MzhaMBYxFDASBgNVBAMMC1AyU1Jvb3RDZXJ0MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEArP7/NQXmW7cQ/ZR1mv3Y3I29Lt7HTOqzo/1KUOoVH3NItbQIRAQbwKy3UWrOFz4eGNX2GWtNRMdCyWsKeqy9Ltsdfcm1IbKXkl84DFeU/ZacXu4Dl3xX3gV5du4TLZjEowJELyur11Ea2YcjPRQ/FzAF9/hGuboS1HZQEPLx4FdUs9OxCYOtc0MxBCwLfVTTRqarb0Ne+arNYd4kCzIhAke1nOyKAJBda5ZL+VHy3S5S8qGlD46jm8HXugmAkUygS4oIIXOmj/1O9sNAi3LN60zufSzCmP8Rm/iUGX+DHAGGiXxwZOKQLEDaZXKqoHjMPP0XudmSWwOIbyeQVrLhkwIDAQABozEwLzAOBgNVHQ8BAf8EBAMCAgQwHQYDVR0OBBYEFEfeNU2trYxNLF9ONmuJUsT13pKDMA0GCSqGSIb3DQEBCwUAA4IBAQBmM6RJzsGGipxyMhimHKN2xlkejhVsgBoTAhOU0llW9aUSwINJ9zFUGgI8IzUFy1VG776fchHp0LMRmPSIUYk5btEPxbsrPtumPuMH8EQGrS+Rt4pD+78c8H1fEPkq5CmDl/PKu4JoFGv+aFcE+Od0hlILstIF10Qysf++QXDolKfzJa/56bgMeYKFiju73loiRM57ns8ddXpfLl792UVpRkFU62LNns6Y1LKTwapmUF4IvIuAIzd6LZNOQng64LAKXtKnViJ1JQiXwf4CEzhgvAti3/ejpb3U90hsrUcyZi6wBv9bZLcAJRWpz61JNYliM1d1grSwQDKGXNQE4xuM"),
				},
			},
			RadiusServers: []network.RadiusServerArgs{
				{
					RadiusServerAddress: pulumi.String("10.0.0.0"),
					RadiusServerScore:   pulumi.Float64(25),
					RadiusServerSecret:  pulumi.String("radiusServerSecret"),
				},
			},
			ResourceGroupName: pulumi.String("rg1"),
			Tags: pulumi.StringMap{
				"key1": pulumi.String("value1"),
			},
			VpnClientIpsecPolicies: []network.IpsecPolicyArgs{
				{
					DhGroup:             pulumi.String("DHGroup14"),
					IkeEncryption:       pulumi.String("AES256"),
					IkeIntegrity:        pulumi.String("SHA384"),
					IpsecEncryption:     pulumi.String("AES256"),
					IpsecIntegrity:      pulumi.String("SHA256"),
					PfsGroup:            pulumi.String("PFS14"),
					SaDataSizeKilobytes: pulumi.Int(429497),
					SaLifeTimeSeconds:   pulumi.Int(86472),
				},
			},
			VpnClientRevokedCertificates: []network.VpnServerConfigVpnClientRevokedCertificateArgs{
				{
					Name:       pulumi.String("vpnServerConfigVpnClientRevokedCert1"),
					Thumbprint: pulumi.String("83FFBFC8848B5A5836C94D0112367E16148A286F"),
				},
			},
			VpnClientRootCertificates: []network.VpnServerConfigVpnClientRootCertificateArgs{
				{
					Name:           pulumi.String("vpnServerConfigVpnClientRootCert1"),
					PublicCertData: pulumi.String("MIIC5zCCAc+gAwIBAgIQErQ0Hk4aDJxIA+Q5RagB+jANBgkqhkiG9w0BAQsFADAWMRQwEgYDVQQDDAtQMlNSb290Q2VydDAeFw0xNzEyMTQyMTA3MzhaFw0xODEyMTQyMTI3MzhaMBYxFDASBgNVBAMMC1AyU1Jvb3RDZXJ0MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEArP7/NQXmW7cQ/ZR1mv3Y3I29Lt7HTOqzo/1KUOoVH3NItbQIRAQbwKy3UWrOFz4eGNX2GWtNRMdCyWsKeqy9Ltsdfcm1IbKXkl84DFeU/ZacXu4Dl3xX3gV5du4TLZjEowJELyur11Ea2YcjPRQ/FzAF9/hGuboS1HZQEPLx4FdUs9OxCYOtc0MxBCwLfVTTRqarb0Ne+arNYd4kCzIhAke1nOyKAJBda5ZL+VHy3S5S8qGlD46jm8HXugmAkUygS4oIIXOmj/1O9sNAi3LN60zufSzCmP8Rm/iUGX+DHAGGiXxwZOKQLEDaZXKqoHjMPP0XudmSWwOIbyeQVrLhkwIDAQABozEwLzAOBgNVHQ8BAf8EBAMCAgQwHQYDVR0OBBYEFEfeNU2trYxNLF9ONmuJUsT13pKDMA0GCSqGSIb3DQEBCwUAA4IBAQBmM6RJzsGGipxyMhimHKN2xlkejhVsgBoTAhOU0llW9aUSwINJ9zFUGgI8IzUFy1VG776fchHp0LMRmPSIUYk5btEPxbsrPtumPuMH8EQGrS+Rt4pD+78c8H1fEPkq5CmDl/PKu4JoFGv+aFcE+Od0hlILstIF10Qysf++QXDolKfzJa/56bgMeYKFiju73loiRM57ns8ddXpfLl792UVpRkFU62LNns6Y1LKTwapmUF4IvIuAIzd6LZNOQng64LAKXtKnViJ1JQiXwf4CEzhgvAti3/ejpb3U90hsrUcyZi6wBv9bZLcAJRWpz61JNYliM1d1grSwQDKGXNQE4xuN"),
				},
			},
			VpnProtocols: pulumi.StringArray{
				pulumi.String("IkeV2"),
			},
			VpnServerConfigurationName: pulumi.String("vpnServerConfiguration1"),
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
import com.pulumi.azurenative.network.VpnServerConfiguration;
import com.pulumi.azurenative.network.VpnServerConfigurationArgs;
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
        var vpnServerConfiguration = new VpnServerConfiguration("vpnServerConfiguration", VpnServerConfigurationArgs.builder()        
            .configurationPolicyGroups(            
                Map.ofEntries(
                    Map.entry("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/vpnServerConfigurations/vpnServerConfiguration1/vpnServerConfigurationPolicyGroups/policyGroup1"),
                    Map.entry("isDefault", true),
                    Map.entry("name", "policyGroup1"),
                    Map.entry("policyMembers", Map.ofEntries(
                        Map.entry("attributeType", "RadiusAzureGroupId"),
                        Map.entry("attributeValue", "6ad1bd08"),
                        Map.entry("name", "policy1")
                    )),
                    Map.entry("priority", 0)
                ),
                Map.ofEntries(
                    Map.entry("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/vpnServerConfigurations/vpnServerConfiguration1/vpnServerConfigurationPolicyGroups/policyGroup2"),
                    Map.entry("isDefault", true),
                    Map.entry("name", "policyGroup2"),
                    Map.entry("policyMembers", Map.ofEntries(
                        Map.entry("attributeType", "CertificateGroupId"),
                        Map.entry("attributeValue", "red.com"),
                        Map.entry("name", "policy2")
                    )),
                    Map.entry("priority", 0)
                ))
            .location("West US")
            .radiusClientRootCertificates(Map.ofEntries(
                Map.entry("name", "vpnServerConfigRadiusClientRootCert1"),
                Map.entry("thumbprint", "83FFBFC8848B5A5836C94D0112367E16148A286F")
            ))
            .radiusServerRootCertificates(Map.ofEntries(
                Map.entry("name", "vpnServerConfigRadiusServerRootCer1"),
                Map.entry("publicCertData", "MIIC5zCCAc+gAwIBAgIQErQ0Hk4aDJxIA+Q5RagB+jANBgkqhkiG9w0BAQsFADAWMRQwEgYDVQQDDAtQMlNSb290Q2VydDAeFw0xNzEyMTQyMTA3MzhaFw0xODEyMTQyMTI3MzhaMBYxFDASBgNVBAMMC1AyU1Jvb3RDZXJ0MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEArP7/NQXmW7cQ/ZR1mv3Y3I29Lt7HTOqzo/1KUOoVH3NItbQIRAQbwKy3UWrOFz4eGNX2GWtNRMdCyWsKeqy9Ltsdfcm1IbKXkl84DFeU/ZacXu4Dl3xX3gV5du4TLZjEowJELyur11Ea2YcjPRQ/FzAF9/hGuboS1HZQEPLx4FdUs9OxCYOtc0MxBCwLfVTTRqarb0Ne+arNYd4kCzIhAke1nOyKAJBda5ZL+VHy3S5S8qGlD46jm8HXugmAkUygS4oIIXOmj/1O9sNAi3LN60zufSzCmP8Rm/iUGX+DHAGGiXxwZOKQLEDaZXKqoHjMPP0XudmSWwOIbyeQVrLhkwIDAQABozEwLzAOBgNVHQ8BAf8EBAMCAgQwHQYDVR0OBBYEFEfeNU2trYxNLF9ONmuJUsT13pKDMA0GCSqGSIb3DQEBCwUAA4IBAQBmM6RJzsGGipxyMhimHKN2xlkejhVsgBoTAhOU0llW9aUSwINJ9zFUGgI8IzUFy1VG776fchHp0LMRmPSIUYk5btEPxbsrPtumPuMH8EQGrS+Rt4pD+78c8H1fEPkq5CmDl/PKu4JoFGv+aFcE+Od0hlILstIF10Qysf++QXDolKfzJa/56bgMeYKFiju73loiRM57ns8ddXpfLl792UVpRkFU62LNns6Y1LKTwapmUF4IvIuAIzd6LZNOQng64LAKXtKnViJ1JQiXwf4CEzhgvAti3/ejpb3U90hsrUcyZi6wBv9bZLcAJRWpz61JNYliM1d1grSwQDKGXNQE4xuM")
            ))
            .radiusServers(Map.ofEntries(
                Map.entry("radiusServerAddress", "10.0.0.0"),
                Map.entry("radiusServerScore", 25),
                Map.entry("radiusServerSecret", "radiusServerSecret")
            ))
            .resourceGroupName("rg1")
            .tags(Map.of("key1", "value1"))
            .vpnClientIpsecPolicies(Map.ofEntries(
                Map.entry("dhGroup", "DHGroup14"),
                Map.entry("ikeEncryption", "AES256"),
                Map.entry("ikeIntegrity", "SHA384"),
                Map.entry("ipsecEncryption", "AES256"),
                Map.entry("ipsecIntegrity", "SHA256"),
                Map.entry("pfsGroup", "PFS14"),
                Map.entry("saDataSizeKilobytes", 429497),
                Map.entry("saLifeTimeSeconds", 86472)
            ))
            .vpnClientRevokedCertificates(Map.ofEntries(
                Map.entry("name", "vpnServerConfigVpnClientRevokedCert1"),
                Map.entry("thumbprint", "83FFBFC8848B5A5836C94D0112367E16148A286F")
            ))
            .vpnClientRootCertificates(Map.ofEntries(
                Map.entry("name", "vpnServerConfigVpnClientRootCert1"),
                Map.entry("publicCertData", "MIIC5zCCAc+gAwIBAgIQErQ0Hk4aDJxIA+Q5RagB+jANBgkqhkiG9w0BAQsFADAWMRQwEgYDVQQDDAtQMlNSb290Q2VydDAeFw0xNzEyMTQyMTA3MzhaFw0xODEyMTQyMTI3MzhaMBYxFDASBgNVBAMMC1AyU1Jvb3RDZXJ0MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEArP7/NQXmW7cQ/ZR1mv3Y3I29Lt7HTOqzo/1KUOoVH3NItbQIRAQbwKy3UWrOFz4eGNX2GWtNRMdCyWsKeqy9Ltsdfcm1IbKXkl84DFeU/ZacXu4Dl3xX3gV5du4TLZjEowJELyur11Ea2YcjPRQ/FzAF9/hGuboS1HZQEPLx4FdUs9OxCYOtc0MxBCwLfVTTRqarb0Ne+arNYd4kCzIhAke1nOyKAJBda5ZL+VHy3S5S8qGlD46jm8HXugmAkUygS4oIIXOmj/1O9sNAi3LN60zufSzCmP8Rm/iUGX+DHAGGiXxwZOKQLEDaZXKqoHjMPP0XudmSWwOIbyeQVrLhkwIDAQABozEwLzAOBgNVHQ8BAf8EBAMCAgQwHQYDVR0OBBYEFEfeNU2trYxNLF9ONmuJUsT13pKDMA0GCSqGSIb3DQEBCwUAA4IBAQBmM6RJzsGGipxyMhimHKN2xlkejhVsgBoTAhOU0llW9aUSwINJ9zFUGgI8IzUFy1VG776fchHp0LMRmPSIUYk5btEPxbsrPtumPuMH8EQGrS+Rt4pD+78c8H1fEPkq5CmDl/PKu4JoFGv+aFcE+Od0hlILstIF10Qysf++QXDolKfzJa/56bgMeYKFiju73loiRM57ns8ddXpfLl792UVpRkFU62LNns6Y1LKTwapmUF4IvIuAIzd6LZNOQng64LAKXtKnViJ1JQiXwf4CEzhgvAti3/ejpb3U90hsrUcyZi6wBv9bZLcAJRWpz61JNYliM1d1grSwQDKGXNQE4xuN")
            ))
            .vpnProtocols("IkeV2")
            .vpnServerConfigurationName("vpnServerConfiguration1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const vpnServerConfiguration = new azure_native.network.VpnServerConfiguration("vpnServerConfiguration", {
    configurationPolicyGroups: [
        {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/vpnServerConfigurations/vpnServerConfiguration1/vpnServerConfigurationPolicyGroups/policyGroup1",
            isDefault: true,
            name: "policyGroup1",
            policyMembers: [{
                attributeType: "RadiusAzureGroupId",
                attributeValue: "6ad1bd08",
                name: "policy1",
            }],
            priority: 0,
        },
        {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/vpnServerConfigurations/vpnServerConfiguration1/vpnServerConfigurationPolicyGroups/policyGroup2",
            isDefault: true,
            name: "policyGroup2",
            policyMembers: [{
                attributeType: "CertificateGroupId",
                attributeValue: "red.com",
                name: "policy2",
            }],
            priority: 0,
        },
    ],
    location: "West US",
    radiusClientRootCertificates: [{
        name: "vpnServerConfigRadiusClientRootCert1",
        thumbprint: "83FFBFC8848B5A5836C94D0112367E16148A286F",
    }],
    radiusServerRootCertificates: [{
        name: "vpnServerConfigRadiusServerRootCer1",
        publicCertData: "MIIC5zCCAc+gAwIBAgIQErQ0Hk4aDJxIA+Q5RagB+jANBgkqhkiG9w0BAQsFADAWMRQwEgYDVQQDDAtQMlNSb290Q2VydDAeFw0xNzEyMTQyMTA3MzhaFw0xODEyMTQyMTI3MzhaMBYxFDASBgNVBAMMC1AyU1Jvb3RDZXJ0MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEArP7/NQXmW7cQ/ZR1mv3Y3I29Lt7HTOqzo/1KUOoVH3NItbQIRAQbwKy3UWrOFz4eGNX2GWtNRMdCyWsKeqy9Ltsdfcm1IbKXkl84DFeU/ZacXu4Dl3xX3gV5du4TLZjEowJELyur11Ea2YcjPRQ/FzAF9/hGuboS1HZQEPLx4FdUs9OxCYOtc0MxBCwLfVTTRqarb0Ne+arNYd4kCzIhAke1nOyKAJBda5ZL+VHy3S5S8qGlD46jm8HXugmAkUygS4oIIXOmj/1O9sNAi3LN60zufSzCmP8Rm/iUGX+DHAGGiXxwZOKQLEDaZXKqoHjMPP0XudmSWwOIbyeQVrLhkwIDAQABozEwLzAOBgNVHQ8BAf8EBAMCAgQwHQYDVR0OBBYEFEfeNU2trYxNLF9ONmuJUsT13pKDMA0GCSqGSIb3DQEBCwUAA4IBAQBmM6RJzsGGipxyMhimHKN2xlkejhVsgBoTAhOU0llW9aUSwINJ9zFUGgI8IzUFy1VG776fchHp0LMRmPSIUYk5btEPxbsrPtumPuMH8EQGrS+Rt4pD+78c8H1fEPkq5CmDl/PKu4JoFGv+aFcE+Od0hlILstIF10Qysf++QXDolKfzJa/56bgMeYKFiju73loiRM57ns8ddXpfLl792UVpRkFU62LNns6Y1LKTwapmUF4IvIuAIzd6LZNOQng64LAKXtKnViJ1JQiXwf4CEzhgvAti3/ejpb3U90hsrUcyZi6wBv9bZLcAJRWpz61JNYliM1d1grSwQDKGXNQE4xuM",
    }],
    radiusServers: [{
        radiusServerAddress: "10.0.0.0",
        radiusServerScore: 25,
        radiusServerSecret: "radiusServerSecret",
    }],
    resourceGroupName: "rg1",
    tags: {
        key1: "value1",
    },
    vpnClientIpsecPolicies: [{
        dhGroup: "DHGroup14",
        ikeEncryption: "AES256",
        ikeIntegrity: "SHA384",
        ipsecEncryption: "AES256",
        ipsecIntegrity: "SHA256",
        pfsGroup: "PFS14",
        saDataSizeKilobytes: 429497,
        saLifeTimeSeconds: 86472,
    }],
    vpnClientRevokedCertificates: [{
        name: "vpnServerConfigVpnClientRevokedCert1",
        thumbprint: "83FFBFC8848B5A5836C94D0112367E16148A286F",
    }],
    vpnClientRootCertificates: [{
        name: "vpnServerConfigVpnClientRootCert1",
        publicCertData: "MIIC5zCCAc+gAwIBAgIQErQ0Hk4aDJxIA+Q5RagB+jANBgkqhkiG9w0BAQsFADAWMRQwEgYDVQQDDAtQMlNSb290Q2VydDAeFw0xNzEyMTQyMTA3MzhaFw0xODEyMTQyMTI3MzhaMBYxFDASBgNVBAMMC1AyU1Jvb3RDZXJ0MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEArP7/NQXmW7cQ/ZR1mv3Y3I29Lt7HTOqzo/1KUOoVH3NItbQIRAQbwKy3UWrOFz4eGNX2GWtNRMdCyWsKeqy9Ltsdfcm1IbKXkl84DFeU/ZacXu4Dl3xX3gV5du4TLZjEowJELyur11Ea2YcjPRQ/FzAF9/hGuboS1HZQEPLx4FdUs9OxCYOtc0MxBCwLfVTTRqarb0Ne+arNYd4kCzIhAke1nOyKAJBda5ZL+VHy3S5S8qGlD46jm8HXugmAkUygS4oIIXOmj/1O9sNAi3LN60zufSzCmP8Rm/iUGX+DHAGGiXxwZOKQLEDaZXKqoHjMPP0XudmSWwOIbyeQVrLhkwIDAQABozEwLzAOBgNVHQ8BAf8EBAMCAgQwHQYDVR0OBBYEFEfeNU2trYxNLF9ONmuJUsT13pKDMA0GCSqGSIb3DQEBCwUAA4IBAQBmM6RJzsGGipxyMhimHKN2xlkejhVsgBoTAhOU0llW9aUSwINJ9zFUGgI8IzUFy1VG776fchHp0LMRmPSIUYk5btEPxbsrPtumPuMH8EQGrS+Rt4pD+78c8H1fEPkq5CmDl/PKu4JoFGv+aFcE+Od0hlILstIF10Qysf++QXDolKfzJa/56bgMeYKFiju73loiRM57ns8ddXpfLl792UVpRkFU62LNns6Y1LKTwapmUF4IvIuAIzd6LZNOQng64LAKXtKnViJ1JQiXwf4CEzhgvAti3/ejpb3U90hsrUcyZi6wBv9bZLcAJRWpz61JNYliM1d1grSwQDKGXNQE4xuN",
    }],
    vpnProtocols: ["IkeV2"],
    vpnServerConfigurationName: "vpnServerConfiguration1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

vpn_server_configuration = azure_native.network.VpnServerConfiguration("vpnServerConfiguration",
    configuration_policy_groups=[
        {
            "id": "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/vpnServerConfigurations/vpnServerConfiguration1/vpnServerConfigurationPolicyGroups/policyGroup1",
            "isDefault": True,
            "name": "policyGroup1",
            "policyMembers": [azure_native.network.VpnServerConfigurationPolicyGroupMemberArgs(
                attribute_type="RadiusAzureGroupId",
                attribute_value="6ad1bd08",
                name="policy1",
            )],
            "priority": 0,
        },
        {
            "id": "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/vpnServerConfigurations/vpnServerConfiguration1/vpnServerConfigurationPolicyGroups/policyGroup2",
            "isDefault": True,
            "name": "policyGroup2",
            "policyMembers": [azure_native.network.VpnServerConfigurationPolicyGroupMemberArgs(
                attribute_type="CertificateGroupId",
                attribute_value="red.com",
                name="policy2",
            )],
            "priority": 0,
        },
    ],
    location="West US",
    radius_client_root_certificates=[azure_native.network.VpnServerConfigRadiusClientRootCertificateArgs(
        name="vpnServerConfigRadiusClientRootCert1",
        thumbprint="83FFBFC8848B5A5836C94D0112367E16148A286F",
    )],
    radius_server_root_certificates=[azure_native.network.VpnServerConfigRadiusServerRootCertificateArgs(
        name="vpnServerConfigRadiusServerRootCer1",
        public_cert_data="MIIC5zCCAc+gAwIBAgIQErQ0Hk4aDJxIA+Q5RagB+jANBgkqhkiG9w0BAQsFADAWMRQwEgYDVQQDDAtQMlNSb290Q2VydDAeFw0xNzEyMTQyMTA3MzhaFw0xODEyMTQyMTI3MzhaMBYxFDASBgNVBAMMC1AyU1Jvb3RDZXJ0MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEArP7/NQXmW7cQ/ZR1mv3Y3I29Lt7HTOqzo/1KUOoVH3NItbQIRAQbwKy3UWrOFz4eGNX2GWtNRMdCyWsKeqy9Ltsdfcm1IbKXkl84DFeU/ZacXu4Dl3xX3gV5du4TLZjEowJELyur11Ea2YcjPRQ/FzAF9/hGuboS1HZQEPLx4FdUs9OxCYOtc0MxBCwLfVTTRqarb0Ne+arNYd4kCzIhAke1nOyKAJBda5ZL+VHy3S5S8qGlD46jm8HXugmAkUygS4oIIXOmj/1O9sNAi3LN60zufSzCmP8Rm/iUGX+DHAGGiXxwZOKQLEDaZXKqoHjMPP0XudmSWwOIbyeQVrLhkwIDAQABozEwLzAOBgNVHQ8BAf8EBAMCAgQwHQYDVR0OBBYEFEfeNU2trYxNLF9ONmuJUsT13pKDMA0GCSqGSIb3DQEBCwUAA4IBAQBmM6RJzsGGipxyMhimHKN2xlkejhVsgBoTAhOU0llW9aUSwINJ9zFUGgI8IzUFy1VG776fchHp0LMRmPSIUYk5btEPxbsrPtumPuMH8EQGrS+Rt4pD+78c8H1fEPkq5CmDl/PKu4JoFGv+aFcE+Od0hlILstIF10Qysf++QXDolKfzJa/56bgMeYKFiju73loiRM57ns8ddXpfLl792UVpRkFU62LNns6Y1LKTwapmUF4IvIuAIzd6LZNOQng64LAKXtKnViJ1JQiXwf4CEzhgvAti3/ejpb3U90hsrUcyZi6wBv9bZLcAJRWpz61JNYliM1d1grSwQDKGXNQE4xuM",
    )],
    radius_servers=[azure_native.network.RadiusServerArgs(
        radius_server_address="10.0.0.0",
        radius_server_score=25,
        radius_server_secret="radiusServerSecret",
    )],
    resource_group_name="rg1",
    tags={
        "key1": "value1",
    },
    vpn_client_ipsec_policies=[azure_native.network.IpsecPolicyArgs(
        dh_group="DHGroup14",
        ike_encryption="AES256",
        ike_integrity="SHA384",
        ipsec_encryption="AES256",
        ipsec_integrity="SHA256",
        pfs_group="PFS14",
        sa_data_size_kilobytes=429497,
        sa_life_time_seconds=86472,
    )],
    vpn_client_revoked_certificates=[azure_native.network.VpnServerConfigVpnClientRevokedCertificateArgs(
        name="vpnServerConfigVpnClientRevokedCert1",
        thumbprint="83FFBFC8848B5A5836C94D0112367E16148A286F",
    )],
    vpn_client_root_certificates=[azure_native.network.VpnServerConfigVpnClientRootCertificateArgs(
        name="vpnServerConfigVpnClientRootCert1",
        public_cert_data="MIIC5zCCAc+gAwIBAgIQErQ0Hk4aDJxIA+Q5RagB+jANBgkqhkiG9w0BAQsFADAWMRQwEgYDVQQDDAtQMlNSb290Q2VydDAeFw0xNzEyMTQyMTA3MzhaFw0xODEyMTQyMTI3MzhaMBYxFDASBgNVBAMMC1AyU1Jvb3RDZXJ0MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEArP7/NQXmW7cQ/ZR1mv3Y3I29Lt7HTOqzo/1KUOoVH3NItbQIRAQbwKy3UWrOFz4eGNX2GWtNRMdCyWsKeqy9Ltsdfcm1IbKXkl84DFeU/ZacXu4Dl3xX3gV5du4TLZjEowJELyur11Ea2YcjPRQ/FzAF9/hGuboS1HZQEPLx4FdUs9OxCYOtc0MxBCwLfVTTRqarb0Ne+arNYd4kCzIhAke1nOyKAJBda5ZL+VHy3S5S8qGlD46jm8HXugmAkUygS4oIIXOmj/1O9sNAi3LN60zufSzCmP8Rm/iUGX+DHAGGiXxwZOKQLEDaZXKqoHjMPP0XudmSWwOIbyeQVrLhkwIDAQABozEwLzAOBgNVHQ8BAf8EBAMCAgQwHQYDVR0OBBYEFEfeNU2trYxNLF9ONmuJUsT13pKDMA0GCSqGSIb3DQEBCwUAA4IBAQBmM6RJzsGGipxyMhimHKN2xlkejhVsgBoTAhOU0llW9aUSwINJ9zFUGgI8IzUFy1VG776fchHp0LMRmPSIUYk5btEPxbsrPtumPuMH8EQGrS+Rt4pD+78c8H1fEPkq5CmDl/PKu4JoFGv+aFcE+Od0hlILstIF10Qysf++QXDolKfzJa/56bgMeYKFiju73loiRM57ns8ddXpfLl792UVpRkFU62LNns6Y1LKTwapmUF4IvIuAIzd6LZNOQng64LAKXtKnViJ1JQiXwf4CEzhgvAti3/ejpb3U90hsrUcyZi6wBv9bZLcAJRWpz61JNYliM1d1grSwQDKGXNQE4xuN",
    )],
    vpn_protocols=["IkeV2"],
    vpn_server_configuration_name="vpnServerConfiguration1")

```

```yaml
resources:
  vpnServerConfiguration:
    type: azure-native:network:VpnServerConfiguration
    properties:
      configurationPolicyGroups:
        - id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/vpnServerConfigurations/vpnServerConfiguration1/vpnServerConfigurationPolicyGroups/policyGroup1
          isDefault: true
          name: policyGroup1
          policyMembers:
            - attributeType: RadiusAzureGroupId
              attributeValue: 6ad1bd08
              name: policy1
          priority: 0
        - id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/vpnServerConfigurations/vpnServerConfiguration1/vpnServerConfigurationPolicyGroups/policyGroup2
          isDefault: true
          name: policyGroup2
          policyMembers:
            - attributeType: CertificateGroupId
              attributeValue: red.com
              name: policy2
          priority: 0
      location: West US
      radiusClientRootCertificates:
        - name: vpnServerConfigRadiusClientRootCert1
          thumbprint: 83FFBFC8848B5A5836C94D0112367E16148A286F
      radiusServerRootCertificates:
        - name: vpnServerConfigRadiusServerRootCer1
          publicCertData: MIIC5zCCAc+gAwIBAgIQErQ0Hk4aDJxIA+Q5RagB+jANBgkqhkiG9w0BAQsFADAWMRQwEgYDVQQDDAtQMlNSb290Q2VydDAeFw0xNzEyMTQyMTA3MzhaFw0xODEyMTQyMTI3MzhaMBYxFDASBgNVBAMMC1AyU1Jvb3RDZXJ0MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEArP7/NQXmW7cQ/ZR1mv3Y3I29Lt7HTOqzo/1KUOoVH3NItbQIRAQbwKy3UWrOFz4eGNX2GWtNRMdCyWsKeqy9Ltsdfcm1IbKXkl84DFeU/ZacXu4Dl3xX3gV5du4TLZjEowJELyur11Ea2YcjPRQ/FzAF9/hGuboS1HZQEPLx4FdUs9OxCYOtc0MxBCwLfVTTRqarb0Ne+arNYd4kCzIhAke1nOyKAJBda5ZL+VHy3S5S8qGlD46jm8HXugmAkUygS4oIIXOmj/1O9sNAi3LN60zufSzCmP8Rm/iUGX+DHAGGiXxwZOKQLEDaZXKqoHjMPP0XudmSWwOIbyeQVrLhkwIDAQABozEwLzAOBgNVHQ8BAf8EBAMCAgQwHQYDVR0OBBYEFEfeNU2trYxNLF9ONmuJUsT13pKDMA0GCSqGSIb3DQEBCwUAA4IBAQBmM6RJzsGGipxyMhimHKN2xlkejhVsgBoTAhOU0llW9aUSwINJ9zFUGgI8IzUFy1VG776fchHp0LMRmPSIUYk5btEPxbsrPtumPuMH8EQGrS+Rt4pD+78c8H1fEPkq5CmDl/PKu4JoFGv+aFcE+Od0hlILstIF10Qysf++QXDolKfzJa/56bgMeYKFiju73loiRM57ns8ddXpfLl792UVpRkFU62LNns6Y1LKTwapmUF4IvIuAIzd6LZNOQng64LAKXtKnViJ1JQiXwf4CEzhgvAti3/ejpb3U90hsrUcyZi6wBv9bZLcAJRWpz61JNYliM1d1grSwQDKGXNQE4xuM
      radiusServers:
        - radiusServerAddress: 10.0.0.0
          radiusServerScore: 25
          radiusServerSecret: radiusServerSecret
      resourceGroupName: rg1
      tags:
        key1: value1
      vpnClientIpsecPolicies:
        - dhGroup: DHGroup14
          ikeEncryption: AES256
          ikeIntegrity: SHA384
          ipsecEncryption: AES256
          ipsecIntegrity: SHA256
          pfsGroup: PFS14
          saDataSizeKilobytes: 429497
          saLifeTimeSeconds: 86472
      vpnClientRevokedCertificates:
        - name: vpnServerConfigVpnClientRevokedCert1
          thumbprint: 83FFBFC8848B5A5836C94D0112367E16148A286F
      vpnClientRootCertificates:
        - name: vpnServerConfigVpnClientRootCert1
          publicCertData: MIIC5zCCAc+gAwIBAgIQErQ0Hk4aDJxIA+Q5RagB+jANBgkqhkiG9w0BAQsFADAWMRQwEgYDVQQDDAtQMlNSb290Q2VydDAeFw0xNzEyMTQyMTA3MzhaFw0xODEyMTQyMTI3MzhaMBYxFDASBgNVBAMMC1AyU1Jvb3RDZXJ0MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEArP7/NQXmW7cQ/ZR1mv3Y3I29Lt7HTOqzo/1KUOoVH3NItbQIRAQbwKy3UWrOFz4eGNX2GWtNRMdCyWsKeqy9Ltsdfcm1IbKXkl84DFeU/ZacXu4Dl3xX3gV5du4TLZjEowJELyur11Ea2YcjPRQ/FzAF9/hGuboS1HZQEPLx4FdUs9OxCYOtc0MxBCwLfVTTRqarb0Ne+arNYd4kCzIhAke1nOyKAJBda5ZL+VHy3S5S8qGlD46jm8HXugmAkUygS4oIIXOmj/1O9sNAi3LN60zufSzCmP8Rm/iUGX+DHAGGiXxwZOKQLEDaZXKqoHjMPP0XudmSWwOIbyeQVrLhkwIDAQABozEwLzAOBgNVHQ8BAf8EBAMCAgQwHQYDVR0OBBYEFEfeNU2trYxNLF9ONmuJUsT13pKDMA0GCSqGSIb3DQEBCwUAA4IBAQBmM6RJzsGGipxyMhimHKN2xlkejhVsgBoTAhOU0llW9aUSwINJ9zFUGgI8IzUFy1VG776fchHp0LMRmPSIUYk5btEPxbsrPtumPuMH8EQGrS+Rt4pD+78c8H1fEPkq5CmDl/PKu4JoFGv+aFcE+Od0hlILstIF10Qysf++QXDolKfzJa/56bgMeYKFiju73loiRM57ns8ddXpfLl792UVpRkFU62LNns6Y1LKTwapmUF4IvIuAIzd6LZNOQng64LAKXtKnViJ1JQiXwf4CEzhgvAti3/ejpb3U90hsrUcyZi6wBv9bZLcAJRWpz61JNYliM1d1grSwQDKGXNQE4xuN
      vpnProtocols:
        - IkeV2
      vpnServerConfigurationName: vpnServerConfiguration1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:VpnServerConfiguration vpnServerConfiguration1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/vpnServerConfigurations/vpnServerConfiguration1 
```
