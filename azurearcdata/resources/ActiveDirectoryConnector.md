Active directory connector resource
API Version: 2023-03-15-preview.
Previous API Version: 2022-03-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update an Active Directory connector instance.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var activeDirectoryConnector = new AzureNative.AzureArcData.ActiveDirectoryConnector("activeDirectoryConnector", new()
    {
        ActiveDirectoryConnectorName = "testADConnector",
        DataControllerName = "testdataController",
        Properties = new AzureNative.AzureArcData.Inputs.ActiveDirectoryConnectorPropertiesArgs
        {
            Spec = new AzureNative.AzureArcData.Inputs.ActiveDirectoryConnectorSpecArgs
            {
                ActiveDirectory = new AzureNative.AzureArcData.Inputs.ActiveDirectoryConnectorDomainDetailsArgs
                {
                    DomainControllers = new AzureNative.AzureArcData.Inputs.ActiveDirectoryDomainControllersArgs
                    {
                        PrimaryDomainController = new AzureNative.AzureArcData.Inputs.ActiveDirectoryDomainControllerArgs
                        {
                            Hostname = "dc1.contoso.local",
                        },
                        SecondaryDomainControllers = new[]
                        {
                            new AzureNative.AzureArcData.Inputs.ActiveDirectoryDomainControllerArgs
                            {
                                Hostname = "dc2.contoso.local",
                            },
                            new AzureNative.AzureArcData.Inputs.ActiveDirectoryDomainControllerArgs
                            {
                                Hostname = "dc3.contoso.local",
                            },
                        },
                    },
                    Realm = "CONTOSO.LOCAL",
                    ServiceAccountProvisioning = "manual",
                },
                Dns = new AzureNative.AzureArcData.Inputs.ActiveDirectoryConnectorDNSDetailsArgs
                {
                    NameserverIPAddresses = new[]
                    {
                        "11.11.111.111",
                        "22.22.222.222",
                    },
                    PreferK8sDnsForPtrLookups = false,
                    Replicas = 1,
                },
            },
        },
        ResourceGroupName = "testrg",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.azurearcdata.ActiveDirectoryConnector;
import com.pulumi.azurenative.azurearcdata.ActiveDirectoryConnectorArgs;
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
        var activeDirectoryConnector = new ActiveDirectoryConnector("activeDirectoryConnector", ActiveDirectoryConnectorArgs.builder()        
            .activeDirectoryConnectorName("testADConnector")
            .dataControllerName("testdataController")
            .properties(Map.of("spec", Map.ofEntries(
                Map.entry("activeDirectory", Map.ofEntries(
                    Map.entry("domainControllers", Map.ofEntries(
                        Map.entry("primaryDomainController", Map.of("hostname", "dc1.contoso.local")),
                        Map.entry("secondaryDomainControllers",                         
                            Map.of("hostname", "dc2.contoso.local"),
                            Map.of("hostname", "dc3.contoso.local"))
                    )),
                    Map.entry("realm", "CONTOSO.LOCAL"),
                    Map.entry("serviceAccountProvisioning", "manual")
                )),
                Map.entry("dns", Map.ofEntries(
                    Map.entry("nameserverIPAddresses",                     
                        "11.11.111.111",
                        "22.22.222.222"),
                    Map.entry("preferK8sDnsForPtrLookups", false),
                    Map.entry("replicas", 1)
                ))
            )))
            .resourceGroupName("testrg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const activeDirectoryConnector = new azure_native.azurearcdata.ActiveDirectoryConnector("activeDirectoryConnector", {
    activeDirectoryConnectorName: "testADConnector",
    dataControllerName: "testdataController",
    properties: {
        spec: {
            activeDirectory: {
                domainControllers: {
                    primaryDomainController: {
                        hostname: "dc1.contoso.local",
                    },
                    secondaryDomainControllers: [
                        {
                            hostname: "dc2.contoso.local",
                        },
                        {
                            hostname: "dc3.contoso.local",
                        },
                    ],
                },
                realm: "CONTOSO.LOCAL",
                serviceAccountProvisioning: "manual",
            },
            dns: {
                nameserverIPAddresses: [
                    "11.11.111.111",
                    "22.22.222.222",
                ],
                preferK8sDnsForPtrLookups: false,
                replicas: 1,
            },
        },
    },
    resourceGroupName: "testrg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

active_directory_connector = azure_native.azurearcdata.ActiveDirectoryConnector("activeDirectoryConnector",
    active_directory_connector_name="testADConnector",
    data_controller_name="testdataController",
    properties=azure_native.azurearcdata.ActiveDirectoryConnectorPropertiesResponseArgs(
        spec={
            "activeDirectory": {
                "domainControllers": {
                    "primaryDomainController": azure_native.azurearcdata.ActiveDirectoryDomainControllerArgs(
                        hostname="dc1.contoso.local",
                    ),
                    "secondaryDomainControllers": [
                        azure_native.azurearcdata.ActiveDirectoryDomainControllerArgs(
                            hostname="dc2.contoso.local",
                        ),
                        azure_native.azurearcdata.ActiveDirectoryDomainControllerArgs(
                            hostname="dc3.contoso.local",
                        ),
                    ],
                },
                "realm": "CONTOSO.LOCAL",
                "serviceAccountProvisioning": "manual",
            },
            "dns": azure_native.azurearcdata.ActiveDirectoryConnectorDNSDetailsArgs(
                nameserver_ip_addresses=[
                    "11.11.111.111",
                    "22.22.222.222",
                ],
                prefer_k8s_dns_for_ptr_lookups=False,
                replicas=1,
            ),
        },
    ),
    resource_group_name="testrg")

```

```yaml
resources:
  activeDirectoryConnector:
    type: azure-native:azurearcdata:ActiveDirectoryConnector
    properties:
      activeDirectoryConnectorName: testADConnector
      dataControllerName: testdataController
      properties:
        spec:
          activeDirectory:
            domainControllers:
              primaryDomainController:
                hostname: dc1.contoso.local
              secondaryDomainControllers:
                - hostname: dc2.contoso.local
                - hostname: dc3.contoso.local
            realm: CONTOSO.LOCAL
            serviceAccountProvisioning: manual
          dns:
            nameserverIPAddresses:
              - 11.11.111.111
              - 22.22.222.222
            preferK8sDnsForPtrLookups: false
            replicas: 1
      resourceGroupName: testrg

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:azurearcdata:ActiveDirectoryConnector testADConnector /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.AzureArcData/dataControllers/testdataController/activeDirectoryConnectors/testADConnector 
```
