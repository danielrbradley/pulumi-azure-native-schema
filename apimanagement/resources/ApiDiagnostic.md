Diagnostic details.
API Version: 2022-08-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ApiManagementCreateApiDiagnostic
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var apiDiagnostic = new AzureNative.ApiManagement.ApiDiagnostic("apiDiagnostic", new()
    {
        AlwaysLog = "allErrors",
        ApiId = "57d1f7558aa04f15146d9d8a",
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
        LoggerId = "/loggers/applicationinsights",
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
import com.pulumi.azurenative.apimanagement.ApiDiagnostic;
import com.pulumi.azurenative.apimanagement.ApiDiagnosticArgs;
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
        var apiDiagnostic = new ApiDiagnostic("apiDiagnostic", ApiDiagnosticArgs.builder()        
            .alwaysLog("allErrors")
            .apiId("57d1f7558aa04f15146d9d8a")
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
            .loggerId("/loggers/applicationinsights")
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

const apiDiagnostic = new azure_native.apimanagement.ApiDiagnostic("apiDiagnostic", {
    alwaysLog: "allErrors",
    apiId: "57d1f7558aa04f15146d9d8a",
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
    loggerId: "/loggers/applicationinsights",
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

api_diagnostic = azure_native.apimanagement.ApiDiagnostic("apiDiagnostic",
    always_log="allErrors",
    api_id="57d1f7558aa04f15146d9d8a",
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
    logger_id="/loggers/applicationinsights",
    resource_group_name="rg1",
    sampling=azure_native.apimanagement.SamplingSettingsArgs(
        percentage=50,
        sampling_type="fixed",
    ),
    service_name="apimService1")

```

```yaml
resources:
  apiDiagnostic:
    type: azure-native:apimanagement:ApiDiagnostic
    properties:
      alwaysLog: allErrors
      apiId: 57d1f7558aa04f15146d9d8a
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
      loggerId: /loggers/applicationinsights
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
$ pulumi import azure-native:apimanagement:ApiDiagnostic applicationinsights /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/apis/57d1f7558aa04f15146d9d8a/diagnostics/applicationinsights 
```
