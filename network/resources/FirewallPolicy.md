FirewallPolicy Resource.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create FirewallPolicy
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var firewallPolicy = new AzureNative.Network.FirewallPolicy("firewallPolicy", new()
    {
        DnsSettings = new AzureNative.Network.Inputs.DnsSettingsArgs
        {
            EnableProxy = true,
            RequireProxyForNetworkRules = false,
            Servers = new[]
            {
                "30.3.4.5",
            },
        },
        ExplicitProxy = new AzureNative.Network.Inputs.ExplicitProxyArgs
        {
            EnableExplicitProxy = true,
            EnablePacFile = true,
            HttpPort = 8087,
            HttpsPort = 8087,
            PacFile = "https://tinawstorage.file.core.windows.net/?sv=2020-02-10&ss=bfqt&srt=sco&sp=rwdlacuptfx&se=2021-06-04T07:01:12Z&st=2021-06-03T23:01:12Z&sip=68.65.171.11&spr=https&sig=Plsa0RRVpGbY0IETZZOT6znOHcSro71LLTTbzquYPgs%3D",
            PacFilePort = 8087,
        },
        FirewallPolicyName = "firewallPolicy",
        Insights = new AzureNative.Network.Inputs.FirewallPolicyInsightsArgs
        {
            IsEnabled = true,
            LogAnalyticsResources = new AzureNative.Network.Inputs.FirewallPolicyLogAnalyticsResourcesArgs
            {
                DefaultWorkspaceId = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourcegroups/rg1/providers/microsoft.operationalinsights/workspaces/defaultWorkspace",
                },
                Workspaces = new[]
                {
                    new AzureNative.Network.Inputs.FirewallPolicyLogAnalyticsWorkspaceArgs
                    {
                        Region = "westus",
                        WorkspaceId = new AzureNative.Network.Inputs.SubResourceArgs
                        {
                            Id = "/subscriptions/subid/resourcegroups/rg1/providers/microsoft.operationalinsights/workspaces/workspace1",
                        },
                    },
                    new AzureNative.Network.Inputs.FirewallPolicyLogAnalyticsWorkspaceArgs
                    {
                        Region = "eastus",
                        WorkspaceId = new AzureNative.Network.Inputs.SubResourceArgs
                        {
                            Id = "/subscriptions/subid/resourcegroups/rg1/providers/microsoft.operationalinsights/workspaces/workspace2",
                        },
                    },
                },
            },
            RetentionDays = 100,
        },
        IntrusionDetection = new AzureNative.Network.Inputs.FirewallPolicyIntrusionDetectionArgs
        {
            Configuration = new AzureNative.Network.Inputs.FirewallPolicyIntrusionDetectionConfigurationArgs
            {
                BypassTrafficSettings = new[]
                {
                    new AzureNative.Network.Inputs.FirewallPolicyIntrusionDetectionBypassTrafficSpecificationsArgs
                    {
                        Description = "Rule 1",
                        DestinationAddresses = new[]
                        {
                            "5.6.7.8",
                        },
                        DestinationPorts = new[]
                        {
                            "*",
                        },
                        Name = "bypassRule1",
                        Protocol = "TCP",
                        SourceAddresses = new[]
                        {
                            "1.2.3.4",
                        },
                    },
                },
                SignatureOverrides = new[]
                {
                    new AzureNative.Network.Inputs.FirewallPolicyIntrusionDetectionSignatureSpecificationArgs
                    {
                        Id = "2525004",
                        Mode = "Deny",
                    },
                },
            },
            Mode = "Alert",
        },
        Location = "West US",
        ResourceGroupName = "rg1",
        Sku = new AzureNative.Network.Inputs.FirewallPolicySkuArgs
        {
            Tier = "Premium",
        },
        Snat = new AzureNative.Network.Inputs.FirewallPolicySNATArgs
        {
            PrivateRanges = new[]
            {
                "IANAPrivateRanges",
            },
        },
        Sql = new AzureNative.Network.Inputs.FirewallPolicySQLArgs
        {
            AllowSqlRedirect = true,
        },
        Tags = 
        {
            { "key1", "value1" },
        },
        ThreatIntelMode = "Alert",
        ThreatIntelWhitelist = new AzureNative.Network.Inputs.FirewallPolicyThreatIntelWhitelistArgs
        {
            Fqdns = new[]
            {
                "*.microsoft.com",
            },
            IpAddresses = new[]
            {
                "20.3.4.5",
            },
        },
        TransportSecurity = new AzureNative.Network.Inputs.FirewallPolicyTransportSecurityArgs
        {
            CertificateAuthority = new AzureNative.Network.Inputs.FirewallPolicyCertificateAuthorityArgs
            {
                KeyVaultSecretId = "https://kv/secret",
                Name = "clientcert",
            },
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.network.FirewallPolicy;
import com.pulumi.azurenative.network.FirewallPolicyArgs;
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
        var firewallPolicy = new FirewallPolicy("firewallPolicy", FirewallPolicyArgs.builder()        
            .dnsSettings(Map.ofEntries(
                Map.entry("enableProxy", true),
                Map.entry("requireProxyForNetworkRules", false),
                Map.entry("servers", "30.3.4.5")
            ))
            .explicitProxy(Map.ofEntries(
                Map.entry("enableExplicitProxy", true),
                Map.entry("enablePacFile", true),
                Map.entry("httpPort", 8087),
                Map.entry("httpsPort", 8087),
                Map.entry("pacFile", "https://tinawstorage.file.core.windows.net/?sv=2020-02-10&ss=bfqt&srt=sco&sp=rwdlacuptfx&se=2021-06-04T07:01:12Z&st=2021-06-03T23:01:12Z&sip=68.65.171.11&spr=https&sig=Plsa0RRVpGbY0IETZZOT6znOHcSro71LLTTbzquYPgs%3D"),
                Map.entry("pacFilePort", 8087)
            ))
            .firewallPolicyName("firewallPolicy")
            .insights(Map.ofEntries(
                Map.entry("isEnabled", true),
                Map.entry("logAnalyticsResources", Map.ofEntries(
                    Map.entry("defaultWorkspaceId", Map.of("id", "/subscriptions/subid/resourcegroups/rg1/providers/microsoft.operationalinsights/workspaces/defaultWorkspace")),
                    Map.entry("workspaces",                     
                        Map.ofEntries(
                            Map.entry("region", "westus"),
                            Map.entry("workspaceId", Map.of("id", "/subscriptions/subid/resourcegroups/rg1/providers/microsoft.operationalinsights/workspaces/workspace1"))
                        ),
                        Map.ofEntries(
                            Map.entry("region", "eastus"),
                            Map.entry("workspaceId", Map.of("id", "/subscriptions/subid/resourcegroups/rg1/providers/microsoft.operationalinsights/workspaces/workspace2"))
                        ))
                )),
                Map.entry("retentionDays", 100)
            ))
            .intrusionDetection(Map.ofEntries(
                Map.entry("configuration", Map.ofEntries(
                    Map.entry("bypassTrafficSettings", Map.ofEntries(
                        Map.entry("description", "Rule 1"),
                        Map.entry("destinationAddresses", "5.6.7.8"),
                        Map.entry("destinationPorts", "*"),
                        Map.entry("name", "bypassRule1"),
                        Map.entry("protocol", "TCP"),
                        Map.entry("sourceAddresses", "1.2.3.4")
                    )),
                    Map.entry("signatureOverrides", Map.ofEntries(
                        Map.entry("id", "2525004"),
                        Map.entry("mode", "Deny")
                    ))
                )),
                Map.entry("mode", "Alert")
            ))
            .location("West US")
            .resourceGroupName("rg1")
            .sku(Map.of("tier", "Premium"))
            .snat(Map.of("privateRanges", "IANAPrivateRanges"))
            .sql(Map.of("allowSqlRedirect", true))
            .tags(Map.of("key1", "value1"))
            .threatIntelMode("Alert")
            .threatIntelWhitelist(Map.ofEntries(
                Map.entry("fqdns", "*.microsoft.com"),
                Map.entry("ipAddresses", "20.3.4.5")
            ))
            .transportSecurity(Map.of("certificateAuthority", Map.ofEntries(
                Map.entry("keyVaultSecretId", "https://kv/secret"),
                Map.entry("name", "clientcert")
            )))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const firewallPolicy = new azure_native.network.FirewallPolicy("firewallPolicy", {
    dnsSettings: {
        enableProxy: true,
        requireProxyForNetworkRules: false,
        servers: ["30.3.4.5"],
    },
    explicitProxy: {
        enableExplicitProxy: true,
        enablePacFile: true,
        httpPort: 8087,
        httpsPort: 8087,
        pacFile: "https://tinawstorage.file.core.windows.net/?sv=2020-02-10&ss=bfqt&srt=sco&sp=rwdlacuptfx&se=2021-06-04T07:01:12Z&st=2021-06-03T23:01:12Z&sip=68.65.171.11&spr=https&sig=Plsa0RRVpGbY0IETZZOT6znOHcSro71LLTTbzquYPgs%3D",
        pacFilePort: 8087,
    },
    firewallPolicyName: "firewallPolicy",
    insights: {
        isEnabled: true,
        logAnalyticsResources: {
            defaultWorkspaceId: {
                id: "/subscriptions/subid/resourcegroups/rg1/providers/microsoft.operationalinsights/workspaces/defaultWorkspace",
            },
            workspaces: [
                {
                    region: "westus",
                    workspaceId: {
                        id: "/subscriptions/subid/resourcegroups/rg1/providers/microsoft.operationalinsights/workspaces/workspace1",
                    },
                },
                {
                    region: "eastus",
                    workspaceId: {
                        id: "/subscriptions/subid/resourcegroups/rg1/providers/microsoft.operationalinsights/workspaces/workspace2",
                    },
                },
            ],
        },
        retentionDays: 100,
    },
    intrusionDetection: {
        configuration: {
            bypassTrafficSettings: [{
                description: "Rule 1",
                destinationAddresses: ["5.6.7.8"],
                destinationPorts: ["*"],
                name: "bypassRule1",
                protocol: "TCP",
                sourceAddresses: ["1.2.3.4"],
            }],
            signatureOverrides: [{
                id: "2525004",
                mode: "Deny",
            }],
        },
        mode: "Alert",
    },
    location: "West US",
    resourceGroupName: "rg1",
    sku: {
        tier: "Premium",
    },
    snat: {
        privateRanges: ["IANAPrivateRanges"],
    },
    sql: {
        allowSqlRedirect: true,
    },
    tags: {
        key1: "value1",
    },
    threatIntelMode: "Alert",
    threatIntelWhitelist: {
        fqdns: ["*.microsoft.com"],
        ipAddresses: ["20.3.4.5"],
    },
    transportSecurity: {
        certificateAuthority: {
            keyVaultSecretId: "https://kv/secret",
            name: "clientcert",
        },
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

firewall_policy = azure_native.network.FirewallPolicy("firewallPolicy",
    dns_settings=azure_native.network.DnsSettingsArgs(
        enable_proxy=True,
        require_proxy_for_network_rules=False,
        servers=["30.3.4.5"],
    ),
    explicit_proxy=azure_native.network.ExplicitProxyArgs(
        enable_explicit_proxy=True,
        enable_pac_file=True,
        http_port=8087,
        https_port=8087,
        pac_file="https://tinawstorage.file.core.windows.net/?sv=2020-02-10&ss=bfqt&srt=sco&sp=rwdlacuptfx&se=2021-06-04T07:01:12Z&st=2021-06-03T23:01:12Z&sip=68.65.171.11&spr=https&sig=Plsa0RRVpGbY0IETZZOT6znOHcSro71LLTTbzquYPgs%3D",
        pac_file_port=8087,
    ),
    firewall_policy_name="firewallPolicy",
    insights=azure_native.network.FirewallPolicyInsightsResponseArgs(
        is_enabled=True,
        log_analytics_resources={
            "defaultWorkspaceId": azure_native.network.SubResourceArgs(
                id="/subscriptions/subid/resourcegroups/rg1/providers/microsoft.operationalinsights/workspaces/defaultWorkspace",
            ),
            "workspaces": [
                {
                    "region": "westus",
                    "workspaceId": azure_native.network.SubResourceArgs(
                        id="/subscriptions/subid/resourcegroups/rg1/providers/microsoft.operationalinsights/workspaces/workspace1",
                    ),
                },
                {
                    "region": "eastus",
                    "workspaceId": azure_native.network.SubResourceArgs(
                        id="/subscriptions/subid/resourcegroups/rg1/providers/microsoft.operationalinsights/workspaces/workspace2",
                    ),
                },
            ],
        },
        retention_days=100,
    ),
    intrusion_detection=azure_native.network.FirewallPolicyIntrusionDetectionResponseArgs(
        configuration={
            "bypassTrafficSettings": [azure_native.network.FirewallPolicyIntrusionDetectionBypassTrafficSpecificationsArgs(
                description="Rule 1",
                destination_addresses=["5.6.7.8"],
                destination_ports=["*"],
                name="bypassRule1",
                protocol="TCP",
                source_addresses=["1.2.3.4"],
            )],
            "signatureOverrides": [azure_native.network.FirewallPolicyIntrusionDetectionSignatureSpecificationArgs(
                id="2525004",
                mode="Deny",
            )],
        },
        mode="Alert",
    ),
    location="West US",
    resource_group_name="rg1",
    sku=azure_native.network.FirewallPolicySkuArgs(
        tier="Premium",
    ),
    snat=azure_native.network.FirewallPolicySNATArgs(
        private_ranges=["IANAPrivateRanges"],
    ),
    sql=azure_native.network.FirewallPolicySQLArgs(
        allow_sql_redirect=True,
    ),
    tags={
        "key1": "value1",
    },
    threat_intel_mode="Alert",
    threat_intel_whitelist=azure_native.network.FirewallPolicyThreatIntelWhitelistArgs(
        fqdns=["*.microsoft.com"],
        ip_addresses=["20.3.4.5"],
    ),
    transport_security=azure_native.network.FirewallPolicyTransportSecurityResponseArgs(
        certificate_authority=azure_native.network.FirewallPolicyCertificateAuthorityArgs(
            key_vault_secret_id="https://kv/secret",
            name="clientcert",
        ),
    ))

```

```yaml
resources:
  firewallPolicy:
    type: azure-native:network:FirewallPolicy
    properties:
      dnsSettings:
        enableProxy: true
        requireProxyForNetworkRules: false
        servers:
          - 30.3.4.5
      explicitProxy:
        enableExplicitProxy: true
        enablePacFile: true
        httpPort: 8087
        httpsPort: 8087
        pacFile: https://tinawstorage.file.core.windows.net/?sv=2020-02-10&ss=bfqt&srt=sco&sp=rwdlacuptfx&se=2021-06-04T07:01:12Z&st=2021-06-03T23:01:12Z&sip=68.65.171.11&spr=https&sig=Plsa0RRVpGbY0IETZZOT6znOHcSro71LLTTbzquYPgs%3D
        pacFilePort: 8087
      firewallPolicyName: firewallPolicy
      insights:
        isEnabled: true
        logAnalyticsResources:
          defaultWorkspaceId:
            id: /subscriptions/subid/resourcegroups/rg1/providers/microsoft.operationalinsights/workspaces/defaultWorkspace
          workspaces:
            - region: westus
              workspaceId:
                id: /subscriptions/subid/resourcegroups/rg1/providers/microsoft.operationalinsights/workspaces/workspace1
            - region: eastus
              workspaceId:
                id: /subscriptions/subid/resourcegroups/rg1/providers/microsoft.operationalinsights/workspaces/workspace2
        retentionDays: 100
      intrusionDetection:
        configuration:
          bypassTrafficSettings:
            - description: Rule 1
              destinationAddresses:
                - 5.6.7.8
              destinationPorts:
                - '*'
              name: bypassRule1
              protocol: TCP
              sourceAddresses:
                - 1.2.3.4
          signatureOverrides:
            - id: '2525004'
              mode: Deny
        mode: Alert
      location: West US
      resourceGroupName: rg1
      sku:
        tier: Premium
      snat:
        privateRanges:
          - IANAPrivateRanges
      sql:
        allowSqlRedirect: true
      tags:
        key1: value1
      threatIntelMode: Alert
      threatIntelWhitelist:
        fqdns:
          - '*.microsoft.com'
        ipAddresses:
          - 20.3.4.5
      transportSecurity:
        certificateAuthority:
          keyVaultSecretId: https://kv/secret
          name: clientcert

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:FirewallPolicy firewallPolicy /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/firewallPolicies/firewallPolicy 
```
