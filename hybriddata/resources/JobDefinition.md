Job Definition.
API Version: 2019-06-01.
Previous API Version: 2019-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### JobDefinitions_CreateOrUpdatePUT83
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var jobDefinition = new AzureNative.HybridData.JobDefinition("jobDefinition", new()
    {
        DataManagerName = "TestAzureSDKOperations",
        DataServiceInput = 
        {
            { "AzureStorageType", "Blob" },
            { "BackupChoice", "UseExistingLatest" },
            { "ContainerName", "containerfromtest" },
            { "DeviceName", "8600-SHG0997877L71FC" },
            { "FileNameFilter", "*" },
            { "IsDirectoryMode", false },
            { "RootDirectories", new[]
            {
                "\\",
            } },
            { "VolumeNames", new[]
            {
                "TestAutomation",
            } },
        },
        DataServiceName = "DataTransformation",
        DataSinkId = "/subscriptions/6e0219f5-327a-4365-904f-05eed4227ad7/resourceGroups/ResourceGroupForSDKTest/providers/Microsoft.HybridData/dataManagers/TestAzureSDKOperations/dataStores/TestAzureStorage1",
        DataSourceId = "/subscriptions/6e0219f5-327a-4365-904f-05eed4227ad7/resourceGroups/ResourceGroupForSDKTest/providers/Microsoft.HybridData/dataManagers/TestAzureSDKOperations/dataStores/TestStorSimpleSource1",
        JobDefinitionName = "jobdeffromtestcode1",
        ResourceGroupName = "ResourceGroupForSDKTest",
        RunLocation = AzureNative.HybridData.RunLocation.Westus,
        State = AzureNative.HybridData.State.Enabled,
        UserConfirmation = AzureNative.HybridData.UserConfirmation.Required,
    });

});


```

```go
package main

