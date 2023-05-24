A SqlManagedInstance.
API Version: 2023-03-15-preview.
Previous API Version: 2021-06-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a SQL Managed Instance
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sqlManagedInstance = new AzureNative.AzureArcData.SqlManagedInstance("sqlManagedInstance", new()
    {
        ExtendedLocation = new AzureNative.AzureArcData.Inputs.ExtendedLocationArgs
        {
            Name = "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.ExtendedLocation/customLocations/arclocation",
            Type = "CustomLocation",
        },
        Location = "northeurope",
        Properties = new AzureNative.AzureArcData.Inputs.SqlManagedInstancePropertiesArgs
        {
            ActiveDirectoryInformation = new AzureNative.AzureArcData.Inputs.ActiveDirectoryInformationArgs
            {
                KeytabInformation = new AzureNative.AzureArcData.Inputs.KeytabInformationArgs
                {
                    Keytab = "********",
                },
            },
            Admin = "Admin user",
            BasicLoginInformation = new AzureNative.AzureArcData.Inputs.BasicLoginInformationArgs
            {
                Password = "********",
                Username = "username",
            },
            ClusterId = "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Kubernetes/connectedClusters/connectedk8s",
            EndTime = "Instance end time",
            ExtensionId = "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Kubernetes/connectedClusters/connectedk8s/providers/Microsoft.KubernetesConfiguration/extensions/extension",
            K8sRaw = new AzureNative.AzureArcData.Inputs.SqlManagedInstanceK8sRawArgs
            {
                Spec = new AzureNative.AzureArcData.Inputs.SqlManagedInstanceK8sSpecArgs
                {
                    Replicas = 1,
                    Scheduling = new AzureNative.AzureArcData.Inputs.K8sSchedulingArgs
                    {
                        Default = new AzureNative.AzureArcData.Inputs.K8sSchedulingOptionsArgs
                        {
                            Resources = new AzureNative.AzureArcData.Inputs.K8sResourceRequirementsArgs
                            {
                                Limits = 
                                {
                                    { "additionalProperty", "additionalValue" },
                                    { "cpu", "1" },
                                    { "memory", "8Gi" },
                                },
                                Requests = 
                                {
                                    { "additionalProperty", "additionalValue" },
                                    { "cpu", "1" },
                                    { "memory", "8Gi" },
                                },
                            },
                        },
                    },
                },
            },
            LicenseType = "LicenseIncluded",
            StartTime = "Instance start time",
        },
        ResourceGroupName = "testrg",
        Sku = new AzureNative.AzureArcData.Inputs.SqlManagedInstanceSkuArgs
        {
            Dev = true,
            Name = AzureNative.AzureArcData.SqlManagedInstanceSkuName.VCore,
            Tier = AzureNative.AzureArcData.SqlManagedInstanceSkuTier.GeneralPurpose,
        },
        SqlManagedInstanceName = "testsqlManagedInstance",
        Tags = 
        {
            { "mytag", "myval" },
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.azurearcdata.SqlManagedInstance;
import com.pulumi.azurenative.azurearcdata.SqlManagedInstanceArgs;
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
        var sqlManagedInstance = new SqlManagedInstance("sqlManagedInstance", SqlManagedInstanceArgs.builder()        
            .extendedLocation(Map.ofEntries(
                Map.entry("name", "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.ExtendedLocation/customLocations/arclocation"),
                Map.entry("type", "CustomLocation")
            ))
            .location("northeurope")
            .properties(Map.ofEntries(
                Map.entry("activeDirectoryInformation", Map.of("keytabInformation", Map.of("keytab", "********"))),
                Map.entry("admin", "Admin user"),
                Map.entry("basicLoginInformation", Map.ofEntries(
                    Map.entry("password", "********"),
                    Map.entry("username", "username")
                )),
                Map.entry("clusterId", "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Kubernetes/connectedClusters/connectedk8s"),
                Map.entry("endTime", "Instance end time"),
                Map.entry("extensionId", "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Kubernetes/connectedClusters/connectedk8s/providers/Microsoft.KubernetesConfiguration/extensions/extension"),
                Map.entry("k8sRaw", Map.of("spec", Map.ofEntries(
                    Map.entry("replicas", 1),
                    Map.entry("scheduling", Map.of("default", Map.of("resources", Map.ofEntries(
                        Map.entry("limits", Map.ofEntries(
                            Map.entry("additionalProperty", "additionalValue"),
                            Map.entry("cpu", "1"),
                            Map.entry("memory", "8Gi")
                        )),
                        Map.entry("requests", Map.ofEntries(
                            Map.entry("additionalProperty", "additionalValue"),
                            Map.entry("cpu", "1"),
                            Map.entry("memory", "8Gi")
                        ))
                    ))))
                ))),
                Map.entry("licenseType", "LicenseIncluded"),
                Map.entry("startTime", "Instance start time")
            ))
            .resourceGroupName("testrg")
            .sku(Map.ofEntries(
                Map.entry("dev", true),
                Map.entry("name", "vCore"),
                Map.entry("tier", "GeneralPurpose")
            ))
            .sqlManagedInstanceName("testsqlManagedInstance")
            .tags(Map.of("mytag", "myval"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sqlManagedInstance = new azure_native.azurearcdata.SqlManagedInstance("sqlManagedInstance", {
    extendedLocation: {
        name: "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.ExtendedLocation/customLocations/arclocation",
        type: "CustomLocation",
    },
    location: "northeurope",
    properties: {
        activeDirectoryInformation: {
            keytabInformation: {
                keytab: "********",
            },
        },
        admin: "Admin user",
        basicLoginInformation: {
            password: "********",
            username: "username",
        },
        clusterId: "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Kubernetes/connectedClusters/connectedk8s",
        endTime: "Instance end time",
        extensionId: "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Kubernetes/connectedClusters/connectedk8s/providers/Microsoft.KubernetesConfiguration/extensions/extension",
        k8sRaw: {
            spec: {
                replicas: 1,
                scheduling: {
                    "default": {
                        resources: {
                            limits: {
                                additionalProperty: "additionalValue",
                                cpu: "1",
                                memory: "8Gi",
                            },
                            requests: {
                                additionalProperty: "additionalValue",
                                cpu: "1",
                                memory: "8Gi",
                            },
                        },
                    },
                },
            },
        },
        licenseType: "LicenseIncluded",
        startTime: "Instance start time",
    },
    resourceGroupName: "testrg",
    sku: {
        dev: true,
        name: azure_native.azurearcdata.SqlManagedInstanceSkuName.VCore,
        tier: azure_native.azurearcdata.SqlManagedInstanceSkuTier.GeneralPurpose,
    },
    sqlManagedInstanceName: "testsqlManagedInstance",
    tags: {
        mytag: "myval",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sql_managed_instance = azure_native.azurearcdata.SqlManagedInstance("sqlManagedInstance",
    extended_location=azure_native.azurearcdata.ExtendedLocationArgs(
        name="/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.ExtendedLocation/customLocations/arclocation",
        type="CustomLocation",
    ),
    location="northeurope",
    properties=azure_native.azurearcdata.SqlManagedInstancePropertiesResponseArgs(
        active_directory_information=azure_native.azurearcdata.ActiveDirectoryInformationArgs(
            keytab_information=azure_native.azurearcdata.KeytabInformationArgs(
                keytab="********",
            ),
        ),
        admin="Admin user",
        basic_login_information=azure_native.azurearcdata.BasicLoginInformationArgs(
            password="********",
            username="username",
        ),
        cluster_id="/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Kubernetes/connectedClusters/connectedk8s",
        end_time="Instance end time",
        extension_id="/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Kubernetes/connectedClusters/connectedk8s/providers/Microsoft.KubernetesConfiguration/extensions/extension",
        k8s_raw={
            "spec": {
                "replicas": 1,
                "scheduling": {
                    "default": {
                        "resources": azure_native.azurearcdata.K8sResourceRequirementsArgs(
                            limits={
                                "additionalProperty": "additionalValue",
                                "cpu": "1",
                                "memory": "8Gi",
                            },
                            requests={
                                "additionalProperty": "additionalValue",
                                "cpu": "1",
                                "memory": "8Gi",
                            },
                        ),
                    },
                },
            },
        },
        license_type="LicenseIncluded",
        start_time="Instance start time",
    ),
    resource_group_name="testrg",
    sku=azure_native.azurearcdata.SqlManagedInstanceSkuArgs(
        dev=True,
        name=azure_native.azurearcdata.SqlManagedInstanceSkuName.V_CORE,
        tier=azure_native.azurearcdata.SqlManagedInstanceSkuTier.GENERAL_PURPOSE,
    ),
    sql_managed_instance_name="testsqlManagedInstance",
    tags={
        "mytag": "myval",
    })

```

```yaml
resources:
  sqlManagedInstance:
    type: azure-native:azurearcdata:SqlManagedInstance
    properties:
      extendedLocation:
        name: /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.ExtendedLocation/customLocations/arclocation
        type: CustomLocation
      location: northeurope
      properties:
        activeDirectoryInformation:
          keytabInformation:
            keytab: '********'
        admin: Admin user
        basicLoginInformation:
          password: '********'
          username: username
        clusterId: /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Kubernetes/connectedClusters/connectedk8s
        endTime: Instance end time
        extensionId: /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.Kubernetes/connectedClusters/connectedk8s/providers/Microsoft.KubernetesConfiguration/extensions/extension
        k8sRaw:
          spec:
            replicas: 1
            scheduling:
              default:
                resources:
                  limits:
                    additionalProperty: additionalValue
                    cpu: '1'
                    memory: 8Gi
                  requests:
                    additionalProperty: additionalValue
                    cpu: '1'
                    memory: 8Gi
        licenseType: LicenseIncluded
        startTime: Instance start time
      resourceGroupName: testrg
      sku:
        dev: true
        name: vCore
        tier: GeneralPurpose
      sqlManagedInstanceName: testsqlManagedInstance
      tags:
        mytag: myval

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:azurearcdata:SqlManagedInstance testsqlManagedInstance /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.AzureArcData/sqlManagedInstances/testsqlManagedInstance 
```
