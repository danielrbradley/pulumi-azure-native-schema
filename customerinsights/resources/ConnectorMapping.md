The connector mapping resource format.
API Version: 2017-04-26.
Previous API Version: 2017-04-26. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ConnectorMappings_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var connectorMapping = new AzureNative.CustomerInsights.ConnectorMapping("connectorMapping", new()
    {
        ConnectorName = "testConnector8858",
        Description = "Test mapping",
        DisplayName = "testMapping12491",
        EntityType = AzureNative.CustomerInsights.EntityTypes.Interaction,
        EntityTypeName = "TestInteractionType2967",
        HubName = "sdkTestHub",
        MappingName = "testMapping12491",
        MappingProperties = new AzureNative.CustomerInsights.Inputs.ConnectorMappingPropertiesArgs
        {
            Availability = new AzureNative.CustomerInsights.Inputs.ConnectorMappingAvailabilityArgs
            {
                Frequency = AzureNative.CustomerInsights.FrequencyTypes.Hour,
                Interval = 5,
            },
            CompleteOperation = new AzureNative.CustomerInsights.Inputs.ConnectorMappingCompleteOperationArgs
            {
                CompletionOperationType = AzureNative.CustomerInsights.CompletionOperationTypes.DeleteFile,
                DestinationFolder = "fakePath",
            },
            ErrorManagement = new AzureNative.CustomerInsights.Inputs.ConnectorMappingErrorManagementArgs
            {
                ErrorLimit = 10,
                ErrorManagementType = AzureNative.CustomerInsights.ErrorManagementTypes.StopImport,
            },
            FileFilter = "unknown",
            FolderPath = "http://sample.dne/file",
            Format = new AzureNative.CustomerInsights.Inputs.ConnectorMappingFormatArgs
            {
                ColumnDelimiter = "|",
                FormatType = AzureNative.CustomerInsights.FormatTypes.TextFormat,
            },
            HasHeader = false,
            Structure = new[]
            {
                new AzureNative.CustomerInsights.Inputs.ConnectorMappingStructureArgs
                {
                    ColumnName = "unknown1",
                    IsEncrypted = false,
                    PropertyName = "unknwon1",
                },
                new AzureNative.CustomerInsights.Inputs.ConnectorMappingStructureArgs
                {
                    ColumnName = "unknown2",
                    IsEncrypted = true,
                    PropertyName = "unknwon2",
                },
            },
        },
        ResourceGroupName = "TestHubRG",
    });

});


```

```go
package main