import (
	hybriddata "github.com/pulumi/pulumi-azure-native-sdk/hybriddata"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := hybriddata.NewJobDefinition(ctx, "jobDefinition", &hybriddata.JobDefinitionArgs{
			DataManagerName: pulumi.String("TestAzureSDKOperations"),
			DataServiceInput: pulumi.Any{
				AzureStorageType: "Blob",
				BackupChoice:     "UseExistingLatest",
				ContainerName:    "containerfromtest",
				DeviceName:       "8600-SHG0997877L71FC",
				FileNameFilter:   "*",
				IsDirectoryMode:  false,
				RootDirectories: []string{
					"\\",
				},
				VolumeNames: []string{
					"TestAutomation",
				},
			},
			DataServiceName:   pulumi.String("DataTransformation"),
			DataSinkId:        pulumi.String("/subscriptions/6e0219f5-327a-4365-904f-05eed4227ad7/resourceGroups/ResourceGroupForSDKTest/providers/Microsoft.HybridData/dataManagers/TestAzureSDKOperations/dataStores/TestAzureStorage1"),
			DataSourceId:      pulumi.String("/subscriptions/6e0219f5-327a-4365-904f-05eed4227ad7/resourceGroups/ResourceGroupForSDKTest/providers/Microsoft.HybridData/dataManagers/TestAzureSDKOperations/dataStores/TestStorSimpleSource1"),
			JobDefinitionName: pulumi.String("jobdeffromtestcode1"),
			ResourceGroupName: pulumi.String("ResourceGroupForSDKTest"),
			RunLocation:       hybriddata.RunLocationWestus,
			State:             hybriddata.StateEnabled,
			UserConfirmation:  hybriddata.UserConfirmationRequired,
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
import com.pulumi.azurenative.hybriddata.JobDefinition;
import com.pulumi.azurenative.hybriddata.JobDefinitionArgs;
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
        var jobDefinition = new JobDefinition("jobDefinition", JobDefinitionArgs.builder()        
            .dataManagerName("TestAzureSDKOperations")
            .dataServiceInput(Map.ofEntries(
                Map.entry("AzureStorageType", "Blob"),
                Map.entry("BackupChoice", "UseExistingLatest"),
                Map.entry("ContainerName", "containerfromtest"),
                Map.entry("DeviceName", "8600-SHG0997877L71FC"),
                Map.entry("FileNameFilter", "*"),
                Map.entry("IsDirectoryMode", false),
                Map.entry("RootDirectories", "\\"),
                Map.entry("VolumeNames", "TestAutomation")
            ))
            .dataServiceName("DataTransformation")
            .dataSinkId("/subscriptions/6e0219f5-327a-4365-904f-05eed4227ad7/resourceGroups/ResourceGroupForSDKTest/providers/Microsoft.HybridData/dataManagers/TestAzureSDKOperations/dataStores/TestAzureStorage1")
            .dataSourceId("/subscriptions/6e0219f5-327a-4365-904f-05eed4227ad7/resourceGroups/ResourceGroupForSDKTest/providers/Microsoft.HybridData/dataManagers/TestAzureSDKOperations/dataStores/TestStorSimpleSource1")
            .jobDefinitionName("jobdeffromtestcode1")
            .resourceGroupName("ResourceGroupForSDKTest")
            .runLocation("westus")
            .state("Enabled")
            .userConfirmation("Required")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const jobDefinition = new azure_native.hybriddata.JobDefinition("jobDefinition", {
    dataManagerName: "TestAzureSDKOperations",
    dataServiceInput: {
        AzureStorageType: "Blob",
        BackupChoice: "UseExistingLatest",
        ContainerName: "containerfromtest",
        DeviceName: "8600-SHG0997877L71FC",
        FileNameFilter: "*",
        IsDirectoryMode: false,
        RootDirectories: ["\\"],
        VolumeNames: ["TestAutomation"],
    },
    dataServiceName: "DataTransformation",
    dataSinkId: "/subscriptions/6e0219f5-327a-4365-904f-05eed4227ad7/resourceGroups/ResourceGroupForSDKTest/providers/Microsoft.HybridData/dataManagers/TestAzureSDKOperations/dataStores/TestAzureStorage1",
    dataSourceId: "/subscriptions/6e0219f5-327a-4365-904f-05eed4227ad7/resourceGroups/ResourceGroupForSDKTest/providers/Microsoft.HybridData/dataManagers/TestAzureSDKOperations/dataStores/TestStorSimpleSource1",
    jobDefinitionName: "jobdeffromtestcode1",
    resourceGroupName: "ResourceGroupForSDKTest",
    runLocation: azure_native.hybriddata.RunLocation.Westus,
    state: azure_native.hybriddata.State.Enabled,
    userConfirmation: azure_native.hybriddata.UserConfirmation.Required,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

job_definition = azure_native.hybriddata.JobDefinition("jobDefinition",
    data_manager_name="TestAzureSDKOperations",
    data_service_input={
        "AzureStorageType": "Blob",
        "BackupChoice": "UseExistingLatest",
        "ContainerName": "containerfromtest",
        "DeviceName": "8600-SHG0997877L71FC",
        "FileNameFilter": "*",
        "IsDirectoryMode": False,
        "RootDirectories": ["\\"],
        "VolumeNames": ["TestAutomation"],
    },
    data_service_name="DataTransformation",
    data_sink_id="/subscriptions/6e0219f5-327a-4365-904f-05eed4227ad7/resourceGroups/ResourceGroupForSDKTest/providers/Microsoft.HybridData/dataManagers/TestAzureSDKOperations/dataStores/TestAzureStorage1",
    data_source_id="/subscriptions/6e0219f5-327a-4365-904f-05eed4227ad7/resourceGroups/ResourceGroupForSDKTest/providers/Microsoft.HybridData/dataManagers/TestAzureSDKOperations/dataStores/TestStorSimpleSource1",
    job_definition_name="jobdeffromtestcode1",
    resource_group_name="ResourceGroupForSDKTest",
    run_location=azure_native.hybriddata.RunLocation.WESTUS,
    state=azure_native.hybriddata.State.ENABLED,
    user_confirmation=azure_native.hybriddata.UserConfirmation.REQUIRED)

```

```yaml
resources:
  jobDefinition:
    type: azure-native:hybriddata:JobDefinition
    properties:
      dataManagerName: TestAzureSDKOperations
      dataServiceInput:
        AzureStorageType: Blob
        BackupChoice: UseExistingLatest
        ContainerName: containerfromtest
        DeviceName: 8600-SHG0997877L71FC
        FileNameFilter: '*'
        IsDirectoryMode: false
        RootDirectories:
          - \
        VolumeNames:
          - TestAutomation
      dataServiceName: DataTransformation
      dataSinkId: /subscriptions/6e0219f5-327a-4365-904f-05eed4227ad7/resourceGroups/ResourceGroupForSDKTest/providers/Microsoft.HybridData/dataManagers/TestAzureSDKOperations/dataStores/TestAzureStorage1
      dataSourceId: /subscriptions/6e0219f5-327a-4365-904f-05eed4227ad7/resourceGroups/ResourceGroupForSDKTest/providers/Microsoft.HybridData/dataManagers/TestAzureSDKOperations/dataStores/TestStorSimpleSource1
      jobDefinitionName: jobdeffromtestcode1
      resourceGroupName: ResourceGroupForSDKTest
      runLocation: westus
      state: Enabled
      userConfirmation: Required

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:hybriddata:JobDefinition jobdeffromtestcode1 /subscriptions/6e0219f5-327a-4365-904f-05eed4227ad7/resourceGroups/ResourceGroupForSDKTest/providers/Microsoft.HybridData/dataManagers/TestAzureSDKOperations/dataServices/DataTransformation/jobDefinitions/jobdeffromtestcode1 
```
