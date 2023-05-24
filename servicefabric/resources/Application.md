The application resource.
API Version: 2023-02-01-preview.
Previous API Version: 2020-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Put an application with maximum parameters
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var application = new AzureNative.ServiceFabric.Application("application", new()
    {
        ApplicationName = "myApp",
        ClusterName = "myCluster",
        Location = "eastus",
        Parameters = 
        {
            { "param1", "value1" },
        },
        ResourceGroupName = "resRg",
        Tags = 
        {
            { "a", "b" },
        },
        UpgradePolicy = new AzureNative.ServiceFabric.Inputs.ApplicationUpgradePolicyArgs
        {
            ApplicationHealthPolicy = new AzureNative.ServiceFabric.Inputs.ApplicationHealthPolicyArgs
            {
                ConsiderWarningAsError = true,
                DefaultServiceTypeHealthPolicy = new AzureNative.ServiceFabric.Inputs.ServiceTypeHealthPolicyArgs
                {
                    MaxPercentUnhealthyPartitionsPerService = 0,
                    MaxPercentUnhealthyReplicasPerPartition = 0,
                    MaxPercentUnhealthyServices = 0,
                },
                MaxPercentUnhealthyDeployedApplications = 0,
                ServiceTypeHealthPolicyMap = 
                {
                    { "myService", new AzureNative.ServiceFabric.Inputs.ServiceTypeHealthPolicyArgs
                    {
                        MaxPercentUnhealthyPartitionsPerService = 30,
                        MaxPercentUnhealthyReplicasPerPartition = 30,
                        MaxPercentUnhealthyServices = 30,
                    } },
                },
            },
            ForceRestart = false,
            InstanceCloseDelayDuration = 600,
            RecreateApplication = false,
            RollingUpgradeMonitoringPolicy = new AzureNative.ServiceFabric.Inputs.RollingUpgradeMonitoringPolicyArgs
            {
                FailureAction = "Rollback",
                HealthCheckRetryTimeout = "00:10:00",
                HealthCheckStableDuration = "00:05:00",
                HealthCheckWaitDuration = "00:02:00",
                UpgradeDomainTimeout = "00:15:00",
                UpgradeTimeout = "01:00:00",
            },
            UpgradeMode = "UnmonitoredAuto",
            UpgradeReplicaSetCheckTimeout = 3600,
        },
        Version = "/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/resRg/providers/Microsoft.ServiceFabric/managedclusters/myCluster/applicationTypes/myAppType/versions/1.0",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.servicefabric.Application;
import com.pulumi.azurenative.servicefabric.ApplicationArgs;
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
        var application = new Application("application", ApplicationArgs.builder()        
            .applicationName("myApp")
            .clusterName("myCluster")
            .location("eastus")
            .parameters(Map.of("param1", "value1"))
            .resourceGroupName("resRg")
            .tags(Map.of("a", "b"))
            .upgradePolicy(Map.ofEntries(
                Map.entry("applicationHealthPolicy", Map.ofEntries(
                    Map.entry("considerWarningAsError", true),
                    Map.entry("defaultServiceTypeHealthPolicy", Map.ofEntries(
                        Map.entry("maxPercentUnhealthyPartitionsPerService", 0),
                        Map.entry("maxPercentUnhealthyReplicasPerPartition", 0),
                        Map.entry("maxPercentUnhealthyServices", 0)
                    )),
                    Map.entry("maxPercentUnhealthyDeployedApplications", 0),
                    Map.entry("serviceTypeHealthPolicyMap", Map.of("myService", Map.ofEntries(
                        Map.entry("maxPercentUnhealthyPartitionsPerService", 30),
                        Map.entry("maxPercentUnhealthyReplicasPerPartition", 30),
                        Map.entry("maxPercentUnhealthyServices", 30)
                    )))
                )),
                Map.entry("forceRestart", false),
                Map.entry("instanceCloseDelayDuration", 600),
                Map.entry("recreateApplication", false),
                Map.entry("rollingUpgradeMonitoringPolicy", Map.ofEntries(
                    Map.entry("failureAction", "Rollback"),
                    Map.entry("healthCheckRetryTimeout", "00:10:00"),
                    Map.entry("healthCheckStableDuration", "00:05:00"),
                    Map.entry("healthCheckWaitDuration", "00:02:00"),
                    Map.entry("upgradeDomainTimeout", "00:15:00"),
                    Map.entry("upgradeTimeout", "01:00:00")
                )),
                Map.entry("upgradeMode", "UnmonitoredAuto"),
                Map.entry("upgradeReplicaSetCheckTimeout", 3600)
            ))
            .version("/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/resRg/providers/Microsoft.ServiceFabric/managedclusters/myCluster/applicationTypes/myAppType/versions/1.0")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const application = new azure_native.servicefabric.Application("application", {
    applicationName: "myApp",
    clusterName: "myCluster",
    location: "eastus",
    parameters: {
        param1: "value1",
    },
    resourceGroupName: "resRg",
    tags: {
        a: "b",
    },
    upgradePolicy: {
        applicationHealthPolicy: {
            considerWarningAsError: true,
            defaultServiceTypeHealthPolicy: {
                maxPercentUnhealthyPartitionsPerService: 0,
                maxPercentUnhealthyReplicasPerPartition: 0,
                maxPercentUnhealthyServices: 0,
            },
            maxPercentUnhealthyDeployedApplications: 0,
            serviceTypeHealthPolicyMap: {
                myService: {
                    maxPercentUnhealthyPartitionsPerService: 30,
                    maxPercentUnhealthyReplicasPerPartition: 30,
                    maxPercentUnhealthyServices: 30,
                },
            },
        },
        forceRestart: false,
        instanceCloseDelayDuration: 600,
        recreateApplication: false,
        rollingUpgradeMonitoringPolicy: {
            failureAction: "Rollback",
            healthCheckRetryTimeout: "00:10:00",
            healthCheckStableDuration: "00:05:00",
            healthCheckWaitDuration: "00:02:00",
            upgradeDomainTimeout: "00:15:00",
            upgradeTimeout: "01:00:00",
        },
        upgradeMode: "UnmonitoredAuto",
        upgradeReplicaSetCheckTimeout: 3600,
    },
    version: "/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/resRg/providers/Microsoft.ServiceFabric/managedclusters/myCluster/applicationTypes/myAppType/versions/1.0",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

application = azure_native.servicefabric.Application("application",
    application_name="myApp",
    cluster_name="myCluster",
    location="eastus",
    parameters={
        "param1": "value1",
    },
    resource_group_name="resRg",
    tags={
        "a": "b",
    },
    upgrade_policy=azure_native.servicefabric.ApplicationUpgradePolicyResponseArgs(
        application_health_policy={
            "considerWarningAsError": True,
            "defaultServiceTypeHealthPolicy": azure_native.servicefabric.ServiceTypeHealthPolicyArgs(
                max_percent_unhealthy_partitions_per_service=0,
                max_percent_unhealthy_replicas_per_partition=0,
                max_percent_unhealthy_services=0,
            ),
            "maxPercentUnhealthyDeployedApplications": 0,
            "serviceTypeHealthPolicyMap": {
                "myService": azure_native.servicefabric.ServiceTypeHealthPolicyArgs(
                    max_percent_unhealthy_partitions_per_service=30,
                    max_percent_unhealthy_replicas_per_partition=30,
                    max_percent_unhealthy_services=30,
                ),
            },
        },
        force_restart=False,
        instance_close_delay_duration=600,
        recreate_application=False,
        rolling_upgrade_monitoring_policy=azure_native.servicefabric.RollingUpgradeMonitoringPolicyArgs(
            failure_action="Rollback",
            health_check_retry_timeout="00:10:00",
            health_check_stable_duration="00:05:00",
            health_check_wait_duration="00:02:00",
            upgrade_domain_timeout="00:15:00",
            upgrade_timeout="01:00:00",
        ),
        upgrade_mode="UnmonitoredAuto",
        upgrade_replica_set_check_timeout=3600,
    ),
    version="/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/resRg/providers/Microsoft.ServiceFabric/managedclusters/myCluster/applicationTypes/myAppType/versions/1.0")

```

```yaml
resources:
  application:
    type: azure-native:servicefabric:Application
    properties:
      applicationName: myApp
      clusterName: myCluster
      location: eastus
      parameters:
        param1: value1
      resourceGroupName: resRg
      tags:
        a: b
      upgradePolicy:
        applicationHealthPolicy:
          considerWarningAsError: true
          defaultServiceTypeHealthPolicy:
            maxPercentUnhealthyPartitionsPerService: 0
            maxPercentUnhealthyReplicasPerPartition: 0
            maxPercentUnhealthyServices: 0
          maxPercentUnhealthyDeployedApplications: 0
          serviceTypeHealthPolicyMap:
            myService:
              maxPercentUnhealthyPartitionsPerService: 30
              maxPercentUnhealthyReplicasPerPartition: 30
              maxPercentUnhealthyServices: 30
        forceRestart: false
        instanceCloseDelayDuration: 600
        recreateApplication: false
        rollingUpgradeMonitoringPolicy:
          failureAction: Rollback
          healthCheckRetryTimeout: 00:10:00
          healthCheckStableDuration: 00:05:00
          healthCheckWaitDuration: 00:02:00
          upgradeDomainTimeout: 00:15:00
          upgradeTimeout: 01:00:00
        upgradeMode: UnmonitoredAuto
        upgradeReplicaSetCheckTimeout: 3600
      version: /subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/resRg/providers/Microsoft.ServiceFabric/managedclusters/myCluster/applicationTypes/myAppType/versions/1.0

```

{{% /example %}}
{{% example %}}
### Put an application with minimum parameters
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var application = new AzureNative.ServiceFabric.Application("application", new()
    {
        ApplicationName = "myApp",
        ClusterName = "myCluster",
        Location = "eastus",
        ResourceGroupName = "resRg",
        Version = "/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/resRg/providers/Microsoft.ServiceFabric/managedclusters/myCluster/applicationTypes/myAppType/versions/1.0",
    });

});


```

```go
package main

import (
	servicefabric "github.com/pulumi/pulumi-azure-native-sdk/servicefabric"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := servicefabric.NewApplication(ctx, "application", &servicefabric.ApplicationArgs{
			ApplicationName:   pulumi.String("myApp"),
			ClusterName:       pulumi.String("myCluster"),
			Location:          pulumi.String("eastus"),
			ResourceGroupName: pulumi.String("resRg"),
			Version:           pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/resRg/providers/Microsoft.ServiceFabric/managedclusters/myCluster/applicationTypes/myAppType/versions/1.0"),
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
import com.pulumi.azurenative.servicefabric.Application;
import com.pulumi.azurenative.servicefabric.ApplicationArgs;
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
        var application = new Application("application", ApplicationArgs.builder()        
            .applicationName("myApp")
            .clusterName("myCluster")
            .location("eastus")
            .resourceGroupName("resRg")
            .version("/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/resRg/providers/Microsoft.ServiceFabric/managedclusters/myCluster/applicationTypes/myAppType/versions/1.0")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const application = new azure_native.servicefabric.Application("application", {
    applicationName: "myApp",
    clusterName: "myCluster",
    location: "eastus",
    resourceGroupName: "resRg",
    version: "/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/resRg/providers/Microsoft.ServiceFabric/managedclusters/myCluster/applicationTypes/myAppType/versions/1.0",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

application = azure_native.servicefabric.Application("application",
    application_name="myApp",
    cluster_name="myCluster",
    location="eastus",
    resource_group_name="resRg",
    version="/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/resRg/providers/Microsoft.ServiceFabric/managedclusters/myCluster/applicationTypes/myAppType/versions/1.0")

```

```yaml
resources:
  application:
    type: azure-native:servicefabric:Application
    properties:
      applicationName: myApp
      clusterName: myCluster
      location: eastus
      resourceGroupName: resRg
      version: /subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/resRg/providers/Microsoft.ServiceFabric/managedclusters/myCluster/applicationTypes/myAppType/versions/1.0

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:servicefabric:Application myApp /subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/resRg/providers/Microsoft.ServiceFabric/managedclusters/myCluster/applications/myApp 
```
