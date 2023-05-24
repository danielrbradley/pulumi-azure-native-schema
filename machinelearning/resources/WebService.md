Instance of an Azure ML web service resource.
API Version: 2017-01-01.
Previous API Version: 2017-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### PUT WebService
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var webService = new AzureNative.MachineLearning.WebService("webService", new()
    {
        Location = "West US",
        Properties = new AzureNative.MachineLearning.Inputs.WebServicePropertiesForGraphArgs
        {
            Assets = 
            {
                { "asset1", new AzureNative.MachineLearning.Inputs.AssetItemArgs
                {
                    LocationInfo = new AzureNative.MachineLearning.Inputs.BlobLocationArgs
                    {
                        Credentials = "",
                        Uri = "aml://module/moduleId-1",
                    },
                    Name = "Execute R Script",
                    Type = "Module",
                } },
                { "asset2", new AzureNative.MachineLearning.Inputs.AssetItemArgs
                {
                    LocationInfo = new AzureNative.MachineLearning.Inputs.BlobLocationArgs
                    {
                        Credentials = "",
                        Uri = "aml://module/moduleId-2",
                    },
                    Name = "Import Data",
                    Type = "Module",
                } },
            },
            CommitmentPlan = new AzureNative.MachineLearning.Inputs.CommitmentPlanArgs
            {
                Id = "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.MachineLearning/commitmentPlans/commitmentPlanName",
            },
            Description = "Web Service Description",
            Diagnostics = new AzureNative.MachineLearning.Inputs.DiagnosticsConfigurationArgs
            {
                Level = "None",
            },
            ExampleRequest = new AzureNative.MachineLearning.Inputs.ExampleRequestArgs
            {
                Inputs = 
                {
                    { "input1", new[]
                    {
                        new[]
                        {
                            "age",
                        },
                        new[]
                        {
                            "workclass",
                        },
                        new[]
                        {
                            "fnlwgt",
                        },
                        new[]
                        {
                            "education",
                        },
                        new[]
                        {
                            "education-num",
                        },
                    } },
                },
            },
            ExposeSampleData = true,
            Input = new AzureNative.MachineLearning.Inputs.ServiceInputOutputSpecificationArgs
            {
                Description = "",
                Properties = 
                {
                    { "input1", new AzureNative.MachineLearning.Inputs.TableSpecificationArgs
                    {
                        Description = "",
                        Properties = 
                        {
                            { "column_name", new AzureNative.MachineLearning.Inputs.ColumnSpecificationArgs
                            {
                                Type = "String",
                                XMsIsnullable = false,
                            } },
                        },
                        Title = "",
                        Type = "object",
                    } },
                },
                Title = "",
                Type = "object",
            },
            MachineLearningWorkspace = new AzureNative.MachineLearning.Inputs.MachineLearningWorkspaceArgs
            {
                Id = "workspaceId",
            },
            Output = new AzureNative.MachineLearning.Inputs.ServiceInputOutputSpecificationArgs
            {
                Description = "",
                Properties = 
                {
                    { "output1", new AzureNative.MachineLearning.Inputs.TableSpecificationArgs
                    {
                        Description = "",
                        Properties = 
                        {
                            { "age", new AzureNative.MachineLearning.Inputs.ColumnSpecificationArgs
                            {
                                Format = "Int32",
                                Type = "Integer",
                                XMsIsnullable = true,
                            } },
                            { "workclass", new AzureNative.MachineLearning.Inputs.ColumnSpecificationArgs
                            {
                                Type = "String",
                                XMsIsnullable = false,
                            } },
                        },
                        Title = "",
                        Type = "object",
                    } },
                },
                Title = "",
                Type = "object",
            },
            Package = new AzureNative.MachineLearning.Inputs.GraphPackageArgs
            {
                Edges = new[]
                {
                    new AzureNative.MachineLearning.Inputs.GraphEdgeArgs
                    {
                        SourceNodeId = "node2",
                        SourcePortId = "Results dataset",
                        TargetNodeId = "node1",
                        TargetPortId = "Dataset2",
                    },
                    new AzureNative.MachineLearning.Inputs.GraphEdgeArgs
                    {
                        SourceNodeId = "node3",
                        TargetNodeId = "node1",
                        TargetPortId = "Dataset1",
                    },
                    new AzureNative.MachineLearning.Inputs.GraphEdgeArgs
                    {
                        SourceNodeId = "node1",
                        SourcePortId = "Result Dataset",
                        TargetNodeId = "node4",
                    },
                },
                GraphParameters = null,
                Nodes = 
                {
                    { "node1", new AzureNative.MachineLearning.Inputs.GraphNodeArgs
                    {
                        AssetId = "asset1",
                        Parameters = 
                        {
                            { "R Script", new AzureNative.MachineLearning.Inputs.WebServiceParameterArgs
                            {
                                CertificateThumbprint = "",
                                Value = "The R Script",
                            } },
                            { "R Version", new AzureNative.MachineLearning.Inputs.WebServiceParameterArgs
                            {
                                CertificateThumbprint = "",
                                Value = "CRAN R 3.1.0",
                            } },
                        },
                    } },
                    { "node2", new AzureNative.MachineLearning.Inputs.GraphNodeArgs
                    {
                        AssetId = "asset2",
                        Parameters = 
                        {
                            { "Account Key", new AzureNative.MachineLearning.Inputs.WebServiceParameterArgs
                            {
                                CertificateThumbprint = "TheThumbprint",
                                Value = "Encrypted Key",
                            } },
                            { "Account Name", new AzureNative.MachineLearning.Inputs.WebServiceParameterArgs
                            {
                                CertificateThumbprint = "",
                                Value = "accountName",
                            } },
                            { "Please Specify Authentication Type", new AzureNative.MachineLearning.Inputs.WebServiceParameterArgs
                            {
                                CertificateThumbprint = "",
                                Value = "Account",
                            } },
                            { "Please Specify Data Source", new AzureNative.MachineLearning.Inputs.WebServiceParameterArgs
                            {
                                CertificateThumbprint = "",
                                Value = "AzureBlobStorage",
                            } },
                        },
                    } },
                    { "node3", new AzureNative.MachineLearning.Inputs.GraphNodeArgs
                    {
                        InputId = "input1",
                    } },
                    { "node4", new AzureNative.MachineLearning.Inputs.GraphNodeArgs
                    {
                        OutputId = "output1",
                    } },
                },
            },
            PackageType = "Graph",
            Parameters = null,
            PayloadsInBlobStorage = false,
            ReadOnly = false,
            RealtimeConfiguration = new AzureNative.MachineLearning.Inputs.RealtimeConfigurationArgs
            {
                MaxConcurrentCalls = 4,
            },
            StorageAccount = new AzureNative.MachineLearning.Inputs.StorageAccountArgs
            {
                Key = "Storage_Key",
                Name = "Storage_Name",
            },
            Title = "Web Service Title",
        },
        ResourceGroupName = "OneResourceGroupName",
        Tags = 
        {
            { "tag1", "value1" },
            { "tag2", "value2" },
        },
        WebServiceName = "TargetWebServiceName",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.machinelearning.WebService;
import com.pulumi.azurenative.machinelearning.WebServiceArgs;
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
        var webService = new WebService("webService", WebServiceArgs.builder()        
            .location("West US")
            .properties(Map.ofEntries(
                Map.entry("assets", Map.ofEntries(
                    Map.entry("asset1", Map.ofEntries(
                        Map.entry("locationInfo", Map.ofEntries(
                            Map.entry("credentials", ""),
                            Map.entry("uri", "aml://module/moduleId-1")
                        )),
                        Map.entry("name", "Execute R Script"),
                        Map.entry("type", "Module")
                    )),
                    Map.entry("asset2", Map.ofEntries(
                        Map.entry("locationInfo", Map.ofEntries(
                            Map.entry("credentials", ""),
                            Map.entry("uri", "aml://module/moduleId-2")
                        )),
                        Map.entry("name", "Import Data"),
                        Map.entry("type", "Module")
                    ))
                )),
                Map.entry("commitmentPlan", Map.of("id", "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.MachineLearning/commitmentPlans/commitmentPlanName")),
                Map.entry("description", "Web Service Description"),
                Map.entry("diagnostics", Map.of("level", "None")),
                Map.entry("exampleRequest", Map.of("inputs", Map.of("input1",                 
                    "age",
                    "workclass",
                    "fnlwgt",
                    "education",
                    "education-num"))),
                Map.entry("exposeSampleData", true),
                Map.entry("input", Map.ofEntries(
                    Map.entry("description", ""),
                    Map.entry("properties", Map.of("input1", Map.ofEntries(
                        Map.entry("description", ""),
                        Map.entry("properties", Map.of("column_name", Map.ofEntries(
                            Map.entry("type", "String"),
                            Map.entry("xMsIsnullable", false)
                        ))),
                        Map.entry("title", ""),
                        Map.entry("type", "object")
                    ))),
                    Map.entry("title", ""),
                    Map.entry("type", "object")
                )),
                Map.entry("machineLearningWorkspace", Map.of("id", "workspaceId")),
                Map.entry("output", Map.ofEntries(
                    Map.entry("description", ""),
                    Map.entry("properties", Map.of("output1", Map.ofEntries(
                        Map.entry("description", ""),
                        Map.entry("properties", Map.ofEntries(
                            Map.entry("age", Map.ofEntries(
                                Map.entry("format", "Int32"),
                                Map.entry("type", "Integer"),
                                Map.entry("xMsIsnullable", true)
                            )),
                            Map.entry("workclass", Map.ofEntries(
                                Map.entry("type", "String"),
                                Map.entry("xMsIsnullable", false)
                            ))
                        )),
                        Map.entry("title", ""),
                        Map.entry("type", "object")
                    ))),
                    Map.entry("title", ""),
                    Map.entry("type", "object")
                )),
                Map.entry("package", Map.ofEntries(
                    Map.entry("edges",                     
                        Map.ofEntries(
                            Map.entry("sourceNodeId", "node2"),
                            Map.entry("sourcePortId", "Results dataset"),
                            Map.entry("targetNodeId", "node1"),
                            Map.entry("targetPortId", "Dataset2")
                        ),
                        Map.ofEntries(
                            Map.entry("sourceNodeId", "node3"),
                            Map.entry("targetNodeId", "node1"),
                            Map.entry("targetPortId", "Dataset1")
                        ),
                        Map.ofEntries(
                            Map.entry("sourceNodeId", "node1"),
                            Map.entry("sourcePortId", "Result Dataset"),
                            Map.entry("targetNodeId", "node4")
                        )),
                    Map.entry("graphParameters", ),
                    Map.entry("nodes", Map.ofEntries(
                        Map.entry("node1", Map.ofEntries(
                            Map.entry("assetId", "asset1"),
                            Map.entry("parameters", Map.ofEntries(
                                Map.entry("R Script", Map.ofEntries(
                                    Map.entry("certificateThumbprint", ""),
                                    Map.entry("value", "The R Script")
                                )),
                                Map.entry("R Version", Map.ofEntries(
                                    Map.entry("certificateThumbprint", ""),
                                    Map.entry("value", "CRAN R 3.1.0")
                                ))
                            ))
                        )),
                        Map.entry("node2", Map.ofEntries(
                            Map.entry("assetId", "asset2"),
                            Map.entry("parameters", Map.ofEntries(
                                Map.entry("Account Key", Map.ofEntries(
                                    Map.entry("certificateThumbprint", "TheThumbprint"),
                                    Map.entry("value", "Encrypted Key")
                                )),
                                Map.entry("Account Name", Map.ofEntries(
                                    Map.entry("certificateThumbprint", ""),
                                    Map.entry("value", "accountName")
                                )),
                                Map.entry("Please Specify Authentication Type", Map.ofEntries(
                                    Map.entry("certificateThumbprint", ""),
                                    Map.entry("value", "Account")
                                )),
                                Map.entry("Please Specify Data Source", Map.ofEntries(
                                    Map.entry("certificateThumbprint", ""),
                                    Map.entry("value", "AzureBlobStorage")
                                ))
                            ))
                        )),
                        Map.entry("node3", Map.of("inputId", "input1")),
                        Map.entry("node4", Map.of("outputId", "output1"))
                    ))
                )),
                Map.entry("packageType", "Graph"),
                Map.entry("parameters", ),
                Map.entry("payloadsInBlobStorage", false),
                Map.entry("readOnly", false),
                Map.entry("realtimeConfiguration", Map.of("maxConcurrentCalls", 4)),
                Map.entry("storageAccount", Map.ofEntries(
                    Map.entry("key", "Storage_Key"),
                    Map.entry("name", "Storage_Name")
                )),
                Map.entry("title", "Web Service Title")
            ))
            .resourceGroupName("OneResourceGroupName")
            .tags(Map.ofEntries(
                Map.entry("tag1", "value1"),
                Map.entry("tag2", "value2")
            ))
            .webServiceName("TargetWebServiceName")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const webService = new azure_native.machinelearning.WebService("webService", {
    location: "West US",
    properties: {
        assets: {
            asset1: {
                locationInfo: {
                    credentials: "",
                    uri: "aml://module/moduleId-1",
                },
                name: "Execute R Script",
                type: "Module",
            },
            asset2: {
                locationInfo: {
                    credentials: "",
                    uri: "aml://module/moduleId-2",
                },
                name: "Import Data",
                type: "Module",
            },
        },
        commitmentPlan: {
            id: "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.MachineLearning/commitmentPlans/commitmentPlanName",
        },
        description: "Web Service Description",
        diagnostics: {
            level: "None",
        },
        exampleRequest: {
            inputs: {
                input1: [
                    ["age"],
                    ["workclass"],
                    ["fnlwgt"],
                    ["education"],
                    ["education-num"],
                ],
            },
        },
        exposeSampleData: true,
        input: {
            description: "",
            properties: {
                input1: {
                    description: "",
                    properties: {
                        column_name: {
                            type: "String",
                            xMsIsnullable: false,
                        },
                    },
                    title: "",
                    type: "object",
                },
            },
            title: "",
            type: "object",
        },
        machineLearningWorkspace: {
            id: "workspaceId",
        },
        output: {
            description: "",
            properties: {
                output1: {
                    description: "",
                    properties: {
                        age: {
                            format: "Int32",
                            type: "Integer",
                            xMsIsnullable: true,
                        },
                        workclass: {
                            type: "String",
                            xMsIsnullable: false,
                        },
                    },
                    title: "",
                    type: "object",
                },
            },
            title: "",
            type: "object",
        },
        "package": {
            edges: [
                {
                    sourceNodeId: "node2",
                    sourcePortId: "Results dataset",
                    targetNodeId: "node1",
                    targetPortId: "Dataset2",
                },
                {
                    sourceNodeId: "node3",
                    targetNodeId: "node1",
                    targetPortId: "Dataset1",
                },
                {
                    sourceNodeId: "node1",
                    sourcePortId: "Result Dataset",
                    targetNodeId: "node4",
                },
            ],
            graphParameters: {},
            nodes: {
                node1: {
                    assetId: "asset1",
                    parameters: {
                        "R Script": {
                            certificateThumbprint: "",
                            value: "The R Script",
                        },
                        "R Version": {
                            certificateThumbprint: "",
                            value: "CRAN R 3.1.0",
                        },
                    },
                },
                node2: {
                    assetId: "asset2",
                    parameters: {
                        "Account Key": {
                            certificateThumbprint: "TheThumbprint",
                            value: "Encrypted Key",
                        },
                        "Account Name": {
                            certificateThumbprint: "",
                            value: "accountName",
                        },
                        "Please Specify Authentication Type": {
                            certificateThumbprint: "",
                            value: "Account",
                        },
                        "Please Specify Data Source": {
                            certificateThumbprint: "",
                            value: "AzureBlobStorage",
                        },
                    },
                },
                node3: {
                    inputId: "input1",
                },
                node4: {
                    outputId: "output1",
                },
            },
        },
        packageType: "Graph",
        parameters: {},
        payloadsInBlobStorage: false,
        readOnly: false,
        realtimeConfiguration: {
            maxConcurrentCalls: 4,
        },
        storageAccount: {
            key: "Storage_Key",
            name: "Storage_Name",
        },
        title: "Web Service Title",
    },
    resourceGroupName: "OneResourceGroupName",
    tags: {
        tag1: "value1",
        tag2: "value2",
    },
    webServiceName: "TargetWebServiceName",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

web_service = azure_native.machinelearning.WebService("webService",
    location="West US",
    properties=azure_native.machinelearning.WebServicePropertiesForGraphResponseArgs(
        assets={
            "asset1": azure_native.machinelearning.AssetItemArgs(
                location_info=azure_native.machinelearning.BlobLocationArgs(
                    credentials="",
                    uri="aml://module/moduleId-1",
                ),
                name="Execute R Script",
                type="Module",
            ),
            "asset2": azure_native.machinelearning.AssetItemArgs(
                location_info=azure_native.machinelearning.BlobLocationArgs(
                    credentials="",
                    uri="aml://module/moduleId-2",
                ),
                name="Import Data",
                type="Module",
            ),
        },
        commitment_plan=azure_native.machinelearning.CommitmentPlanArgs(
            id="/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.MachineLearning/commitmentPlans/commitmentPlanName",
        ),
        description="Web Service Description",
        diagnostics=azure_native.machinelearning.DiagnosticsConfigurationArgs(
            level="None",
        ),
        example_request=azure_native.machinelearning.ExampleRequestArgs(
            inputs={
                "input1": [
                    ["age"],
                    ["workclass"],
                    ["fnlwgt"],
                    ["education"],
                    ["education-num"],
                ],
            },
        ),
        expose_sample_data=True,
        input={
            "description": "",
            "properties": {
                "input1": azure_native.machinelearning.TableSpecificationArgs(
                    description="",
                    properties={
                        "column_name": azure_native.machinelearning.ColumnSpecificationArgs(
                            type="String",
                            x_ms_isnullable=False,
                        ),
                    },
                    title="",
                    type="object",
                ),
            },
            "title": "",
            "type": "object",
        },
        machine_learning_workspace=azure_native.machinelearning.MachineLearningWorkspaceArgs(
            id="workspaceId",
        ),
        output={
            "description": "",
            "properties": {
                "output1": azure_native.machinelearning.TableSpecificationArgs(
                    description="",
                    properties={
                        "age": azure_native.machinelearning.ColumnSpecificationArgs(
                            format="Int32",
                            type="Integer",
                            x_ms_isnullable=True,
                        ),
                        "workclass": azure_native.machinelearning.ColumnSpecificationArgs(
                            type="String",
                            x_ms_isnullable=False,
                        ),
                    },
                    title="",
                    type="object",
                ),
            },
            "title": "",
            "type": "object",
        },
        package={
            "edges": [
                azure_native.machinelearning.GraphEdgeArgs(
                    source_node_id="node2",
                    source_port_id="Results dataset",
                    target_node_id="node1",
                    target_port_id="Dataset2",
                ),
                azure_native.machinelearning.GraphEdgeArgs(
                    source_node_id="node3",
                    target_node_id="node1",
                    target_port_id="Dataset1",
                ),
                azure_native.machinelearning.GraphEdgeArgs(
                    source_node_id="node1",
                    source_port_id="Result Dataset",
                    target_node_id="node4",
                ),
            ],
            "graphParameters": {},
            "nodes": {
                "node1": azure_native.machinelearning.GraphNodeArgs(
                    asset_id="asset1",
                    parameters={
                        "R Script": azure_native.machinelearning.WebServiceParameterArgs(
                            certificate_thumbprint="",
                            value="The R Script",
                        ),
                        "R Version": azure_native.machinelearning.WebServiceParameterArgs(
                            certificate_thumbprint="",
                            value="CRAN R 3.1.0",
                        ),
                    },
                ),
                "node2": azure_native.machinelearning.GraphNodeArgs(
                    asset_id="asset2",
                    parameters={
                        "Account Key": azure_native.machinelearning.WebServiceParameterArgs(
                            certificate_thumbprint="TheThumbprint",
                            value="Encrypted Key",
                        ),
                        "Account Name": azure_native.machinelearning.WebServiceParameterArgs(
                            certificate_thumbprint="",
                            value="accountName",
                        ),
                        "Please Specify Authentication Type": azure_native.machinelearning.WebServiceParameterArgs(
                            certificate_thumbprint="",
                            value="Account",
                        ),
                        "Please Specify Data Source": azure_native.machinelearning.WebServiceParameterArgs(
                            certificate_thumbprint="",
                            value="AzureBlobStorage",
                        ),
                    },
                ),
                "node3": azure_native.machinelearning.GraphNodeArgs(
                    input_id="input1",
                ),
                "node4": azure_native.machinelearning.GraphNodeArgs(
                    output_id="output1",
                ),
            },
        },
        package_type="Graph",
        parameters={},
        payloads_in_blob_storage=False,
        read_only=False,
        realtime_configuration=azure_native.machinelearning.RealtimeConfigurationArgs(
            max_concurrent_calls=4,
        ),
        storage_account=azure_native.machinelearning.StorageAccountArgs(
            key="Storage_Key",
            name="Storage_Name",
        ),
        title="Web Service Title",
    ),
    resource_group_name="OneResourceGroupName",
    tags={
        "tag1": "value1",
        "tag2": "value2",
    },
    web_service_name="TargetWebServiceName")

```

```yaml
resources:
  webService:
    type: azure-native:machinelearning:WebService
    properties:
      location: West US
      properties:
        assets:
          asset1:
            locationInfo:
              credentials:
              uri: aml://module/moduleId-1
            name: Execute R Script
            type: Module
          asset2:
            locationInfo:
              credentials:
              uri: aml://module/moduleId-2
            name: Import Data
            type: Module
        commitmentPlan:
          id: /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.MachineLearning/commitmentPlans/commitmentPlanName
        description: Web Service Description
        diagnostics:
          level: None
        exampleRequest:
          inputs:
            input1:
              - - age
              - - workclass
              - - fnlwgt
              - - education
              - - education-num
        exposeSampleData: true
        input:
          description:
          properties:
            input1:
              description:
              properties:
                column_name:
                  type: String
                  xMsIsnullable: false
              title:
              type: object
          title:
          type: object
        machineLearningWorkspace:
          id: workspaceId
        output:
          description:
          properties:
            output1:
              description:
              properties:
                age:
                  format: Int32
                  type: Integer
                  xMsIsnullable: true
                workclass:
                  type: String
                  xMsIsnullable: false
              title:
              type: object
          title:
          type: object
        package:
          edges:
            - sourceNodeId: node2
              sourcePortId: Results dataset
              targetNodeId: node1
              targetPortId: Dataset2
            - sourceNodeId: node3
              targetNodeId: node1
              targetPortId: Dataset1
            - sourceNodeId: node1
              sourcePortId: Result Dataset
              targetNodeId: node4
          graphParameters: {}
          nodes:
            node1:
              assetId: asset1
              parameters:
                R Script:
                  certificateThumbprint:
                  value: The R Script
                R Version:
                  certificateThumbprint:
                  value: CRAN R 3.1.0
            node2:
              assetId: asset2
              parameters:
                Account Key:
                  certificateThumbprint: TheThumbprint
                  value: Encrypted Key
                Account Name:
                  certificateThumbprint:
                  value: accountName
                Please Specify Authentication Type:
                  certificateThumbprint:
                  value: Account
                Please Specify Data Source:
                  certificateThumbprint:
                  value: AzureBlobStorage
            node3:
              inputId: input1
            node4:
              outputId: output1
        packageType: Graph
        parameters: {}
        payloadsInBlobStorage: false
        readOnly: false
        realtimeConfiguration:
          maxConcurrentCalls: 4
        storageAccount:
          key: Storage_Key
          name: Storage_Name
        title: Web Service Title
      resourceGroupName: OneResourceGroupName
      tags:
        tag1: value1
        tag2: value2
      webServiceName: TargetWebServiceName

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:machinelearning:WebService myresource1 TheWebServiceId 
```