import (
	customerinsights "github.com/pulumi/pulumi-azure-native-sdk/customerinsights"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := customerinsights.NewConnectorMapping(ctx, "connectorMapping", &customerinsights.ConnectorMappingArgs{
			ConnectorName:  pulumi.String("testConnector8858"),
			Description:    pulumi.String("Test mapping"),
			DisplayName:    pulumi.String("testMapping12491"),
			EntityType:     customerinsights.EntityTypesInteraction,
			EntityTypeName: pulumi.String("TestInteractionType2967"),
			HubName:        pulumi.String("sdkTestHub"),
			MappingName:    pulumi.String("testMapping12491"),
			MappingProperties: customerinsights.ConnectorMappingPropertiesResponse{
				Availability: &customerinsights.ConnectorMappingAvailabilityArgs{
					Frequency: customerinsights.FrequencyTypesHour,
					Interval:  pulumi.Int(5),
				},
				CompleteOperation: &customerinsights.ConnectorMappingCompleteOperationArgs{
					CompletionOperationType: customerinsights.CompletionOperationTypesDeleteFile,
					DestinationFolder:       pulumi.String("fakePath"),
				},
				ErrorManagement: &customerinsights.ConnectorMappingErrorManagementArgs{
					ErrorLimit:          pulumi.Int(10),
					ErrorManagementType: customerinsights.ErrorManagementTypesStopImport,
				},
				FileFilter: pulumi.String("unknown"),
				FolderPath: pulumi.String("http://sample.dne/file"),
				Format: &customerinsights.ConnectorMappingFormatArgs{
					ColumnDelimiter: pulumi.String("|"),
					FormatType:      customerinsights.FormatTypesTextFormat,
				},
				HasHeader: pulumi.Bool(false),
				Structure: customerinsights.ConnectorMappingStructureArray{
					&customerinsights.ConnectorMappingStructureArgs{
						ColumnName:   pulumi.String("unknown1"),
						IsEncrypted:  pulumi.Bool(false),
						PropertyName: pulumi.String("unknwon1"),
					},
					&customerinsights.ConnectorMappingStructureArgs{
						ColumnName:   pulumi.String("unknown2"),
						IsEncrypted:  pulumi.Bool(true),
						PropertyName: pulumi.String("unknwon2"),
					},
				},
			},
			ResourceGroupName: pulumi.String("TestHubRG"),
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
import com.pulumi.azurenative.customerinsights.ConnectorMapping;
import com.pulumi.azurenative.customerinsights.ConnectorMappingArgs;
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
        var connectorMapping = new ConnectorMapping("connectorMapping", ConnectorMappingArgs.builder()        
            .connectorName("testConnector8858")
            .description("Test mapping")
            .displayName("testMapping12491")
            .entityType("Interaction")
            .entityTypeName("TestInteractionType2967")
            .hubName("sdkTestHub")
            .mappingName("testMapping12491")
            .mappingProperties(Map.ofEntries(
                Map.entry("availability", Map.ofEntries(
                    Map.entry("frequency", "Hour"),
                    Map.entry("interval", 5)
                )),
                Map.entry("completeOperation", Map.ofEntries(
                    Map.entry("completionOperationType", "DeleteFile"),
                    Map.entry("destinationFolder", "fakePath")
                )),
                Map.entry("errorManagement", Map.ofEntries(
                    Map.entry("errorLimit", 10),
                    Map.entry("errorManagementType", "StopImport")
                )),
                Map.entry("fileFilter", "unknown"),
                Map.entry("folderPath", "http://sample.dne/file"),
                Map.entry("format", Map.ofEntries(
                    Map.entry("columnDelimiter", "|"),
                    Map.entry("formatType", "TextFormat")
                )),
                Map.entry("hasHeader", false),
                Map.entry("structure",                 
                    Map.ofEntries(
                        Map.entry("columnName", "unknown1"),
                        Map.entry("isEncrypted", false),
                        Map.entry("propertyName", "unknwon1")
                    ),
                    Map.ofEntries(
                        Map.entry("columnName", "unknown2"),
                        Map.entry("isEncrypted", true),
                        Map.entry("propertyName", "unknwon2")
                    ))
            ))
            .resourceGroupName("TestHubRG")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const connectorMapping = new azure_native.customerinsights.ConnectorMapping("connectorMapping", {
    connectorName: "testConnector8858",
    description: "Test mapping",
    displayName: "testMapping12491",
    entityType: azure_native.customerinsights.EntityTypes.Interaction,
    entityTypeName: "TestInteractionType2967",
    hubName: "sdkTestHub",
    mappingName: "testMapping12491",
    mappingProperties: {
        availability: {
            frequency: azure_native.customerinsights.FrequencyTypes.Hour,
            interval: 5,
        },
        completeOperation: {
            completionOperationType: azure_native.customerinsights.CompletionOperationTypes.DeleteFile,
            destinationFolder: "fakePath",
        },
        errorManagement: {
            errorLimit: 10,
            errorManagementType: azure_native.customerinsights.ErrorManagementTypes.StopImport,
        },
        fileFilter: "unknown",
        folderPath: "http://sample.dne/file",
        format: {
            columnDelimiter: "|",
            formatType: azure_native.customerinsights.FormatTypes.TextFormat,
        },
        hasHeader: false,
        structure: [
            {
                columnName: "unknown1",
                isEncrypted: false,
                propertyName: "unknwon1",
            },
            {
                columnName: "unknown2",
                isEncrypted: true,
                propertyName: "unknwon2",
            },
        ],
    },
    resourceGroupName: "TestHubRG",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

connector_mapping = azure_native.customerinsights.ConnectorMapping("connectorMapping",
    connector_name="testConnector8858",
    description="Test mapping",
    display_name="testMapping12491",
    entity_type=azure_native.customerinsights.EntityTypes.INTERACTION,
    entity_type_name="TestInteractionType2967",
    hub_name="sdkTestHub",
    mapping_name="testMapping12491",
    mapping_properties=azure_native.customerinsights.ConnectorMappingPropertiesResponseArgs(
        availability=azure_native.customerinsights.ConnectorMappingAvailabilityArgs(
            frequency=azure_native.customerinsights.FrequencyTypes.HOUR,
            interval=5,
        ),
        complete_operation=azure_native.customerinsights.ConnectorMappingCompleteOperationArgs(
            completion_operation_type=azure_native.customerinsights.CompletionOperationTypes.DELETE_FILE,
            destination_folder="fakePath",
        ),
        error_management=azure_native.customerinsights.ConnectorMappingErrorManagementArgs(
            error_limit=10,
            error_management_type=azure_native.customerinsights.ErrorManagementTypes.STOP_IMPORT,
        ),
        file_filter="unknown",
        folder_path="http://sample.dne/file",
        format=azure_native.customerinsights.ConnectorMappingFormatArgs(
            column_delimiter="|",
            format_type=azure_native.customerinsights.FormatTypes.TEXT_FORMAT,
        ),
        has_header=False,
        structure=[
            azure_native.customerinsights.ConnectorMappingStructureArgs(
                column_name="unknown1",
                is_encrypted=False,
                property_name="unknwon1",
            ),
            azure_native.customerinsights.ConnectorMappingStructureArgs(
                column_name="unknown2",
                is_encrypted=True,
                property_name="unknwon2",
            ),
        ],
    ),
    resource_group_name="TestHubRG")

```

```yaml
resources:
  connectorMapping:
    type: azure-native:customerinsights:ConnectorMapping
    properties:
      connectorName: testConnector8858
      description: Test mapping
      displayName: testMapping12491
      entityType: Interaction
      entityTypeName: TestInteractionType2967
      hubName: sdkTestHub
      mappingName: testMapping12491
      mappingProperties:
        availability:
          frequency: Hour
          interval: 5
        completeOperation:
          completionOperationType: DeleteFile
          destinationFolder: fakePath
        errorManagement:
          errorLimit: 10
          errorManagementType: StopImport
        fileFilter: unknown
        folderPath: http://sample.dne/file
        format:
          columnDelimiter: '|'
          formatType: TextFormat
        hasHeader: false
        structure:
          - columnName: unknown1
            isEncrypted: false
            propertyName: unknwon1
          - columnName: unknown2
            isEncrypted: true
            propertyName: unknwon2
      resourceGroupName: TestHubRG

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:customerinsights:ConnectorMapping sdkTestHub/testConnector8858/testMapping12491 /subscriptions/c909e979-ef71-4def-a970-bc7c154db8c5/resourceGroups/TestHubRG/providers/Microsoft.CustomerInsights/hubs/sdkTestHub/connectors/testConnector8858/mappings/testMapping12491 
```
