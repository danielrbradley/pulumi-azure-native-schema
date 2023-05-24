The task that has the ARM resource and task properties. 
The task will have all information to schedule a run against it.
API Version: 2019-04-01.
Previous API Version: 2019-06-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Tasks_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var task = new AzureNative.ContainerRegistry.Task("task", new()
    {
        AgentConfiguration = new AzureNative.ContainerRegistry.Inputs.AgentPropertiesArgs
        {
            Cpu = 2,
        },
        Identity = new AzureNative.ContainerRegistry.Inputs.IdentityPropertiesArgs
        {
            Type = AzureNative.ContainerRegistry.ResourceIdentityType.SystemAssigned,
        },
        Location = "eastus",
        Platform = new AzureNative.ContainerRegistry.Inputs.PlatformPropertiesArgs
        {
            Architecture = "amd64",
            Os = "Linux",
        },
        RegistryName = "myRegistry",
        ResourceGroupName = "myResourceGroup",
        Status = "Enabled",
        Step = new AzureNative.ContainerRegistry.Inputs.DockerBuildStepArgs
        {
            Arguments = new[]
            {
                new AzureNative.ContainerRegistry.Inputs.ArgumentArgs
                {
                    IsSecret = false,
                    Name = "mytestargument",
                    Value = "mytestvalue",
                },
                new AzureNative.ContainerRegistry.Inputs.ArgumentArgs
                {
                    IsSecret = true,
                    Name = "mysecrettestargument",
                    Value = "mysecrettestvalue",
                },
            },
            ContextPath = "src",
            DockerFilePath = "src/DockerFile",
            ImageNames = new[]
            {
                "azurerest:testtag",
            },
            IsPushEnabled = true,
            NoCache = false,
            Type = "Docker",
        },
        Tags = 
        {
            { "testkey", "value" },
        },
        TaskName = "mytTask",
        Trigger = new AzureNative.ContainerRegistry.Inputs.TriggerPropertiesArgs
        {
            BaseImageTrigger = new AzureNative.ContainerRegistry.Inputs.BaseImageTriggerArgs
            {
                BaseImageTriggerType = "Runtime",
                Name = "myBaseImageTrigger",
            },
            SourceTriggers = new[]
            {
                new AzureNative.ContainerRegistry.Inputs.SourceTriggerArgs
                {
                    Name = "mySourceTrigger",
                    SourceRepository = new AzureNative.ContainerRegistry.Inputs.SourcePropertiesArgs
                    {
                        Branch = "master",
                        RepositoryUrl = "https://github.com/Azure/azure-rest-api-specs",
                        SourceControlAuthProperties = new AzureNative.ContainerRegistry.Inputs.AuthInfoArgs
                        {
                            Token = "xxxxx",
                            TokenType = "PAT",
                        },
                        SourceControlType = "Github",
                    },
                    SourceTriggerEvents = new[]
                    {
                        "commit",
                    },
                },
            },
            TimerTriggers = new[]
            {
                new AzureNative.ContainerRegistry.Inputs.TimerTriggerArgs
                {
                    Name = "myTimerTrigger",
                    Schedule = "30 9 * * 1-5",
                },
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
import com.pulumi.azurenative.containerregistry.Task;
import com.pulumi.azurenative.containerregistry.TaskArgs;
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
        var task = new Task("task", TaskArgs.builder()        
            .agentConfiguration(Map.of("cpu", 2))
            .identity(Map.of("type", "SystemAssigned"))
            .location("eastus")
            .platform(Map.ofEntries(
                Map.entry("architecture", "amd64"),
                Map.entry("os", "Linux")
            ))
            .registryName("myRegistry")
            .resourceGroupName("myResourceGroup")
            .status("Enabled")
            .step(Map.ofEntries(
                Map.entry("arguments",                 
                    Map.ofEntries(
                        Map.entry("isSecret", false),
                        Map.entry("name", "mytestargument"),
                        Map.entry("value", "mytestvalue")
                    ),
                    Map.ofEntries(
                        Map.entry("isSecret", true),
                        Map.entry("name", "mysecrettestargument"),
                        Map.entry("value", "mysecrettestvalue")
                    )),
                Map.entry("contextPath", "src"),
                Map.entry("dockerFilePath", "src/DockerFile"),
                Map.entry("imageNames", "azurerest:testtag"),
                Map.entry("isPushEnabled", true),
                Map.entry("noCache", false),
                Map.entry("type", "Docker")
            ))
            .tags(Map.of("testkey", "value"))
            .taskName("mytTask")
            .trigger(Map.ofEntries(
                Map.entry("baseImageTrigger", Map.ofEntries(
                    Map.entry("baseImageTriggerType", "Runtime"),
                    Map.entry("name", "myBaseImageTrigger")
                )),
                Map.entry("sourceTriggers", Map.ofEntries(
                    Map.entry("name", "mySourceTrigger"),
                    Map.entry("sourceRepository", Map.ofEntries(
                        Map.entry("branch", "master"),
                        Map.entry("repositoryUrl", "https://github.com/Azure/azure-rest-api-specs"),
                        Map.entry("sourceControlAuthProperties", Map.ofEntries(
                            Map.entry("token", "xxxxx"),
                            Map.entry("tokenType", "PAT")
                        )),
                        Map.entry("sourceControlType", "Github")
                    )),
                    Map.entry("sourceTriggerEvents", "commit")
                )),
                Map.entry("timerTriggers", Map.ofEntries(
                    Map.entry("name", "myTimerTrigger"),
                    Map.entry("schedule", "30 9 * * 1-5")
                ))
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const task = new azure_native.containerregistry.Task("task", {
    agentConfiguration: {
        cpu: 2,
    },
    identity: {
        type: azure_native.containerregistry.ResourceIdentityType.SystemAssigned,
    },
    location: "eastus",
    platform: {
        architecture: "amd64",
        os: "Linux",
    },
    registryName: "myRegistry",
    resourceGroupName: "myResourceGroup",
    status: "Enabled",
    step: {
        arguments: [
            {
                isSecret: false,
                name: "mytestargument",
                value: "mytestvalue",
            },
            {
                isSecret: true,
                name: "mysecrettestargument",
                value: "mysecrettestvalue",
            },
        ],
        contextPath: "src",
        dockerFilePath: "src/DockerFile",
        imageNames: ["azurerest:testtag"],
        isPushEnabled: true,
        noCache: false,
        type: "Docker",
    },
    tags: {
        testkey: "value",
    },
    taskName: "mytTask",
    trigger: {
        baseImageTrigger: {
            baseImageTriggerType: "Runtime",
            name: "myBaseImageTrigger",
        },
        sourceTriggers: [{
            name: "mySourceTrigger",
            sourceRepository: {
                branch: "master",
                repositoryUrl: "https://github.com/Azure/azure-rest-api-specs",
                sourceControlAuthProperties: {
                    token: "xxxxx",
                    tokenType: "PAT",
                },
                sourceControlType: "Github",
            },
            sourceTriggerEvents: ["commit"],
        }],
        timerTriggers: [{
            name: "myTimerTrigger",
            schedule: "30 9 * * 1-5",
        }],
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

task = azure_native.containerregistry.Task("task",
    agent_configuration=azure_native.containerregistry.AgentPropertiesArgs(
        cpu=2,
    ),
    identity=azure_native.containerregistry.IdentityPropertiesArgs(
        type=azure_native.containerregistry.ResourceIdentityType.SYSTEM_ASSIGNED,
    ),
    location="eastus",
    platform=azure_native.containerregistry.PlatformPropertiesArgs(
        architecture="amd64",
        os="Linux",
    ),
    registry_name="myRegistry",
    resource_group_name="myResourceGroup",
    status="Enabled",
    step=azure_native.containerregistry.DockerBuildStepArgs(
        arguments=[
            azure_native.containerregistry.ArgumentArgs(
                is_secret=False,
                name="mytestargument",
                value="mytestvalue",
            ),
            azure_native.containerregistry.ArgumentArgs(
                is_secret=True,
                name="mysecrettestargument",
                value="mysecrettestvalue",
            ),
        ],
        context_path="src",
        docker_file_path="src/DockerFile",
        image_names=["azurerest:testtag"],
        is_push_enabled=True,
        no_cache=False,
        type="Docker",
    ),
    tags={
        "testkey": "value",
    },
    task_name="mytTask",
    trigger=azure_native.containerregistry.TriggerPropertiesResponseArgs(
        base_image_trigger=azure_native.containerregistry.BaseImageTriggerArgs(
            base_image_trigger_type="Runtime",
            name="myBaseImageTrigger",
        ),
        source_triggers=[{
            "name": "mySourceTrigger",
            "sourceRepository": {
                "branch": "master",
                "repositoryUrl": "https://github.com/Azure/azure-rest-api-specs",
                "sourceControlAuthProperties": azure_native.containerregistry.AuthInfoArgs(
                    token="xxxxx",
                    token_type="PAT",
                ),
                "sourceControlType": "Github",
            },
            "sourceTriggerEvents": ["commit"],
        }],
        timer_triggers=[azure_native.containerregistry.TimerTriggerArgs(
            name="myTimerTrigger",
            schedule="30 9 * * 1-5",
        )],
    ))

```

```yaml
resources:
  task:
    type: azure-native:containerregistry:Task
    properties:
      agentConfiguration:
        cpu: 2
      identity:
        type: SystemAssigned
      location: eastus
      platform:
        architecture: amd64
        os: Linux
      registryName: myRegistry
      resourceGroupName: myResourceGroup
      status: Enabled
      step:
        arguments:
          - isSecret: false
            name: mytestargument
            value: mytestvalue
          - isSecret: true
            name: mysecrettestargument
            value: mysecrettestvalue
        contextPath: src
        dockerFilePath: src/DockerFile
        imageNames:
          - azurerest:testtag
        isPushEnabled: true
        noCache: false
        type: Docker
      tags:
        testkey: value
      taskName: mytTask
      trigger:
        baseImageTrigger:
          baseImageTriggerType: Runtime
          name: myBaseImageTrigger
        sourceTriggers:
          - name: mySourceTrigger
            sourceRepository:
              branch: master
              repositoryUrl: https://github.com/Azure/azure-rest-api-specs
              sourceControlAuthProperties:
                token: xxxxx
                tokenType: PAT
              sourceControlType: Github
            sourceTriggerEvents:
              - commit
        timerTriggers:
          - name: myTimerTrigger
            schedule: 30 9 * * 1-5

```

{{% /example %}}
{{% example %}}
### Tasks_Create_WithSystemAndUserIdentities
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var task = new AzureNative.ContainerRegistry.Task("task", new()
    {
        AgentConfiguration = new AzureNative.ContainerRegistry.Inputs.AgentPropertiesArgs
        {
            Cpu = 2,
        },
        Identity = new AzureNative.ContainerRegistry.Inputs.IdentityPropertiesArgs
        {
            Type = AzureNative.ContainerRegistry.ResourceIdentityType.SystemAssigned_UserAssigned,
            UserAssignedIdentities = 
            {
                { "/subscriptions/f9d7ebed-adbd-4cb4-b973-aaf82c136138/resourcegroups/myResourceGroup1/providers/Microsoft.ManagedIdentity/userAssignedIdentities/identity2", null },
            },
        },
        Location = "eastus",
        Platform = new AzureNative.ContainerRegistry.Inputs.PlatformPropertiesArgs
        {
            Architecture = "amd64",
            Os = "Linux",
        },
        RegistryName = "myRegistry",
        ResourceGroupName = "myResourceGroup",
        Status = "Enabled",
        Step = new AzureNative.ContainerRegistry.Inputs.DockerBuildStepArgs
        {
            Arguments = new[]
            {
                new AzureNative.ContainerRegistry.Inputs.ArgumentArgs
                {
                    IsSecret = false,
                    Name = "mytestargument",
                    Value = "mytestvalue",
                },
                new AzureNative.ContainerRegistry.Inputs.ArgumentArgs
                {
                    IsSecret = true,
                    Name = "mysecrettestargument",
                    Value = "mysecrettestvalue",
                },
            },
            ContextPath = "src",
            DockerFilePath = "src/DockerFile",
            ImageNames = new[]
            {
                "azurerest:testtag",
            },
            IsPushEnabled = true,
            NoCache = false,
            Type = "Docker",
        },
        Tags = 
        {
            { "testkey", "value" },
        },
        TaskName = "mytTask",
        Trigger = new AzureNative.ContainerRegistry.Inputs.TriggerPropertiesArgs
        {
            BaseImageTrigger = new AzureNative.ContainerRegistry.Inputs.BaseImageTriggerArgs
            {
                BaseImageTriggerType = "Runtime",
                Name = "myBaseImageTrigger",
            },
            SourceTriggers = new[]
            {
                new AzureNative.ContainerRegistry.Inputs.SourceTriggerArgs
                {
                    Name = "mySourceTrigger",
                    SourceRepository = new AzureNative.ContainerRegistry.Inputs.SourcePropertiesArgs
                    {
                        Branch = "master",
                        RepositoryUrl = "https://github.com/Azure/azure-rest-api-specs",
                        SourceControlAuthProperties = new AzureNative.ContainerRegistry.Inputs.AuthInfoArgs
                        {
                            Token = "xxxxx",
                            TokenType = "PAT",
                        },
                        SourceControlType = "Github",
                    },
                    SourceTriggerEvents = new[]
                    {
                        "commit",
                    },
                },
            },
            TimerTriggers = new[]
            {
                new AzureNative.ContainerRegistry.Inputs.TimerTriggerArgs
                {
                    Name = "myTimerTrigger",
                    Schedule = "30 9 * * 1-5",
                },
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
import com.pulumi.azurenative.containerregistry.Task;
import com.pulumi.azurenative.containerregistry.TaskArgs;
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
        var task = new Task("task", TaskArgs.builder()        
            .agentConfiguration(Map.of("cpu", 2))
            .identity(Map.ofEntries(
                Map.entry("type", "SystemAssigned, UserAssigned"),
                Map.entry("userAssignedIdentities", Map.of("/subscriptions/f9d7ebed-adbd-4cb4-b973-aaf82c136138/resourcegroups/myResourceGroup1/providers/Microsoft.ManagedIdentity/userAssignedIdentities/identity2", ))
            ))
            .location("eastus")
            .platform(Map.ofEntries(
                Map.entry("architecture", "amd64"),
                Map.entry("os", "Linux")
            ))
            .registryName("myRegistry")
            .resourceGroupName("myResourceGroup")
            .status("Enabled")
            .step(Map.ofEntries(
                Map.entry("arguments",                 
                    Map.ofEntries(
                        Map.entry("isSecret", false),
                        Map.entry("name", "mytestargument"),
                        Map.entry("value", "mytestvalue")
                    ),
                    Map.ofEntries(
                        Map.entry("isSecret", true),
                        Map.entry("name", "mysecrettestargument"),
                        Map.entry("value", "mysecrettestvalue")
                    )),
                Map.entry("contextPath", "src"),
                Map.entry("dockerFilePath", "src/DockerFile"),
                Map.entry("imageNames", "azurerest:testtag"),
                Map.entry("isPushEnabled", true),
                Map.entry("noCache", false),
                Map.entry("type", "Docker")
            ))
            .tags(Map.of("testkey", "value"))
            .taskName("mytTask")
            .trigger(Map.ofEntries(
                Map.entry("baseImageTrigger", Map.ofEntries(
                    Map.entry("baseImageTriggerType", "Runtime"),
                    Map.entry("name", "myBaseImageTrigger")
                )),
                Map.entry("sourceTriggers", Map.ofEntries(
                    Map.entry("name", "mySourceTrigger"),
                    Map.entry("sourceRepository", Map.ofEntries(
                        Map.entry("branch", "master"),
                        Map.entry("repositoryUrl", "https://github.com/Azure/azure-rest-api-specs"),
                        Map.entry("sourceControlAuthProperties", Map.ofEntries(
                            Map.entry("token", "xxxxx"),
                            Map.entry("tokenType", "PAT")
                        )),
                        Map.entry("sourceControlType", "Github")
                    )),
                    Map.entry("sourceTriggerEvents", "commit")
                )),
                Map.entry("timerTriggers", Map.ofEntries(
                    Map.entry("name", "myTimerTrigger"),
                    Map.entry("schedule", "30 9 * * 1-5")
                ))
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const task = new azure_native.containerregistry.Task("task", {
    agentConfiguration: {
        cpu: 2,
    },
    identity: {
        type: azure_native.containerregistry.ResourceIdentityType.SystemAssigned_UserAssigned,
        userAssignedIdentities: {
            "/subscriptions/f9d7ebed-adbd-4cb4-b973-aaf82c136138/resourcegroups/myResourceGroup1/providers/Microsoft.ManagedIdentity/userAssignedIdentities/identity2": {},
        },
    },
    location: "eastus",
    platform: {
        architecture: "amd64",
        os: "Linux",
    },
    registryName: "myRegistry",
    resourceGroupName: "myResourceGroup",
    status: "Enabled",
    step: {
        arguments: [
            {
                isSecret: false,
                name: "mytestargument",
                value: "mytestvalue",
            },
            {
                isSecret: true,
                name: "mysecrettestargument",
                value: "mysecrettestvalue",
            },
        ],
        contextPath: "src",
        dockerFilePath: "src/DockerFile",
        imageNames: ["azurerest:testtag"],
        isPushEnabled: true,
        noCache: false,
        type: "Docker",
    },
    tags: {
        testkey: "value",
    },
    taskName: "mytTask",
    trigger: {
        baseImageTrigger: {
            baseImageTriggerType: "Runtime",
            name: "myBaseImageTrigger",
        },
        sourceTriggers: [{
            name: "mySourceTrigger",
            sourceRepository: {
                branch: "master",
                repositoryUrl: "https://github.com/Azure/azure-rest-api-specs",
                sourceControlAuthProperties: {
                    token: "xxxxx",
                    tokenType: "PAT",
                },
                sourceControlType: "Github",
            },
            sourceTriggerEvents: ["commit"],
        }],
        timerTriggers: [{
            name: "myTimerTrigger",
            schedule: "30 9 * * 1-5",
        }],
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

task = azure_native.containerregistry.Task("task",
    agent_configuration=azure_native.containerregistry.AgentPropertiesArgs(
        cpu=2,
    ),
    identity=azure_native.containerregistry.IdentityPropertiesResponseArgs(
        type=azure_native.containerregistry.ResourceIdentityType.SYSTEM_ASSIGNED_USER_ASSIGNED,
        user_assigned_identities={
            "/subscriptions/f9d7ebed-adbd-4cb4-b973-aaf82c136138/resourcegroups/myResourceGroup1/providers/Microsoft.ManagedIdentity/userAssignedIdentities/identity2": azure_native.containerregistry.UserIdentityPropertiesArgs(),
        },
    ),
    location="eastus",
    platform=azure_native.containerregistry.PlatformPropertiesArgs(
        architecture="amd64",
        os="Linux",
    ),
    registry_name="myRegistry",
    resource_group_name="myResourceGroup",
    status="Enabled",
    step=azure_native.containerregistry.DockerBuildStepArgs(
        arguments=[
            azure_native.containerregistry.ArgumentArgs(
                is_secret=False,
                name="mytestargument",
                value="mytestvalue",
            ),
            azure_native.containerregistry.ArgumentArgs(
                is_secret=True,
                name="mysecrettestargument",
                value="mysecrettestvalue",
            ),
        ],
        context_path="src",
        docker_file_path="src/DockerFile",
        image_names=["azurerest:testtag"],
        is_push_enabled=True,
        no_cache=False,
        type="Docker",
    ),
    tags={
        "testkey": "value",
    },
    task_name="mytTask",
    trigger=azure_native.containerregistry.TriggerPropertiesResponseArgs(
        base_image_trigger=azure_native.containerregistry.BaseImageTriggerArgs(
            base_image_trigger_type="Runtime",
            name="myBaseImageTrigger",
        ),
        source_triggers=[{
            "name": "mySourceTrigger",
            "sourceRepository": {
                "branch": "master",
                "repositoryUrl": "https://github.com/Azure/azure-rest-api-specs",
                "sourceControlAuthProperties": azure_native.containerregistry.AuthInfoArgs(
                    token="xxxxx",
                    token_type="PAT",
                ),
                "sourceControlType": "Github",
            },
            "sourceTriggerEvents": ["commit"],
        }],
        timer_triggers=[azure_native.containerregistry.TimerTriggerArgs(
            name="myTimerTrigger",
            schedule="30 9 * * 1-5",
        )],
    ))

```

```yaml
resources:
  task:
    type: azure-native:containerregistry:Task
    properties:
      agentConfiguration:
        cpu: 2
      identity:
        type: SystemAssigned, UserAssigned
        userAssignedIdentities:
          ? /subscriptions/f9d7ebed-adbd-4cb4-b973-aaf82c136138/resourcegroups/myResourceGroup1/providers/Microsoft.ManagedIdentity/userAssignedIdentities/identity2
          : {}
      location: eastus
      platform:
        architecture: amd64
        os: Linux
      registryName: myRegistry
      resourceGroupName: myResourceGroup
      status: Enabled
      step:
        arguments:
          - isSecret: false
            name: mytestargument
            value: mytestvalue
          - isSecret: true
            name: mysecrettestargument
            value: mysecrettestvalue
        contextPath: src
        dockerFilePath: src/DockerFile
        imageNames:
          - azurerest:testtag
        isPushEnabled: true
        noCache: false
        type: Docker
      tags:
        testkey: value
      taskName: mytTask
      trigger:
        baseImageTrigger:
          baseImageTriggerType: Runtime
          name: myBaseImageTrigger
        sourceTriggers:
          - name: mySourceTrigger
            sourceRepository:
              branch: master
              repositoryUrl: https://github.com/Azure/azure-rest-api-specs
              sourceControlAuthProperties:
                token: xxxxx
                tokenType: PAT
              sourceControlType: Github
            sourceTriggerEvents:
              - commit
        timerTriggers:
          - name: myTimerTrigger
            schedule: 30 9 * * 1-5

```

{{% /example %}}
{{% example %}}
### Tasks_Create_WithUserIdentities
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var task = new AzureNative.ContainerRegistry.Task("task", new()
    {
        AgentConfiguration = new AzureNative.ContainerRegistry.Inputs.AgentPropertiesArgs
        {
            Cpu = 2,
        },
        Identity = new AzureNative.ContainerRegistry.Inputs.IdentityPropertiesArgs
        {
            Type = AzureNative.ContainerRegistry.ResourceIdentityType.UserAssigned,
            UserAssignedIdentities = 
            {
                { "/subscriptions/f9d7ebed-adbd-4cb4-b973-aaf82c136138/resourcegroups/myResourceGroup/providers/Microsoft.ManagedIdentity/userAssignedIdentities/identity1", null },
                { "/subscriptions/f9d7ebed-adbd-4cb4-b973-aaf82c136138/resourcegroups/myResourceGroup1/providers/Microsoft.ManagedIdentity/userAssignedIdentities/identity2", null },
            },
        },
        Location = "eastus",
        Platform = new AzureNative.ContainerRegistry.Inputs.PlatformPropertiesArgs
        {
            Architecture = "amd64",
            Os = "Linux",
        },
        RegistryName = "myRegistry",
        ResourceGroupName = "myResourceGroup",
        Status = "Enabled",
        Step = new AzureNative.ContainerRegistry.Inputs.DockerBuildStepArgs
        {
            Arguments = new[]
            {
                new AzureNative.ContainerRegistry.Inputs.ArgumentArgs
                {
                    IsSecret = false,
                    Name = "mytestargument",
                    Value = "mytestvalue",
                },
                new AzureNative.ContainerRegistry.Inputs.ArgumentArgs
                {
                    IsSecret = true,
                    Name = "mysecrettestargument",
                    Value = "mysecrettestvalue",
                },
            },
            ContextPath = "src",
            DockerFilePath = "src/DockerFile",
            ImageNames = new[]
            {
                "azurerest:testtag",
            },
            IsPushEnabled = true,
            NoCache = false,
            Type = "Docker",
        },
        Tags = 
        {
            { "testkey", "value" },
        },
        TaskName = "mytTask",
        Trigger = new AzureNative.ContainerRegistry.Inputs.TriggerPropertiesArgs
        {
            BaseImageTrigger = new AzureNative.ContainerRegistry.Inputs.BaseImageTriggerArgs
            {
                BaseImageTriggerType = "Runtime",
                Name = "myBaseImageTrigger",
            },
            SourceTriggers = new[]
            {
                new AzureNative.ContainerRegistry.Inputs.SourceTriggerArgs
                {
                    Name = "mySourceTrigger",
                    SourceRepository = new AzureNative.ContainerRegistry.Inputs.SourcePropertiesArgs
                    {
                        Branch = "master",
                        RepositoryUrl = "https://github.com/Azure/azure-rest-api-specs",
                        SourceControlAuthProperties = new AzureNative.ContainerRegistry.Inputs.AuthInfoArgs
                        {
                            Token = "xxxxx",
                            TokenType = "PAT",
                        },
                        SourceControlType = "Github",
                    },
                    SourceTriggerEvents = new[]
                    {
                        "commit",
                    },
                },
            },
            TimerTriggers = new[]
            {
                new AzureNative.ContainerRegistry.Inputs.TimerTriggerArgs
                {
                    Name = "myTimerTrigger",
                    Schedule = "30 9 * * 1-5",
                },
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
import com.pulumi.azurenative.containerregistry.Task;
import com.pulumi.azurenative.containerregistry.TaskArgs;
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
        var task = new Task("task", TaskArgs.builder()        
            .agentConfiguration(Map.of("cpu", 2))
            .identity(Map.ofEntries(
                Map.entry("type", "UserAssigned"),
                Map.entry("userAssignedIdentities", Map.ofEntries(
                    Map.entry("/subscriptions/f9d7ebed-adbd-4cb4-b973-aaf82c136138/resourcegroups/myResourceGroup/providers/Microsoft.ManagedIdentity/userAssignedIdentities/identity1", ),
                    Map.entry("/subscriptions/f9d7ebed-adbd-4cb4-b973-aaf82c136138/resourcegroups/myResourceGroup1/providers/Microsoft.ManagedIdentity/userAssignedIdentities/identity2", )
                ))
            ))
            .location("eastus")
            .platform(Map.ofEntries(
                Map.entry("architecture", "amd64"),
                Map.entry("os", "Linux")
            ))
            .registryName("myRegistry")
            .resourceGroupName("myResourceGroup")
            .status("Enabled")
            .step(Map.ofEntries(
                Map.entry("arguments",                 
                    Map.ofEntries(
                        Map.entry("isSecret", false),
                        Map.entry("name", "mytestargument"),
                        Map.entry("value", "mytestvalue")
                    ),
                    Map.ofEntries(
                        Map.entry("isSecret", true),
                        Map.entry("name", "mysecrettestargument"),
                        Map.entry("value", "mysecrettestvalue")
                    )),
                Map.entry("contextPath", "src"),
                Map.entry("dockerFilePath", "src/DockerFile"),
                Map.entry("imageNames", "azurerest:testtag"),
                Map.entry("isPushEnabled", true),
                Map.entry("noCache", false),
                Map.entry("type", "Docker")
            ))
            .tags(Map.of("testkey", "value"))
            .taskName("mytTask")
            .trigger(Map.ofEntries(
                Map.entry("baseImageTrigger", Map.ofEntries(
                    Map.entry("baseImageTriggerType", "Runtime"),
                    Map.entry("name", "myBaseImageTrigger")
                )),
                Map.entry("sourceTriggers", Map.ofEntries(
                    Map.entry("name", "mySourceTrigger"),
                    Map.entry("sourceRepository", Map.ofEntries(
                        Map.entry("branch", "master"),
                        Map.entry("repositoryUrl", "https://github.com/Azure/azure-rest-api-specs"),
                        Map.entry("sourceControlAuthProperties", Map.ofEntries(
                            Map.entry("token", "xxxxx"),
                            Map.entry("tokenType", "PAT")
                        )),
                        Map.entry("sourceControlType", "Github")
                    )),
                    Map.entry("sourceTriggerEvents", "commit")
                )),
                Map.entry("timerTriggers", Map.ofEntries(
                    Map.entry("name", "myTimerTrigger"),
                    Map.entry("schedule", "30 9 * * 1-5")
                ))
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const task = new azure_native.containerregistry.Task("task", {
    agentConfiguration: {
        cpu: 2,
    },
    identity: {
        type: azure_native.containerregistry.ResourceIdentityType.UserAssigned,
        userAssignedIdentities: {
            "/subscriptions/f9d7ebed-adbd-4cb4-b973-aaf82c136138/resourcegroups/myResourceGroup/providers/Microsoft.ManagedIdentity/userAssignedIdentities/identity1": {},
            "/subscriptions/f9d7ebed-adbd-4cb4-b973-aaf82c136138/resourcegroups/myResourceGroup1/providers/Microsoft.ManagedIdentity/userAssignedIdentities/identity2": {},
        },
    },
    location: "eastus",
    platform: {
        architecture: "amd64",
        os: "Linux",
    },
    registryName: "myRegistry",
    resourceGroupName: "myResourceGroup",
    status: "Enabled",
    step: {
        arguments: [
            {
                isSecret: false,
                name: "mytestargument",
                value: "mytestvalue",
            },
            {
                isSecret: true,
                name: "mysecrettestargument",
                value: "mysecrettestvalue",
            },
        ],
        contextPath: "src",
        dockerFilePath: "src/DockerFile",
        imageNames: ["azurerest:testtag"],
        isPushEnabled: true,
        noCache: false,
        type: "Docker",
    },
    tags: {
        testkey: "value",
    },
    taskName: "mytTask",
    trigger: {
        baseImageTrigger: {
            baseImageTriggerType: "Runtime",
            name: "myBaseImageTrigger",
        },
        sourceTriggers: [{
            name: "mySourceTrigger",
            sourceRepository: {
                branch: "master",
                repositoryUrl: "https://github.com/Azure/azure-rest-api-specs",
                sourceControlAuthProperties: {
                    token: "xxxxx",
                    tokenType: "PAT",
                },
                sourceControlType: "Github",
            },
            sourceTriggerEvents: ["commit"],
        }],
        timerTriggers: [{
            name: "myTimerTrigger",
            schedule: "30 9 * * 1-5",
        }],
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

task = azure_native.containerregistry.Task("task",
    agent_configuration=azure_native.containerregistry.AgentPropertiesArgs(
        cpu=2,
    ),
    identity=azure_native.containerregistry.IdentityPropertiesResponseArgs(
        type=azure_native.containerregistry.ResourceIdentityType.USER_ASSIGNED,
        user_assigned_identities={
            "/subscriptions/f9d7ebed-adbd-4cb4-b973-aaf82c136138/resourcegroups/myResourceGroup/providers/Microsoft.ManagedIdentity/userAssignedIdentities/identity1": azure_native.containerregistry.UserIdentityPropertiesArgs(),
            "/subscriptions/f9d7ebed-adbd-4cb4-b973-aaf82c136138/resourcegroups/myResourceGroup1/providers/Microsoft.ManagedIdentity/userAssignedIdentities/identity2": azure_native.containerregistry.UserIdentityPropertiesArgs(),
        },
    ),
    location="eastus",
    platform=azure_native.containerregistry.PlatformPropertiesArgs(
        architecture="amd64",
        os="Linux",
    ),
    registry_name="myRegistry",
    resource_group_name="myResourceGroup",
    status="Enabled",
    step=azure_native.containerregistry.DockerBuildStepArgs(
        arguments=[
            azure_native.containerregistry.ArgumentArgs(
                is_secret=False,
                name="mytestargument",
                value="mytestvalue",
            ),
            azure_native.containerregistry.ArgumentArgs(
                is_secret=True,
                name="mysecrettestargument",
                value="mysecrettestvalue",
            ),
        ],
        context_path="src",
        docker_file_path="src/DockerFile",
        image_names=["azurerest:testtag"],
        is_push_enabled=True,
        no_cache=False,
        type="Docker",
    ),
    tags={
        "testkey": "value",
    },
    task_name="mytTask",
    trigger=azure_native.containerregistry.TriggerPropertiesResponseArgs(
        base_image_trigger=azure_native.containerregistry.BaseImageTriggerArgs(
            base_image_trigger_type="Runtime",
            name="myBaseImageTrigger",
        ),
        source_triggers=[{
            "name": "mySourceTrigger",
            "sourceRepository": {
                "branch": "master",
                "repositoryUrl": "https://github.com/Azure/azure-rest-api-specs",
                "sourceControlAuthProperties": azure_native.containerregistry.AuthInfoArgs(
                    token="xxxxx",
                    token_type="PAT",
                ),
                "sourceControlType": "Github",
            },
            "sourceTriggerEvents": ["commit"],
        }],
        timer_triggers=[azure_native.containerregistry.TimerTriggerArgs(
            name="myTimerTrigger",
            schedule="30 9 * * 1-5",
        )],
    ))

```

```yaml
resources:
  task:
    type: azure-native:containerregistry:Task
    properties:
      agentConfiguration:
        cpu: 2
      identity:
        type: UserAssigned
        userAssignedIdentities:
          ? /subscriptions/f9d7ebed-adbd-4cb4-b973-aaf82c136138/resourcegroups/myResourceGroup/providers/Microsoft.ManagedIdentity/userAssignedIdentities/identity1
          : {}
          ? /subscriptions/f9d7ebed-adbd-4cb4-b973-aaf82c136138/resourcegroups/myResourceGroup1/providers/Microsoft.ManagedIdentity/userAssignedIdentities/identity2
          : {}
      location: eastus
      platform:
        architecture: amd64
        os: Linux
      registryName: myRegistry
      resourceGroupName: myResourceGroup
      status: Enabled
      step:
        arguments:
          - isSecret: false
            name: mytestargument
            value: mytestvalue
          - isSecret: true
            name: mysecrettestargument
            value: mysecrettestvalue
        contextPath: src
        dockerFilePath: src/DockerFile
        imageNames:
          - azurerest:testtag
        isPushEnabled: true
        noCache: false
        type: Docker
      tags:
        testkey: value
      taskName: mytTask
      trigger:
        baseImageTrigger:
          baseImageTriggerType: Runtime
          name: myBaseImageTrigger
        sourceTriggers:
          - name: mySourceTrigger
            sourceRepository:
              branch: master
              repositoryUrl: https://github.com/Azure/azure-rest-api-specs
              sourceControlAuthProperties:
                token: xxxxx
                tokenType: PAT
              sourceControlType: Github
            sourceTriggerEvents:
              - commit
        timerTriggers:
          - name: myTimerTrigger
            schedule: 30 9 * * 1-5

```

{{% /example %}}
{{% example %}}
### Tasks_Create_WithUserIdentities_WithSystemIdentity
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var task = new AzureNative.ContainerRegistry.Task("task", new()
    {
        AgentConfiguration = new AzureNative.ContainerRegistry.Inputs.AgentPropertiesArgs
        {
            Cpu = 2,
        },
        Identity = new AzureNative.ContainerRegistry.Inputs.IdentityPropertiesArgs
        {
            Type = AzureNative.ContainerRegistry.ResourceIdentityType.SystemAssigned,
        },
        Location = "eastus",
        Platform = new AzureNative.ContainerRegistry.Inputs.PlatformPropertiesArgs
        {
            Architecture = "amd64",
            Os = "Linux",
        },
        RegistryName = "myRegistry",
        ResourceGroupName = "myResourceGroup",
        Status = "Enabled",
        Step = new AzureNative.ContainerRegistry.Inputs.DockerBuildStepArgs
        {
            Arguments = new[]
            {
                new AzureNative.ContainerRegistry.Inputs.ArgumentArgs
                {
                    IsSecret = false,
                    Name = "mytestargument",
                    Value = "mytestvalue",
                },
                new AzureNative.ContainerRegistry.Inputs.ArgumentArgs
                {
                    IsSecret = true,
                    Name = "mysecrettestargument",
                    Value = "mysecrettestvalue",
                },
            },
            ContextPath = "src",
            DockerFilePath = "src/DockerFile",
            ImageNames = new[]
            {
                "azurerest:testtag",
            },
            IsPushEnabled = true,
            NoCache = false,
            Type = "Docker",
        },
        Tags = 
        {
            { "testkey", "value" },
        },
        TaskName = "mytTask",
        Trigger = new AzureNative.ContainerRegistry.Inputs.TriggerPropertiesArgs
        {
            BaseImageTrigger = new AzureNative.ContainerRegistry.Inputs.BaseImageTriggerArgs
            {
                BaseImageTriggerType = "Runtime",
                Name = "myBaseImageTrigger",
            },
            SourceTriggers = new[]
            {
                new AzureNative.ContainerRegistry.Inputs.SourceTriggerArgs
                {
                    Name = "mySourceTrigger",
                    SourceRepository = new AzureNative.ContainerRegistry.Inputs.SourcePropertiesArgs
                    {
                        Branch = "master",
                        RepositoryUrl = "https://github.com/Azure/azure-rest-api-specs",
                        SourceControlAuthProperties = new AzureNative.ContainerRegistry.Inputs.AuthInfoArgs
                        {
                            Token = "xxxxx",
                            TokenType = "PAT",
                        },
                        SourceControlType = "Github",
                    },
                    SourceTriggerEvents = new[]
                    {
                        "commit",
                    },
                },
            },
            TimerTriggers = new[]
            {
                new AzureNative.ContainerRegistry.Inputs.TimerTriggerArgs
                {
                    Name = "myTimerTrigger",
                    Schedule = "30 9 * * 1-5",
                },
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
import com.pulumi.azurenative.containerregistry.Task;
import com.pulumi.azurenative.containerregistry.TaskArgs;
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
        var task = new Task("task", TaskArgs.builder()        
            .agentConfiguration(Map.of("cpu", 2))
            .identity(Map.of("type", "SystemAssigned"))
            .location("eastus")
            .platform(Map.ofEntries(
                Map.entry("architecture", "amd64"),
                Map.entry("os", "Linux")
            ))
            .registryName("myRegistry")
            .resourceGroupName("myResourceGroup")
            .status("Enabled")
            .step(Map.ofEntries(
                Map.entry("arguments",                 
                    Map.ofEntries(
                        Map.entry("isSecret", false),
                        Map.entry("name", "mytestargument"),
                        Map.entry("value", "mytestvalue")
                    ),
                    Map.ofEntries(
                        Map.entry("isSecret", true),
                        Map.entry("name", "mysecrettestargument"),
                        Map.entry("value", "mysecrettestvalue")
                    )),
                Map.entry("contextPath", "src"),
                Map.entry("dockerFilePath", "src/DockerFile"),
                Map.entry("imageNames", "azurerest:testtag"),
                Map.entry("isPushEnabled", true),
                Map.entry("noCache", false),
                Map.entry("type", "Docker")
            ))
            .tags(Map.of("testkey", "value"))
            .taskName("mytTask")
            .trigger(Map.ofEntries(
                Map.entry("baseImageTrigger", Map.ofEntries(
                    Map.entry("baseImageTriggerType", "Runtime"),
                    Map.entry("name", "myBaseImageTrigger")
                )),
                Map.entry("sourceTriggers", Map.ofEntries(
                    Map.entry("name", "mySourceTrigger"),
                    Map.entry("sourceRepository", Map.ofEntries(
                        Map.entry("branch", "master"),
                        Map.entry("repositoryUrl", "https://github.com/Azure/azure-rest-api-specs"),
                        Map.entry("sourceControlAuthProperties", Map.ofEntries(
                            Map.entry("token", "xxxxx"),
                            Map.entry("tokenType", "PAT")
                        )),
                        Map.entry("sourceControlType", "Github")
                    )),
                    Map.entry("sourceTriggerEvents", "commit")
                )),
                Map.entry("timerTriggers", Map.ofEntries(
                    Map.entry("name", "myTimerTrigger"),
                    Map.entry("schedule", "30 9 * * 1-5")
                ))
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const task = new azure_native.containerregistry.Task("task", {
    agentConfiguration: {
        cpu: 2,
    },
    identity: {
        type: azure_native.containerregistry.ResourceIdentityType.SystemAssigned,
    },
    location: "eastus",
    platform: {
        architecture: "amd64",
        os: "Linux",
    },
    registryName: "myRegistry",
    resourceGroupName: "myResourceGroup",
    status: "Enabled",
    step: {
        arguments: [
            {
                isSecret: false,
                name: "mytestargument",
                value: "mytestvalue",
            },
            {
                isSecret: true,
                name: "mysecrettestargument",
                value: "mysecrettestvalue",
            },
        ],
        contextPath: "src",
        dockerFilePath: "src/DockerFile",
        imageNames: ["azurerest:testtag"],
        isPushEnabled: true,
        noCache: false,
        type: "Docker",
    },
    tags: {
        testkey: "value",
    },
    taskName: "mytTask",
    trigger: {
        baseImageTrigger: {
            baseImageTriggerType: "Runtime",
            name: "myBaseImageTrigger",
        },
        sourceTriggers: [{
            name: "mySourceTrigger",
            sourceRepository: {
                branch: "master",
                repositoryUrl: "https://github.com/Azure/azure-rest-api-specs",
                sourceControlAuthProperties: {
                    token: "xxxxx",
                    tokenType: "PAT",
                },
                sourceControlType: "Github",
            },
            sourceTriggerEvents: ["commit"],
        }],
        timerTriggers: [{
            name: "myTimerTrigger",
            schedule: "30 9 * * 1-5",
        }],
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

task = azure_native.containerregistry.Task("task",
    agent_configuration=azure_native.containerregistry.AgentPropertiesArgs(
        cpu=2,
    ),
    identity=azure_native.containerregistry.IdentityPropertiesArgs(
        type=azure_native.containerregistry.ResourceIdentityType.SYSTEM_ASSIGNED,
    ),
    location="eastus",
    platform=azure_native.containerregistry.PlatformPropertiesArgs(
        architecture="amd64",
        os="Linux",
    ),
    registry_name="myRegistry",
    resource_group_name="myResourceGroup",
    status="Enabled",
    step=azure_native.containerregistry.DockerBuildStepArgs(
        arguments=[
            azure_native.containerregistry.ArgumentArgs(
                is_secret=False,
                name="mytestargument",
                value="mytestvalue",
            ),
            azure_native.containerregistry.ArgumentArgs(
                is_secret=True,
                name="mysecrettestargument",
                value="mysecrettestvalue",
            ),
        ],
        context_path="src",
        docker_file_path="src/DockerFile",
        image_names=["azurerest:testtag"],
        is_push_enabled=True,
        no_cache=False,
        type="Docker",
    ),
    tags={
        "testkey": "value",
    },
    task_name="mytTask",
    trigger=azure_native.containerregistry.TriggerPropertiesResponseArgs(
        base_image_trigger=azure_native.containerregistry.BaseImageTriggerArgs(
            base_image_trigger_type="Runtime",
            name="myBaseImageTrigger",
        ),
        source_triggers=[{
            "name": "mySourceTrigger",
            "sourceRepository": {
                "branch": "master",
                "repositoryUrl": "https://github.com/Azure/azure-rest-api-specs",
                "sourceControlAuthProperties": azure_native.containerregistry.AuthInfoArgs(
                    token="xxxxx",
                    token_type="PAT",
                ),
                "sourceControlType": "Github",
            },
            "sourceTriggerEvents": ["commit"],
        }],
        timer_triggers=[azure_native.containerregistry.TimerTriggerArgs(
            name="myTimerTrigger",
            schedule="30 9 * * 1-5",
        )],
    ))

```

```yaml
resources:
  task:
    type: azure-native:containerregistry:Task
    properties:
      agentConfiguration:
        cpu: 2
      identity:
        type: SystemAssigned
      location: eastus
      platform:
        architecture: amd64
        os: Linux
      registryName: myRegistry
      resourceGroupName: myResourceGroup
      status: Enabled
      step:
        arguments:
          - isSecret: false
            name: mytestargument
            value: mytestvalue
          - isSecret: true
            name: mysecrettestargument
            value: mysecrettestvalue
        contextPath: src
        dockerFilePath: src/DockerFile
        imageNames:
          - azurerest:testtag
        isPushEnabled: true
        noCache: false
        type: Docker
      tags:
        testkey: value
      taskName: mytTask
      trigger:
        baseImageTrigger:
          baseImageTriggerType: Runtime
          name: myBaseImageTrigger
        sourceTriggers:
          - name: mySourceTrigger
            sourceRepository:
              branch: master
              repositoryUrl: https://github.com/Azure/azure-rest-api-specs
              sourceControlAuthProperties:
                token: xxxxx
                tokenType: PAT
              sourceControlType: Github
            sourceTriggerEvents:
              - commit
        timerTriggers:
          - name: myTimerTrigger
            schedule: 30 9 * * 1-5

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:containerregistry:Task myTask /subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/myResourceGroup/providers/Microsoft.ContainerRegistry/registries/myRegistry/tasks/myTask 
```
