Azure Resource Manager resource envelope.
API Version: 2022-10-01.
Previous API Version: 2021-03-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateOrUpdate AutoML Job.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var job = new AzureNative.MachineLearningServices.Job("job", new()
    {
        Id = "string",
        JobBaseProperties = new AzureNative.MachineLearningServices.Inputs.AutoMLJobArgs
        {
            ComputeId = "string",
            Description = "string",
            DisplayName = "string",
            EnvironmentId = "string",
            EnvironmentVariables = 
            {
                { "string", "string" },
            },
            ExperimentName = "string",
            Identity = new AzureNative.MachineLearningServices.Inputs.AmlTokenArgs
            {
                IdentityType = "AMLToken",
            },
            IsArchived = false,
            JobType = "AutoML",
            Outputs = 
            {
                { "string", new AzureNative.MachineLearningServices.Inputs.UriFileJobOutputArgs
                {
                    Description = "string",
                    JobOutputType = "uri_file",
                    Mode = "ReadWriteMount",
                    Uri = "string",
                } },
            },
            Properties = 
            {
                { "string", "string" },
            },
            Resources = new AzureNative.MachineLearningServices.Inputs.JobResourceConfigurationArgs
            {
                InstanceCount = 1,
                InstanceType = "string",
                Properties = 
                {
                    { "string", 
                    {
                        { "9bec0ab0-c62f-4fa9-a97c-7b24bbcc90ad", null },
                    } },
                },
            },
            Services = 
            {
                { "string", new AzureNative.MachineLearningServices.Inputs.JobServiceArgs
                {
                    Endpoint = "string",
                    JobServiceType = "string",
                    Port = 1,
                    Properties = 
                    {
                        { "string", "string" },
                    },
                } },
            },
            Tags = 
            {
                { "string", "string" },
            },
            TaskDetails = new AzureNative.MachineLearningServices.Inputs.ImageClassificationArgs
            {
                LimitSettings = new AzureNative.MachineLearningServices.Inputs.ImageLimitSettingsArgs
                {
                    MaxTrials = 2,
                },
                ModelSettings = new AzureNative.MachineLearningServices.Inputs.ImageModelSettingsClassificationArgs
                {
                    ValidationCropSize = 2,
                },
                SearchSpace = new[]
                {
                    new AzureNative.MachineLearningServices.Inputs.ImageModelDistributionSettingsClassificationArgs
                    {
                        ValidationCropSize = "choice(2, 360)",
                    },
                },
                TargetColumnName = "string",
                TaskType = "ImageClassification",
                TrainingData = new AzureNative.MachineLearningServices.Inputs.MLTableJobInputArgs
                {
                    JobInputType = "mltable",
                    Uri = "string",
                },
            },
        },
        ResourceGroupName = "test-rg",
        WorkspaceName = "my-aml-workspace",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.machinelearningservices.Job;
import com.pulumi.azurenative.machinelearningservices.JobArgs;
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
        var job = new Job("job", JobArgs.builder()        
            .id("string")
            .jobBaseProperties(Map.ofEntries(
                Map.entry("computeId", "string"),
                Map.entry("description", "string"),
                Map.entry("displayName", "string"),
                Map.entry("environmentId", "string"),
                Map.entry("environmentVariables", AutoMLJobArgs.builder()
                    .string("string")
                    .build()),
                Map.entry("experimentName", "string"),
                Map.entry("identity", Map.of("identityType", "AMLToken")),
                Map.entry("isArchived", false),
                Map.entry("jobType", "AutoML"),
                Map.entry("outputs", Map.of("string", Map.ofEntries(
                    Map.entry("description", "string"),
                    Map.entry("jobOutputType", "uri_file"),
                    Map.entry("mode", "ReadWriteMount"),
                    Map.entry("uri", "string")
                ))),
                Map.entry("properties", AutoMLJobArgs.builder()
                    .string("string")
                    .build()),
                Map.entry("resources", Map.ofEntries(
                    Map.entry("instanceCount", 1),
                    Map.entry("instanceType", "string"),
                    Map.entry("properties", AutoMLJobArgs.builder()
                        .string(%!v(PANIC=Format method: runtime error: invalid memory address or nil pointer dereference))
                        .build())
                )),
                Map.entry("services", Map.of("string", Map.ofEntries(
                    Map.entry("endpoint", "string"),
                    Map.entry("jobServiceType", "string"),
                    Map.entry("port", 1),
                    Map.entry("properties", AutoMLJobArgs.builder()
                        .string("string")
                        .build())
                ))),
                Map.entry("tags", AutoMLJobArgs.builder()
                    .string("string")
                    .build()),
                Map.entry("taskDetails", Map.ofEntries(
                    Map.entry("limitSettings", Map.of("maxTrials", 2)),
                    Map.entry("modelSettings", Map.of("validationCropSize", 2)),
                    Map.entry("searchSpace", Map.of("validationCropSize", "choice(2, 360)")),
                    Map.entry("targetColumnName", "string"),
                    Map.entry("taskType", "ImageClassification"),
                    Map.entry("trainingData", Map.ofEntries(
                        Map.entry("jobInputType", "mltable"),
                        Map.entry("uri", "string")
                    ))
                ))
            ))
            .resourceGroupName("test-rg")
            .workspaceName("my-aml-workspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const job = new azure_native.machinelearningservices.Job("job", {
    id: "string",
    jobBaseProperties: {
        computeId: "string",
        description: "string",
        displayName: "string",
        environmentId: "string",
        environmentVariables: {
            string: "string",
        },
        experimentName: "string",
        identity: {
            identityType: "AMLToken",
        },
        isArchived: false,
        jobType: "AutoML",
        outputs: {
            string: {
                description: "string",
                jobOutputType: "uri_file",
                mode: "ReadWriteMount",
                uri: "string",
            },
        },
        properties: {
            string: "string",
        },
        resources: {
            instanceCount: 1,
            instanceType: "string",
            properties: {
                string: {
                    "9bec0ab0-c62f-4fa9-a97c-7b24bbcc90ad": undefined,
                },
            },
        },
        services: {
            string: {
                endpoint: "string",
                jobServiceType: "string",
                port: 1,
                properties: {
                    string: "string",
                },
            },
        },
        tags: {
            string: "string",
        },
        taskDetails: {
            limitSettings: {
                maxTrials: 2,
            },
            modelSettings: {
                validationCropSize: 2,
            },
            searchSpace: [{
                validationCropSize: "choice(2, 360)",
            }],
            targetColumnName: "string",
            taskType: "ImageClassification",
            trainingData: {
                jobInputType: "mltable",
                uri: "string",
            },
        },
    },
    resourceGroupName: "test-rg",
    workspaceName: "my-aml-workspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

job = azure_native.machinelearningservices.Job("job",
    id="string",
    job_base_properties=azure_native.machinelearningservices.AutoMLJobArgs(
        compute_id="string",
        description="string",
        display_name="string",
        environment_id="string",
        environment_variables={
            "string": "string",
        },
        experiment_name="string",
        identity=azure_native.machinelearningservices.AmlTokenArgs(
            identity_type="AMLToken",
        ),
        is_archived=False,
        job_type="AutoML",
        outputs={
            "string": azure_native.machinelearningservices.UriFileJobOutputArgs(
                description="string",
                job_output_type="uri_file",
                mode="ReadWriteMount",
                uri="string",
            ),
        },
        properties={
            "string": "string",
        },
        resources=azure_native.machinelearningservices.JobResourceConfigurationArgs(
            instance_count=1,
            instance_type="string",
            properties={
                "string": {
                    "9bec0ab0-c62f-4fa9-a97c-7b24bbcc90ad": None,
                },
            },
        ),
        services={
            "string": azure_native.machinelearningservices.JobServiceArgs(
                endpoint="string",
                job_service_type="string",
                port=1,
                properties={
                    "string": "string",
                },
            ),
        },
        tags={
            "string": "string",
        },
        task_details=azure_native.machinelearningservices.ImageClassificationArgs(
            limit_settings=azure_native.machinelearningservices.ImageLimitSettingsArgs(
                max_trials=2,
            ),
            model_settings=azure_native.machinelearningservices.ImageModelSettingsClassificationArgs(
                validation_crop_size=2,
            ),
            search_space=[azure_native.machinelearningservices.ImageModelDistributionSettingsClassificationArgs(
                validation_crop_size="choice(2, 360)",
            )],
            target_column_name="string",
            task_type="ImageClassification",
            training_data=azure_native.machinelearningservices.MLTableJobInputArgs(
                job_input_type="mltable",
                uri="string",
            ),
        ),
    ),
    resource_group_name="test-rg",
    workspace_name="my-aml-workspace")

```

```yaml
resources:
  job:
    type: azure-native:machinelearningservices:Job
    properties:
      id: string
      jobBaseProperties:
        computeId: string
        description: string
        displayName: string
        environmentId: string
        environmentVariables:
          string: string
        experimentName: string
        identity:
          identityType: AMLToken
        isArchived: false
        jobType: AutoML
        outputs:
          string:
            description: string
            jobOutputType: uri_file
            mode: ReadWriteMount
            uri: string
        properties:
          string: string
        resources:
          instanceCount: 1
          instanceType: string
          properties:
            string:
              9bec0ab0-c62f-4fa9-a97c-7b24bbcc90ad: null
        services:
          string:
            endpoint: string
            jobServiceType: string
            port: 1
            properties:
              string: string
        tags:
          string: string
        taskDetails:
          limitSettings:
            maxTrials: 2
          modelSettings:
            validationCropSize: 2
          searchSpace:
            - validationCropSize: choice(2, 360)
          targetColumnName: string
          taskType: ImageClassification
          trainingData:
            jobInputType: mltable
            uri: string
      resourceGroupName: test-rg
      workspaceName: my-aml-workspace

```

{{% /example %}}
{{% example %}}
### CreateOrUpdate Command Job.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var job = new AzureNative.MachineLearningServices.Job("job", new()
    {
        Id = "string",
        JobBaseProperties = new AzureNative.MachineLearningServices.Inputs.CommandJobArgs
        {
            CodeId = "string",
            Command = "string",
            ComputeId = "string",
            Description = "string",
            DisplayName = "string",
            Distribution = new AzureNative.MachineLearningServices.Inputs.TensorFlowArgs
            {
                DistributionType = "TensorFlow",
                ParameterServerCount = 1,
                WorkerCount = 1,
            },
            EnvironmentId = "string",
            EnvironmentVariables = 
            {
                { "string", "string" },
            },
            ExperimentName = "string",
            Identity = new AzureNative.MachineLearningServices.Inputs.AmlTokenArgs
            {
                IdentityType = "AMLToken",
            },
            Inputs = 
            {
                { "string", new AzureNative.MachineLearningServices.Inputs.LiteralJobInputArgs
                {
                    Description = "string",
                    JobInputType = "literal",
                    Value = "string",
                } },
            },
            JobType = "Command",
            Limits = new AzureNative.MachineLearningServices.Inputs.CommandJobLimitsArgs
            {
                JobLimitsType = "Command",
                Timeout = "PT5M",
            },
            Outputs = 
            {
                { "string", new AzureNative.MachineLearningServices.Inputs.UriFileJobOutputArgs
                {
                    Description = "string",
                    JobOutputType = "uri_file",
                    Mode = "ReadWriteMount",
                    Uri = "string",
                } },
            },
            Properties = 
            {
                { "string", "string" },
            },
            Resources = new AzureNative.MachineLearningServices.Inputs.JobResourceConfigurationArgs
            {
                InstanceCount = 1,
                InstanceType = "string",
                Properties = 
                {
                    { "string", 
                    {
                        { "e6b6493e-7d5e-4db3-be1e-306ec641327e", null },
                    } },
                },
            },
            Services = 
            {
                { "string", new AzureNative.MachineLearningServices.Inputs.JobServiceArgs
                {
                    Endpoint = "string",
                    JobServiceType = "string",
                    Port = 1,
                    Properties = 
                    {
                        { "string", "string" },
                    },
                } },
            },
            Tags = 
            {
                { "string", "string" },
            },
        },
        ResourceGroupName = "test-rg",
        WorkspaceName = "my-aml-workspace",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.machinelearningservices.Job;
import com.pulumi.azurenative.machinelearningservices.JobArgs;
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
        var job = new Job("job", JobArgs.builder()        
            .id("string")
            .jobBaseProperties(Map.ofEntries(
                Map.entry("codeId", "string"),
                Map.entry("command", "string"),
                Map.entry("computeId", "string"),
                Map.entry("description", "string"),
                Map.entry("displayName", "string"),
                Map.entry("distribution", Map.ofEntries(
                    Map.entry("distributionType", "TensorFlow"),
                    Map.entry("parameterServerCount", 1),
                    Map.entry("workerCount", 1)
                )),
                Map.entry("environmentId", "string"),
                Map.entry("environmentVariables", AutoMLJobArgs.builder()
                    .string("string")
                    .build()),
                Map.entry("experimentName", "string"),
                Map.entry("identity", Map.of("identityType", "AMLToken")),
                Map.entry("inputs", Map.of("string", Map.ofEntries(
                    Map.entry("description", "string"),
                    Map.entry("jobInputType", "literal"),
                    Map.entry("value", "string")
                ))),
                Map.entry("jobType", "Command"),
                Map.entry("limits", Map.ofEntries(
                    Map.entry("jobLimitsType", "Command"),
                    Map.entry("timeout", "PT5M")
                )),
                Map.entry("outputs", Map.of("string", Map.ofEntries(
                    Map.entry("description", "string"),
                    Map.entry("jobOutputType", "uri_file"),
                    Map.entry("mode", "ReadWriteMount"),
                    Map.entry("uri", "string")
                ))),
                Map.entry("properties", AutoMLJobArgs.builder()
                    .string("string")
                    .build()),
                Map.entry("resources", Map.ofEntries(
                    Map.entry("instanceCount", 1),
                    Map.entry("instanceType", "string"),
                    Map.entry("properties", AutoMLJobArgs.builder()
                        .string(%!v(PANIC=Format method: runtime error: invalid memory address or nil pointer dereference))
                        .build())
                )),
                Map.entry("services", Map.of("string", Map.ofEntries(
                    Map.entry("endpoint", "string"),
                    Map.entry("jobServiceType", "string"),
                    Map.entry("port", 1),
                    Map.entry("properties", AutoMLJobArgs.builder()
                        .string("string")
                        .build())
                ))),
                Map.entry("tags", AutoMLJobArgs.builder()
                    .string("string")
                    .build())
            ))
            .resourceGroupName("test-rg")
            .workspaceName("my-aml-workspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const job = new azure_native.machinelearningservices.Job("job", {
    id: "string",
    jobBaseProperties: {
        codeId: "string",
        command: "string",
        computeId: "string",
        description: "string",
        displayName: "string",
        distribution: {
            distributionType: "TensorFlow",
            parameterServerCount: 1,
            workerCount: 1,
        },
        environmentId: "string",
        environmentVariables: {
            string: "string",
        },
        experimentName: "string",
        identity: {
            identityType: "AMLToken",
        },
        inputs: {
            string: {
                description: "string",
                jobInputType: "literal",
                value: "string",
            },
        },
        jobType: "Command",
        limits: {
            jobLimitsType: "Command",
            timeout: "PT5M",
        },
        outputs: {
            string: {
                description: "string",
                jobOutputType: "uri_file",
                mode: "ReadWriteMount",
                uri: "string",
            },
        },
        properties: {
            string: "string",
        },
        resources: {
            instanceCount: 1,
            instanceType: "string",
            properties: {
                string: {
                    "e6b6493e-7d5e-4db3-be1e-306ec641327e": undefined,
                },
            },
        },
        services: {
            string: {
                endpoint: "string",
                jobServiceType: "string",
                port: 1,
                properties: {
                    string: "string",
                },
            },
        },
        tags: {
            string: "string",
        },
    },
    resourceGroupName: "test-rg",
    workspaceName: "my-aml-workspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

job = azure_native.machinelearningservices.Job("job",
    id="string",
    job_base_properties=azure_native.machinelearningservices.CommandJobArgs(
        code_id="string",
        command="string",
        compute_id="string",
        description="string",
        display_name="string",
        distribution=azure_native.machinelearningservices.TensorFlowArgs(
            distribution_type="TensorFlow",
            parameter_server_count=1,
            worker_count=1,
        ),
        environment_id="string",
        environment_variables={
            "string": "string",
        },
        experiment_name="string",
        identity=azure_native.machinelearningservices.AmlTokenArgs(
            identity_type="AMLToken",
        ),
        inputs={
            "string": azure_native.machinelearningservices.LiteralJobInputArgs(
                description="string",
                job_input_type="literal",
                value="string",
            ),
        },
        job_type="Command",
        limits=azure_native.machinelearningservices.CommandJobLimitsArgs(
            job_limits_type="Command",
            timeout="PT5M",
        ),
        outputs={
            "string": azure_native.machinelearningservices.UriFileJobOutputArgs(
                description="string",
                job_output_type="uri_file",
                mode="ReadWriteMount",
                uri="string",
            ),
        },
        properties={
            "string": "string",
        },
        resources=azure_native.machinelearningservices.JobResourceConfigurationArgs(
            instance_count=1,
            instance_type="string",
            properties={
                "string": {
                    "e6b6493e-7d5e-4db3-be1e-306ec641327e": None,
                },
            },
        ),
        services={
            "string": azure_native.machinelearningservices.JobServiceArgs(
                endpoint="string",
                job_service_type="string",
                port=1,
                properties={
                    "string": "string",
                },
            ),
        },
        tags={
            "string": "string",
        },
    ),
    resource_group_name="test-rg",
    workspace_name="my-aml-workspace")

```

```yaml
resources:
  job:
    type: azure-native:machinelearningservices:Job
    properties:
      id: string
      jobBaseProperties:
        codeId: string
        command: string
        computeId: string
        description: string
        displayName: string
        distribution:
          distributionType: TensorFlow
          parameterServerCount: 1
          workerCount: 1
        environmentId: string
        environmentVariables:
          string: string
        experimentName: string
        identity:
          identityType: AMLToken
        inputs:
          string:
            description: string
            jobInputType: literal
            value: string
        jobType: Command
        limits:
          jobLimitsType: Command
          timeout: PT5M
        outputs:
          string:
            description: string
            jobOutputType: uri_file
            mode: ReadWriteMount
            uri: string
        properties:
          string: string
        resources:
          instanceCount: 1
          instanceType: string
          properties:
            string:
              e6b6493e-7d5e-4db3-be1e-306ec641327e: null
        services:
          string:
            endpoint: string
            jobServiceType: string
            port: 1
            properties:
              string: string
        tags:
          string: string
      resourceGroupName: test-rg
      workspaceName: my-aml-workspace

```

{{% /example %}}
{{% example %}}
### CreateOrUpdate Pipeline Job.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var job = new AzureNative.MachineLearningServices.Job("job", new()
    {
        Id = "string",
        JobBaseProperties = new AzureNative.MachineLearningServices.Inputs.PipelineJobArgs
        {
            ComputeId = "string",
            Description = "string",
            DisplayName = "string",
            ExperimentName = "string",
            Inputs = 
            {
                { "string", new AzureNative.MachineLearningServices.Inputs.LiteralJobInputArgs
                {
                    Description = "string",
                    JobInputType = "literal",
                    Value = "string",
                } },
            },
            JobType = "Pipeline",
            Outputs = 
            {
                { "string", new AzureNative.MachineLearningServices.Inputs.UriFileJobOutputArgs
                {
                    Description = "string",
                    JobOutputType = "uri_file",
                    Mode = "Upload",
                    Uri = "string",
                } },
            },
            Properties = 
            {
                { "string", "string" },
            },
            Services = 
            {
                { "string", new AzureNative.MachineLearningServices.Inputs.JobServiceArgs
                {
                    Endpoint = "string",
                    JobServiceType = "string",
                    Port = 1,
                    Properties = 
                    {
                        { "string", "string" },
                    },
                } },
            },
            Settings = null,
            Tags = 
            {
                { "string", "string" },
            },
        },
        ResourceGroupName = "test-rg",
        WorkspaceName = "my-aml-workspace",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.machinelearningservices.Job;
import com.pulumi.azurenative.machinelearningservices.JobArgs;
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
        var job = new Job("job", JobArgs.builder()        
            .id("string")
            .jobBaseProperties(Map.ofEntries(
                Map.entry("computeId", "string"),
                Map.entry("description", "string"),
                Map.entry("displayName", "string"),
                Map.entry("experimentName", "string"),
                Map.entry("inputs", Map.of("string", Map.ofEntries(
                    Map.entry("description", "string"),
                    Map.entry("jobInputType", "literal"),
                    Map.entry("value", "string")
                ))),
                Map.entry("jobType", "Pipeline"),
                Map.entry("outputs", Map.of("string", Map.ofEntries(
                    Map.entry("description", "string"),
                    Map.entry("jobOutputType", "uri_file"),
                    Map.entry("mode", "Upload"),
                    Map.entry("uri", "string")
                ))),
                Map.entry("properties", AutoMLJobArgs.builder()
                    .string("string")
                    .build()),
                Map.entry("services", Map.of("string", Map.ofEntries(
                    Map.entry("endpoint", "string"),
                    Map.entry("jobServiceType", "string"),
                    Map.entry("port", 1),
                    Map.entry("properties", AutoMLJobArgs.builder()
                        .string("string")
                        .build())
                ))),
                Map.entry("settings", ),
                Map.entry("tags", AutoMLJobArgs.builder()
                    .string("string")
                    .build())
            ))
            .resourceGroupName("test-rg")
            .workspaceName("my-aml-workspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const job = new azure_native.machinelearningservices.Job("job", {
    id: "string",
    jobBaseProperties: {
        computeId: "string",
        description: "string",
        displayName: "string",
        experimentName: "string",
        inputs: {
            string: {
                description: "string",
                jobInputType: "literal",
                value: "string",
            },
        },
        jobType: "Pipeline",
        outputs: {
            string: {
                description: "string",
                jobOutputType: "uri_file",
                mode: "Upload",
                uri: "string",
            },
        },
        properties: {
            string: "string",
        },
        services: {
            string: {
                endpoint: "string",
                jobServiceType: "string",
                port: 1,
                properties: {
                    string: "string",
                },
            },
        },
        settings: {},
        tags: {
            string: "string",
        },
    },
    resourceGroupName: "test-rg",
    workspaceName: "my-aml-workspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

job = azure_native.machinelearningservices.Job("job",
    id="string",
    job_base_properties=azure_native.machinelearningservices.PipelineJobArgs(
        compute_id="string",
        description="string",
        display_name="string",
        experiment_name="string",
        inputs={
            "string": azure_native.machinelearningservices.LiteralJobInputArgs(
                description="string",
                job_input_type="literal",
                value="string",
            ),
        },
        job_type="Pipeline",
        outputs={
            "string": azure_native.machinelearningservices.UriFileJobOutputArgs(
                description="string",
                job_output_type="uri_file",
                mode="Upload",
                uri="string",
            ),
        },
        properties={
            "string": "string",
        },
        services={
            "string": azure_native.machinelearningservices.JobServiceArgs(
                endpoint="string",
                job_service_type="string",
                port=1,
                properties={
                    "string": "string",
                },
            ),
        },
        settings={},
        tags={
            "string": "string",
        },
    ),
    resource_group_name="test-rg",
    workspace_name="my-aml-workspace")

```

```yaml
resources:
  job:
    type: azure-native:machinelearningservices:Job
    properties:
      id: string
      jobBaseProperties:
        computeId: string
        description: string
        displayName: string
        experimentName: string
        inputs:
          string:
            description: string
            jobInputType: literal
            value: string
        jobType: Pipeline
        outputs:
          string:
            description: string
            jobOutputType: uri_file
            mode: Upload
            uri: string
        properties:
          string: string
        services:
          string:
            endpoint: string
            jobServiceType: string
            port: 1
            properties:
              string: string
        settings: {}
        tags:
          string: string
      resourceGroupName: test-rg
      workspaceName: my-aml-workspace

```

{{% /example %}}
{{% example %}}
### CreateOrUpdate Sweep Job.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var job = new AzureNative.MachineLearningServices.Job("job", new()
    {
        Id = "string",
        JobBaseProperties = new AzureNative.MachineLearningServices.Inputs.SweepJobArgs
        {
            ComputeId = "string",
            Description = "string",
            DisplayName = "string",
            EarlyTermination = new AzureNative.MachineLearningServices.Inputs.MedianStoppingPolicyArgs
            {
                DelayEvaluation = 1,
                EvaluationInterval = 1,
                PolicyType = "MedianStopping",
            },
            ExperimentName = "string",
            JobType = "Sweep",
            Limits = new AzureNative.MachineLearningServices.Inputs.SweepJobLimitsArgs
            {
                JobLimitsType = "Sweep",
                MaxConcurrentTrials = 1,
                MaxTotalTrials = 1,
                TrialTimeout = "PT1S",
            },
            Objective = new AzureNative.MachineLearningServices.Inputs.ObjectiveArgs
            {
                Goal = "Minimize",
                PrimaryMetric = "string",
            },
            Properties = 
            {
                { "string", "string" },
            },
            SamplingAlgorithm = new AzureNative.MachineLearningServices.Inputs.GridSamplingAlgorithmArgs
            {
                SamplingAlgorithmType = "Grid",
            },
            SearchSpace = 
            {
                { "string", null },
            },
            Services = 
            {
                { "string", new AzureNative.MachineLearningServices.Inputs.JobServiceArgs
                {
                    Endpoint = "string",
                    JobServiceType = "string",
                    Port = 1,
                    Properties = 
                    {
                        { "string", "string" },
                    },
                } },
            },
            Tags = 
            {
                { "string", "string" },
            },
            Trial = new AzureNative.MachineLearningServices.Inputs.TrialComponentArgs
            {
                CodeId = "string",
                Command = "string",
                Distribution = new AzureNative.MachineLearningServices.Inputs.MpiArgs
                {
                    DistributionType = "Mpi",
                    ProcessCountPerInstance = 1,
                },
                EnvironmentId = "string",
                EnvironmentVariables = 
                {
                    { "string", "string" },
                },
                Resources = new AzureNative.MachineLearningServices.Inputs.JobResourceConfigurationArgs
                {
                    InstanceCount = 1,
                    InstanceType = "string",
                    Properties = 
                    {
                        { "string", 
                        {
                            { "e6b6493e-7d5e-4db3-be1e-306ec641327e", null },
                        } },
                    },
                },
            },
        },
        ResourceGroupName = "test-rg",
        WorkspaceName = "my-aml-workspace",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.machinelearningservices.Job;
import com.pulumi.azurenative.machinelearningservices.JobArgs;
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
        var job = new Job("job", JobArgs.builder()        
            .id("string")
            .jobBaseProperties(Map.ofEntries(
                Map.entry("computeId", "string"),
                Map.entry("description", "string"),
                Map.entry("displayName", "string"),
                Map.entry("earlyTermination", Map.ofEntries(
                    Map.entry("delayEvaluation", 1),
                    Map.entry("evaluationInterval", 1),
                    Map.entry("policyType", "MedianStopping")
                )),
                Map.entry("experimentName", "string"),
                Map.entry("jobType", "Sweep"),
                Map.entry("limits", Map.ofEntries(
                    Map.entry("jobLimitsType", "Sweep"),
                    Map.entry("maxConcurrentTrials", 1),
                    Map.entry("maxTotalTrials", 1),
                    Map.entry("trialTimeout", "PT1S")
                )),
                Map.entry("objective", Map.ofEntries(
                    Map.entry("goal", "Minimize"),
                    Map.entry("primaryMetric", "string")
                )),
                Map.entry("properties", AutoMLJobArgs.builder()
                    .string("string")
                    .build()),
                Map.entry("samplingAlgorithm", Map.of("samplingAlgorithmType", "Grid")),
                Map.entry("searchSpace", AutoMLJobArgs.builder()
                    .string()
                    .build()),
                Map.entry("services", Map.of("string", Map.ofEntries(
                    Map.entry("endpoint", "string"),
                    Map.entry("jobServiceType", "string"),
                    Map.entry("port", 1),
                    Map.entry("properties", AutoMLJobArgs.builder()
                        .string("string")
                        .build())
                ))),
                Map.entry("tags", AutoMLJobArgs.builder()
                    .string("string")
                    .build()),
                Map.entry("trial", Map.ofEntries(
                    Map.entry("codeId", "string"),
                    Map.entry("command", "string"),
                    Map.entry("distribution", Map.ofEntries(
                        Map.entry("distributionType", "Mpi"),
                        Map.entry("processCountPerInstance", 1)
                    )),
                    Map.entry("environmentId", "string"),
                    Map.entry("environmentVariables", AutoMLJobArgs.builder()
                        .string("string")
                        .build()),
                    Map.entry("resources", Map.ofEntries(
                        Map.entry("instanceCount", 1),
                        Map.entry("instanceType", "string"),
                        Map.entry("properties", AutoMLJobArgs.builder()
                            .string(%!v(PANIC=Format method: runtime error: invalid memory address or nil pointer dereference))
                            .build())
                    ))
                ))
            ))
            .resourceGroupName("test-rg")
            .workspaceName("my-aml-workspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const job = new azure_native.machinelearningservices.Job("job", {
    id: "string",
    jobBaseProperties: {
        computeId: "string",
        description: "string",
        displayName: "string",
        earlyTermination: {
            delayEvaluation: 1,
            evaluationInterval: 1,
            policyType: "MedianStopping",
        },
        experimentName: "string",
        jobType: "Sweep",
        limits: {
            jobLimitsType: "Sweep",
            maxConcurrentTrials: 1,
            maxTotalTrials: 1,
            trialTimeout: "PT1S",
        },
        objective: {
            goal: "Minimize",
            primaryMetric: "string",
        },
        properties: {
            string: "string",
        },
        samplingAlgorithm: {
            samplingAlgorithmType: "Grid",
        },
        searchSpace: {
            string: {},
        },
        services: {
            string: {
                endpoint: "string",
                jobServiceType: "string",
                port: 1,
                properties: {
                    string: "string",
                },
            },
        },
        tags: {
            string: "string",
        },
        trial: {
            codeId: "string",
            command: "string",
            distribution: {
                distributionType: "Mpi",
                processCountPerInstance: 1,
            },
            environmentId: "string",
            environmentVariables: {
                string: "string",
            },
            resources: {
                instanceCount: 1,
                instanceType: "string",
                properties: {
                    string: {
                        "e6b6493e-7d5e-4db3-be1e-306ec641327e": undefined,
                    },
                },
            },
        },
    },
    resourceGroupName: "test-rg",
    workspaceName: "my-aml-workspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

job = azure_native.machinelearningservices.Job("job",
    id="string",
    job_base_properties=azure_native.machinelearningservices.SweepJobArgs(
        compute_id="string",
        description="string",
        display_name="string",
        early_termination=azure_native.machinelearningservices.MedianStoppingPolicyArgs(
            delay_evaluation=1,
            evaluation_interval=1,
            policy_type="MedianStopping",
        ),
        experiment_name="string",
        job_type="Sweep",
        limits=azure_native.machinelearningservices.SweepJobLimitsArgs(
            job_limits_type="Sweep",
            max_concurrent_trials=1,
            max_total_trials=1,
            trial_timeout="PT1S",
        ),
        objective=azure_native.machinelearningservices.ObjectiveArgs(
            goal="Minimize",
            primary_metric="string",
        ),
        properties={
            "string": "string",
        },
        sampling_algorithm=azure_native.machinelearningservices.GridSamplingAlgorithmArgs(
            sampling_algorithm_type="Grid",
        ),
        search_space={
            "string": {},
        },
        services={
            "string": azure_native.machinelearningservices.JobServiceArgs(
                endpoint="string",
                job_service_type="string",
                port=1,
                properties={
                    "string": "string",
                },
            ),
        },
        tags={
            "string": "string",
        },
        trial=azure_native.machinelearningservices.TrialComponentArgs(
            code_id="string",
            command="string",
            distribution=azure_native.machinelearningservices.MpiArgs(
                distribution_type="Mpi",
                process_count_per_instance=1,
            ),
            environment_id="string",
            environment_variables={
                "string": "string",
            },
            resources=azure_native.machinelearningservices.JobResourceConfigurationArgs(
                instance_count=1,
                instance_type="string",
                properties={
                    "string": {
                        "e6b6493e-7d5e-4db3-be1e-306ec641327e": None,
                    },
                },
            ),
        ),
    ),
    resource_group_name="test-rg",
    workspace_name="my-aml-workspace")

```

```yaml
resources:
  job:
    type: azure-native:machinelearningservices:Job
    properties:
      id: string
      jobBaseProperties:
        computeId: string
        description: string
        displayName: string
        earlyTermination:
          delayEvaluation: 1
          evaluationInterval: 1
          policyType: MedianStopping
        experimentName: string
        jobType: Sweep
        limits:
          jobLimitsType: Sweep
          maxConcurrentTrials: 1
          maxTotalTrials: 1
          trialTimeout: PT1S
        objective:
          goal: Minimize
          primaryMetric: string
        properties:
          string: string
        samplingAlgorithm:
          samplingAlgorithmType: Grid
        searchSpace:
          string: {}
        services:
          string:
            endpoint: string
            jobServiceType: string
            port: 1
            properties:
              string: string
        tags:
          string: string
        trial:
          codeId: string
          command: string
          distribution:
            distributionType: Mpi
            processCountPerInstance: 1
          environmentId: string
          environmentVariables:
            string: string
          resources:
            instanceCount: 1
            instanceType: string
            properties:
              string:
                e6b6493e-7d5e-4db3-be1e-306ec641327e: null
      resourceGroupName: test-rg
      workspaceName: my-aml-workspace

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:machinelearningservices:Job string string 
```
