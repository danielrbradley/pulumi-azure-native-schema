Diagnostic details.
API Version: 2022-08-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ApiManagementCreateDiagnostic
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var diagnostic = new AzureNative.ApiManagement.Diagnostic("diagnostic", new()
    {
        AlwaysLog = "allErrors",
        Backend = new AzureNative.ApiManagement.Inputs.PipelineDiagnosticSettingsArgs
        {
            Request = new AzureNative.ApiManagement.Inputs.HttpMessageDiagnosticArgs
            {
                Body = new AzureNative.ApiManagement.Inputs.BodyDiagnosticSettingsArgs
                {
                    Bytes = 512,
                },
                Headers = new[]
                {
                    "Content-type",
                },
            },
            Response = new AzureNative.ApiManagement.Inputs.HttpMessageDiagnosticArgs
            {
                Body = new AzureNative.ApiManagement.Inputs.BodyDiagnosticSettingsArgs
                {
                    Bytes = 512,
                },
                Headers = new[]
                {
                    "Content-type",
                },
            },
        },
        DiagnosticId = "applicationinsights",
        Frontend = new AzureNative.ApiManagement.Inputs.PipelineDiagnosticSettingsArgs
        {
            Request = new AzureNative.ApiManagement.Inputs.HttpMessageDiagnosticArgs
            {
                Body = new AzureNative.ApiManagement.Inputs.BodyDiagnosticSettingsArgs
                {
                    Bytes = 512,
                },
                Headers = new[]
                {
                    "Content-type",
                },
            },
            Response = new AzureNative.ApiManagement.Inputs.HttpMessageDiagnosticArgs
            {
                Body = new AzureNative.ApiManagement.Inputs.BodyDiagnosticSettingsArgs
                {
                    Bytes = 512,
                },
                Headers = new[]
                {
                    "Content-type",
                },
            },
        },
        LoggerId = "/loggers/azuremonitor",
        ResourceGroupName = "rg1",
        Sampling = new AzureNative.ApiManagement.Inputs.SamplingSettingsArgs
        {
            Percentage = 50,
            SamplingType = "fixed",
        },
        ServiceName = "apimService1",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.apimanagement.Diagnostic;
import com.pulumi.azurenative.apimanagement.DiagnosticArgs;
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
        var diagnostic = new Diagnostic("diagnostic", DiagnosticArgs.builder()        
            .alwaysLog("allErrors")
            .backend(Map.ofEntries(
                Map.entry("request", Map.ofEntries(
                    Map.entry("body", Map.of("bytes", 512)),
                    Map.entry("headers", "Content-type")
                )),
                Map.entry("response", Map.ofEntries(
                    Map.entry("body", Map.of("bytes", 512)),
                    Map.entry("headers", "Content-type")
                ))
            ))
            .diagnosticId("applicationinsights")
            .frontend(Map.ofEntries(
                Map.entry("request", Map.ofEntries(
                    Map.entry("body", Map.of("bytes", 512)),
                    Map.entry("headers", "Content-type")
                )),
                Map.entry("response", Map.ofEntries(
                    Map.entry("body", Map.of("bytes", 512)),
                    Map.entry("headers", "Content-type")
                ))
            ))
            .loggerId("/loggers/azuremonitor")
            .resourceGroupName("rg1")
            .sampling(Map.ofEntries(
                Map.entry("percentage", 50),
                Map.entry("samplingType", "fixed")
            ))
            .serviceName("apimService1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const diagnostic = new azure_native.apimanagement.Diagnostic("diagnostic", {
    alwaysLog: "allErrors",
    backend: {
        request: {
            body: {
                bytes: 512,
            },
            headers: ["Content-type"],
        },
        response: {
            body: {
                bytes: 512,
            },
            headers: ["Content-type"],
        },
    },
    diagnosticId: "applicationinsights",
    frontend: {
        request: {
            body: {
                bytes: 512,
            },
            headers: ["Content-type"],
        },
        response: {
            body: {
                bytes: 512,
            },
            headers: ["Content-type"],
        },
    },
    loggerId: "/loggers/azuremonitor",
    resourceGroupName: "rg1",
    sampling: {
        percentage: 50,
        samplingType: "fixed",
    },
    serviceName: "apimService1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

diagnostic = azure_native.apimanagement.Diagnostic("diagnostic",
    always_log="allErrors",
    backend=azure_native.apimanagement.PipelineDiagnosticSettingsResponseArgs(
        request={
            "body": azure_native.apimanagement.BodyDiagnosticSettingsArgs(
                bytes=512,
            ),
            "headers": ["Content-type"],
        },
        response={
            "body": azure_native.apimanagement.BodyDiagnosticSettingsArgs(
                bytes=512,
            ),
            "headers": ["Content-type"],
        },
    ),
    diagnostic_id="applicationinsights",
    frontend=azure_native.apimanagement.PipelineDiagnosticSettingsResponseArgs(
        request={
            "body": azure_native.apimanagement.BodyDiagnosticSettingsArgs(
                bytes=512,
            ),
            "headers": ["Content-type"],
        },
        response={
            "body": azure_native.apimanagement.BodyDiagnosticSettingsArgs(
                bytes=512,
            ),
            "headers": ["Content-type"],
        },
    ),
    logger_id="/loggers/azuremonitor",
    resource_group_name="rg1",
    sampling=azure_native.apimanagement.SamplingSettingsArgs(
        percentage=50,
        sampling_type="fixed",
    ),
    service_name="apimService1")

```

```yaml
resources:
  diagnostic:
    type: azure-native:apimanagement:Diagnostic
    properties:
      alwaysLog: allErrors
      backend:
        request:
          body:
            bytes: 512
          headers:
            - Content-type
        response:
          body:
            bytes: 512
          headers:
            - Content-type
      diagnosticId: applicationinsights
      frontend:
        request:
          body:
            bytes: 512
          headers:
            - Content-type
        response:
          body:
            bytes: 512
          headers:
            - Content-type
      loggerId: /loggers/azuremonitor
      resourceGroupName: rg1
      sampling:
        percentage: 50
        samplingType: fixed
      serviceName: apimService1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:apimanagement:Diagnostic applicationinsights /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/diagnostics/applicationinsights 
```
