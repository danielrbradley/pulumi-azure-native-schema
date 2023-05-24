The HDInsight cluster.
API Version: 2021-06-01.
Previous API Version: 2018-06-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create HDInsight cluster with Autoscale configuration
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var cluster = new AzureNative.HDInsight.Cluster("cluster", new()
    {
        ClusterName = "cluster1",
        Properties = new AzureNative.HDInsight.Inputs.ClusterCreatePropertiesArgs
        {
            ClusterDefinition = new AzureNative.HDInsight.Inputs.ClusterDefinitionArgs
            {
                ComponentVersion = 
                {
                    { "Hadoop", "2.7" },
                },
                Configurations = 
                {
                    { "gateway", 
                    {
                        { "restAuthCredential.isEnabled", true },
                        { "restAuthCredential.password", "**********" },
                        { "restAuthCredential.username", "admin" },
                    } },
                },
                Kind = "hadoop",
            },
            ClusterVersion = "3.6",
            ComputeProfile = new AzureNative.HDInsight.Inputs.ComputeProfileArgs
            {
                Roles = new[]
                {
                    new AzureNative.HDInsight.Inputs.RoleArgs
                    {
                        AutoscaleConfiguration = new AzureNative.HDInsight.Inputs.AutoscaleArgs
                        {
                            Recurrence = new AzureNative.HDInsight.Inputs.AutoscaleRecurrenceArgs
                            {
                                Schedule = new[]
                                {
                                    new AzureNative.HDInsight.Inputs.AutoscaleScheduleArgs
                                    {
                                        Days = new[]
                                        {
                                            "Monday",
                                            "Tuesday",
                                            "Wednesday",
                                            "Thursday",
                                            "Friday",
                                        },
                                        TimeAndCapacity = new AzureNative.HDInsight.Inputs.AutoscaleTimeAndCapacityArgs
                                        {
                                            MaxInstanceCount = 3,
                                            MinInstanceCount = 3,
                                            Time = "09:00",
                                        },
                                    },
                                    new AzureNative.HDInsight.Inputs.AutoscaleScheduleArgs
                                    {
                                        Days = new[]
                                        {
                                            "Monday",
                                            "Tuesday",
                                            "Wednesday",
                                            "Thursday",
                                            "Friday",
                                        },
                                        TimeAndCapacity = new AzureNative.HDInsight.Inputs.AutoscaleTimeAndCapacityArgs
                                        {
                                            MaxInstanceCount = 6,
                                            MinInstanceCount = 6,
                                            Time = "18:00",
                                        },
                                    },
                                    new AzureNative.HDInsight.Inputs.AutoscaleScheduleArgs
                                    {
                                        Days = new[]
                                        {
                                            "Saturday",
                                            "Sunday",
                                        },
                                        TimeAndCapacity = new AzureNative.HDInsight.Inputs.AutoscaleTimeAndCapacityArgs
                                        {
                                            MaxInstanceCount = 2,
                                            MinInstanceCount = 2,
                                            Time = "09:00",
                                        },
                                    },
                                    new AzureNative.HDInsight.Inputs.AutoscaleScheduleArgs
                                    {
                                        Days = new[]
                                        {
                                            "Saturday",
                                            "Sunday",
                                        },
                                        TimeAndCapacity = new AzureNative.HDInsight.Inputs.AutoscaleTimeAndCapacityArgs
                                        {
                                            MaxInstanceCount = 4,
                                            MinInstanceCount = 4,
                                            Time = "18:00",
                                        },
                                    },
                                },
                                TimeZone = "China Standard Time",
                            },
                        },
                        HardwareProfile = new AzureNative.HDInsight.Inputs.HardwareProfileArgs
                        {
                            VmSize = "Standard_D4_V2",
                        },
                        Name = "workernode",
                        OsProfile = new AzureNative.HDInsight.Inputs.OsProfileArgs
                        {
                            LinuxOperatingSystemProfile = new AzureNative.HDInsight.Inputs.LinuxOperatingSystemProfileArgs
                            {
                                Password = "**********",
                                Username = "sshuser",
                            },
                        },
                        ScriptActions = new[] {},
                        TargetInstanceCount = 4,
                    },
                },
            },
            OsType = "Linux",
            StorageProfile = new AzureNative.HDInsight.Inputs.StorageProfileArgs
            {
                Storageaccounts = new[]
                {
                    new AzureNative.HDInsight.Inputs.StorageAccountArgs
                    {
                        Container = "hdinsight-autoscale-tes-2019-06-18t05-49-16-591z",
                        IsDefault = true,
                        Key = "storagekey",
                        Name = "mystorage.blob.core.windows.net",
                    },
                },
            },
            Tier = "Standard",
        },
        ResourceGroupName = "rg1",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.hdinsight.Cluster;
import com.pulumi.azurenative.hdinsight.ClusterArgs;
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
        var cluster = new Cluster("cluster", ClusterArgs.builder()        
            .clusterName("cluster1")
            .properties(Map.ofEntries(
                Map.entry("clusterDefinition", Map.ofEntries(
                    Map.entry("componentVersion", Map.of("Hadoop", "2.7")),
                    Map.entry("configurations", Map.of("gateway", ClusterCreatePropertiesArgs.builder()
%!v(PANIC=Format method: interface conversion: model.Expression is *model.TemplateExpression, not *model.LiteralValueExpression))),
                        Map.entry("kind", "hadoop")
                    )),
                    Map.entry("clusterVersion", "3.6"),
                    Map.entry("computeProfile", Map.of("roles", Map.ofEntries(
                        Map.entry("autoscaleConfiguration", Map.of("recurrence", Map.ofEntries(
                            Map.entry("schedule",                             
                                Map.ofEntries(
                                    Map.entry("days",                                     
                                        "Monday",
                                        "Tuesday",
                                        "Wednesday",
                                        "Thursday",
                                        "Friday"),
                                    Map.entry("timeAndCapacity", Map.ofEntries(
                                        Map.entry("maxInstanceCount", 3),
                                        Map.entry("minInstanceCount", 3),
                                        Map.entry("time", "09:00")
                                    ))
                                ),
                                Map.ofEntries(
                                    Map.entry("days",                                     
                                        "Monday",
                                        "Tuesday",
                                        "Wednesday",
                                        "Thursday",
                                        "Friday"),
                                    Map.entry("timeAndCapacity", Map.ofEntries(
                                        Map.entry("maxInstanceCount", 6),
                                        Map.entry("minInstanceCount", 6),
                                        Map.entry("time", "18:00")
                                    ))
                                ),
                                Map.ofEntries(
                                    Map.entry("days",                                     
                                        "Saturday",
                                        "Sunday"),
                                    Map.entry("timeAndCapacity", Map.ofEntries(
                                        Map.entry("maxInstanceCount", 2),
                                        Map.entry("minInstanceCount", 2),
                                        Map.entry("time", "09:00")
                                    ))
                                ),
                                Map.ofEntries(
                                    Map.entry("days",                                     
                                        "Saturday",
                                        "Sunday"),
                                    Map.entry("timeAndCapacity", Map.ofEntries(
                                        Map.entry("maxInstanceCount", 4),
                                        Map.entry("minInstanceCount", 4),
                                        Map.entry("time", "18:00")
                                    ))
                                )),
                            Map.entry("timeZone", "China Standard Time")
                        ))),
                        Map.entry("hardwareProfile", Map.of("vmSize", "Standard_D4_V2")),
                        Map.entry("name", "workernode"),
                        Map.entry("osProfile", Map.of("linuxOperatingSystemProfile", Map.ofEntries(
                            Map.entry("password", "**********"),
                            Map.entry("username", "sshuser")
                        ))),
                        Map.entry("scriptActions", ),
                        Map.entry("targetInstanceCount", 4)
                    ))),
                    Map.entry("osType", "Linux"),
                    Map.entry("storageProfile", Map.of("storageaccounts", Map.ofEntries(
                        Map.entry("container", "hdinsight-autoscale-tes-2019-06-18t05-49-16-591z"),
                        Map.entry("isDefault", true),
                        Map.entry("key", "storagekey"),
                        Map.entry("name", "mystorage.blob.core.windows.net")
                    ))),
                    Map.entry("tier", "Standard")
                ))
                .resourceGroupName("rg1")
                .build());

        }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const cluster = new azure_native.hdinsight.Cluster("cluster", {
    clusterName: "cluster1",
    properties: {
        clusterDefinition: {
            componentVersion: {
                Hadoop: "2.7",
            },
            configurations: {
                gateway: {
                    "restAuthCredential.isEnabled": true,
                    "restAuthCredential.password": "**********",
                    "restAuthCredential.username": "admin",
                },
            },
            kind: "hadoop",
        },
        clusterVersion: "3.6",
        computeProfile: {
            roles: [{
                autoscaleConfiguration: {
                    recurrence: {
                        schedule: [
                            {
                                days: [
                                    "Monday",
                                    "Tuesday",
                                    "Wednesday",
                                    "Thursday",
                                    "Friday",
                                ],
                                timeAndCapacity: {
                                    maxInstanceCount: 3,
                                    minInstanceCount: 3,
                                    time: "09:00",
                                },
                            },
                            {
                                days: [
                                    "Monday",
                                    "Tuesday",
                                    "Wednesday",
                                    "Thursday",
                                    "Friday",
                                ],
                                timeAndCapacity: {
                                    maxInstanceCount: 6,
                                    minInstanceCount: 6,
                                    time: "18:00",
                                },
                            },
                            {
                                days: [
                                    "Saturday",
                                    "Sunday",
                                ],
                                timeAndCapacity: {
                                    maxInstanceCount: 2,
                                    minInstanceCount: 2,
                                    time: "09:00",
                                },
                            },
                            {
                                days: [
                                    "Saturday",
                                    "Sunday",
                                ],
                                timeAndCapacity: {
                                    maxInstanceCount: 4,
                                    minInstanceCount: 4,
                                    time: "18:00",
                                },
                            },
                        ],
                        timeZone: "China Standard Time",
                    },
                },
                hardwareProfile: {
                    vmSize: "Standard_D4_V2",
                },
                name: "workernode",
                osProfile: {
                    linuxOperatingSystemProfile: {
                        password: "**********",
                        username: "sshuser",
                    },
                },
                scriptActions: [],
                targetInstanceCount: 4,
            }],
        },
        osType: "Linux",
        storageProfile: {
            storageaccounts: [{
                container: "hdinsight-autoscale-tes-2019-06-18t05-49-16-591z",
                isDefault: true,
                key: "storagekey",
                name: "mystorage.blob.core.windows.net",
            }],
        },
        tier: "Standard",
    },
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

cluster = azure_native.hdinsight.Cluster("cluster",
    cluster_name="cluster1",
    properties=azure_native.hdinsight.ClusterGetPropertiesResponseArgs(
        cluster_definition=azure_native.hdinsight.ClusterDefinitionArgs(
            component_version={
                "Hadoop": "2.7",
            },
            configurations={
                "gateway": {
                    "restAuthCredential.isEnabled": True,
                    "restAuthCredential.password": "**********",
                    "restAuthCredential.username": "admin",
                },
            },
            kind="hadoop",
        ),
        cluster_version="3.6",
        compute_profile={
            "roles": [{
                "autoscaleConfiguration": {
                    "recurrence": {
                        "schedule": [
                            {
                                "days": [
                                    "Monday",
                                    "Tuesday",
                                    "Wednesday",
                                    "Thursday",
                                    "Friday",
                                ],
                                "timeAndCapacity": azure_native.hdinsight.AutoscaleTimeAndCapacityArgs(
                                    max_instance_count=3,
                                    min_instance_count=3,
                                    time="09:00",
                                ),
                            },
                            {
                                "days": [
                                    "Monday",
                                    "Tuesday",
                                    "Wednesday",
                                    "Thursday",
                                    "Friday",
                                ],
                                "timeAndCapacity": azure_native.hdinsight.AutoscaleTimeAndCapacityArgs(
                                    max_instance_count=6,
                                    min_instance_count=6,
                                    time="18:00",
                                ),
                            },
                            {
                                "days": [
                                    "Saturday",
                                    "Sunday",
                                ],
                                "timeAndCapacity": azure_native.hdinsight.AutoscaleTimeAndCapacityArgs(
                                    max_instance_count=2,
                                    min_instance_count=2,
                                    time="09:00",
                                ),
                            },
                            {
                                "days": [
                                    "Saturday",
                                    "Sunday",
                                ],
                                "timeAndCapacity": azure_native.hdinsight.AutoscaleTimeAndCapacityArgs(
                                    max_instance_count=4,
                                    min_instance_count=4,
                                    time="18:00",
                                ),
                            },
                        ],
                        "timeZone": "China Standard Time",
                    },
                },
                "hardwareProfile": azure_native.hdinsight.HardwareProfileArgs(
                    vm_size="Standard_D4_V2",
                ),
                "name": "workernode",
                "osProfile": {
                    "linuxOperatingSystemProfile": azure_native.hdinsight.LinuxOperatingSystemProfileArgs(
                        password="**********",
                        username="sshuser",
                    ),
                },
                "scriptActions": [],
                "targetInstanceCount": 4,
            }],
        },
        os_type="Linux",
        storage_profile={
            "storageaccounts": [azure_native.hdinsight.StorageAccountArgs(
                container="hdinsight-autoscale-tes-2019-06-18t05-49-16-591z",
                is_default=True,
                key="storagekey",
                name="mystorage.blob.core.windows.net",
            )],
        },
        tier="Standard",
    ),
    resource_group_name="rg1")

```

```yaml
resources:
  cluster:
    type: azure-native:hdinsight:Cluster
    properties:
      clusterName: cluster1
      properties:
        clusterDefinition:
          componentVersion:
            Hadoop: '2.7'
          configurations:
            gateway:
              restAuthCredential.isEnabled: true
              restAuthCredential.password: '**********'
              restAuthCredential.username: admin
          kind: hadoop
        clusterVersion: '3.6'
        computeProfile:
          roles:
            - autoscaleConfiguration:
                recurrence:
                  schedule:
                    - days:
                        - Monday
                        - Tuesday
                        - Wednesday
                        - Thursday
                        - Friday
                      timeAndCapacity:
                        maxInstanceCount: 3
                        minInstanceCount: 3
                        time: 09:00
                    - days:
                        - Monday
                        - Tuesday
                        - Wednesday
                        - Thursday
                        - Friday
                      timeAndCapacity:
                        maxInstanceCount: 6
                        minInstanceCount: 6
                        time: 18:00
                    - days:
                        - Saturday
                        - Sunday
                      timeAndCapacity:
                        maxInstanceCount: 2
                        minInstanceCount: 2
                        time: 09:00
                    - days:
                        - Saturday
                        - Sunday
                      timeAndCapacity:
                        maxInstanceCount: 4
                        minInstanceCount: 4
                        time: 18:00
                  timeZone: China Standard Time
              hardwareProfile:
                vmSize: Standard_D4_V2
              name: workernode
              osProfile:
                linuxOperatingSystemProfile:
                  password: '**********'
                  username: sshuser
              scriptActions: []
              targetInstanceCount: 4
        osType: Linux
        storageProfile:
          storageaccounts:
            - container: hdinsight-autoscale-tes-2019-06-18t05-49-16-591z
              isDefault: true
              key: storagekey
              name: mystorage.blob.core.windows.net
        tier: Standard
      resourceGroupName: rg1

```

{{% /example %}}
{{% example %}}
### Create Hadoop cluster with Azure Data Lake Storage Gen 2
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var cluster = new AzureNative.HDInsight.Cluster("cluster", new()
    {
        ClusterName = "cluster1",
        Properties = new AzureNative.HDInsight.Inputs.ClusterCreatePropertiesArgs
        {
            ClusterDefinition = new AzureNative.HDInsight.Inputs.ClusterDefinitionArgs
            {
                Configurations = 
                {
                    { "gateway", 
                    {
                        { "restAuthCredential.isEnabled", "true" },
                        { "restAuthCredential.password", "**********" },
                        { "restAuthCredential.username", "admin" },
                    } },
                },
                Kind = "Hadoop",
            },
            ClusterVersion = "3.6",
            ComputeProfile = new AzureNative.HDInsight.Inputs.ComputeProfileArgs
            {
                Roles = new[]
                {
                    new AzureNative.HDInsight.Inputs.RoleArgs
                    {
                        HardwareProfile = new AzureNative.HDInsight.Inputs.HardwareProfileArgs
                        {
                            VmSize = "Standard_D3_V2",
                        },
                        MinInstanceCount = 1,
                        Name = "headnode",
                        OsProfile = new AzureNative.HDInsight.Inputs.OsProfileArgs
                        {
                            LinuxOperatingSystemProfile = new AzureNative.HDInsight.Inputs.LinuxOperatingSystemProfileArgs
                            {
                                Password = "**********",
                                Username = "sshuser",
                            },
                        },
                        TargetInstanceCount = 2,
                    },
                    new AzureNative.HDInsight.Inputs.RoleArgs
                    {
                        HardwareProfile = new AzureNative.HDInsight.Inputs.HardwareProfileArgs
                        {
                            VmSize = "Standard_D3_V2",
                        },
                        MinInstanceCount = 1,
                        Name = "workernode",
                        OsProfile = new AzureNative.HDInsight.Inputs.OsProfileArgs
                        {
                            LinuxOperatingSystemProfile = new AzureNative.HDInsight.Inputs.LinuxOperatingSystemProfileArgs
                            {
                                Password = "**********",
                                Username = "sshuser",
                            },
                        },
                        TargetInstanceCount = 4,
                    },
                    new AzureNative.HDInsight.Inputs.RoleArgs
                    {
                        HardwareProfile = new AzureNative.HDInsight.Inputs.HardwareProfileArgs
                        {
                            VmSize = "Small",
                        },
                        MinInstanceCount = 1,
                        Name = "zookeepernode",
                        OsProfile = new AzureNative.HDInsight.Inputs.OsProfileArgs
                        {
                            LinuxOperatingSystemProfile = new AzureNative.HDInsight.Inputs.LinuxOperatingSystemProfileArgs
                            {
                                Password = "**********",
                                Username = "sshuser",
                            },
                        },
                        TargetInstanceCount = 3,
                    },
                },
            },
            OsType = "Linux",
            StorageProfile = new AzureNative.HDInsight.Inputs.StorageProfileArgs
            {
                Storageaccounts = new[]
                {
                    new AzureNative.HDInsight.Inputs.StorageAccountArgs
                    {
                        FileSystem = "default",
                        IsDefault = true,
                        Key = "storagekey",
                        Name = "mystorage.dfs.core.windows.net",
                    },
                },
            },
            Tier = "Standard",
        },
        ResourceGroupName = "rg1",
        Tags = 
        {
            { "key1", "val1" },
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.hdinsight.Cluster;
import com.pulumi.azurenative.hdinsight.ClusterArgs;
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
        var cluster = new Cluster("cluster", ClusterArgs.builder()        
            .clusterName("cluster1")
            .properties(Map.ofEntries(
                Map.entry("clusterDefinition", Map.ofEntries(
                    Map.entry("configurations", Map.of("gateway", ClusterCreatePropertiesArgs.builder()
%!v(PANIC=Format method: interface conversion: model.Expression is *model.TemplateExpression, not *model.LiteralValueExpression))),
                        Map.entry("kind", "Hadoop")
                    )),
                    Map.entry("clusterVersion", "3.6"),
                    Map.entry("computeProfile", Map.of("roles",                     
                        Map.ofEntries(
                            Map.entry("hardwareProfile", Map.of("vmSize", "Standard_D3_V2")),
                            Map.entry("minInstanceCount", 1),
                            Map.entry("name", "headnode"),
                            Map.entry("osProfile", Map.of("linuxOperatingSystemProfile", Map.ofEntries(
                                Map.entry("password", "**********"),
                                Map.entry("username", "sshuser")
                            ))),
                            Map.entry("targetInstanceCount", 2)
                        ),
                        Map.ofEntries(
                            Map.entry("hardwareProfile", Map.of("vmSize", "Standard_D3_V2")),
                            Map.entry("minInstanceCount", 1),
                            Map.entry("name", "workernode"),
                            Map.entry("osProfile", Map.of("linuxOperatingSystemProfile", Map.ofEntries(
                                Map.entry("password", "**********"),
                                Map.entry("username", "sshuser")
                            ))),
                            Map.entry("targetInstanceCount", 4)
                        ),
                        Map.ofEntries(
                            Map.entry("hardwareProfile", Map.of("vmSize", "Small")),
                            Map.entry("minInstanceCount", 1),
                            Map.entry("name", "zookeepernode"),
                            Map.entry("osProfile", Map.of("linuxOperatingSystemProfile", Map.ofEntries(
                                Map.entry("password", "**********"),
                                Map.entry("username", "sshuser")
                            ))),
                            Map.entry("targetInstanceCount", 3)
                        ))),
                    Map.entry("osType", "Linux"),
                    Map.entry("storageProfile", Map.of("storageaccounts", Map.ofEntries(
                        Map.entry("fileSystem", "default"),
                        Map.entry("isDefault", true),
                        Map.entry("key", "storagekey"),
                        Map.entry("name", "mystorage.dfs.core.windows.net")
                    ))),
                    Map.entry("tier", "Standard")
                ))
                .resourceGroupName("rg1")
                .tags(Map.of("key1", "val1"))
                .build());

        }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const cluster = new azure_native.hdinsight.Cluster("cluster", {
    clusterName: "cluster1",
    properties: {
        clusterDefinition: {
            configurations: {
                gateway: {
                    "restAuthCredential.isEnabled": "true",
                    "restAuthCredential.password": "**********",
                    "restAuthCredential.username": "admin",
                },
            },
            kind: "Hadoop",
        },
        clusterVersion: "3.6",
        computeProfile: {
            roles: [
                {
                    hardwareProfile: {
                        vmSize: "Standard_D3_V2",
                    },
                    minInstanceCount: 1,
                    name: "headnode",
                    osProfile: {
                        linuxOperatingSystemProfile: {
                            password: "**********",
                            username: "sshuser",
                        },
                    },
                    targetInstanceCount: 2,
                },
                {
                    hardwareProfile: {
                        vmSize: "Standard_D3_V2",
                    },
                    minInstanceCount: 1,
                    name: "workernode",
                    osProfile: {
                        linuxOperatingSystemProfile: {
                            password: "**********",
                            username: "sshuser",
                        },
                    },
                    targetInstanceCount: 4,
                },
                {
                    hardwareProfile: {
                        vmSize: "Small",
                    },
                    minInstanceCount: 1,
                    name: "zookeepernode",
                    osProfile: {
                        linuxOperatingSystemProfile: {
                            password: "**********",
                            username: "sshuser",
                        },
                    },
                    targetInstanceCount: 3,
                },
            ],
        },
        osType: "Linux",
        storageProfile: {
            storageaccounts: [{
                fileSystem: "default",
                isDefault: true,
                key: "storagekey",
                name: "mystorage.dfs.core.windows.net",
            }],
        },
        tier: "Standard",
    },
    resourceGroupName: "rg1",
    tags: {
        key1: "val1",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

cluster = azure_native.hdinsight.Cluster("cluster",
    cluster_name="cluster1",
    properties=azure_native.hdinsight.ClusterGetPropertiesResponseArgs(
        cluster_definition=azure_native.hdinsight.ClusterDefinitionArgs(
            configurations={
                "gateway": {
                    "restAuthCredential.isEnabled": "true",
                    "restAuthCredential.password": "**********",
                    "restAuthCredential.username": "admin",
                },
            },
            kind="Hadoop",
        ),
        cluster_version="3.6",
        compute_profile={
            "roles": [
                {
                    "hardwareProfile": azure_native.hdinsight.HardwareProfileArgs(
                        vm_size="Standard_D3_V2",
                    ),
                    "minInstanceCount": 1,
                    "name": "headnode",
                    "osProfile": {
                        "linuxOperatingSystemProfile": azure_native.hdinsight.LinuxOperatingSystemProfileArgs(
                            password="**********",
                            username="sshuser",
                        ),
                    },
                    "targetInstanceCount": 2,
                },
                {
                    "hardwareProfile": azure_native.hdinsight.HardwareProfileArgs(
                        vm_size="Standard_D3_V2",
                    ),
                    "minInstanceCount": 1,
                    "name": "workernode",
                    "osProfile": {
                        "linuxOperatingSystemProfile": azure_native.hdinsight.LinuxOperatingSystemProfileArgs(
                            password="**********",
                            username="sshuser",
                        ),
                    },
                    "targetInstanceCount": 4,
                },
                {
                    "hardwareProfile": azure_native.hdinsight.HardwareProfileArgs(
                        vm_size="Small",
                    ),
                    "minInstanceCount": 1,
                    "name": "zookeepernode",
                    "osProfile": {
                        "linuxOperatingSystemProfile": azure_native.hdinsight.LinuxOperatingSystemProfileArgs(
                            password="**********",
                            username="sshuser",
                        ),
                    },
                    "targetInstanceCount": 3,
                },
            ],
        },
        os_type="Linux",
        storage_profile={
            "storageaccounts": [azure_native.hdinsight.StorageAccountArgs(
                file_system="default",
                is_default=True,
                key="storagekey",
                name="mystorage.dfs.core.windows.net",
            )],
        },
        tier="Standard",
    ),
    resource_group_name="rg1",
    tags={
        "key1": "val1",
    })

```

```yaml
resources:
  cluster:
    type: azure-native:hdinsight:Cluster
    properties:
      clusterName: cluster1
      properties:
        clusterDefinition:
          configurations:
            gateway:
              restAuthCredential.isEnabled: 'true'
              restAuthCredential.password: '**********'
              restAuthCredential.username: admin
          kind: Hadoop
        clusterVersion: '3.6'
        computeProfile:
          roles:
            - hardwareProfile:
                vmSize: Standard_D3_V2
              minInstanceCount: 1
              name: headnode
              osProfile:
                linuxOperatingSystemProfile:
                  password: '**********'
                  username: sshuser
              targetInstanceCount: 2
            - hardwareProfile:
                vmSize: Standard_D3_V2
              minInstanceCount: 1
              name: workernode
              osProfile:
                linuxOperatingSystemProfile:
                  password: '**********'
                  username: sshuser
              targetInstanceCount: 4
            - hardwareProfile:
                vmSize: Small
              minInstanceCount: 1
              name: zookeepernode
              osProfile:
                linuxOperatingSystemProfile:
                  password: '**********'
                  username: sshuser
              targetInstanceCount: 3
        osType: Linux
        storageProfile:
          storageaccounts:
            - fileSystem: default
              isDefault: true
              key: storagekey
              name: mystorage.dfs.core.windows.net
        tier: Standard
      resourceGroupName: rg1
      tags:
        key1: val1

```

{{% /example %}}
{{% example %}}
### Create Hadoop on Linux cluster with SSH password
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var cluster = new AzureNative.HDInsight.Cluster("cluster", new()
    {
        ClusterName = "cluster1",
        Properties = new AzureNative.HDInsight.Inputs.ClusterCreatePropertiesArgs
        {
            ClusterDefinition = new AzureNative.HDInsight.Inputs.ClusterDefinitionArgs
            {
                Configurations = 
                {
                    { "gateway", 
                    {
                        { "restAuthCredential.isEnabled", "true" },
                        { "restAuthCredential.password", "**********" },
                        { "restAuthCredential.username", "admin" },
                    } },
                },
                Kind = "Hadoop",
            },
            ClusterVersion = "3.5",
            ComputeProfile = new AzureNative.HDInsight.Inputs.ComputeProfileArgs
            {
                Roles = new[]
                {
                    new AzureNative.HDInsight.Inputs.RoleArgs
                    {
                        HardwareProfile = new AzureNative.HDInsight.Inputs.HardwareProfileArgs
                        {
                            VmSize = "Standard_D3_V2",
                        },
                        MinInstanceCount = 1,
                        Name = "headnode",
                        OsProfile = new AzureNative.HDInsight.Inputs.OsProfileArgs
                        {
                            LinuxOperatingSystemProfile = new AzureNative.HDInsight.Inputs.LinuxOperatingSystemProfileArgs
                            {
                                Password = "**********",
                                Username = "sshuser",
                            },
                        },
                        TargetInstanceCount = 2,
                    },
                    new AzureNative.HDInsight.Inputs.RoleArgs
                    {
                        HardwareProfile = new AzureNative.HDInsight.Inputs.HardwareProfileArgs
                        {
                            VmSize = "Standard_D3_V2",
                        },
                        MinInstanceCount = 1,
                        Name = "workernode",
                        OsProfile = new AzureNative.HDInsight.Inputs.OsProfileArgs
                        {
                            LinuxOperatingSystemProfile = new AzureNative.HDInsight.Inputs.LinuxOperatingSystemProfileArgs
                            {
                                Password = "**********",
                                Username = "sshuser",
                            },
                        },
                        TargetInstanceCount = 4,
                    },
                    new AzureNative.HDInsight.Inputs.RoleArgs
                    {
                        HardwareProfile = new AzureNative.HDInsight.Inputs.HardwareProfileArgs
                        {
                            VmSize = "Small",
                        },
                        MinInstanceCount = 1,
                        Name = "zookeepernode",
                        OsProfile = new AzureNative.HDInsight.Inputs.OsProfileArgs
                        {
                            LinuxOperatingSystemProfile = new AzureNative.HDInsight.Inputs.LinuxOperatingSystemProfileArgs
                            {
                                Password = "**********",
                                Username = "sshuser",
                            },
                        },
                        TargetInstanceCount = 3,
                    },
                },
            },
            OsType = "Linux",
            StorageProfile = new AzureNative.HDInsight.Inputs.StorageProfileArgs
            {
                Storageaccounts = new[]
                {
                    new AzureNative.HDInsight.Inputs.StorageAccountArgs
                    {
                        Container = "containername",
                        IsDefault = true,
                        Key = "storagekey",
                        Name = "mystorage.blob.core.windows.net",
                    },
                },
            },
            Tier = "Standard",
        },
        ResourceGroupName = "rg1",
        Tags = 
        {
            { "key1", "val1" },
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.hdinsight.Cluster;
import com.pulumi.azurenative.hdinsight.ClusterArgs;
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
        var cluster = new Cluster("cluster", ClusterArgs.builder()        
            .clusterName("cluster1")
            .properties(Map.ofEntries(
                Map.entry("clusterDefinition", Map.ofEntries(
                    Map.entry("configurations", Map.of("gateway", ClusterCreatePropertiesArgs.builder()
%!v(PANIC=Format method: interface conversion: model.Expression is *model.TemplateExpression, not *model.LiteralValueExpression))),
                        Map.entry("kind", "Hadoop")
                    )),
                    Map.entry("clusterVersion", "3.5"),
                    Map.entry("computeProfile", Map.of("roles",                     
                        Map.ofEntries(
                            Map.entry("hardwareProfile", Map.of("vmSize", "Standard_D3_V2")),
                            Map.entry("minInstanceCount", 1),
                            Map.entry("name", "headnode"),
                            Map.entry("osProfile", Map.of("linuxOperatingSystemProfile", Map.ofEntries(
                                Map.entry("password", "**********"),
                                Map.entry("username", "sshuser")
                            ))),
                            Map.entry("targetInstanceCount", 2)
                        ),
                        Map.ofEntries(
                            Map.entry("hardwareProfile", Map.of("vmSize", "Standard_D3_V2")),
                            Map.entry("minInstanceCount", 1),
                            Map.entry("name", "workernode"),
                            Map.entry("osProfile", Map.of("linuxOperatingSystemProfile", Map.ofEntries(
                                Map.entry("password", "**********"),
                                Map.entry("username", "sshuser")
                            ))),
                            Map.entry("targetInstanceCount", 4)
                        ),
                        Map.ofEntries(
                            Map.entry("hardwareProfile", Map.of("vmSize", "Small")),
                            Map.entry("minInstanceCount", 1),
                            Map.entry("name", "zookeepernode"),
                            Map.entry("osProfile", Map.of("linuxOperatingSystemProfile", Map.ofEntries(
                                Map.entry("password", "**********"),
                                Map.entry("username", "sshuser")
                            ))),
                            Map.entry("targetInstanceCount", 3)
                        ))),
                    Map.entry("osType", "Linux"),
                    Map.entry("storageProfile", Map.of("storageaccounts", Map.ofEntries(
                        Map.entry("container", "containername"),
                        Map.entry("isDefault", true),
                        Map.entry("key", "storagekey"),
                        Map.entry("name", "mystorage.blob.core.windows.net")
                    ))),
                    Map.entry("tier", "Standard")
                ))
                .resourceGroupName("rg1")
                .tags(Map.of("key1", "val1"))
                .build());

        }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const cluster = new azure_native.hdinsight.Cluster("cluster", {
    clusterName: "cluster1",
    properties: {
        clusterDefinition: {
            configurations: {
                gateway: {
                    "restAuthCredential.isEnabled": "true",
                    "restAuthCredential.password": "**********",
                    "restAuthCredential.username": "admin",
                },
            },
            kind: "Hadoop",
        },
        clusterVersion: "3.5",
        computeProfile: {
            roles: [
                {
                    hardwareProfile: {
                        vmSize: "Standard_D3_V2",
                    },
                    minInstanceCount: 1,
                    name: "headnode",
                    osProfile: {
                        linuxOperatingSystemProfile: {
                            password: "**********",
                            username: "sshuser",
                        },
                    },
                    targetInstanceCount: 2,
                },
                {
                    hardwareProfile: {
                        vmSize: "Standard_D3_V2",
                    },
                    minInstanceCount: 1,
                    name: "workernode",
                    osProfile: {
                        linuxOperatingSystemProfile: {
                            password: "**********",
                            username: "sshuser",
                        },
                    },
                    targetInstanceCount: 4,
                },
                {
                    hardwareProfile: {
                        vmSize: "Small",
                    },
                    minInstanceCount: 1,
                    name: "zookeepernode",
                    osProfile: {
                        linuxOperatingSystemProfile: {
                            password: "**********",
                            username: "sshuser",
                        },
                    },
                    targetInstanceCount: 3,
                },
            ],
        },
        osType: "Linux",
        storageProfile: {
            storageaccounts: [{
                container: "containername",
                isDefault: true,
                key: "storagekey",
                name: "mystorage.blob.core.windows.net",
            }],
        },
        tier: "Standard",
    },
    resourceGroupName: "rg1",
    tags: {
        key1: "val1",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

cluster = azure_native.hdinsight.Cluster("cluster",
    cluster_name="cluster1",
    properties=azure_native.hdinsight.ClusterGetPropertiesResponseArgs(
        cluster_definition=azure_native.hdinsight.ClusterDefinitionArgs(
            configurations={
                "gateway": {
                    "restAuthCredential.isEnabled": "true",
                    "restAuthCredential.password": "**********",
                    "restAuthCredential.username": "admin",
                },
            },
            kind="Hadoop",
        ),
        cluster_version="3.5",
        compute_profile={
            "roles": [
                {
                    "hardwareProfile": azure_native.hdinsight.HardwareProfileArgs(
                        vm_size="Standard_D3_V2",
                    ),
                    "minInstanceCount": 1,
                    "name": "headnode",
                    "osProfile": {
                        "linuxOperatingSystemProfile": azure_native.hdinsight.LinuxOperatingSystemProfileArgs(
                            password="**********",
                            username="sshuser",
                        ),
                    },
                    "targetInstanceCount": 2,
                },
                {
                    "hardwareProfile": azure_native.hdinsight.HardwareProfileArgs(
                        vm_size="Standard_D3_V2",
                    ),
                    "minInstanceCount": 1,
                    "name": "workernode",
                    "osProfile": {
                        "linuxOperatingSystemProfile": azure_native.hdinsight.LinuxOperatingSystemProfileArgs(
                            password="**********",
                            username="sshuser",
                        ),
                    },
                    "targetInstanceCount": 4,
                },
                {
                    "hardwareProfile": azure_native.hdinsight.HardwareProfileArgs(
                        vm_size="Small",
                    ),
                    "minInstanceCount": 1,
                    "name": "zookeepernode",
                    "osProfile": {
                        "linuxOperatingSystemProfile": azure_native.hdinsight.LinuxOperatingSystemProfileArgs(
                            password="**********",
                            username="sshuser",
                        ),
                    },
                    "targetInstanceCount": 3,
                },
            ],
        },
        os_type="Linux",
        storage_profile={
            "storageaccounts": [azure_native.hdinsight.StorageAccountArgs(
                container="containername",
                is_default=True,
                key="storagekey",
                name="mystorage.blob.core.windows.net",
            )],
        },
        tier="Standard",
    ),
    resource_group_name="rg1",
    tags={
        "key1": "val1",
    })

```

```yaml
resources:
  cluster:
    type: azure-native:hdinsight:Cluster
    properties:
      clusterName: cluster1
      properties:
        clusterDefinition:
          configurations:
            gateway:
              restAuthCredential.isEnabled: 'true'
              restAuthCredential.password: '**********'
              restAuthCredential.username: admin
          kind: Hadoop
        clusterVersion: '3.5'
        computeProfile:
          roles:
            - hardwareProfile:
                vmSize: Standard_D3_V2
              minInstanceCount: 1
              name: headnode
              osProfile:
                linuxOperatingSystemProfile:
                  password: '**********'
                  username: sshuser
              targetInstanceCount: 2
            - hardwareProfile:
                vmSize: Standard_D3_V2
              minInstanceCount: 1
              name: workernode
              osProfile:
                linuxOperatingSystemProfile:
                  password: '**********'
                  username: sshuser
              targetInstanceCount: 4
            - hardwareProfile:
                vmSize: Small
              minInstanceCount: 1
              name: zookeepernode
              osProfile:
                linuxOperatingSystemProfile:
                  password: '**********'
                  username: sshuser
              targetInstanceCount: 3
        osType: Linux
        storageProfile:
          storageaccounts:
            - container: containername
              isDefault: true
              key: storagekey
              name: mystorage.blob.core.windows.net
        tier: Standard
      resourceGroupName: rg1
      tags:
        key1: val1

```

{{% /example %}}
{{% example %}}
### Create Hadoop on Linux cluster with SSH public key
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var cluster = new AzureNative.HDInsight.Cluster("cluster", new()
    {
        ClusterName = "cluster1",
        Properties = new AzureNative.HDInsight.Inputs.ClusterCreatePropertiesArgs
        {
            ClusterDefinition = new AzureNative.HDInsight.Inputs.ClusterDefinitionArgs
            {
                Configurations = 
                {
                    { "gateway", 
                    {
                        { "restAuthCredential.isEnabled", true },
                        { "restAuthCredential.password", "**********" },
                        { "restAuthCredential.username", "admin" },
                    } },
                },
                Kind = "Hadoop",
            },
            ClusterVersion = "3.5",
            ComputeProfile = new AzureNative.HDInsight.Inputs.ComputeProfileArgs
            {
                Roles = new[]
                {
                    new AzureNative.HDInsight.Inputs.RoleArgs
                    {
                        HardwareProfile = new AzureNative.HDInsight.Inputs.HardwareProfileArgs
                        {
                            VmSize = "Standard_D3_V2",
                        },
                        MinInstanceCount = 1,
                        Name = "headnode",
                        OsProfile = new AzureNative.HDInsight.Inputs.OsProfileArgs
                        {
                            LinuxOperatingSystemProfile = new AzureNative.HDInsight.Inputs.LinuxOperatingSystemProfileArgs
                            {
                                SshProfile = new AzureNative.HDInsight.Inputs.SshProfileArgs
                                {
                                    PublicKeys = new[]
                                    {
                                        new AzureNative.HDInsight.Inputs.SshPublicKeyArgs
                                        {
                                            CertificateData = "**********",
                                        },
                                    },
                                },
                                Username = "sshuser",
                            },
                        },
                        TargetInstanceCount = 2,
                    },
                    new AzureNative.HDInsight.Inputs.RoleArgs
                    {
                        HardwareProfile = new AzureNative.HDInsight.Inputs.HardwareProfileArgs
                        {
                            VmSize = "Standard_D3_V2",
                        },
                        MinInstanceCount = 1,
                        Name = "workernode",
                        OsProfile = new AzureNative.HDInsight.Inputs.OsProfileArgs
                        {
                            LinuxOperatingSystemProfile = new AzureNative.HDInsight.Inputs.LinuxOperatingSystemProfileArgs
                            {
                                Password = "**********",
                                Username = "sshuser",
                            },
                        },
                        TargetInstanceCount = 4,
                    },
                    new AzureNative.HDInsight.Inputs.RoleArgs
                    {
                        HardwareProfile = new AzureNative.HDInsight.Inputs.HardwareProfileArgs
                        {
                            VmSize = "Small",
                        },
                        MinInstanceCount = 1,
                        Name = "zookeepernode",
                        OsProfile = new AzureNative.HDInsight.Inputs.OsProfileArgs
                        {
                            LinuxOperatingSystemProfile = new AzureNative.HDInsight.Inputs.LinuxOperatingSystemProfileArgs
                            {
                                Password = "**********",
                                Username = "sshuser",
                            },
                        },
                        TargetInstanceCount = 3,
                    },
                },
            },
            OsType = "Linux",
            StorageProfile = new AzureNative.HDInsight.Inputs.StorageProfileArgs
            {
                Storageaccounts = new[]
                {
                    new AzureNative.HDInsight.Inputs.StorageAccountArgs
                    {
                        Container = "containername",
                        IsDefault = true,
                        Key = "storagekey",
                        Name = "mystorage.blob.core.windows.net",
                    },
                },
            },
            Tier = "Standard",
        },
        ResourceGroupName = "rg1",
        Tags = 
        {
            { "key1", "val1" },
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.hdinsight.Cluster;
import com.pulumi.azurenative.hdinsight.ClusterArgs;
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
        var cluster = new Cluster("cluster", ClusterArgs.builder()        
            .clusterName("cluster1")
            .properties(Map.ofEntries(
                Map.entry("clusterDefinition", Map.ofEntries(
                    Map.entry("configurations", Map.of("gateway", ClusterCreatePropertiesArgs.builder()
%!v(PANIC=Format method: interface conversion: model.Expression is *model.TemplateExpression, not *model.LiteralValueExpression))),
                        Map.entry("kind", "Hadoop")
                    )),
                    Map.entry("clusterVersion", "3.5"),
                    Map.entry("computeProfile", Map.of("roles",                     
                        Map.ofEntries(
                            Map.entry("hardwareProfile", Map.of("vmSize", "Standard_D3_V2")),
                            Map.entry("minInstanceCount", 1),
                            Map.entry("name", "headnode"),
                            Map.entry("osProfile", Map.of("linuxOperatingSystemProfile", Map.ofEntries(
                                Map.entry("sshProfile", Map.of("publicKeys", Map.of("certificateData", "**********"))),
                                Map.entry("username", "sshuser")
                            ))),
                            Map.entry("targetInstanceCount", 2)
                        ),
                        Map.ofEntries(
                            Map.entry("hardwareProfile", Map.of("vmSize", "Standard_D3_V2")),
                            Map.entry("minInstanceCount", 1),
                            Map.entry("name", "workernode"),
                            Map.entry("osProfile", Map.of("linuxOperatingSystemProfile", Map.ofEntries(
                                Map.entry("password", "**********"),
                                Map.entry("username", "sshuser")
                            ))),
                            Map.entry("targetInstanceCount", 4)
                        ),
                        Map.ofEntries(
                            Map.entry("hardwareProfile", Map.of("vmSize", "Small")),
                            Map.entry("minInstanceCount", 1),
                            Map.entry("name", "zookeepernode"),
                            Map.entry("osProfile", Map.of("linuxOperatingSystemProfile", Map.ofEntries(
                                Map.entry("password", "**********"),
                                Map.entry("username", "sshuser")
                            ))),
                            Map.entry("targetInstanceCount", 3)
                        ))),
                    Map.entry("osType", "Linux"),
                    Map.entry("storageProfile", Map.of("storageaccounts", Map.ofEntries(
                        Map.entry("container", "containername"),
                        Map.entry("isDefault", true),
                        Map.entry("key", "storagekey"),
                        Map.entry("name", "mystorage.blob.core.windows.net")
                    ))),
                    Map.entry("tier", "Standard")
                ))
                .resourceGroupName("rg1")
                .tags(Map.of("key1", "val1"))
                .build());

        }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const cluster = new azure_native.hdinsight.Cluster("cluster", {
    clusterName: "cluster1",
    properties: {
        clusterDefinition: {
            configurations: {
                gateway: {
                    "restAuthCredential.isEnabled": true,
                    "restAuthCredential.password": "**********",
                    "restAuthCredential.username": "admin",
                },
            },
            kind: "Hadoop",
        },
        clusterVersion: "3.5",
        computeProfile: {
            roles: [
                {
                    hardwareProfile: {
                        vmSize: "Standard_D3_V2",
                    },
                    minInstanceCount: 1,
                    name: "headnode",
                    osProfile: {
                        linuxOperatingSystemProfile: {
                            sshProfile: {
                                publicKeys: [{
                                    certificateData: "**********",
                                }],
                            },
                            username: "sshuser",
                        },
                    },
                    targetInstanceCount: 2,
                },
                {
                    hardwareProfile: {
                        vmSize: "Standard_D3_V2",
                    },
                    minInstanceCount: 1,
                    name: "workernode",
                    osProfile: {
                        linuxOperatingSystemProfile: {
                            password: "**********",
                            username: "sshuser",
                        },
                    },
                    targetInstanceCount: 4,
                },
                {
                    hardwareProfile: {
                        vmSize: "Small",
                    },
                    minInstanceCount: 1,
                    name: "zookeepernode",
                    osProfile: {
                        linuxOperatingSystemProfile: {
                            password: "**********",
                            username: "sshuser",
                        },
                    },
                    targetInstanceCount: 3,
                },
            ],
        },
        osType: "Linux",
        storageProfile: {
            storageaccounts: [{
                container: "containername",
                isDefault: true,
                key: "storagekey",
                name: "mystorage.blob.core.windows.net",
            }],
        },
        tier: "Standard",
    },
    resourceGroupName: "rg1",
    tags: {
        key1: "val1",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

cluster = azure_native.hdinsight.Cluster("cluster",
    cluster_name="cluster1",
    properties=azure_native.hdinsight.ClusterGetPropertiesResponseArgs(
        cluster_definition=azure_native.hdinsight.ClusterDefinitionArgs(
            configurations={
                "gateway": {
                    "restAuthCredential.isEnabled": True,
                    "restAuthCredential.password": "**********",
                    "restAuthCredential.username": "admin",
                },
            },
            kind="Hadoop",
        ),
        cluster_version="3.5",
        compute_profile={
            "roles": [
                {
                    "hardwareProfile": azure_native.hdinsight.HardwareProfileArgs(
                        vm_size="Standard_D3_V2",
                    ),
                    "minInstanceCount": 1,
                    "name": "headnode",
                    "osProfile": {
                        "linuxOperatingSystemProfile": {
                            "sshProfile": {
                                "publicKeys": [azure_native.hdinsight.SshPublicKeyArgs(
                                    certificate_data="**********",
                                )],
                            },
                            "username": "sshuser",
                        },
                    },
                    "targetInstanceCount": 2,
                },
                {
                    "hardwareProfile": azure_native.hdinsight.HardwareProfileArgs(
                        vm_size="Standard_D3_V2",
                    ),
                    "minInstanceCount": 1,
                    "name": "workernode",
                    "osProfile": {
                        "linuxOperatingSystemProfile": azure_native.hdinsight.LinuxOperatingSystemProfileArgs(
                            password="**********",
                            username="sshuser",
                        ),
                    },
                    "targetInstanceCount": 4,
                },
                {
                    "hardwareProfile": azure_native.hdinsight.HardwareProfileArgs(
                        vm_size="Small",
                    ),
                    "minInstanceCount": 1,
                    "name": "zookeepernode",
                    "osProfile": {
                        "linuxOperatingSystemProfile": azure_native.hdinsight.LinuxOperatingSystemProfileArgs(
                            password="**********",
                            username="sshuser",
                        ),
                    },
                    "targetInstanceCount": 3,
                },
            ],
        },
        os_type="Linux",
        storage_profile={
            "storageaccounts": [azure_native.hdinsight.StorageAccountArgs(
                container="containername",
                is_default=True,
                key="storagekey",
                name="mystorage.blob.core.windows.net",
            )],
        },
        tier="Standard",
    ),
    resource_group_name="rg1",
    tags={
        "key1": "val1",
    })

```

```yaml
resources:
  cluster:
    type: azure-native:hdinsight:Cluster
    properties:
      clusterName: cluster1
      properties:
        clusterDefinition:
          configurations:
            gateway:
              restAuthCredential.isEnabled: true
              restAuthCredential.password: '**********'
              restAuthCredential.username: admin
          kind: Hadoop
        clusterVersion: '3.5'
        computeProfile:
          roles:
            - hardwareProfile:
                vmSize: Standard_D3_V2
              minInstanceCount: 1
              name: headnode
              osProfile:
                linuxOperatingSystemProfile:
                  sshProfile:
                    publicKeys:
                      - certificateData: '**********'
                  username: sshuser
              targetInstanceCount: 2
            - hardwareProfile:
                vmSize: Standard_D3_V2
              minInstanceCount: 1
              name: workernode
              osProfile:
                linuxOperatingSystemProfile:
                  password: '**********'
                  username: sshuser
              targetInstanceCount: 4
            - hardwareProfile:
                vmSize: Small
              minInstanceCount: 1
              name: zookeepernode
              osProfile:
                linuxOperatingSystemProfile:
                  password: '**********'
                  username: sshuser
              targetInstanceCount: 3
        osType: Linux
        storageProfile:
          storageaccounts:
            - container: containername
              isDefault: true
              key: storagekey
              name: mystorage.blob.core.windows.net
        tier: Standard
      resourceGroupName: rg1
      tags:
        key1: val1

```

{{% /example %}}
{{% example %}}
### Create Kafka cluster with Kafka Rest Proxy
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var cluster = new AzureNative.HDInsight.Cluster("cluster", new()
    {
        ClusterName = "cluster1",
        Properties = new AzureNative.HDInsight.Inputs.ClusterCreatePropertiesArgs
        {
            ClusterDefinition = new AzureNative.HDInsight.Inputs.ClusterDefinitionArgs
            {
                ComponentVersion = 
                {
                    { "Kafka", "2.1" },
                },
                Configurations = 
                {
                    { "gateway", 
                    {
                        { "restAuthCredential.isEnabled", true },
                        { "restAuthCredential.password", "**********" },
                        { "restAuthCredential.username", "admin" },
                    } },
                },
                Kind = "kafka",
            },
            ClusterVersion = "4.0",
            ComputeProfile = new AzureNative.HDInsight.Inputs.ComputeProfileArgs
            {
                Roles = new[]
                {
                    new AzureNative.HDInsight.Inputs.RoleArgs
                    {
                        HardwareProfile = new AzureNative.HDInsight.Inputs.HardwareProfileArgs
                        {
                            VmSize = "Large",
                        },
                        Name = "headnode",
                        OsProfile = new AzureNative.HDInsight.Inputs.OsProfileArgs
                        {
                            LinuxOperatingSystemProfile = new AzureNative.HDInsight.Inputs.LinuxOperatingSystemProfileArgs
                            {
                                Password = "**********",
                                Username = "sshuser",
                            },
                        },
                        TargetInstanceCount = 2,
                    },
                    new AzureNative.HDInsight.Inputs.RoleArgs
                    {
                        DataDisksGroups = new[]
                        {
                            new AzureNative.HDInsight.Inputs.DataDisksGroupsArgs
                            {
                                DisksPerNode = 8,
                            },
                        },
                        HardwareProfile = new AzureNative.HDInsight.Inputs.HardwareProfileArgs
                        {
                            VmSize = "Large",
                        },
                        Name = "workernode",
                        OsProfile = new AzureNative.HDInsight.Inputs.OsProfileArgs
                        {
                            LinuxOperatingSystemProfile = new AzureNative.HDInsight.Inputs.LinuxOperatingSystemProfileArgs
                            {
                                Password = "**********",
                                Username = "sshuser",
                            },
                        },
                        TargetInstanceCount = 3,
                    },
                    new AzureNative.HDInsight.Inputs.RoleArgs
                    {
                        HardwareProfile = new AzureNative.HDInsight.Inputs.HardwareProfileArgs
                        {
                            VmSize = "Small",
                        },
                        Name = "zookeepernode",
                        OsProfile = new AzureNative.HDInsight.Inputs.OsProfileArgs
                        {
                            LinuxOperatingSystemProfile = new AzureNative.HDInsight.Inputs.LinuxOperatingSystemProfileArgs
                            {
                                Password = "**********",
                                Username = "sshuser",
                            },
                        },
                        TargetInstanceCount = 3,
                    },
                    new AzureNative.HDInsight.Inputs.RoleArgs
                    {
                        HardwareProfile = new AzureNative.HDInsight.Inputs.HardwareProfileArgs
                        {
                            VmSize = "Standard_D4_v2",
                        },
                        Name = "kafkamanagementnode",
                        OsProfile = new AzureNative.HDInsight.Inputs.OsProfileArgs
                        {
                            LinuxOperatingSystemProfile = new AzureNative.HDInsight.Inputs.LinuxOperatingSystemProfileArgs
                            {
                                Password = "**********",
                                Username = "kafkauser",
                            },
                        },
                        TargetInstanceCount = 2,
                    },
                },
            },
            KafkaRestProperties = new AzureNative.HDInsight.Inputs.KafkaRestPropertiesArgs
            {
                ClientGroupInfo = new AzureNative.HDInsight.Inputs.ClientGroupInfoArgs
                {
                    GroupId = "00000000-0000-0000-0000-111111111111",
                    GroupName = "Kafka security group name",
                },
            },
            OsType = "Linux",
            StorageProfile = new AzureNative.HDInsight.Inputs.StorageProfileArgs
            {
                Storageaccounts = new[]
                {
                    new AzureNative.HDInsight.Inputs.StorageAccountArgs
                    {
                        Container = "containername",
                        IsDefault = true,
                        Key = "storagekey",
                        Name = "mystorage.blob.core.windows.net",
                    },
                },
            },
            Tier = "Standard",
        },
        ResourceGroupName = "rg1",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.hdinsight.Cluster;
import com.pulumi.azurenative.hdinsight.ClusterArgs;
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
        var cluster = new Cluster("cluster", ClusterArgs.builder()        
            .clusterName("cluster1")
            .properties(Map.ofEntries(
                Map.entry("clusterDefinition", Map.ofEntries(
                    Map.entry("componentVersion", Map.of("Kafka", "2.1")),
                    Map.entry("configurations", Map.of("gateway", ClusterCreatePropertiesArgs.builder()
%!v(PANIC=Format method: interface conversion: model.Expression is *model.TemplateExpression, not *model.LiteralValueExpression))),
                        Map.entry("kind", "kafka")
                    )),
                    Map.entry("clusterVersion", "4.0"),
                    Map.entry("computeProfile", Map.of("roles",                     
                        Map.ofEntries(
                            Map.entry("hardwareProfile", Map.of("vmSize", "Large")),
                            Map.entry("name", "headnode"),
                            Map.entry("osProfile", Map.of("linuxOperatingSystemProfile", Map.ofEntries(
                                Map.entry("password", "**********"),
                                Map.entry("username", "sshuser")
                            ))),
                            Map.entry("targetInstanceCount", 2)
                        ),
                        Map.ofEntries(
                            Map.entry("dataDisksGroups", Map.of("disksPerNode", 8)),
                            Map.entry("hardwareProfile", Map.of("vmSize", "Large")),
                            Map.entry("name", "workernode"),
                            Map.entry("osProfile", Map.of("linuxOperatingSystemProfile", Map.ofEntries(
                                Map.entry("password", "**********"),
                                Map.entry("username", "sshuser")
                            ))),
                            Map.entry("targetInstanceCount", 3)
                        ),
                        Map.ofEntries(
                            Map.entry("hardwareProfile", Map.of("vmSize", "Small")),
                            Map.entry("name", "zookeepernode"),
                            Map.entry("osProfile", Map.of("linuxOperatingSystemProfile", Map.ofEntries(
                                Map.entry("password", "**********"),
                                Map.entry("username", "sshuser")
                            ))),
                            Map.entry("targetInstanceCount", 3)
                        ),
                        Map.ofEntries(
                            Map.entry("hardwareProfile", Map.of("vmSize", "Standard_D4_v2")),
                            Map.entry("name", "kafkamanagementnode"),
                            Map.entry("osProfile", Map.of("linuxOperatingSystemProfile", Map.ofEntries(
                                Map.entry("password", "**********"),
                                Map.entry("username", "kafkauser")
                            ))),
                            Map.entry("targetInstanceCount", 2)
                        ))),
                    Map.entry("kafkaRestProperties", Map.of("clientGroupInfo", Map.ofEntries(
                        Map.entry("groupId", "00000000-0000-0000-0000-111111111111"),
                        Map.entry("groupName", "Kafka security group name")
                    ))),
                    Map.entry("osType", "Linux"),
                    Map.entry("storageProfile", Map.of("storageaccounts", Map.ofEntries(
                        Map.entry("container", "containername"),
                        Map.entry("isDefault", true),
                        Map.entry("key", "storagekey"),
                        Map.entry("name", "mystorage.blob.core.windows.net")
                    ))),
                    Map.entry("tier", "Standard")
                ))
                .resourceGroupName("rg1")
                .build());

        }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const cluster = new azure_native.hdinsight.Cluster("cluster", {
    clusterName: "cluster1",
    properties: {
        clusterDefinition: {
            componentVersion: {
                Kafka: "2.1",
            },
            configurations: {
                gateway: {
                    "restAuthCredential.isEnabled": true,
                    "restAuthCredential.password": "**********",
                    "restAuthCredential.username": "admin",
                },
            },
            kind: "kafka",
        },
        clusterVersion: "4.0",
        computeProfile: {
            roles: [
                {
                    hardwareProfile: {
                        vmSize: "Large",
                    },
                    name: "headnode",
                    osProfile: {
                        linuxOperatingSystemProfile: {
                            password: "**********",
                            username: "sshuser",
                        },
                    },
                    targetInstanceCount: 2,
                },
                {
                    dataDisksGroups: [{
                        disksPerNode: 8,
                    }],
                    hardwareProfile: {
                        vmSize: "Large",
                    },
                    name: "workernode",
                    osProfile: {
                        linuxOperatingSystemProfile: {
                            password: "**********",
                            username: "sshuser",
                        },
                    },
                    targetInstanceCount: 3,
                },
                {
                    hardwareProfile: {
                        vmSize: "Small",
                    },
                    name: "zookeepernode",
                    osProfile: {
                        linuxOperatingSystemProfile: {
                            password: "**********",
                            username: "sshuser",
                        },
                    },
                    targetInstanceCount: 3,
                },
                {
                    hardwareProfile: {
                        vmSize: "Standard_D4_v2",
                    },
                    name: "kafkamanagementnode",
                    osProfile: {
                        linuxOperatingSystemProfile: {
                            password: "**********",
                            username: "kafkauser",
                        },
                    },
                    targetInstanceCount: 2,
                },
            ],
        },
        kafkaRestProperties: {
            clientGroupInfo: {
                groupId: "00000000-0000-0000-0000-111111111111",
                groupName: "Kafka security group name",
            },
        },
        osType: "Linux",
        storageProfile: {
            storageaccounts: [{
                container: "containername",
                isDefault: true,
                key: "storagekey",
                name: "mystorage.blob.core.windows.net",
            }],
        },
        tier: "Standard",
    },
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

cluster = azure_native.hdinsight.Cluster("cluster",
    cluster_name="cluster1",
    properties=azure_native.hdinsight.ClusterGetPropertiesResponseArgs(
        cluster_definition=azure_native.hdinsight.ClusterDefinitionArgs(
            component_version={
                "Kafka": "2.1",
            },
            configurations={
                "gateway": {
                    "restAuthCredential.isEnabled": True,
                    "restAuthCredential.password": "**********",
                    "restAuthCredential.username": "admin",
                },
            },
            kind="kafka",
        ),
        cluster_version="4.0",
        compute_profile={
            "roles": [
                {
                    "hardwareProfile": azure_native.hdinsight.HardwareProfileArgs(
                        vm_size="Large",
                    ),
                    "name": "headnode",
                    "osProfile": {
                        "linuxOperatingSystemProfile": azure_native.hdinsight.LinuxOperatingSystemProfileArgs(
                            password="**********",
                            username="sshuser",
                        ),
                    },
                    "targetInstanceCount": 2,
                },
                {
                    "dataDisksGroups": [azure_native.hdinsight.DataDisksGroupsArgs(
                        disks_per_node=8,
                    )],
                    "hardwareProfile": azure_native.hdinsight.HardwareProfileArgs(
                        vm_size="Large",
                    ),
                    "name": "workernode",
                    "osProfile": {
                        "linuxOperatingSystemProfile": azure_native.hdinsight.LinuxOperatingSystemProfileArgs(
                            password="**********",
                            username="sshuser",
                        ),
                    },
                    "targetInstanceCount": 3,
                },
                {
                    "hardwareProfile": azure_native.hdinsight.HardwareProfileArgs(
                        vm_size="Small",
                    ),
                    "name": "zookeepernode",
                    "osProfile": {
                        "linuxOperatingSystemProfile": azure_native.hdinsight.LinuxOperatingSystemProfileArgs(
                            password="**********",
                            username="sshuser",
                        ),
                    },
                    "targetInstanceCount": 3,
                },
                {
                    "hardwareProfile": azure_native.hdinsight.HardwareProfileArgs(
                        vm_size="Standard_D4_v2",
                    ),
                    "name": "kafkamanagementnode",
                    "osProfile": {
                        "linuxOperatingSystemProfile": azure_native.hdinsight.LinuxOperatingSystemProfileArgs(
                            password="**********",
                            username="kafkauser",
                        ),
                    },
                    "targetInstanceCount": 2,
                },
            ],
        },
        kafka_rest_properties={
            "clientGroupInfo": azure_native.hdinsight.ClientGroupInfoArgs(
                group_id="00000000-0000-0000-0000-111111111111",
                group_name="Kafka security group name",
            ),
        },
        os_type="Linux",
        storage_profile={
            "storageaccounts": [azure_native.hdinsight.StorageAccountArgs(
                container="containername",
                is_default=True,
                key="storagekey",
                name="mystorage.blob.core.windows.net",
            )],
        },
        tier="Standard",
    ),
    resource_group_name="rg1")

```

```yaml
resources:
  cluster:
    type: azure-native:hdinsight:Cluster
    properties:
      clusterName: cluster1
      properties:
        clusterDefinition:
          componentVersion:
            Kafka: '2.1'
          configurations:
            gateway:
              restAuthCredential.isEnabled: true
              restAuthCredential.password: '**********'
              restAuthCredential.username: admin
          kind: kafka
        clusterVersion: '4.0'
        computeProfile:
          roles:
            - hardwareProfile:
                vmSize: Large
              name: headnode
              osProfile:
                linuxOperatingSystemProfile:
                  password: '**********'
                  username: sshuser
              targetInstanceCount: 2
            - dataDisksGroups:
                - disksPerNode: 8
              hardwareProfile:
                vmSize: Large
              name: workernode
              osProfile:
                linuxOperatingSystemProfile:
                  password: '**********'
                  username: sshuser
              targetInstanceCount: 3
            - hardwareProfile:
                vmSize: Small
              name: zookeepernode
              osProfile:
                linuxOperatingSystemProfile:
                  password: '**********'
                  username: sshuser
              targetInstanceCount: 3
            - hardwareProfile:
                vmSize: Standard_D4_v2
              name: kafkamanagementnode
              osProfile:
                linuxOperatingSystemProfile:
                  password: '**********'
                  username: kafkauser
              targetInstanceCount: 2
        kafkaRestProperties:
          clientGroupInfo:
            groupId: 00000000-0000-0000-0000-111111111111
            groupName: Kafka security group name
        osType: Linux
        storageProfile:
          storageaccounts:
            - container: containername
              isDefault: true
              key: storagekey
              name: mystorage.blob.core.windows.net
        tier: Standard
      resourceGroupName: rg1

```

{{% /example %}}
{{% example %}}
### Create Secure Hadoop cluster
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var cluster = new AzureNative.HDInsight.Cluster("cluster", new()
    {
        ClusterName = "cluster1",
        Properties = new AzureNative.HDInsight.Inputs.ClusterCreatePropertiesArgs
        {
            ClusterDefinition = new AzureNative.HDInsight.Inputs.ClusterDefinitionArgs
            {
                Configurations = 
                {
                    { "gateway", 
                    {
                        { "restAuthCredential.isEnabled", true },
                        { "restAuthCredential.password", "**********" },
                        { "restAuthCredential.username", "admin" },
                    } },
                },
                Kind = "Hadoop",
            },
            ClusterVersion = "3.5",
            ComputeProfile = new AzureNative.HDInsight.Inputs.ComputeProfileArgs
            {
                Roles = new[]
                {
                    new AzureNative.HDInsight.Inputs.RoleArgs
                    {
                        HardwareProfile = new AzureNative.HDInsight.Inputs.HardwareProfileArgs
                        {
                            VmSize = "Standard_D3_V2",
                        },
                        MinInstanceCount = 1,
                        Name = "headnode",
                        OsProfile = new AzureNative.HDInsight.Inputs.OsProfileArgs
                        {
                            LinuxOperatingSystemProfile = new AzureNative.HDInsight.Inputs.LinuxOperatingSystemProfileArgs
                            {
                                Password = "**********",
                                SshProfile = new AzureNative.HDInsight.Inputs.SshProfileArgs
                                {
                                    PublicKeys = new[]
                                    {
                                        new AzureNative.HDInsight.Inputs.SshPublicKeyArgs
                                        {
                                            CertificateData = "**********",
                                        },
                                    },
                                },
                                Username = "sshuser",
                            },
                        },
                        ScriptActions = new[] {},
                        TargetInstanceCount = 2,
                        VirtualNetworkProfile = new AzureNative.HDInsight.Inputs.VirtualNetworkProfileArgs
                        {
                            Id = "/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname",
                            Subnet = "/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname/subnets/vnetsubnet",
                        },
                    },
                    new AzureNative.HDInsight.Inputs.RoleArgs
                    {
                        HardwareProfile = new AzureNative.HDInsight.Inputs.HardwareProfileArgs
                        {
                            VmSize = "Standard_D3_V2",
                        },
                        MinInstanceCount = 1,
                        Name = "workernode",
                        OsProfile = new AzureNative.HDInsight.Inputs.OsProfileArgs
                        {
                            LinuxOperatingSystemProfile = new AzureNative.HDInsight.Inputs.LinuxOperatingSystemProfileArgs
                            {
                                Password = "**********",
                                SshProfile = new AzureNative.HDInsight.Inputs.SshProfileArgs
                                {
                                    PublicKeys = new[]
                                    {
                                        new AzureNative.HDInsight.Inputs.SshPublicKeyArgs
                                        {
                                            CertificateData = "**********",
                                        },
                                    },
                                },
                                Username = "sshuser",
                            },
                        },
                        ScriptActions = new[] {},
                        TargetInstanceCount = 4,
                        VirtualNetworkProfile = new AzureNative.HDInsight.Inputs.VirtualNetworkProfileArgs
                        {
                            Id = "/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname",
                            Subnet = "/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname/subnets/vnetsubnet",
                        },
                    },
                    new AzureNative.HDInsight.Inputs.RoleArgs
                    {
                        HardwareProfile = new AzureNative.HDInsight.Inputs.HardwareProfileArgs
                        {
                            VmSize = "Small",
                        },
                        MinInstanceCount = 1,
                        Name = "zookeepernode",
                        OsProfile = new AzureNative.HDInsight.Inputs.OsProfileArgs
                        {
                            LinuxOperatingSystemProfile = new AzureNative.HDInsight.Inputs.LinuxOperatingSystemProfileArgs
                            {
                                Password = "**********",
                                SshProfile = new AzureNative.HDInsight.Inputs.SshProfileArgs
                                {
                                    PublicKeys = new[]
                                    {
                                        new AzureNative.HDInsight.Inputs.SshPublicKeyArgs
                                        {
                                            CertificateData = "**********",
                                        },
                                    },
                                },
                                Username = "sshuser",
                            },
                        },
                        ScriptActions = new[] {},
                        TargetInstanceCount = 3,
                        VirtualNetworkProfile = new AzureNative.HDInsight.Inputs.VirtualNetworkProfileArgs
                        {
                            Id = "/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname",
                            Subnet = "/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname/subnets/vnetsubnet",
                        },
                    },
                },
            },
            OsType = "Linux",
            SecurityProfile = new AzureNative.HDInsight.Inputs.SecurityProfileArgs
            {
                ClusterUsersGroupDNs = new[]
                {
                    "hdiusers",
                },
                DirectoryType = "ActiveDirectory",
                Domain = "DomainName",
                DomainUserPassword = "**********",
                DomainUsername = "DomainUsername",
                LdapsUrls = new[]
                {
                    "ldaps://10.10.0.4:636",
                },
                OrganizationalUnitDN = "OU=Hadoop,DC=hdinsight,DC=test",
            },
            StorageProfile = new AzureNative.HDInsight.Inputs.StorageProfileArgs
            {
                Storageaccounts = new[]
                {
                    new AzureNative.HDInsight.Inputs.StorageAccountArgs
                    {
                        Container = "containername",
                        IsDefault = true,
                        Key = "storage account key",
                        Name = "mystorage.blob.core.windows.net",
                    },
                },
            },
            Tier = "Premium",
        },
        ResourceGroupName = "rg1",
        Tags = 
        {
            { "key1", "val1" },
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.hdinsight.Cluster;
import com.pulumi.azurenative.hdinsight.ClusterArgs;
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
        var cluster = new Cluster("cluster", ClusterArgs.builder()        
            .clusterName("cluster1")
            .properties(Map.ofEntries(
                Map.entry("clusterDefinition", Map.ofEntries(
                    Map.entry("configurations", Map.of("gateway", ClusterCreatePropertiesArgs.builder()
%!v(PANIC=Format method: interface conversion: model.Expression is *model.TemplateExpression, not *model.LiteralValueExpression))),
                        Map.entry("kind", "Hadoop")
                    )),
                    Map.entry("clusterVersion", "3.5"),
                    Map.entry("computeProfile", Map.of("roles",                     
                        Map.ofEntries(
                            Map.entry("hardwareProfile", Map.of("vmSize", "Standard_D3_V2")),
                            Map.entry("minInstanceCount", 1),
                            Map.entry("name", "headnode"),
                            Map.entry("osProfile", Map.of("linuxOperatingSystemProfile", Map.ofEntries(
                                Map.entry("password", "**********"),
                                Map.entry("sshProfile", Map.of("publicKeys", Map.of("certificateData", "**********"))),
                                Map.entry("username", "sshuser")
                            ))),
                            Map.entry("scriptActions", ),
                            Map.entry("targetInstanceCount", 2),
                            Map.entry("virtualNetworkProfile", Map.ofEntries(
                                Map.entry("id", "/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname"),
                                Map.entry("subnet", "/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname/subnets/vnetsubnet")
                            ))
                        ),
                        Map.ofEntries(
                            Map.entry("hardwareProfile", Map.of("vmSize", "Standard_D3_V2")),
                            Map.entry("minInstanceCount", 1),
                            Map.entry("name", "workernode"),
                            Map.entry("osProfile", Map.of("linuxOperatingSystemProfile", Map.ofEntries(
                                Map.entry("password", "**********"),
                                Map.entry("sshProfile", Map.of("publicKeys", Map.of("certificateData", "**********"))),
                                Map.entry("username", "sshuser")
                            ))),
                            Map.entry("scriptActions", ),
                            Map.entry("targetInstanceCount", 4),
                            Map.entry("virtualNetworkProfile", Map.ofEntries(
                                Map.entry("id", "/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname"),
                                Map.entry("subnet", "/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname/subnets/vnetsubnet")
                            ))
                        ),
                        Map.ofEntries(
                            Map.entry("hardwareProfile", Map.of("vmSize", "Small")),
                            Map.entry("minInstanceCount", 1),
                            Map.entry("name", "zookeepernode"),
                            Map.entry("osProfile", Map.of("linuxOperatingSystemProfile", Map.ofEntries(
                                Map.entry("password", "**********"),
                                Map.entry("sshProfile", Map.of("publicKeys", Map.of("certificateData", "**********"))),
                                Map.entry("username", "sshuser")
                            ))),
                            Map.entry("scriptActions", ),
                            Map.entry("targetInstanceCount", 3),
                            Map.entry("virtualNetworkProfile", Map.ofEntries(
                                Map.entry("id", "/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname"),
                                Map.entry("subnet", "/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname/subnets/vnetsubnet")
                            ))
                        ))),
                    Map.entry("osType", "Linux"),
                    Map.entry("securityProfile", Map.ofEntries(
                        Map.entry("clusterUsersGroupDNs", "hdiusers"),
                        Map.entry("directoryType", "ActiveDirectory"),
                        Map.entry("domain", "DomainName"),
                        Map.entry("domainUserPassword", "**********"),
                        Map.entry("domainUsername", "DomainUsername"),
                        Map.entry("ldapsUrls", "ldaps://10.10.0.4:636"),
                        Map.entry("organizationalUnitDN", "OU=Hadoop,DC=hdinsight,DC=test")
                    )),
                    Map.entry("storageProfile", Map.of("storageaccounts", Map.ofEntries(
                        Map.entry("container", "containername"),
                        Map.entry("isDefault", true),
                        Map.entry("key", "storage account key"),
                        Map.entry("name", "mystorage.blob.core.windows.net")
                    ))),
                    Map.entry("tier", "Premium")
                ))
                .resourceGroupName("rg1")
                .tags(Map.of("key1", "val1"))
                .build());

        }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const cluster = new azure_native.hdinsight.Cluster("cluster", {
    clusterName: "cluster1",
    properties: {
        clusterDefinition: {
            configurations: {
                gateway: {
                    "restAuthCredential.isEnabled": true,
                    "restAuthCredential.password": "**********",
                    "restAuthCredential.username": "admin",
                },
            },
            kind: "Hadoop",
        },
        clusterVersion: "3.5",
        computeProfile: {
            roles: [
                {
                    hardwareProfile: {
                        vmSize: "Standard_D3_V2",
                    },
                    minInstanceCount: 1,
                    name: "headnode",
                    osProfile: {
                        linuxOperatingSystemProfile: {
                            password: "**********",
                            sshProfile: {
                                publicKeys: [{
                                    certificateData: "**********",
                                }],
                            },
                            username: "sshuser",
                        },
                    },
                    scriptActions: [],
                    targetInstanceCount: 2,
                    virtualNetworkProfile: {
                        id: "/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname",
                        subnet: "/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname/subnets/vnetsubnet",
                    },
                },
                {
                    hardwareProfile: {
                        vmSize: "Standard_D3_V2",
                    },
                    minInstanceCount: 1,
                    name: "workernode",
                    osProfile: {
                        linuxOperatingSystemProfile: {
                            password: "**********",
                            sshProfile: {
                                publicKeys: [{
                                    certificateData: "**********",
                                }],
                            },
                            username: "sshuser",
                        },
                    },
                    scriptActions: [],
                    targetInstanceCount: 4,
                    virtualNetworkProfile: {
                        id: "/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname",
                        subnet: "/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname/subnets/vnetsubnet",
                    },
                },
                {
                    hardwareProfile: {
                        vmSize: "Small",
                    },
                    minInstanceCount: 1,
                    name: "zookeepernode",
                    osProfile: {
                        linuxOperatingSystemProfile: {
                            password: "**********",
                            sshProfile: {
                                publicKeys: [{
                                    certificateData: "**********",
                                }],
                            },
                            username: "sshuser",
                        },
                    },
                    scriptActions: [],
                    targetInstanceCount: 3,
                    virtualNetworkProfile: {
                        id: "/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname",
                        subnet: "/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname/subnets/vnetsubnet",
                    },
                },
            ],
        },
        osType: "Linux",
        securityProfile: {
            clusterUsersGroupDNs: ["hdiusers"],
            directoryType: "ActiveDirectory",
            domain: "DomainName",
            domainUserPassword: "**********",
            domainUsername: "DomainUsername",
            ldapsUrls: ["ldaps://10.10.0.4:636"],
            organizationalUnitDN: "OU=Hadoop,DC=hdinsight,DC=test",
        },
        storageProfile: {
            storageaccounts: [{
                container: "containername",
                isDefault: true,
                key: "storage account key",
                name: "mystorage.blob.core.windows.net",
            }],
        },
        tier: "Premium",
    },
    resourceGroupName: "rg1",
    tags: {
        key1: "val1",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

cluster = azure_native.hdinsight.Cluster("cluster",
    cluster_name="cluster1",
    properties=azure_native.hdinsight.ClusterGetPropertiesResponseArgs(
        cluster_definition=azure_native.hdinsight.ClusterDefinitionArgs(
            configurations={
                "gateway": {
                    "restAuthCredential.isEnabled": True,
                    "restAuthCredential.password": "**********",
                    "restAuthCredential.username": "admin",
                },
            },
            kind="Hadoop",
        ),
        cluster_version="3.5",
        compute_profile={
            "roles": [
                {
                    "hardwareProfile": azure_native.hdinsight.HardwareProfileArgs(
                        vm_size="Standard_D3_V2",
                    ),
                    "minInstanceCount": 1,
                    "name": "headnode",
                    "osProfile": {
                        "linuxOperatingSystemProfile": {
                            "password": "**********",
                            "sshProfile": {
                                "publicKeys": [azure_native.hdinsight.SshPublicKeyArgs(
                                    certificate_data="**********",
                                )],
                            },
                            "username": "sshuser",
                        },
                    },
                    "scriptActions": [],
                    "targetInstanceCount": 2,
                    "virtualNetworkProfile": azure_native.hdinsight.VirtualNetworkProfileArgs(
                        id="/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname",
                        subnet="/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname/subnets/vnetsubnet",
                    ),
                },
                {
                    "hardwareProfile": azure_native.hdinsight.HardwareProfileArgs(
                        vm_size="Standard_D3_V2",
                    ),
                    "minInstanceCount": 1,
                    "name": "workernode",
                    "osProfile": {
                        "linuxOperatingSystemProfile": {
                            "password": "**********",
                            "sshProfile": {
                                "publicKeys": [azure_native.hdinsight.SshPublicKeyArgs(
                                    certificate_data="**********",
                                )],
                            },
                            "username": "sshuser",
                        },
                    },
                    "scriptActions": [],
                    "targetInstanceCount": 4,
                    "virtualNetworkProfile": azure_native.hdinsight.VirtualNetworkProfileArgs(
                        id="/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname",
                        subnet="/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname/subnets/vnetsubnet",
                    ),
                },
                {
                    "hardwareProfile": azure_native.hdinsight.HardwareProfileArgs(
                        vm_size="Small",
                    ),
                    "minInstanceCount": 1,
                    "name": "zookeepernode",
                    "osProfile": {
                        "linuxOperatingSystemProfile": {
                            "password": "**********",
                            "sshProfile": {
                                "publicKeys": [azure_native.hdinsight.SshPublicKeyArgs(
                                    certificate_data="**********",
                                )],
                            },
                            "username": "sshuser",
                        },
                    },
                    "scriptActions": [],
                    "targetInstanceCount": 3,
                    "virtualNetworkProfile": azure_native.hdinsight.VirtualNetworkProfileArgs(
                        id="/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname",
                        subnet="/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname/subnets/vnetsubnet",
                    ),
                },
            ],
        },
        os_type="Linux",
        security_profile=azure_native.hdinsight.SecurityProfileArgs(
            cluster_users_group_dns=["hdiusers"],
            directory_type="ActiveDirectory",
            domain="DomainName",
            domain_user_password="**********",
            domain_username="DomainUsername",
            ldaps_urls=["ldaps://10.10.0.4:636"],
            organizational_unit_dn="OU=Hadoop,DC=hdinsight,DC=test",
        ),
        storage_profile={
            "storageaccounts": [azure_native.hdinsight.StorageAccountArgs(
                container="containername",
                is_default=True,
                key="storage account key",
                name="mystorage.blob.core.windows.net",
            )],
        },
        tier="Premium",
    ),
    resource_group_name="rg1",
    tags={
        "key1": "val1",
    })

```

```yaml
resources:
  cluster:
    type: azure-native:hdinsight:Cluster
    properties:
      clusterName: cluster1
      properties:
        clusterDefinition:
          configurations:
            gateway:
              restAuthCredential.isEnabled: true
              restAuthCredential.password: '**********'
              restAuthCredential.username: admin
          kind: Hadoop
        clusterVersion: '3.5'
        computeProfile:
          roles:
            - hardwareProfile:
                vmSize: Standard_D3_V2
              minInstanceCount: 1
              name: headnode
              osProfile:
                linuxOperatingSystemProfile:
                  password: '**********'
                  sshProfile:
                    publicKeys:
                      - certificateData: '**********'
                  username: sshuser
              scriptActions: []
              targetInstanceCount: 2
              virtualNetworkProfile:
                id: /subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname
                subnet: /subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname/subnets/vnetsubnet
            - hardwareProfile:
                vmSize: Standard_D3_V2
              minInstanceCount: 1
              name: workernode
              osProfile:
                linuxOperatingSystemProfile:
                  password: '**********'
                  sshProfile:
                    publicKeys:
                      - certificateData: '**********'
                  username: sshuser
              scriptActions: []
              targetInstanceCount: 4
              virtualNetworkProfile:
                id: /subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname
                subnet: /subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname/subnets/vnetsubnet
            - hardwareProfile:
                vmSize: Small
              minInstanceCount: 1
              name: zookeepernode
              osProfile:
                linuxOperatingSystemProfile:
                  password: '**********'
                  sshProfile:
                    publicKeys:
                      - certificateData: '**********'
                  username: sshuser
              scriptActions: []
              targetInstanceCount: 3
              virtualNetworkProfile:
                id: /subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname
                subnet: /subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname/subnets/vnetsubnet
        osType: Linux
        securityProfile:
          clusterUsersGroupDNs:
            - hdiusers
          directoryType: ActiveDirectory
          domain: DomainName
          domainUserPassword: '**********'
          domainUsername: DomainUsername
          ldapsUrls:
            - ldaps://10.10.0.4:636
          organizationalUnitDN: OU=Hadoop,DC=hdinsight,DC=test
        storageProfile:
          storageaccounts:
            - container: containername
              isDefault: true
              key: storage account key
              name: mystorage.blob.core.windows.net
        tier: Premium
      resourceGroupName: rg1
      tags:
        key1: val1

```

{{% /example %}}
{{% example %}}
### Create Spark on Linux Cluster with SSH password
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var cluster = new AzureNative.HDInsight.Cluster("cluster", new()
    {
        ClusterName = "cluster1",
        Properties = new AzureNative.HDInsight.Inputs.ClusterCreatePropertiesArgs
        {
            ClusterDefinition = new AzureNative.HDInsight.Inputs.ClusterDefinitionArgs
            {
                ComponentVersion = 
                {
                    { "Spark", "2.0" },
                },
                Configurations = 
                {
                    { "gateway", 
                    {
                        { "restAuthCredential.isEnabled", true },
                        { "restAuthCredential.password", "**********" },
                        { "restAuthCredential.username", "admin" },
                    } },
                },
                Kind = "Spark",
            },
            ClusterVersion = "3.5",
            ComputeProfile = new AzureNative.HDInsight.Inputs.ComputeProfileArgs
            {
                Roles = new[]
                {
                    new AzureNative.HDInsight.Inputs.RoleArgs
                    {
                        HardwareProfile = new AzureNative.HDInsight.Inputs.HardwareProfileArgs
                        {
                            VmSize = "Standard_D12_V2",
                        },
                        MinInstanceCount = 1,
                        Name = "headnode",
                        OsProfile = new AzureNative.HDInsight.Inputs.OsProfileArgs
                        {
                            LinuxOperatingSystemProfile = new AzureNative.HDInsight.Inputs.LinuxOperatingSystemProfileArgs
                            {
                                Password = "**********",
                                Username = "sshuser",
                            },
                        },
                        TargetInstanceCount = 2,
                    },
                    new AzureNative.HDInsight.Inputs.RoleArgs
                    {
                        HardwareProfile = new AzureNative.HDInsight.Inputs.HardwareProfileArgs
                        {
                            VmSize = "Standard_D4_V2",
                        },
                        MinInstanceCount = 1,
                        Name = "workernode",
                        OsProfile = new AzureNative.HDInsight.Inputs.OsProfileArgs
                        {
                            LinuxOperatingSystemProfile = new AzureNative.HDInsight.Inputs.LinuxOperatingSystemProfileArgs
                            {
                                Password = "**********",
                                Username = "sshuser",
                            },
                        },
                        TargetInstanceCount = 4,
                    },
                },
            },
            OsType = "Linux",
            StorageProfile = new AzureNative.HDInsight.Inputs.StorageProfileArgs
            {
                Storageaccounts = new[]
                {
                    new AzureNative.HDInsight.Inputs.StorageAccountArgs
                    {
                        Container = "containername",
                        IsDefault = true,
                        Key = "storageapikey*",
                        Name = "mystorage.blob.core.windows.net",
                    },
                },
            },
            Tier = "Standard",
        },
        ResourceGroupName = "rg1",
        Tags = 
        {
            { "key1", "val1" },
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.hdinsight.Cluster;
import com.pulumi.azurenative.hdinsight.ClusterArgs;
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
        var cluster = new Cluster("cluster", ClusterArgs.builder()        
            .clusterName("cluster1")
            .properties(Map.ofEntries(
                Map.entry("clusterDefinition", Map.ofEntries(
                    Map.entry("componentVersion", Map.of("Spark", "2.0")),
                    Map.entry("configurations", Map.of("gateway", ClusterCreatePropertiesArgs.builder()
%!v(PANIC=Format method: interface conversion: model.Expression is *model.TemplateExpression, not *model.LiteralValueExpression))),
                        Map.entry("kind", "Spark")
                    )),
                    Map.entry("clusterVersion", "3.5"),
                    Map.entry("computeProfile", Map.of("roles",                     
                        Map.ofEntries(
                            Map.entry("hardwareProfile", Map.of("vmSize", "Standard_D12_V2")),
                            Map.entry("minInstanceCount", 1),
                            Map.entry("name", "headnode"),
                            Map.entry("osProfile", Map.of("linuxOperatingSystemProfile", Map.ofEntries(
                                Map.entry("password", "**********"),
                                Map.entry("username", "sshuser")
                            ))),
                            Map.entry("targetInstanceCount", 2)
                        ),
                        Map.ofEntries(
                            Map.entry("hardwareProfile", Map.of("vmSize", "Standard_D4_V2")),
                            Map.entry("minInstanceCount", 1),
                            Map.entry("name", "workernode"),
                            Map.entry("osProfile", Map.of("linuxOperatingSystemProfile", Map.ofEntries(
                                Map.entry("password", "**********"),
                                Map.entry("username", "sshuser")
                            ))),
                            Map.entry("targetInstanceCount", 4)
                        ))),
                    Map.entry("osType", "Linux"),
                    Map.entry("storageProfile", Map.of("storageaccounts", Map.ofEntries(
                        Map.entry("container", "containername"),
                        Map.entry("isDefault", true),
                        Map.entry("key", "storageapikey*"),
                        Map.entry("name", "mystorage.blob.core.windows.net")
                    ))),
                    Map.entry("tier", "Standard")
                ))
                .resourceGroupName("rg1")
                .tags(Map.of("key1", "val1"))
                .build());

        }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const cluster = new azure_native.hdinsight.Cluster("cluster", {
    clusterName: "cluster1",
    properties: {
        clusterDefinition: {
            componentVersion: {
                Spark: "2.0",
            },
            configurations: {
                gateway: {
                    "restAuthCredential.isEnabled": true,
                    "restAuthCredential.password": "**********",
                    "restAuthCredential.username": "admin",
                },
            },
            kind: "Spark",
        },
        clusterVersion: "3.5",
        computeProfile: {
            roles: [
                {
                    hardwareProfile: {
                        vmSize: "Standard_D12_V2",
                    },
                    minInstanceCount: 1,
                    name: "headnode",
                    osProfile: {
                        linuxOperatingSystemProfile: {
                            password: "**********",
                            username: "sshuser",
                        },
                    },
                    targetInstanceCount: 2,
                },
                {
                    hardwareProfile: {
                        vmSize: "Standard_D4_V2",
                    },
                    minInstanceCount: 1,
                    name: "workernode",
                    osProfile: {
                        linuxOperatingSystemProfile: {
                            password: "**********",
                            username: "sshuser",
                        },
                    },
                    targetInstanceCount: 4,
                },
            ],
        },
        osType: "Linux",
        storageProfile: {
            storageaccounts: [{
                container: "containername",
                isDefault: true,
                key: "storageapikey*",
                name: "mystorage.blob.core.windows.net",
            }],
        },
        tier: "Standard",
    },
    resourceGroupName: "rg1",
    tags: {
        key1: "val1",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

cluster = azure_native.hdinsight.Cluster("cluster",
    cluster_name="cluster1",
    properties=azure_native.hdinsight.ClusterGetPropertiesResponseArgs(
        cluster_definition=azure_native.hdinsight.ClusterDefinitionArgs(
            component_version={
                "Spark": "2.0",
            },
            configurations={
                "gateway": {
                    "restAuthCredential.isEnabled": True,
                    "restAuthCredential.password": "**********",
                    "restAuthCredential.username": "admin",
                },
            },
            kind="Spark",
        ),
        cluster_version="3.5",
        compute_profile={
            "roles": [
                {
                    "hardwareProfile": azure_native.hdinsight.HardwareProfileArgs(
                        vm_size="Standard_D12_V2",
                    ),
                    "minInstanceCount": 1,
                    "name": "headnode",
                    "osProfile": {
                        "linuxOperatingSystemProfile": azure_native.hdinsight.LinuxOperatingSystemProfileArgs(
                            password="**********",
                            username="sshuser",
                        ),
                    },
                    "targetInstanceCount": 2,
                },
                {
                    "hardwareProfile": azure_native.hdinsight.HardwareProfileArgs(
                        vm_size="Standard_D4_V2",
                    ),
                    "minInstanceCount": 1,
                    "name": "workernode",
                    "osProfile": {
                        "linuxOperatingSystemProfile": azure_native.hdinsight.LinuxOperatingSystemProfileArgs(
                            password="**********",
                            username="sshuser",
                        ),
                    },
                    "targetInstanceCount": 4,
                },
            ],
        },
        os_type="Linux",
        storage_profile={
            "storageaccounts": [azure_native.hdinsight.StorageAccountArgs(
                container="containername",
                is_default=True,
                key="storageapikey*",
                name="mystorage.blob.core.windows.net",
            )],
        },
        tier="Standard",
    ),
    resource_group_name="rg1",
    tags={
        "key1": "val1",
    })

```

```yaml
resources:
  cluster:
    type: azure-native:hdinsight:Cluster
    properties:
      clusterName: cluster1
      properties:
        clusterDefinition:
          componentVersion:
            Spark: '2.0'
          configurations:
            gateway:
              restAuthCredential.isEnabled: true
              restAuthCredential.password: '**********'
              restAuthCredential.username: admin
          kind: Spark
        clusterVersion: '3.5'
        computeProfile:
          roles:
            - hardwareProfile:
                vmSize: Standard_D12_V2
              minInstanceCount: 1
              name: headnode
              osProfile:
                linuxOperatingSystemProfile:
                  password: '**********'
                  username: sshuser
              targetInstanceCount: 2
            - hardwareProfile:
                vmSize: Standard_D4_V2
              minInstanceCount: 1
              name: workernode
              osProfile:
                linuxOperatingSystemProfile:
                  password: '**********'
                  username: sshuser
              targetInstanceCount: 4
        osType: Linux
        storageProfile:
          storageaccounts:
            - container: containername
              isDefault: true
              key: storageapikey*
              name: mystorage.blob.core.windows.net
        tier: Standard
      resourceGroupName: rg1
      tags:
        key1: val1

```

{{% /example %}}
{{% example %}}
### Create cluster with TLS 1.2
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var cluster = new AzureNative.HDInsight.Cluster("cluster", new()
    {
        ClusterName = "cluster1",
        Properties = new AzureNative.HDInsight.Inputs.ClusterCreatePropertiesArgs
        {
            ClusterDefinition = new AzureNative.HDInsight.Inputs.ClusterDefinitionArgs
            {
                Configurations = 
                {
                    { "gateway", 
                    {
                        { "restAuthCredential.isEnabled", true },
                        { "restAuthCredential.password", "**********" },
                        { "restAuthCredential.username", "admin" },
                    } },
                },
                Kind = "Hadoop",
            },
            ClusterVersion = "3.6",
            ComputeProfile = new AzureNative.HDInsight.Inputs.ComputeProfileArgs
            {
                Roles = new[]
                {
                    new AzureNative.HDInsight.Inputs.RoleArgs
                    {
                        HardwareProfile = new AzureNative.HDInsight.Inputs.HardwareProfileArgs
                        {
                            VmSize = "Large",
                        },
                        Name = "headnode",
                        OsProfile = new AzureNative.HDInsight.Inputs.OsProfileArgs
                        {
                            LinuxOperatingSystemProfile = new AzureNative.HDInsight.Inputs.LinuxOperatingSystemProfileArgs
                            {
                                Password = "**********",
                                Username = "sshuser",
                            },
                        },
                        TargetInstanceCount = 2,
                    },
                    new AzureNative.HDInsight.Inputs.RoleArgs
                    {
                        HardwareProfile = new AzureNative.HDInsight.Inputs.HardwareProfileArgs
                        {
                            VmSize = "Large",
                        },
                        Name = "workernode",
                        OsProfile = new AzureNative.HDInsight.Inputs.OsProfileArgs
                        {
                            LinuxOperatingSystemProfile = new AzureNative.HDInsight.Inputs.LinuxOperatingSystemProfileArgs
                            {
                                Password = "**********",
                                Username = "sshuser",
                            },
                        },
                        TargetInstanceCount = 3,
                    },
                    new AzureNative.HDInsight.Inputs.RoleArgs
                    {
                        HardwareProfile = new AzureNative.HDInsight.Inputs.HardwareProfileArgs
                        {
                            VmSize = "Small",
                        },
                        Name = "zookeepernode",
                        OsProfile = new AzureNative.HDInsight.Inputs.OsProfileArgs
                        {
                            LinuxOperatingSystemProfile = new AzureNative.HDInsight.Inputs.LinuxOperatingSystemProfileArgs
                            {
                                Password = "**********",
                                Username = "sshuser",
                            },
                        },
                        TargetInstanceCount = 3,
                    },
                },
            },
            MinSupportedTlsVersion = "1.2",
            OsType = "Linux",
            StorageProfile = new AzureNative.HDInsight.Inputs.StorageProfileArgs
            {
                Storageaccounts = new[]
                {
                    new AzureNative.HDInsight.Inputs.StorageAccountArgs
                    {
                        Container = "default8525",
                        IsDefault = true,
                        Key = "storagekey",
                        Name = "mystorage.blob.core.windows.net",
                    },
                },
            },
            Tier = "Standard",
        },
        ResourceGroupName = "rg1",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.hdinsight.Cluster;
import com.pulumi.azurenative.hdinsight.ClusterArgs;
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
        var cluster = new Cluster("cluster", ClusterArgs.builder()        
            .clusterName("cluster1")
            .properties(Map.ofEntries(
                Map.entry("clusterDefinition", Map.ofEntries(
                    Map.entry("configurations", Map.of("gateway", ClusterCreatePropertiesArgs.builder()
%!v(PANIC=Format method: interface conversion: model.Expression is *model.TemplateExpression, not *model.LiteralValueExpression))),
                        Map.entry("kind", "Hadoop")
                    )),
                    Map.entry("clusterVersion", "3.6"),
                    Map.entry("computeProfile", Map.of("roles",                     
                        Map.ofEntries(
                            Map.entry("hardwareProfile", Map.of("vmSize", "Large")),
                            Map.entry("name", "headnode"),
                            Map.entry("osProfile", Map.of("linuxOperatingSystemProfile", Map.ofEntries(
                                Map.entry("password", "**********"),
                                Map.entry("username", "sshuser")
                            ))),
                            Map.entry("targetInstanceCount", 2)
                        ),
                        Map.ofEntries(
                            Map.entry("hardwareProfile", Map.of("vmSize", "Large")),
                            Map.entry("name", "workernode"),
                            Map.entry("osProfile", Map.of("linuxOperatingSystemProfile", Map.ofEntries(
                                Map.entry("password", "**********"),
                                Map.entry("username", "sshuser")
                            ))),
                            Map.entry("targetInstanceCount", 3)
                        ),
                        Map.ofEntries(
                            Map.entry("hardwareProfile", Map.of("vmSize", "Small")),
                            Map.entry("name", "zookeepernode"),
                            Map.entry("osProfile", Map.of("linuxOperatingSystemProfile", Map.ofEntries(
                                Map.entry("password", "**********"),
                                Map.entry("username", "sshuser")
                            ))),
                            Map.entry("targetInstanceCount", 3)
                        ))),
                    Map.entry("minSupportedTlsVersion", "1.2"),
                    Map.entry("osType", "Linux"),
                    Map.entry("storageProfile", Map.of("storageaccounts", Map.ofEntries(
                        Map.entry("container", "default8525"),
                        Map.entry("isDefault", true),
                        Map.entry("key", "storagekey"),
                        Map.entry("name", "mystorage.blob.core.windows.net")
                    ))),
                    Map.entry("tier", "Standard")
                ))
                .resourceGroupName("rg1")
                .build());

        }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const cluster = new azure_native.hdinsight.Cluster("cluster", {
    clusterName: "cluster1",
    properties: {
        clusterDefinition: {
            configurations: {
                gateway: {
                    "restAuthCredential.isEnabled": true,
                    "restAuthCredential.password": "**********",
                    "restAuthCredential.username": "admin",
                },
            },
            kind: "Hadoop",
        },
        clusterVersion: "3.6",
        computeProfile: {
            roles: [
                {
                    hardwareProfile: {
                        vmSize: "Large",
                    },
                    name: "headnode",
                    osProfile: {
                        linuxOperatingSystemProfile: {
                            password: "**********",
                            username: "sshuser",
                        },
                    },
                    targetInstanceCount: 2,
                },
                {
                    hardwareProfile: {
                        vmSize: "Large",
                    },
                    name: "workernode",
                    osProfile: {
                        linuxOperatingSystemProfile: {
                            password: "**********",
                            username: "sshuser",
                        },
                    },
                    targetInstanceCount: 3,
                },
                {
                    hardwareProfile: {
                        vmSize: "Small",
                    },
                    name: "zookeepernode",
                    osProfile: {
                        linuxOperatingSystemProfile: {
                            password: "**********",
                            username: "sshuser",
                        },
                    },
                    targetInstanceCount: 3,
                },
            ],
        },
        minSupportedTlsVersion: "1.2",
        osType: "Linux",
        storageProfile: {
            storageaccounts: [{
                container: "default8525",
                isDefault: true,
                key: "storagekey",
                name: "mystorage.blob.core.windows.net",
            }],
        },
        tier: "Standard",
    },
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

cluster = azure_native.hdinsight.Cluster("cluster",
    cluster_name="cluster1",
    properties=azure_native.hdinsight.ClusterGetPropertiesResponseArgs(
        cluster_definition=azure_native.hdinsight.ClusterDefinitionArgs(
            configurations={
                "gateway": {
                    "restAuthCredential.isEnabled": True,
                    "restAuthCredential.password": "**********",
                    "restAuthCredential.username": "admin",
                },
            },
            kind="Hadoop",
        ),
        cluster_version="3.6",
        compute_profile={
            "roles": [
                {
                    "hardwareProfile": azure_native.hdinsight.HardwareProfileArgs(
                        vm_size="Large",
                    ),
                    "name": "headnode",
                    "osProfile": {
                        "linuxOperatingSystemProfile": azure_native.hdinsight.LinuxOperatingSystemProfileArgs(
                            password="**********",
                            username="sshuser",
                        ),
                    },
                    "targetInstanceCount": 2,
                },
                {
                    "hardwareProfile": azure_native.hdinsight.HardwareProfileArgs(
                        vm_size="Large",
                    ),
                    "name": "workernode",
                    "osProfile": {
                        "linuxOperatingSystemProfile": azure_native.hdinsight.LinuxOperatingSystemProfileArgs(
                            password="**********",
                            username="sshuser",
                        ),
                    },
                    "targetInstanceCount": 3,
                },
                {
                    "hardwareProfile": azure_native.hdinsight.HardwareProfileArgs(
                        vm_size="Small",
                    ),
                    "name": "zookeepernode",
                    "osProfile": {
                        "linuxOperatingSystemProfile": azure_native.hdinsight.LinuxOperatingSystemProfileArgs(
                            password="**********",
                            username="sshuser",
                        ),
                    },
                    "targetInstanceCount": 3,
                },
            ],
        },
        min_supported_tls_version="1.2",
        os_type="Linux",
        storage_profile={
            "storageaccounts": [azure_native.hdinsight.StorageAccountArgs(
                container="default8525",
                is_default=True,
                key="storagekey",
                name="mystorage.blob.core.windows.net",
            )],
        },
        tier="Standard",
    ),
    resource_group_name="rg1")

```

```yaml
resources:
  cluster:
    type: azure-native:hdinsight:Cluster
    properties:
      clusterName: cluster1
      properties:
        clusterDefinition:
          configurations:
            gateway:
              restAuthCredential.isEnabled: true
              restAuthCredential.password: '**********'
              restAuthCredential.username: admin
          kind: Hadoop
        clusterVersion: '3.6'
        computeProfile:
          roles:
            - hardwareProfile:
                vmSize: Large
              name: headnode
              osProfile:
                linuxOperatingSystemProfile:
                  password: '**********'
                  username: sshuser
              targetInstanceCount: 2
            - hardwareProfile:
                vmSize: Large
              name: workernode
              osProfile:
                linuxOperatingSystemProfile:
                  password: '**********'
                  username: sshuser
              targetInstanceCount: 3
            - hardwareProfile:
                vmSize: Small
              name: zookeepernode
              osProfile:
                linuxOperatingSystemProfile:
                  password: '**********'
                  username: sshuser
              targetInstanceCount: 3
        minSupportedTlsVersion: '1.2'
        osType: Linux
        storageProfile:
          storageaccounts:
            - container: default8525
              isDefault: true
              key: storagekey
              name: mystorage.blob.core.windows.net
        tier: Standard
      resourceGroupName: rg1

```

{{% /example %}}
{{% example %}}
### Create cluster with availability zones
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var cluster = new AzureNative.HDInsight.Cluster("cluster", new()
    {
        ClusterName = "cluster1",
        Properties = new AzureNative.HDInsight.Inputs.ClusterCreatePropertiesArgs
        {
            ClusterDefinition = new AzureNative.HDInsight.Inputs.ClusterDefinitionArgs
            {
                Configurations = 
                {
                    { "ambari-conf", 
                    {
                        { "database-name", "{ambari database name}" },
                        { "database-server", "{sql server name}.database.windows.net" },
                        { "database-user-name", "**********" },
                        { "database-user-password", "**********" },
                    } },
                    { "gateway", 
                    {
                        { "restAuthCredential.isEnabled", true },
                        { "restAuthCredential.password", "**********" },
                        { "restAuthCredential.username", "admin" },
                    } },
                    { "hive-env", 
                    {
                        { "hive_database", "Existing MSSQL Server database with SQL authentication" },
                        { "hive_database_name", "{hive metastore name}" },
                        { "hive_database_type", "mssql" },
                        { "hive_existing_mssql_server_database", "{hive metastore name}" },
                        { "hive_existing_mssql_server_host", "{sql server name}.database.windows.net" },
                        { "hive_hostname", "{sql server name}.database.windows.net" },
                    } },
                    { "hive-site", 
                    {
                        { "javax.jdo.option.ConnectionDriverName", "com.microsoft.sqlserver.jdbc.SQLServerDriver" },
                        { "javax.jdo.option.ConnectionPassword", "**********!" },
                        { "javax.jdo.option.ConnectionURL", "jdbc:sqlserver://{sql server name}.database.windows.net;database={hive metastore name};encrypt=true;trustServerCertificate=true;create=false;loginTimeout=300;sendStringParametersAsUnicode=true;prepareSQL=0" },
                        { "javax.jdo.option.ConnectionUserName", "**********" },
                    } },
                    { "oozie-env", 
                    {
                        { "oozie_database", "Existing MSSQL Server database with SQL authentication" },
                        { "oozie_database_name", "{oozie metastore name}" },
                        { "oozie_database_type", "mssql" },
                        { "oozie_existing_mssql_server_database", "{oozie metastore name}" },
                        { "oozie_existing_mssql_server_host", "{sql server name}.database.windows.net" },
                        { "oozie_hostname", "{sql server name}.database.windows.net" },
                    } },
                    { "oozie-site", 
                    {
                        { "oozie.db.schema.name", "oozie" },
                        { "oozie.service.JPAService.jdbc.driver", "com.microsoft.sqlserver.jdbc.SQLServerDriver" },
                        { "oozie.service.JPAService.jdbc.password", "**********" },
                        { "oozie.service.JPAService.jdbc.url", "jdbc:sqlserver://{sql server name}.database.windows.net;database={oozie metastore name};encrypt=true;trustServerCertificate=true;create=false;loginTimeout=300;sendStringParametersAsUnicode=true;prepareSQL=0" },
                        { "oozie.service.JPAService.jdbc.username", "**********" },
                    } },
                },
                Kind = "hadoop",
            },
            ClusterVersion = "3.6",
            ComputeProfile = new AzureNative.HDInsight.Inputs.ComputeProfileArgs
            {
                Roles = new[]
                {
                    new AzureNative.HDInsight.Inputs.RoleArgs
                    {
                        HardwareProfile = new AzureNative.HDInsight.Inputs.HardwareProfileArgs
                        {
                            VmSize = "standard_d3",
                        },
                        Name = "headnode",
                        OsProfile = new AzureNative.HDInsight.Inputs.OsProfileArgs
                        {
                            LinuxOperatingSystemProfile = new AzureNative.HDInsight.Inputs.LinuxOperatingSystemProfileArgs
                            {
                                Password = "**********",
                                SshProfile = new AzureNative.HDInsight.Inputs.SshProfileArgs
                                {
                                    PublicKeys = new[]
                                    {
                                        new AzureNative.HDInsight.Inputs.SshPublicKeyArgs
                                        {
                                            CertificateData = "**********",
                                        },
                                    },
                                },
                                Username = "sshuser",
                            },
                        },
                        TargetInstanceCount = 2,
                        VirtualNetworkProfile = new AzureNative.HDInsight.Inputs.VirtualNetworkProfileArgs
                        {
                            Id = "/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname",
                            Subnet = "/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname/subnets/vnetsubnet",
                        },
                    },
                    new AzureNative.HDInsight.Inputs.RoleArgs
                    {
                        HardwareProfile = new AzureNative.HDInsight.Inputs.HardwareProfileArgs
                        {
                            VmSize = "standard_d3",
                        },
                        Name = "workernode",
                        OsProfile = new AzureNative.HDInsight.Inputs.OsProfileArgs
                        {
                            LinuxOperatingSystemProfile = new AzureNative.HDInsight.Inputs.LinuxOperatingSystemProfileArgs
                            {
                                Password = "**********",
                                SshProfile = new AzureNative.HDInsight.Inputs.SshProfileArgs
                                {
                                    PublicKeys = new[]
                                    {
                                        new AzureNative.HDInsight.Inputs.SshPublicKeyArgs
                                        {
                                            CertificateData = "**********",
                                        },
                                    },
                                },
                                Username = "sshuser",
                            },
                        },
                        TargetInstanceCount = 2,
                        VirtualNetworkProfile = new AzureNative.HDInsight.Inputs.VirtualNetworkProfileArgs
                        {
                            Id = "/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname",
                            Subnet = "/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname/subnets/vnetsubnet",
                        },
                    },
                },
            },
            OsType = "Linux",
            StorageProfile = new AzureNative.HDInsight.Inputs.StorageProfileArgs
            {
                Storageaccounts = new[]
                {
                    new AzureNative.HDInsight.Inputs.StorageAccountArgs
                    {
                        Container = "containername",
                        IsDefault = true,
                        Key = "storage account key",
                        Name = "mystorage",
                    },
                },
            },
        },
        ResourceGroupName = "rg1",
        Zones = new[]
        {
            "1",
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.hdinsight.Cluster;
import com.pulumi.azurenative.hdinsight.ClusterArgs;
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
        var cluster = new Cluster("cluster", ClusterArgs.builder()        
            .clusterName("cluster1")
            .properties(Map.ofEntries(
                Map.entry("clusterDefinition", Map.ofEntries(
                    Map.entry("configurations", Map.ofEntries(
                        Map.entry("ambari-conf", ClusterCreatePropertiesArgs.builder()
                            .database_name("{ambari database name}")
                            .database_server("{sql server name}.database.windows.net")
                            .database_user_name("**********")
                            .database_user_password("**********")
                            .build()),
                        Map.entry("gateway", ClusterCreatePropertiesArgs.builder()
%!v(PANIC=Format method: interface conversion: model.Expression is *model.TemplateExpression, not *model.LiteralValueExpression)),
                            Map.entry("hive-env", ClusterCreatePropertiesArgs.builder()
                                .hive_database("Existing MSSQL Server database with SQL authentication")
                                .hive_database_name("{hive metastore name}")
                                .hive_database_type("mssql")
                                .hive_existing_mssql_server_database("{hive metastore name}")
                                .hive_existing_mssql_server_host("{sql server name}.database.windows.net")
                                .hive_hostname("{sql server name}.database.windows.net")
                                .build()),
                            Map.entry("hive-site", ClusterCreatePropertiesArgs.builder()
%!v(PANIC=Format method: interface conversion: model.Expression is *model.TemplateExpression, not *model.LiteralValueExpression)),
                                Map.entry("oozie-env", ClusterCreatePropertiesArgs.builder()
                                    .oozie_database("Existing MSSQL Server database with SQL authentication")
                                    .oozie_database_name("{oozie metastore name}")
                                    .oozie_database_type("mssql")
                                    .oozie_existing_mssql_server_database("{oozie metastore name}")
                                    .oozie_existing_mssql_server_host("{sql server name}.database.windows.net")
                                    .oozie_hostname("{sql server name}.database.windows.net")
                                    .build()),
                                Map.entry("oozie-site", ClusterCreatePropertiesArgs.builder()
%!v(PANIC=Format method: interface conversion: model.Expression is *model.TemplateExpression, not *model.LiteralValueExpression))
                                )),
                                Map.entry("kind", "hadoop")
                            )),
                            Map.entry("clusterVersion", "3.6"),
                            Map.entry("computeProfile", Map.of("roles",                             
                                Map.ofEntries(
                                    Map.entry("hardwareProfile", Map.of("vmSize", "standard_d3")),
                                    Map.entry("name", "headnode"),
                                    Map.entry("osProfile", Map.of("linuxOperatingSystemProfile", Map.ofEntries(
                                        Map.entry("password", "**********"),
                                        Map.entry("sshProfile", Map.of("publicKeys", Map.of("certificateData", "**********"))),
                                        Map.entry("username", "sshuser")
                                    ))),
                                    Map.entry("targetInstanceCount", 2),
                                    Map.entry("virtualNetworkProfile", Map.ofEntries(
                                        Map.entry("id", "/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname"),
                                        Map.entry("subnet", "/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname/subnets/vnetsubnet")
                                    ))
                                ),
                                Map.ofEntries(
                                    Map.entry("hardwareProfile", Map.of("vmSize", "standard_d3")),
                                    Map.entry("name", "workernode"),
                                    Map.entry("osProfile", Map.of("linuxOperatingSystemProfile", Map.ofEntries(
                                        Map.entry("password", "**********"),
                                        Map.entry("sshProfile", Map.of("publicKeys", Map.of("certificateData", "**********"))),
                                        Map.entry("username", "sshuser")
                                    ))),
                                    Map.entry("targetInstanceCount", 2),
                                    Map.entry("virtualNetworkProfile", Map.ofEntries(
                                        Map.entry("id", "/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname"),
                                        Map.entry("subnet", "/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname/subnets/vnetsubnet")
                                    ))
                                ))),
                            Map.entry("osType", "Linux"),
                            Map.entry("storageProfile", Map.of("storageaccounts", Map.ofEntries(
                                Map.entry("container", "containername"),
                                Map.entry("isDefault", true),
                                Map.entry("key", "storage account key"),
                                Map.entry("name", "mystorage")
                            )))
                        ))
                        .resourceGroupName("rg1")
                        .zones("1")
                        .build());

                }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const cluster = new azure_native.hdinsight.Cluster("cluster", {
    clusterName: "cluster1",
    properties: {
        clusterDefinition: {
            configurations: {
                "ambari-conf": {
                    "database-name": "{ambari database name}",
                    "database-server": "{sql server name}.database.windows.net",
                    "database-user-name": "**********",
                    "database-user-password": "**********",
                },
                gateway: {
                    "restAuthCredential.isEnabled": true,
                    "restAuthCredential.password": "**********",
                    "restAuthCredential.username": "admin",
                },
                "hive-env": {
                    hive_database: "Existing MSSQL Server database with SQL authentication",
                    hive_database_name: "{hive metastore name}",
                    hive_database_type: "mssql",
                    hive_existing_mssql_server_database: "{hive metastore name}",
                    hive_existing_mssql_server_host: "{sql server name}.database.windows.net",
                    hive_hostname: "{sql server name}.database.windows.net",
                },
                "hive-site": {
                    "javax.jdo.option.ConnectionDriverName": "com.microsoft.sqlserver.jdbc.SQLServerDriver",
                    "javax.jdo.option.ConnectionPassword": "**********!",
                    "javax.jdo.option.ConnectionURL": "jdbc:sqlserver://{sql server name}.database.windows.net;database={hive metastore name};encrypt=true;trustServerCertificate=true;create=false;loginTimeout=300;sendStringParametersAsUnicode=true;prepareSQL=0",
                    "javax.jdo.option.ConnectionUserName": "**********",
                },
                "oozie-env": {
                    oozie_database: "Existing MSSQL Server database with SQL authentication",
                    oozie_database_name: "{oozie metastore name}",
                    oozie_database_type: "mssql",
                    oozie_existing_mssql_server_database: "{oozie metastore name}",
                    oozie_existing_mssql_server_host: "{sql server name}.database.windows.net",
                    oozie_hostname: "{sql server name}.database.windows.net",
                },
                "oozie-site": {
                    "oozie.db.schema.name": "oozie",
                    "oozie.service.JPAService.jdbc.driver": "com.microsoft.sqlserver.jdbc.SQLServerDriver",
                    "oozie.service.JPAService.jdbc.password": "**********",
                    "oozie.service.JPAService.jdbc.url": "jdbc:sqlserver://{sql server name}.database.windows.net;database={oozie metastore name};encrypt=true;trustServerCertificate=true;create=false;loginTimeout=300;sendStringParametersAsUnicode=true;prepareSQL=0",
                    "oozie.service.JPAService.jdbc.username": "**********",
                },
            },
            kind: "hadoop",
        },
        clusterVersion: "3.6",
        computeProfile: {
            roles: [
                {
                    hardwareProfile: {
                        vmSize: "standard_d3",
                    },
                    name: "headnode",
                    osProfile: {
                        linuxOperatingSystemProfile: {
                            password: "**********",
                            sshProfile: {
                                publicKeys: [{
                                    certificateData: "**********",
                                }],
                            },
                            username: "sshuser",
                        },
                    },
                    targetInstanceCount: 2,
                    virtualNetworkProfile: {
                        id: "/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname",
                        subnet: "/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname/subnets/vnetsubnet",
                    },
                },
                {
                    hardwareProfile: {
                        vmSize: "standard_d3",
                    },
                    name: "workernode",
                    osProfile: {
                        linuxOperatingSystemProfile: {
                            password: "**********",
                            sshProfile: {
                                publicKeys: [{
                                    certificateData: "**********",
                                }],
                            },
                            username: "sshuser",
                        },
                    },
                    targetInstanceCount: 2,
                    virtualNetworkProfile: {
                        id: "/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname",
                        subnet: "/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname/subnets/vnetsubnet",
                    },
                },
            ],
        },
        osType: "Linux",
        storageProfile: {
            storageaccounts: [{
                container: "containername",
                isDefault: true,
                key: "storage account key",
                name: "mystorage",
            }],
        },
    },
    resourceGroupName: "rg1",
    zones: ["1"],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

cluster = azure_native.hdinsight.Cluster("cluster",
    cluster_name="cluster1",
    properties=azure_native.hdinsight.ClusterGetPropertiesResponseArgs(
        cluster_definition=azure_native.hdinsight.ClusterDefinitionArgs(
            configurations={
                "ambari-conf": {
                    "database-name": "{ambari database name}",
                    "database-server": "{sql server name}.database.windows.net",
                    "database-user-name": "**********",
                    "database-user-password": "**********",
                },
                "gateway": {
                    "restAuthCredential.isEnabled": True,
                    "restAuthCredential.password": "**********",
                    "restAuthCredential.username": "admin",
                },
                "hive-env": {
                    "hive_database": "Existing MSSQL Server database with SQL authentication",
                    "hive_database_name": "{hive metastore name}",
                    "hive_database_type": "mssql",
                    "hive_existing_mssql_server_database": "{hive metastore name}",
                    "hive_existing_mssql_server_host": "{sql server name}.database.windows.net",
                    "hive_hostname": "{sql server name}.database.windows.net",
                },
                "hive-site": {
                    "javax.jdo.option.ConnectionDriverName": "com.microsoft.sqlserver.jdbc.SQLServerDriver",
                    "javax.jdo.option.ConnectionPassword": "**********!",
                    "javax.jdo.option.ConnectionURL": "jdbc:sqlserver://{sql server name}.database.windows.net;database={hive metastore name};encrypt=true;trustServerCertificate=true;create=false;loginTimeout=300;sendStringParametersAsUnicode=true;prepareSQL=0",
                    "javax.jdo.option.ConnectionUserName": "**********",
                },
                "oozie-env": {
                    "oozie_database": "Existing MSSQL Server database with SQL authentication",
                    "oozie_database_name": "{oozie metastore name}",
                    "oozie_database_type": "mssql",
                    "oozie_existing_mssql_server_database": "{oozie metastore name}",
                    "oozie_existing_mssql_server_host": "{sql server name}.database.windows.net",
                    "oozie_hostname": "{sql server name}.database.windows.net",
                },
                "oozie-site": {
                    "oozie.db.schema.name": "oozie",
                    "oozie.service.JPAService.jdbc.driver": "com.microsoft.sqlserver.jdbc.SQLServerDriver",
                    "oozie.service.JPAService.jdbc.password": "**********",
                    "oozie.service.JPAService.jdbc.url": "jdbc:sqlserver://{sql server name}.database.windows.net;database={oozie metastore name};encrypt=true;trustServerCertificate=true;create=false;loginTimeout=300;sendStringParametersAsUnicode=true;prepareSQL=0",
                    "oozie.service.JPAService.jdbc.username": "**********",
                },
            },
            kind="hadoop",
        ),
        cluster_version="3.6",
        compute_profile={
            "roles": [
                {
                    "hardwareProfile": azure_native.hdinsight.HardwareProfileArgs(
                        vm_size="standard_d3",
                    ),
                    "name": "headnode",
                    "osProfile": {
                        "linuxOperatingSystemProfile": {
                            "password": "**********",
                            "sshProfile": {
                                "publicKeys": [azure_native.hdinsight.SshPublicKeyArgs(
                                    certificate_data="**********",
                                )],
                            },
                            "username": "sshuser",
                        },
                    },
                    "targetInstanceCount": 2,
                    "virtualNetworkProfile": azure_native.hdinsight.VirtualNetworkProfileArgs(
                        id="/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname",
                        subnet="/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname/subnets/vnetsubnet",
                    ),
                },
                {
                    "hardwareProfile": azure_native.hdinsight.HardwareProfileArgs(
                        vm_size="standard_d3",
                    ),
                    "name": "workernode",
                    "osProfile": {
                        "linuxOperatingSystemProfile": {
                            "password": "**********",
                            "sshProfile": {
                                "publicKeys": [azure_native.hdinsight.SshPublicKeyArgs(
                                    certificate_data="**********",
                                )],
                            },
                            "username": "sshuser",
                        },
                    },
                    "targetInstanceCount": 2,
                    "virtualNetworkProfile": azure_native.hdinsight.VirtualNetworkProfileArgs(
                        id="/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname",
                        subnet="/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname/subnets/vnetsubnet",
                    ),
                },
            ],
        },
        os_type="Linux",
        storage_profile={
            "storageaccounts": [azure_native.hdinsight.StorageAccountArgs(
                container="containername",
                is_default=True,
                key="storage account key",
                name="mystorage",
            )],
        },
    ),
    resource_group_name="rg1",
    zones=["1"])

```

```yaml
resources:
  cluster:
    type: azure-native:hdinsight:Cluster
    properties:
      clusterName: cluster1
      properties:
        clusterDefinition:
          configurations:
            ambari-conf:
              database-name: '{ambari database name}'
              database-server: '{sql server name}.database.windows.net'
              database-user-name: '**********'
              database-user-password: '**********'
            gateway:
              restAuthCredential.isEnabled: true
              restAuthCredential.password: '**********'
              restAuthCredential.username: admin
            hive-env:
              hive_database: Existing MSSQL Server database with SQL authentication
              hive_database_name: '{hive metastore name}'
              hive_database_type: mssql
              hive_existing_mssql_server_database: '{hive metastore name}'
              hive_existing_mssql_server_host: '{sql server name}.database.windows.net'
              hive_hostname: '{sql server name}.database.windows.net'
            hive-site:
              javax.jdo.option.ConnectionDriverName: com.microsoft.sqlserver.jdbc.SQLServerDriver
              javax.jdo.option.ConnectionPassword: '**********!'
              javax.jdo.option.ConnectionURL: jdbc:sqlserver://{sql server name}.database.windows.net;database={hive metastore name};encrypt=true;trustServerCertificate=true;create=false;loginTimeout=300;sendStringParametersAsUnicode=true;prepareSQL=0
              javax.jdo.option.ConnectionUserName: '**********'
            oozie-env:
              oozie_database: Existing MSSQL Server database with SQL authentication
              oozie_database_name: '{oozie metastore name}'
              oozie_database_type: mssql
              oozie_existing_mssql_server_database: '{oozie metastore name}'
              oozie_existing_mssql_server_host: '{sql server name}.database.windows.net'
              oozie_hostname: '{sql server name}.database.windows.net'
            oozie-site:
              oozie.db.schema.name: oozie
              oozie.service.JPAService.jdbc.driver: com.microsoft.sqlserver.jdbc.SQLServerDriver
              oozie.service.JPAService.jdbc.password: '**********'
              oozie.service.JPAService.jdbc.url: jdbc:sqlserver://{sql server name}.database.windows.net;database={oozie metastore name};encrypt=true;trustServerCertificate=true;create=false;loginTimeout=300;sendStringParametersAsUnicode=true;prepareSQL=0
              oozie.service.JPAService.jdbc.username: '**********'
          kind: hadoop
        clusterVersion: '3.6'
        computeProfile:
          roles:
            - hardwareProfile:
                vmSize: standard_d3
              name: headnode
              osProfile:
                linuxOperatingSystemProfile:
                  password: '**********'
                  sshProfile:
                    publicKeys:
                      - certificateData: '**********'
                  username: sshuser
              targetInstanceCount: 2
              virtualNetworkProfile:
                id: /subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname
                subnet: /subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname/subnets/vnetsubnet
            - hardwareProfile:
                vmSize: standard_d3
              name: workernode
              osProfile:
                linuxOperatingSystemProfile:
                  password: '**********'
                  sshProfile:
                    publicKeys:
                      - certificateData: '**********'
                  username: sshuser
              targetInstanceCount: 2
              virtualNetworkProfile:
                id: /subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname
                subnet: /subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname/subnets/vnetsubnet
        osType: Linux
        storageProfile:
          storageaccounts:
            - container: containername
              isDefault: true
              key: storage account key
              name: mystorage
      resourceGroupName: rg1
      zones:
        - '1'

```

{{% /example %}}
{{% example %}}
### Create cluster with compute isolation properties
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var cluster = new AzureNative.HDInsight.Cluster("cluster", new()
    {
        ClusterName = "cluster1",
        Properties = new AzureNative.HDInsight.Inputs.ClusterCreatePropertiesArgs
        {
            ClusterDefinition = new AzureNative.HDInsight.Inputs.ClusterDefinitionArgs
            {
                Configurations = 
                {
                    { "gateway", 
                    {
                        { "restAuthCredential.isEnabled", true },
                        { "restAuthCredential.password", "**********" },
                        { "restAuthCredential.username", "admin" },
                    } },
                },
                Kind = "hadoop",
            },
            ClusterVersion = "3.6",
            ComputeIsolationProperties = new AzureNative.HDInsight.Inputs.ComputeIsolationPropertiesArgs
            {
                EnableComputeIsolation = true,
            },
            ComputeProfile = new AzureNative.HDInsight.Inputs.ComputeProfileArgs
            {
                Roles = new[]
                {
                    new AzureNative.HDInsight.Inputs.RoleArgs
                    {
                        HardwareProfile = new AzureNative.HDInsight.Inputs.HardwareProfileArgs
                        {
                            VmSize = "standard_d3",
                        },
                        Name = "headnode",
                        OsProfile = new AzureNative.HDInsight.Inputs.OsProfileArgs
                        {
                            LinuxOperatingSystemProfile = new AzureNative.HDInsight.Inputs.LinuxOperatingSystemProfileArgs
                            {
                                Password = "**********",
                                SshProfile = new AzureNative.HDInsight.Inputs.SshProfileArgs
                                {
                                    PublicKeys = new[]
                                    {
                                        new AzureNative.HDInsight.Inputs.SshPublicKeyArgs
                                        {
                                            CertificateData = "**********",
                                        },
                                    },
                                },
                                Username = "sshuser",
                            },
                        },
                        TargetInstanceCount = 2,
                    },
                    new AzureNative.HDInsight.Inputs.RoleArgs
                    {
                        HardwareProfile = new AzureNative.HDInsight.Inputs.HardwareProfileArgs
                        {
                            VmSize = "standard_d3",
                        },
                        Name = "workernode",
                        OsProfile = new AzureNative.HDInsight.Inputs.OsProfileArgs
                        {
                            LinuxOperatingSystemProfile = new AzureNative.HDInsight.Inputs.LinuxOperatingSystemProfileArgs
                            {
                                Password = "**********",
                                SshProfile = new AzureNative.HDInsight.Inputs.SshProfileArgs
                                {
                                    PublicKeys = new[]
                                    {
                                        new AzureNative.HDInsight.Inputs.SshPublicKeyArgs
                                        {
                                            CertificateData = "**********",
                                        },
                                    },
                                },
                                Username = "sshuser",
                            },
                        },
                        TargetInstanceCount = 2,
                    },
                },
            },
            OsType = "Linux",
            StorageProfile = new AzureNative.HDInsight.Inputs.StorageProfileArgs
            {
                Storageaccounts = new[]
                {
                    new AzureNative.HDInsight.Inputs.StorageAccountArgs
                    {
                        Container = "containername",
                        IsDefault = true,
                        Key = "storage account key",
                        Name = "mystorage",
                    },
                },
            },
        },
        ResourceGroupName = "rg1",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.hdinsight.Cluster;
import com.pulumi.azurenative.hdinsight.ClusterArgs;
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
        var cluster = new Cluster("cluster", ClusterArgs.builder()        
            .clusterName("cluster1")
            .properties(Map.ofEntries(
                Map.entry("clusterDefinition", Map.ofEntries(
                    Map.entry("configurations", Map.of("gateway", ClusterCreatePropertiesArgs.builder()
%!v(PANIC=Format method: interface conversion: model.Expression is *model.TemplateExpression, not *model.LiteralValueExpression))),
                        Map.entry("kind", "hadoop")
                    )),
                    Map.entry("clusterVersion", "3.6"),
                    Map.entry("computeIsolationProperties", Map.of("enableComputeIsolation", true)),
                    Map.entry("computeProfile", Map.of("roles",                     
                        Map.ofEntries(
                            Map.entry("hardwareProfile", Map.of("vmSize", "standard_d3")),
                            Map.entry("name", "headnode"),
                            Map.entry("osProfile", Map.of("linuxOperatingSystemProfile", Map.ofEntries(
                                Map.entry("password", "**********"),
                                Map.entry("sshProfile", Map.of("publicKeys", Map.of("certificateData", "**********"))),
                                Map.entry("username", "sshuser")
                            ))),
                            Map.entry("targetInstanceCount", 2)
                        ),
                        Map.ofEntries(
                            Map.entry("hardwareProfile", Map.of("vmSize", "standard_d3")),
                            Map.entry("name", "workernode"),
                            Map.entry("osProfile", Map.of("linuxOperatingSystemProfile", Map.ofEntries(
                                Map.entry("password", "**********"),
                                Map.entry("sshProfile", Map.of("publicKeys", Map.of("certificateData", "**********"))),
                                Map.entry("username", "sshuser")
                            ))),
                            Map.entry("targetInstanceCount", 2)
                        ))),
                    Map.entry("osType", "Linux"),
                    Map.entry("storageProfile", Map.of("storageaccounts", Map.ofEntries(
                        Map.entry("container", "containername"),
                        Map.entry("isDefault", true),
                        Map.entry("key", "storage account key"),
                        Map.entry("name", "mystorage")
                    )))
                ))
                .resourceGroupName("rg1")
                .build());

        }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const cluster = new azure_native.hdinsight.Cluster("cluster", {
    clusterName: "cluster1",
    properties: {
        clusterDefinition: {
            configurations: {
                gateway: {
                    "restAuthCredential.isEnabled": true,
                    "restAuthCredential.password": "**********",
                    "restAuthCredential.username": "admin",
                },
            },
            kind: "hadoop",
        },
        clusterVersion: "3.6",
        computeIsolationProperties: {
            enableComputeIsolation: true,
        },
        computeProfile: {
            roles: [
                {
                    hardwareProfile: {
                        vmSize: "standard_d3",
                    },
                    name: "headnode",
                    osProfile: {
                        linuxOperatingSystemProfile: {
                            password: "**********",
                            sshProfile: {
                                publicKeys: [{
                                    certificateData: "**********",
                                }],
                            },
                            username: "sshuser",
                        },
                    },
                    targetInstanceCount: 2,
                },
                {
                    hardwareProfile: {
                        vmSize: "standard_d3",
                    },
                    name: "workernode",
                    osProfile: {
                        linuxOperatingSystemProfile: {
                            password: "**********",
                            sshProfile: {
                                publicKeys: [{
                                    certificateData: "**********",
                                }],
                            },
                            username: "sshuser",
                        },
                    },
                    targetInstanceCount: 2,
                },
            ],
        },
        osType: "Linux",
        storageProfile: {
            storageaccounts: [{
                container: "containername",
                isDefault: true,
                key: "storage account key",
                name: "mystorage",
            }],
        },
    },
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

cluster = azure_native.hdinsight.Cluster("cluster",
    cluster_name="cluster1",
    properties=azure_native.hdinsight.ClusterGetPropertiesResponseArgs(
        cluster_definition=azure_native.hdinsight.ClusterDefinitionArgs(
            configurations={
                "gateway": {
                    "restAuthCredential.isEnabled": True,
                    "restAuthCredential.password": "**********",
                    "restAuthCredential.username": "admin",
                },
            },
            kind="hadoop",
        ),
        cluster_version="3.6",
        compute_isolation_properties=azure_native.hdinsight.ComputeIsolationPropertiesArgs(
            enable_compute_isolation=True,
        ),
        compute_profile={
            "roles": [
                {
                    "hardwareProfile": azure_native.hdinsight.HardwareProfileArgs(
                        vm_size="standard_d3",
                    ),
                    "name": "headnode",
                    "osProfile": {
                        "linuxOperatingSystemProfile": {
                            "password": "**********",
                            "sshProfile": {
                                "publicKeys": [azure_native.hdinsight.SshPublicKeyArgs(
                                    certificate_data="**********",
                                )],
                            },
                            "username": "sshuser",
                        },
                    },
                    "targetInstanceCount": 2,
                },
                {
                    "hardwareProfile": azure_native.hdinsight.HardwareProfileArgs(
                        vm_size="standard_d3",
                    ),
                    "name": "workernode",
                    "osProfile": {
                        "linuxOperatingSystemProfile": {
                            "password": "**********",
                            "sshProfile": {
                                "publicKeys": [azure_native.hdinsight.SshPublicKeyArgs(
                                    certificate_data="**********",
                                )],
                            },
                            "username": "sshuser",
                        },
                    },
                    "targetInstanceCount": 2,
                },
            ],
        },
        os_type="Linux",
        storage_profile={
            "storageaccounts": [azure_native.hdinsight.StorageAccountArgs(
                container="containername",
                is_default=True,
                key="storage account key",
                name="mystorage",
            )],
        },
    ),
    resource_group_name="rg1")

```

```yaml
resources:
  cluster:
    type: azure-native:hdinsight:Cluster
    properties:
      clusterName: cluster1
      properties:
        clusterDefinition:
          configurations:
            gateway:
              restAuthCredential.isEnabled: true
              restAuthCredential.password: '**********'
              restAuthCredential.username: admin
          kind: hadoop
        clusterVersion: '3.6'
        computeIsolationProperties:
          enableComputeIsolation: true
        computeProfile:
          roles:
            - hardwareProfile:
                vmSize: standard_d3
              name: headnode
              osProfile:
                linuxOperatingSystemProfile:
                  password: '**********'
                  sshProfile:
                    publicKeys:
                      - certificateData: '**********'
                  username: sshuser
              targetInstanceCount: 2
            - hardwareProfile:
                vmSize: standard_d3
              name: workernode
              osProfile:
                linuxOperatingSystemProfile:
                  password: '**********'
                  sshProfile:
                    publicKeys:
                      - certificateData: '**********'
                  username: sshuser
              targetInstanceCount: 2
        osType: Linux
        storageProfile:
          storageaccounts:
            - container: containername
              isDefault: true
              key: storage account key
              name: mystorage
      resourceGroupName: rg1

```

{{% /example %}}
{{% example %}}
### Create cluster with encryption at host
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var cluster = new AzureNative.HDInsight.Cluster("cluster", new()
    {
        ClusterName = "cluster1",
        Properties = new AzureNative.HDInsight.Inputs.ClusterCreatePropertiesArgs
        {
            ClusterDefinition = new AzureNative.HDInsight.Inputs.ClusterDefinitionArgs
            {
                Configurations = 
                {
                    { "gateway", 
                    {
                        { "restAuthCredential.isEnabled", true },
                        { "restAuthCredential.password", "**********" },
                        { "restAuthCredential.username", "admin" },
                    } },
                },
                Kind = "Hadoop",
            },
            ClusterVersion = "3.6",
            ComputeProfile = new AzureNative.HDInsight.Inputs.ComputeProfileArgs
            {
                Roles = new[]
                {
                    new AzureNative.HDInsight.Inputs.RoleArgs
                    {
                        HardwareProfile = new AzureNative.HDInsight.Inputs.HardwareProfileArgs
                        {
                            VmSize = "Standard_DS14_v2",
                        },
                        Name = "headnode",
                        OsProfile = new AzureNative.HDInsight.Inputs.OsProfileArgs
                        {
                            LinuxOperatingSystemProfile = new AzureNative.HDInsight.Inputs.LinuxOperatingSystemProfileArgs
                            {
                                Password = "**********",
                                Username = "sshuser",
                            },
                        },
                        TargetInstanceCount = 2,
                    },
                    new AzureNative.HDInsight.Inputs.RoleArgs
                    {
                        HardwareProfile = new AzureNative.HDInsight.Inputs.HardwareProfileArgs
                        {
                            VmSize = "Standard_DS14_v2",
                        },
                        Name = "workernode",
                        OsProfile = new AzureNative.HDInsight.Inputs.OsProfileArgs
                        {
                            LinuxOperatingSystemProfile = new AzureNative.HDInsight.Inputs.LinuxOperatingSystemProfileArgs
                            {
                                Password = "**********",
                                Username = "sshuser",
                            },
                        },
                        TargetInstanceCount = 3,
                    },
                    new AzureNative.HDInsight.Inputs.RoleArgs
                    {
                        HardwareProfile = new AzureNative.HDInsight.Inputs.HardwareProfileArgs
                        {
                            VmSize = "Standard_DS14_v2",
                        },
                        Name = "zookeepernode",
                        OsProfile = new AzureNative.HDInsight.Inputs.OsProfileArgs
                        {
                            LinuxOperatingSystemProfile = new AzureNative.HDInsight.Inputs.LinuxOperatingSystemProfileArgs
                            {
                                Password = "**********",
                                Username = "sshuser",
                            },
                        },
                        TargetInstanceCount = 3,
                    },
                },
            },
            DiskEncryptionProperties = new AzureNative.HDInsight.Inputs.DiskEncryptionPropertiesArgs
            {
                EncryptionAtHost = true,
            },
            OsType = "Linux",
            StorageProfile = new AzureNative.HDInsight.Inputs.StorageProfileArgs
            {
                Storageaccounts = new[]
                {
                    new AzureNative.HDInsight.Inputs.StorageAccountArgs
                    {
                        Container = "default8525",
                        IsDefault = true,
                        Key = "storagekey",
                        Name = "mystorage.blob.core.windows.net",
                    },
                },
            },
            Tier = "Standard",
        },
        ResourceGroupName = "rg1",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.hdinsight.Cluster;
import com.pulumi.azurenative.hdinsight.ClusterArgs;
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
        var cluster = new Cluster("cluster", ClusterArgs.builder()        
            .clusterName("cluster1")
            .properties(Map.ofEntries(
                Map.entry("clusterDefinition", Map.ofEntries(
                    Map.entry("configurations", Map.of("gateway", ClusterCreatePropertiesArgs.builder()
%!v(PANIC=Format method: interface conversion: model.Expression is *model.TemplateExpression, not *model.LiteralValueExpression))),
                        Map.entry("kind", "Hadoop")
                    )),
                    Map.entry("clusterVersion", "3.6"),
                    Map.entry("computeProfile", Map.of("roles",                     
                        Map.ofEntries(
                            Map.entry("hardwareProfile", Map.of("vmSize", "Standard_DS14_v2")),
                            Map.entry("name", "headnode"),
                            Map.entry("osProfile", Map.of("linuxOperatingSystemProfile", Map.ofEntries(
                                Map.entry("password", "**********"),
                                Map.entry("username", "sshuser")
                            ))),
                            Map.entry("targetInstanceCount", 2)
                        ),
                        Map.ofEntries(
                            Map.entry("hardwareProfile", Map.of("vmSize", "Standard_DS14_v2")),
                            Map.entry("name", "workernode"),
                            Map.entry("osProfile", Map.of("linuxOperatingSystemProfile", Map.ofEntries(
                                Map.entry("password", "**********"),
                                Map.entry("username", "sshuser")
                            ))),
                            Map.entry("targetInstanceCount", 3)
                        ),
                        Map.ofEntries(
                            Map.entry("hardwareProfile", Map.of("vmSize", "Standard_DS14_v2")),
                            Map.entry("name", "zookeepernode"),
                            Map.entry("osProfile", Map.of("linuxOperatingSystemProfile", Map.ofEntries(
                                Map.entry("password", "**********"),
                                Map.entry("username", "sshuser")
                            ))),
                            Map.entry("targetInstanceCount", 3)
                        ))),
                    Map.entry("diskEncryptionProperties", Map.of("encryptionAtHost", true)),
                    Map.entry("osType", "Linux"),
                    Map.entry("storageProfile", Map.of("storageaccounts", Map.ofEntries(
                        Map.entry("container", "default8525"),
                        Map.entry("isDefault", true),
                        Map.entry("key", "storagekey"),
                        Map.entry("name", "mystorage.blob.core.windows.net")
                    ))),
                    Map.entry("tier", "Standard")
                ))
                .resourceGroupName("rg1")
                .build());

        }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const cluster = new azure_native.hdinsight.Cluster("cluster", {
    clusterName: "cluster1",
    properties: {
        clusterDefinition: {
            configurations: {
                gateway: {
                    "restAuthCredential.isEnabled": true,
                    "restAuthCredential.password": "**********",
                    "restAuthCredential.username": "admin",
                },
            },
            kind: "Hadoop",
        },
        clusterVersion: "3.6",
        computeProfile: {
            roles: [
                {
                    hardwareProfile: {
                        vmSize: "Standard_DS14_v2",
                    },
                    name: "headnode",
                    osProfile: {
                        linuxOperatingSystemProfile: {
                            password: "**********",
                            username: "sshuser",
                        },
                    },
                    targetInstanceCount: 2,
                },
                {
                    hardwareProfile: {
                        vmSize: "Standard_DS14_v2",
                    },
                    name: "workernode",
                    osProfile: {
                        linuxOperatingSystemProfile: {
                            password: "**********",
                            username: "sshuser",
                        },
                    },
                    targetInstanceCount: 3,
                },
                {
                    hardwareProfile: {
                        vmSize: "Standard_DS14_v2",
                    },
                    name: "zookeepernode",
                    osProfile: {
                        linuxOperatingSystemProfile: {
                            password: "**********",
                            username: "sshuser",
                        },
                    },
                    targetInstanceCount: 3,
                },
            ],
        },
        diskEncryptionProperties: {
            encryptionAtHost: true,
        },
        osType: "Linux",
        storageProfile: {
            storageaccounts: [{
                container: "default8525",
                isDefault: true,
                key: "storagekey",
                name: "mystorage.blob.core.windows.net",
            }],
        },
        tier: "Standard",
    },
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

cluster = azure_native.hdinsight.Cluster("cluster",
    cluster_name="cluster1",
    properties=azure_native.hdinsight.ClusterGetPropertiesResponseArgs(
        cluster_definition=azure_native.hdinsight.ClusterDefinitionArgs(
            configurations={
                "gateway": {
                    "restAuthCredential.isEnabled": True,
                    "restAuthCredential.password": "**********",
                    "restAuthCredential.username": "admin",
                },
            },
            kind="Hadoop",
        ),
        cluster_version="3.6",
        compute_profile={
            "roles": [
                {
                    "hardwareProfile": azure_native.hdinsight.HardwareProfileArgs(
                        vm_size="Standard_DS14_v2",
                    ),
                    "name": "headnode",
                    "osProfile": {
                        "linuxOperatingSystemProfile": azure_native.hdinsight.LinuxOperatingSystemProfileArgs(
                            password="**********",
                            username="sshuser",
                        ),
                    },
                    "targetInstanceCount": 2,
                },
                {
                    "hardwareProfile": azure_native.hdinsight.HardwareProfileArgs(
                        vm_size="Standard_DS14_v2",
                    ),
                    "name": "workernode",
                    "osProfile": {
                        "linuxOperatingSystemProfile": azure_native.hdinsight.LinuxOperatingSystemProfileArgs(
                            password="**********",
                            username="sshuser",
                        ),
                    },
                    "targetInstanceCount": 3,
                },
                {
                    "hardwareProfile": azure_native.hdinsight.HardwareProfileArgs(
                        vm_size="Standard_DS14_v2",
                    ),
                    "name": "zookeepernode",
                    "osProfile": {
                        "linuxOperatingSystemProfile": azure_native.hdinsight.LinuxOperatingSystemProfileArgs(
                            password="**********",
                            username="sshuser",
                        ),
                    },
                    "targetInstanceCount": 3,
                },
            ],
        },
        disk_encryption_properties=azure_native.hdinsight.DiskEncryptionPropertiesArgs(
            encryption_at_host=True,
        ),
        os_type="Linux",
        storage_profile={
            "storageaccounts": [azure_native.hdinsight.StorageAccountArgs(
                container="default8525",
                is_default=True,
                key="storagekey",
                name="mystorage.blob.core.windows.net",
            )],
        },
        tier="Standard",
    ),
    resource_group_name="rg1")

```

```yaml
resources:
  cluster:
    type: azure-native:hdinsight:Cluster
    properties:
      clusterName: cluster1
      properties:
        clusterDefinition:
          configurations:
            gateway:
              restAuthCredential.isEnabled: true
              restAuthCredential.password: '**********'
              restAuthCredential.username: admin
          kind: Hadoop
        clusterVersion: '3.6'
        computeProfile:
          roles:
            - hardwareProfile:
                vmSize: Standard_DS14_v2
              name: headnode
              osProfile:
                linuxOperatingSystemProfile:
                  password: '**********'
                  username: sshuser
              targetInstanceCount: 2
            - hardwareProfile:
                vmSize: Standard_DS14_v2
              name: workernode
              osProfile:
                linuxOperatingSystemProfile:
                  password: '**********'
                  username: sshuser
              targetInstanceCount: 3
            - hardwareProfile:
                vmSize: Standard_DS14_v2
              name: zookeepernode
              osProfile:
                linuxOperatingSystemProfile:
                  password: '**********'
                  username: sshuser
              targetInstanceCount: 3
        diskEncryptionProperties:
          encryptionAtHost: true
        osType: Linux
        storageProfile:
          storageaccounts:
            - container: default8525
              isDefault: true
              key: storagekey
              name: mystorage.blob.core.windows.net
        tier: Standard
      resourceGroupName: rg1

```

{{% /example %}}
{{% example %}}
### Create cluster with encryption in transit
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var cluster = new AzureNative.HDInsight.Cluster("cluster", new()
    {
        ClusterName = "cluster1",
        Properties = new AzureNative.HDInsight.Inputs.ClusterCreatePropertiesArgs
        {
            ClusterDefinition = new AzureNative.HDInsight.Inputs.ClusterDefinitionArgs
            {
                Configurations = 
                {
                    { "gateway", 
                    {
                        { "restAuthCredential.isEnabled", true },
                        { "restAuthCredential.password", "**********" },
                        { "restAuthCredential.username", "admin" },
                    } },
                },
                Kind = "Hadoop",
            },
            ClusterVersion = "3.6",
            ComputeProfile = new AzureNative.HDInsight.Inputs.ComputeProfileArgs
            {
                Roles = new[]
                {
                    new AzureNative.HDInsight.Inputs.RoleArgs
                    {
                        HardwareProfile = new AzureNative.HDInsight.Inputs.HardwareProfileArgs
                        {
                            VmSize = "Large",
                        },
                        Name = "headnode",
                        OsProfile = new AzureNative.HDInsight.Inputs.OsProfileArgs
                        {
                            LinuxOperatingSystemProfile = new AzureNative.HDInsight.Inputs.LinuxOperatingSystemProfileArgs
                            {
                                Password = "**********",
                                Username = "sshuser",
                            },
                        },
                        TargetInstanceCount = 2,
                    },
                    new AzureNative.HDInsight.Inputs.RoleArgs
                    {
                        HardwareProfile = new AzureNative.HDInsight.Inputs.HardwareProfileArgs
                        {
                            VmSize = "Large",
                        },
                        Name = "workernode",
                        OsProfile = new AzureNative.HDInsight.Inputs.OsProfileArgs
                        {
                            LinuxOperatingSystemProfile = new AzureNative.HDInsight.Inputs.LinuxOperatingSystemProfileArgs
                            {
                                Password = "**********",
                                Username = "sshuser",
                            },
                        },
                        TargetInstanceCount = 3,
                    },
                    new AzureNative.HDInsight.Inputs.RoleArgs
                    {
                        HardwareProfile = new AzureNative.HDInsight.Inputs.HardwareProfileArgs
                        {
                            VmSize = "Small",
                        },
                        Name = "zookeepernode",
                        OsProfile = new AzureNative.HDInsight.Inputs.OsProfileArgs
                        {
                            LinuxOperatingSystemProfile = new AzureNative.HDInsight.Inputs.LinuxOperatingSystemProfileArgs
                            {
                                Password = "**********",
                                Username = "sshuser",
                            },
                        },
                        TargetInstanceCount = 3,
                    },
                },
            },
            EncryptionInTransitProperties = new AzureNative.HDInsight.Inputs.EncryptionInTransitPropertiesArgs
            {
                IsEncryptionInTransitEnabled = true,
            },
            OsType = "Linux",
            StorageProfile = new AzureNative.HDInsight.Inputs.StorageProfileArgs
            {
                Storageaccounts = new[]
                {
                    new AzureNative.HDInsight.Inputs.StorageAccountArgs
                    {
                        Container = "default8525",
                        IsDefault = true,
                        Key = "storagekey",
                        Name = "mystorage.blob.core.windows.net",
                    },
                },
            },
            Tier = "Standard",
        },
        ResourceGroupName = "rg1",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.hdinsight.Cluster;
import com.pulumi.azurenative.hdinsight.ClusterArgs;
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
        var cluster = new Cluster("cluster", ClusterArgs.builder()        
            .clusterName("cluster1")
            .properties(Map.ofEntries(
                Map.entry("clusterDefinition", Map.ofEntries(
                    Map.entry("configurations", Map.of("gateway", ClusterCreatePropertiesArgs.builder()
%!v(PANIC=Format method: interface conversion: model.Expression is *model.TemplateExpression, not *model.LiteralValueExpression))),
                        Map.entry("kind", "Hadoop")
                    )),
                    Map.entry("clusterVersion", "3.6"),
                    Map.entry("computeProfile", Map.of("roles",                     
                        Map.ofEntries(
                            Map.entry("hardwareProfile", Map.of("vmSize", "Large")),
                            Map.entry("name", "headnode"),
                            Map.entry("osProfile", Map.of("linuxOperatingSystemProfile", Map.ofEntries(
                                Map.entry("password", "**********"),
                                Map.entry("username", "sshuser")
                            ))),
                            Map.entry("targetInstanceCount", 2)
                        ),
                        Map.ofEntries(
                            Map.entry("hardwareProfile", Map.of("vmSize", "Large")),
                            Map.entry("name", "workernode"),
                            Map.entry("osProfile", Map.of("linuxOperatingSystemProfile", Map.ofEntries(
                                Map.entry("password", "**********"),
                                Map.entry("username", "sshuser")
                            ))),
                            Map.entry("targetInstanceCount", 3)
                        ),
                        Map.ofEntries(
                            Map.entry("hardwareProfile", Map.of("vmSize", "Small")),
                            Map.entry("name", "zookeepernode"),
                            Map.entry("osProfile", Map.of("linuxOperatingSystemProfile", Map.ofEntries(
                                Map.entry("password", "**********"),
                                Map.entry("username", "sshuser")
                            ))),
                            Map.entry("targetInstanceCount", 3)
                        ))),
                    Map.entry("encryptionInTransitProperties", Map.of("isEncryptionInTransitEnabled", true)),
                    Map.entry("osType", "Linux"),
                    Map.entry("storageProfile", Map.of("storageaccounts", Map.ofEntries(
                        Map.entry("container", "default8525"),
                        Map.entry("isDefault", true),
                        Map.entry("key", "storagekey"),
                        Map.entry("name", "mystorage.blob.core.windows.net")
                    ))),
                    Map.entry("tier", "Standard")
                ))
                .resourceGroupName("rg1")
                .build());

        }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const cluster = new azure_native.hdinsight.Cluster("cluster", {
    clusterName: "cluster1",
    properties: {
        clusterDefinition: {
            configurations: {
                gateway: {
                    "restAuthCredential.isEnabled": true,
                    "restAuthCredential.password": "**********",
                    "restAuthCredential.username": "admin",
                },
            },
            kind: "Hadoop",
        },
        clusterVersion: "3.6",
        computeProfile: {
            roles: [
                {
                    hardwareProfile: {
                        vmSize: "Large",
                    },
                    name: "headnode",
                    osProfile: {
                        linuxOperatingSystemProfile: {
                            password: "**********",
                            username: "sshuser",
                        },
                    },
                    targetInstanceCount: 2,
                },
                {
                    hardwareProfile: {
                        vmSize: "Large",
                    },
                    name: "workernode",
                    osProfile: {
                        linuxOperatingSystemProfile: {
                            password: "**********",
                            username: "sshuser",
                        },
                    },
                    targetInstanceCount: 3,
                },
                {
                    hardwareProfile: {
                        vmSize: "Small",
                    },
                    name: "zookeepernode",
                    osProfile: {
                        linuxOperatingSystemProfile: {
                            password: "**********",
                            username: "sshuser",
                        },
                    },
                    targetInstanceCount: 3,
                },
            ],
        },
        encryptionInTransitProperties: {
            isEncryptionInTransitEnabled: true,
        },
        osType: "Linux",
        storageProfile: {
            storageaccounts: [{
                container: "default8525",
                isDefault: true,
                key: "storagekey",
                name: "mystorage.blob.core.windows.net",
            }],
        },
        tier: "Standard",
    },
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

cluster = azure_native.hdinsight.Cluster("cluster",
    cluster_name="cluster1",
    properties=azure_native.hdinsight.ClusterGetPropertiesResponseArgs(
        cluster_definition=azure_native.hdinsight.ClusterDefinitionArgs(
            configurations={
                "gateway": {
                    "restAuthCredential.isEnabled": True,
                    "restAuthCredential.password": "**********",
                    "restAuthCredential.username": "admin",
                },
            },
            kind="Hadoop",
        ),
        cluster_version="3.6",
        compute_profile={
            "roles": [
                {
                    "hardwareProfile": azure_native.hdinsight.HardwareProfileArgs(
                        vm_size="Large",
                    ),
                    "name": "headnode",
                    "osProfile": {
                        "linuxOperatingSystemProfile": azure_native.hdinsight.LinuxOperatingSystemProfileArgs(
                            password="**********",
                            username="sshuser",
                        ),
                    },
                    "targetInstanceCount": 2,
                },
                {
                    "hardwareProfile": azure_native.hdinsight.HardwareProfileArgs(
                        vm_size="Large",
                    ),
                    "name": "workernode",
                    "osProfile": {
                        "linuxOperatingSystemProfile": azure_native.hdinsight.LinuxOperatingSystemProfileArgs(
                            password="**********",
                            username="sshuser",
                        ),
                    },
                    "targetInstanceCount": 3,
                },
                {
                    "hardwareProfile": azure_native.hdinsight.HardwareProfileArgs(
                        vm_size="Small",
                    ),
                    "name": "zookeepernode",
                    "osProfile": {
                        "linuxOperatingSystemProfile": azure_native.hdinsight.LinuxOperatingSystemProfileArgs(
                            password="**********",
                            username="sshuser",
                        ),
                    },
                    "targetInstanceCount": 3,
                },
            ],
        },
        encryption_in_transit_properties=azure_native.hdinsight.EncryptionInTransitPropertiesArgs(
            is_encryption_in_transit_enabled=True,
        ),
        os_type="Linux",
        storage_profile={
            "storageaccounts": [azure_native.hdinsight.StorageAccountArgs(
                container="default8525",
                is_default=True,
                key="storagekey",
                name="mystorage.blob.core.windows.net",
            )],
        },
        tier="Standard",
    ),
    resource_group_name="rg1")

```

```yaml
resources:
  cluster:
    type: azure-native:hdinsight:Cluster
    properties:
      clusterName: cluster1
      properties:
        clusterDefinition:
          configurations:
            gateway:
              restAuthCredential.isEnabled: true
              restAuthCredential.password: '**********'
              restAuthCredential.username: admin
          kind: Hadoop
        clusterVersion: '3.6'
        computeProfile:
          roles:
            - hardwareProfile:
                vmSize: Large
              name: headnode
              osProfile:
                linuxOperatingSystemProfile:
                  password: '**********'
                  username: sshuser
              targetInstanceCount: 2
            - hardwareProfile:
                vmSize: Large
              name: workernode
              osProfile:
                linuxOperatingSystemProfile:
                  password: '**********'
                  username: sshuser
              targetInstanceCount: 3
            - hardwareProfile:
                vmSize: Small
              name: zookeepernode
              osProfile:
                linuxOperatingSystemProfile:
                  password: '**********'
                  username: sshuser
              targetInstanceCount: 3
        encryptionInTransitProperties:
          isEncryptionInTransitEnabled: true
        osType: Linux
        storageProfile:
          storageaccounts:
            - container: default8525
              isDefault: true
              key: storagekey
              name: mystorage.blob.core.windows.net
        tier: Standard
      resourceGroupName: rg1

```

{{% /example %}}
{{% example %}}
### Create cluster with network properties
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var cluster = new AzureNative.HDInsight.Cluster("cluster", new()
    {
        ClusterName = "cluster1",
        Properties = new AzureNative.HDInsight.Inputs.ClusterCreatePropertiesArgs
        {
            ClusterDefinition = new AzureNative.HDInsight.Inputs.ClusterDefinitionArgs
            {
                Configurations = 
                {
                    { "gateway", 
                    {
                        { "restAuthCredential.isEnabled", true },
                        { "restAuthCredential.password", "**********" },
                        { "restAuthCredential.username", "admin" },
                    } },
                },
                Kind = "hadoop",
            },
            ClusterVersion = "3.6",
            ComputeProfile = new AzureNative.HDInsight.Inputs.ComputeProfileArgs
            {
                Roles = new[]
                {
                    new AzureNative.HDInsight.Inputs.RoleArgs
                    {
                        HardwareProfile = new AzureNative.HDInsight.Inputs.HardwareProfileArgs
                        {
                            VmSize = "standard_d3",
                        },
                        Name = "headnode",
                        OsProfile = new AzureNative.HDInsight.Inputs.OsProfileArgs
                        {
                            LinuxOperatingSystemProfile = new AzureNative.HDInsight.Inputs.LinuxOperatingSystemProfileArgs
                            {
                                Password = "**********",
                                SshProfile = new AzureNative.HDInsight.Inputs.SshProfileArgs
                                {
                                    PublicKeys = new[]
                                    {
                                        new AzureNative.HDInsight.Inputs.SshPublicKeyArgs
                                        {
                                            CertificateData = "**********",
                                        },
                                    },
                                },
                                Username = "sshuser",
                            },
                        },
                        TargetInstanceCount = 2,
                        VirtualNetworkProfile = new AzureNative.HDInsight.Inputs.VirtualNetworkProfileArgs
                        {
                            Id = "/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname",
                            Subnet = "/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname/subnets/vnetsubnet",
                        },
                    },
                    new AzureNative.HDInsight.Inputs.RoleArgs
                    {
                        HardwareProfile = new AzureNative.HDInsight.Inputs.HardwareProfileArgs
                        {
                            VmSize = "standard_d3",
                        },
                        Name = "workernode",
                        OsProfile = new AzureNative.HDInsight.Inputs.OsProfileArgs
                        {
                            LinuxOperatingSystemProfile = new AzureNative.HDInsight.Inputs.LinuxOperatingSystemProfileArgs
                            {
                                Password = "**********",
                                SshProfile = new AzureNative.HDInsight.Inputs.SshProfileArgs
                                {
                                    PublicKeys = new[]
                                    {
                                        new AzureNative.HDInsight.Inputs.SshPublicKeyArgs
                                        {
                                            CertificateData = "**********",
                                        },
                                    },
                                },
                                Username = "sshuser",
                            },
                        },
                        TargetInstanceCount = 2,
                        VirtualNetworkProfile = new AzureNative.HDInsight.Inputs.VirtualNetworkProfileArgs
                        {
                            Id = "/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname",
                            Subnet = "/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname/subnets/vnetsubnet",
                        },
                    },
                },
            },
            NetworkProperties = new AzureNative.HDInsight.Inputs.NetworkPropertiesArgs
            {
                PrivateLink = "Enabled",
                ResourceProviderConnection = "Outbound",
            },
            OsType = "Linux",
            StorageProfile = new AzureNative.HDInsight.Inputs.StorageProfileArgs
            {
                Storageaccounts = new[]
                {
                    new AzureNative.HDInsight.Inputs.StorageAccountArgs
                    {
                        Container = "containername",
                        IsDefault = true,
                        Key = "storage account key",
                        Name = "mystorage",
                    },
                },
            },
        },
        ResourceGroupName = "rg1",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.hdinsight.Cluster;
import com.pulumi.azurenative.hdinsight.ClusterArgs;
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
        var cluster = new Cluster("cluster", ClusterArgs.builder()        
            .clusterName("cluster1")
            .properties(Map.ofEntries(
                Map.entry("clusterDefinition", Map.ofEntries(
                    Map.entry("configurations", Map.of("gateway", ClusterCreatePropertiesArgs.builder()
%!v(PANIC=Format method: interface conversion: model.Expression is *model.TemplateExpression, not *model.LiteralValueExpression))),
                        Map.entry("kind", "hadoop")
                    )),
                    Map.entry("clusterVersion", "3.6"),
                    Map.entry("computeProfile", Map.of("roles",                     
                        Map.ofEntries(
                            Map.entry("hardwareProfile", Map.of("vmSize", "standard_d3")),
                            Map.entry("name", "headnode"),
                            Map.entry("osProfile", Map.of("linuxOperatingSystemProfile", Map.ofEntries(
                                Map.entry("password", "**********"),
                                Map.entry("sshProfile", Map.of("publicKeys", Map.of("certificateData", "**********"))),
                                Map.entry("username", "sshuser")
                            ))),
                            Map.entry("targetInstanceCount", 2),
                            Map.entry("virtualNetworkProfile", Map.ofEntries(
                                Map.entry("id", "/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname"),
                                Map.entry("subnet", "/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname/subnets/vnetsubnet")
                            ))
                        ),
                        Map.ofEntries(
                            Map.entry("hardwareProfile", Map.of("vmSize", "standard_d3")),
                            Map.entry("name", "workernode"),
                            Map.entry("osProfile", Map.of("linuxOperatingSystemProfile", Map.ofEntries(
                                Map.entry("password", "**********"),
                                Map.entry("sshProfile", Map.of("publicKeys", Map.of("certificateData", "**********"))),
                                Map.entry("username", "sshuser")
                            ))),
                            Map.entry("targetInstanceCount", 2),
                            Map.entry("virtualNetworkProfile", Map.ofEntries(
                                Map.entry("id", "/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname"),
                                Map.entry("subnet", "/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname/subnets/vnetsubnet")
                            ))
                        ))),
                    Map.entry("networkProperties", Map.ofEntries(
                        Map.entry("privateLink", "Enabled"),
                        Map.entry("resourceProviderConnection", "Outbound")
                    )),
                    Map.entry("osType", "Linux"),
                    Map.entry("storageProfile", Map.of("storageaccounts", Map.ofEntries(
                        Map.entry("container", "containername"),
                        Map.entry("isDefault", true),
                        Map.entry("key", "storage account key"),
                        Map.entry("name", "mystorage")
                    )))
                ))
                .resourceGroupName("rg1")
                .build());

        }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const cluster = new azure_native.hdinsight.Cluster("cluster", {
    clusterName: "cluster1",
    properties: {
        clusterDefinition: {
            configurations: {
                gateway: {
                    "restAuthCredential.isEnabled": true,
                    "restAuthCredential.password": "**********",
                    "restAuthCredential.username": "admin",
                },
            },
            kind: "hadoop",
        },
        clusterVersion: "3.6",
        computeProfile: {
            roles: [
                {
                    hardwareProfile: {
                        vmSize: "standard_d3",
                    },
                    name: "headnode",
                    osProfile: {
                        linuxOperatingSystemProfile: {
                            password: "**********",
                            sshProfile: {
                                publicKeys: [{
                                    certificateData: "**********",
                                }],
                            },
                            username: "sshuser",
                        },
                    },
                    targetInstanceCount: 2,
                    virtualNetworkProfile: {
                        id: "/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname",
                        subnet: "/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname/subnets/vnetsubnet",
                    },
                },
                {
                    hardwareProfile: {
                        vmSize: "standard_d3",
                    },
                    name: "workernode",
                    osProfile: {
                        linuxOperatingSystemProfile: {
                            password: "**********",
                            sshProfile: {
                                publicKeys: [{
                                    certificateData: "**********",
                                }],
                            },
                            username: "sshuser",
                        },
                    },
                    targetInstanceCount: 2,
                    virtualNetworkProfile: {
                        id: "/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname",
                        subnet: "/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname/subnets/vnetsubnet",
                    },
                },
            ],
        },
        networkProperties: {
            privateLink: "Enabled",
            resourceProviderConnection: "Outbound",
        },
        osType: "Linux",
        storageProfile: {
            storageaccounts: [{
                container: "containername",
                isDefault: true,
                key: "storage account key",
                name: "mystorage",
            }],
        },
    },
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

cluster = azure_native.hdinsight.Cluster("cluster",
    cluster_name="cluster1",
    properties=azure_native.hdinsight.ClusterGetPropertiesResponseArgs(
        cluster_definition=azure_native.hdinsight.ClusterDefinitionArgs(
            configurations={
                "gateway": {
                    "restAuthCredential.isEnabled": True,
                    "restAuthCredential.password": "**********",
                    "restAuthCredential.username": "admin",
                },
            },
            kind="hadoop",
        ),
        cluster_version="3.6",
        compute_profile={
            "roles": [
                {
                    "hardwareProfile": azure_native.hdinsight.HardwareProfileArgs(
                        vm_size="standard_d3",
                    ),
                    "name": "headnode",
                    "osProfile": {
                        "linuxOperatingSystemProfile": {
                            "password": "**********",
                            "sshProfile": {
                                "publicKeys": [azure_native.hdinsight.SshPublicKeyArgs(
                                    certificate_data="**********",
                                )],
                            },
                            "username": "sshuser",
                        },
                    },
                    "targetInstanceCount": 2,
                    "virtualNetworkProfile": azure_native.hdinsight.VirtualNetworkProfileArgs(
                        id="/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname",
                        subnet="/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname/subnets/vnetsubnet",
                    ),
                },
                {
                    "hardwareProfile": azure_native.hdinsight.HardwareProfileArgs(
                        vm_size="standard_d3",
                    ),
                    "name": "workernode",
                    "osProfile": {
                        "linuxOperatingSystemProfile": {
                            "password": "**********",
                            "sshProfile": {
                                "publicKeys": [azure_native.hdinsight.SshPublicKeyArgs(
                                    certificate_data="**********",
                                )],
                            },
                            "username": "sshuser",
                        },
                    },
                    "targetInstanceCount": 2,
                    "virtualNetworkProfile": azure_native.hdinsight.VirtualNetworkProfileArgs(
                        id="/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname",
                        subnet="/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname/subnets/vnetsubnet",
                    ),
                },
            ],
        },
        network_properties=azure_native.hdinsight.NetworkPropertiesArgs(
            private_link="Enabled",
            resource_provider_connection="Outbound",
        ),
        os_type="Linux",
        storage_profile={
            "storageaccounts": [azure_native.hdinsight.StorageAccountArgs(
                container="containername",
                is_default=True,
                key="storage account key",
                name="mystorage",
            )],
        },
    ),
    resource_group_name="rg1")

```

```yaml
resources:
  cluster:
    type: azure-native:hdinsight:Cluster
    properties:
      clusterName: cluster1
      properties:
        clusterDefinition:
          configurations:
            gateway:
              restAuthCredential.isEnabled: true
              restAuthCredential.password: '**********'
              restAuthCredential.username: admin
          kind: hadoop
        clusterVersion: '3.6'
        computeProfile:
          roles:
            - hardwareProfile:
                vmSize: standard_d3
              name: headnode
              osProfile:
                linuxOperatingSystemProfile:
                  password: '**********'
                  sshProfile:
                    publicKeys:
                      - certificateData: '**********'
                  username: sshuser
              targetInstanceCount: 2
              virtualNetworkProfile:
                id: /subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname
                subnet: /subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname/subnets/vnetsubnet
            - hardwareProfile:
                vmSize: standard_d3
              name: workernode
              osProfile:
                linuxOperatingSystemProfile:
                  password: '**********'
                  sshProfile:
                    publicKeys:
                      - certificateData: '**********'
                  username: sshuser
              targetInstanceCount: 2
              virtualNetworkProfile:
                id: /subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname
                subnet: /subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/vnetname/subnets/vnetsubnet
        networkProperties:
          privateLink: Enabled
          resourceProviderConnection: Outbound
        osType: Linux
        storageProfile:
          storageaccounts:
            - container: containername
              isDefault: true
              key: storage account key
              name: mystorage
      resourceGroupName: rg1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:hdinsight:Cluster cluster1 /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/rg1/providers/Microsoft.HDInsight/clusters/cluster1 
```
