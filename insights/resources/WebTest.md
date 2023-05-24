An Application Insights WebTest definition.
API Version: 2022-06-15.
Previous API Version: 2015-05-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### webTestCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var webTest = new AzureNative.Insights.WebTest("webTest", new()
    {
        Configuration = new AzureNative.Insights.Inputs.WebTestPropertiesConfigurationArgs
        {
            WebTest = "<WebTest Name=\"my-webtest\" Id=\"678ddf96-1ab8-44c8-9274-123456789abc\" Enabled=\"True\" CssProjectStructure=\"\" CssIteration=\"\" Timeout=\"120\" WorkItemIds=\"\" xmlns=\"http://microsoft.com/schemas/VisualStudio/TeamTest/2010\" Description=\"\" CredentialUserName=\"\" CredentialPassword=\"\" PreAuthenticate=\"True\" Proxy=\"default\" StopOnError=\"False\" RecordedResultFile=\"\" ResultsLocale=\"\" ><Items><Request Method=\"GET\" Guid=\"a4162485-9114-fcfc-e086-123456789abc\" Version=\"1.1\" Url=\"http://my-component.azurewebsites.net\" ThinkTime=\"0\" Timeout=\"120\" ParseDependentRequests=\"True\" FollowRedirects=\"True\" RecordResult=\"True\" Cache=\"False\" ResponseTimeGoal=\"0\" Encoding=\"utf-8\" ExpectedHttpStatusCode=\"200\" ExpectedResponseUrl=\"\" ReportingName=\"\" IgnoreHttpStatusCode=\"False\" /></Items></WebTest>",
        },
        Description = "Ping web test alert for mytestwebapp",
        Enabled = true,
        Frequency = 900,
        Kind = AzureNative.Insights.WebTestKind.Ping,
        Location = "South Central US",
        Locations = new[]
        {
            new AzureNative.Insights.Inputs.WebTestGeolocationArgs
            {
                Location = "us-fl-mia-edge",
            },
        },
        ResourceGroupName = "my-resource-group",
        RetryEnabled = true,
        SyntheticMonitorId = "my-webtest-my-component",
        Timeout = 120,
        WebTestKind = AzureNative.Insights.WebTestKind.Ping,
        WebTestName = "my-webtest-my-component",
    });

});


```

```go
package main

import (
	insights "github.com/pulumi/pulumi-azure-native-sdk/insights"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := insights.NewWebTest(ctx, "webTest", &insights.WebTestArgs{
			Configuration: &insights.WebTestPropertiesConfigurationArgs{
				WebTest: pulumi.String("<WebTest Name=\"my-webtest\" Id=\"678ddf96-1ab8-44c8-9274-123456789abc\" Enabled=\"True\" CssProjectStructure=\"\" CssIteration=\"\" Timeout=\"120\" WorkItemIds=\"\" xmlns=\"http://microsoft.com/schemas/VisualStudio/TeamTest/2010\" Description=\"\" CredentialUserName=\"\" CredentialPassword=\"\" PreAuthenticate=\"True\" Proxy=\"default\" StopOnError=\"False\" RecordedResultFile=\"\" ResultsLocale=\"\" ><Items><Request Method=\"GET\" Guid=\"a4162485-9114-fcfc-e086-123456789abc\" Version=\"1.1\" Url=\"http://my-component.azurewebsites.net\" ThinkTime=\"0\" Timeout=\"120\" ParseDependentRequests=\"True\" FollowRedirects=\"True\" RecordResult=\"True\" Cache=\"False\" ResponseTimeGoal=\"0\" Encoding=\"utf-8\" ExpectedHttpStatusCode=\"200\" ExpectedResponseUrl=\"\" ReportingName=\"\" IgnoreHttpStatusCode=\"False\" /></Items></WebTest>"),
			},
			Description: pulumi.String("Ping web test alert for mytestwebapp"),
			Enabled:     pulumi.Bool(true),
			Frequency:   pulumi.Int(900),
			Kind:        insights.WebTestKindPing,
			Location:    pulumi.String("South Central US"),
			Locations: []insights.WebTestGeolocationArgs{
				{
					Location: pulumi.String("us-fl-mia-edge"),
				},
			},
			ResourceGroupName:  pulumi.String("my-resource-group"),
			RetryEnabled:       pulumi.Bool(true),
			SyntheticMonitorId: pulumi.String("my-webtest-my-component"),
			Timeout:            pulumi.Int(120),
			WebTestKind:        insights.WebTestKindPing,
			WebTestName:        pulumi.String("my-webtest-my-component"),
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
import com.pulumi.azurenative.insights.WebTest;
import com.pulumi.azurenative.insights.WebTestArgs;
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
        var webTest = new WebTest("webTest", WebTestArgs.builder()        
            .configuration(Map.of("webTest", "<WebTest Name=\"my-webtest\" Id=\"678ddf96-1ab8-44c8-9274-123456789abc\" Enabled=\"True\" CssProjectStructure=\"\" CssIteration=\"\" Timeout=\"120\" WorkItemIds=\"\" xmlns=\"http://microsoft.com/schemas/VisualStudio/TeamTest/2010\" Description=\"\" CredentialUserName=\"\" CredentialPassword=\"\" PreAuthenticate=\"True\" Proxy=\"default\" StopOnError=\"False\" RecordedResultFile=\"\" ResultsLocale=\"\" ><Items><Request Method=\"GET\" Guid=\"a4162485-9114-fcfc-e086-123456789abc\" Version=\"1.1\" Url=\"http://my-component.azurewebsites.net\" ThinkTime=\"0\" Timeout=\"120\" ParseDependentRequests=\"True\" FollowRedirects=\"True\" RecordResult=\"True\" Cache=\"False\" ResponseTimeGoal=\"0\" Encoding=\"utf-8\" ExpectedHttpStatusCode=\"200\" ExpectedResponseUrl=\"\" ReportingName=\"\" IgnoreHttpStatusCode=\"False\" /></Items></WebTest>"))
            .description("Ping web test alert for mytestwebapp")
            .enabled(true)
            .frequency(900)
            .kind("ping")
            .location("South Central US")
            .locations(Map.of("location", "us-fl-mia-edge"))
            .resourceGroupName("my-resource-group")
            .retryEnabled(true)
            .syntheticMonitorId("my-webtest-my-component")
            .timeout(120)
            .webTestKind("ping")
            .webTestName("my-webtest-my-component")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const webTest = new azure_native.insights.WebTest("webTest", {
    configuration: {
        webTest: "<WebTest Name=\"my-webtest\" Id=\"678ddf96-1ab8-44c8-9274-123456789abc\" Enabled=\"True\" CssProjectStructure=\"\" CssIteration=\"\" Timeout=\"120\" WorkItemIds=\"\" xmlns=\"http://microsoft.com/schemas/VisualStudio/TeamTest/2010\" Description=\"\" CredentialUserName=\"\" CredentialPassword=\"\" PreAuthenticate=\"True\" Proxy=\"default\" StopOnError=\"False\" RecordedResultFile=\"\" ResultsLocale=\"\" ><Items><Request Method=\"GET\" Guid=\"a4162485-9114-fcfc-e086-123456789abc\" Version=\"1.1\" Url=\"http://my-component.azurewebsites.net\" ThinkTime=\"0\" Timeout=\"120\" ParseDependentRequests=\"True\" FollowRedirects=\"True\" RecordResult=\"True\" Cache=\"False\" ResponseTimeGoal=\"0\" Encoding=\"utf-8\" ExpectedHttpStatusCode=\"200\" ExpectedResponseUrl=\"\" ReportingName=\"\" IgnoreHttpStatusCode=\"False\" /></Items></WebTest>",
    },
    description: "Ping web test alert for mytestwebapp",
    enabled: true,
    frequency: 900,
    kind: azure_native.insights.WebTestKind.Ping,
    location: "South Central US",
    locations: [{
        location: "us-fl-mia-edge",
    }],
    resourceGroupName: "my-resource-group",
    retryEnabled: true,
    syntheticMonitorId: "my-webtest-my-component",
    timeout: 120,
    webTestKind: azure_native.insights.WebTestKind.Ping,
    webTestName: "my-webtest-my-component",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

web_test = azure_native.insights.WebTest("webTest",
    configuration=azure_native.insights.WebTestPropertiesConfigurationArgs(
        web_test="<WebTest Name=\"my-webtest\" Id=\"678ddf96-1ab8-44c8-9274-123456789abc\" Enabled=\"True\" CssProjectStructure=\"\" CssIteration=\"\" Timeout=\"120\" WorkItemIds=\"\" xmlns=\"http://microsoft.com/schemas/VisualStudio/TeamTest/2010\" Description=\"\" CredentialUserName=\"\" CredentialPassword=\"\" PreAuthenticate=\"True\" Proxy=\"default\" StopOnError=\"False\" RecordedResultFile=\"\" ResultsLocale=\"\" ><Items><Request Method=\"GET\" Guid=\"a4162485-9114-fcfc-e086-123456789abc\" Version=\"1.1\" Url=\"http://my-component.azurewebsites.net\" ThinkTime=\"0\" Timeout=\"120\" ParseDependentRequests=\"True\" FollowRedirects=\"True\" RecordResult=\"True\" Cache=\"False\" ResponseTimeGoal=\"0\" Encoding=\"utf-8\" ExpectedHttpStatusCode=\"200\" ExpectedResponseUrl=\"\" ReportingName=\"\" IgnoreHttpStatusCode=\"False\" /></Items></WebTest>",
    ),
    description="Ping web test alert for mytestwebapp",
    enabled=True,
    frequency=900,
    kind=azure_native.insights.WebTestKind.PING,
    location="South Central US",
    locations=[azure_native.insights.WebTestGeolocationArgs(
        location="us-fl-mia-edge",
    )],
    resource_group_name="my-resource-group",
    retry_enabled=True,
    synthetic_monitor_id="my-webtest-my-component",
    timeout=120,
    web_test_kind=azure_native.insights.WebTestKind.PING,
    web_test_name="my-webtest-my-component")

```

```yaml
resources:
  webTest:
    type: azure-native:insights:WebTest
    properties:
      configuration:
        webTest: <WebTest Name="my-webtest" Id="678ddf96-1ab8-44c8-9274-123456789abc" Enabled="True" CssProjectStructure="" CssIteration="" Timeout="120" WorkItemIds="" xmlns="http://microsoft.com/schemas/VisualStudio/TeamTest/2010" Description="" CredentialUserName="" CredentialPassword="" PreAuthenticate="True" Proxy="default" StopOnError="False" RecordedResultFile="" ResultsLocale="" ><Items><Request Method="GET" Guid="a4162485-9114-fcfc-e086-123456789abc" Version="1.1" Url="http://my-component.azurewebsites.net" ThinkTime="0" Timeout="120" ParseDependentRequests="True" FollowRedirects="True" RecordResult="True" Cache="False" ResponseTimeGoal="0" Encoding="utf-8" ExpectedHttpStatusCode="200" ExpectedResponseUrl="" ReportingName="" IgnoreHttpStatusCode="False" /></Items></WebTest>
      description: Ping web test alert for mytestwebapp
      enabled: true
      frequency: 900
      kind: ping
      location: South Central US
      locations:
        - location: us-fl-mia-edge
      resourceGroupName: my-resource-group
      retryEnabled: true
      syntheticMonitorId: my-webtest-my-component
      timeout: 120
      webTestKind: ping
      webTestName: my-webtest-my-component

```

{{% /example %}}
{{% example %}}
### webTestCreateStandard
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var webTest = new AzureNative.Insights.WebTest("webTest", new()
    {
        Description = "Ping web test alert for mytestwebapp",
        Enabled = true,
        Frequency = 900,
        Location = "South Central US",
        Locations = new[]
        {
            new AzureNative.Insights.Inputs.WebTestGeolocationArgs
            {
                Location = "us-fl-mia-edge",
            },
        },
        Request = new AzureNative.Insights.Inputs.WebTestPropertiesRequestArgs
        {
            Headers = new[]
            {
                new AzureNative.Insights.Inputs.HeaderFieldArgs
                {
                    HeaderFieldName = "Content-Language",
                    HeaderFieldValue = "de-DE",
                },
                new AzureNative.Insights.Inputs.HeaderFieldArgs
                {
                    HeaderFieldName = "Accept-Language",
                    HeaderFieldValue = "de-DE",
                },
            },
            HttpVerb = "POST",
            RequestBody = "SGVsbG8gd29ybGQ=",
            RequestUrl = "https://bing.com",
        },
        ResourceGroupName = "my-resource-group",
        RetryEnabled = true,
        SyntheticMonitorId = "my-webtest-my-component",
        Timeout = 120,
        ValidationRules = new AzureNative.Insights.Inputs.WebTestPropertiesValidationRulesArgs
        {
            SSLCertRemainingLifetimeCheck = 100,
            SSLCheck = true,
        },
        WebTestKind = AzureNative.Insights.WebTestKind.Standard,
        WebTestName = "my-webtest-my-component",
    });

});


```

```go
package main

import (
	insights "github.com/pulumi/pulumi-azure-native-sdk/insights"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := insights.NewWebTest(ctx, "webTest", &insights.WebTestArgs{
			Description: pulumi.String("Ping web test alert for mytestwebapp"),
			Enabled:     pulumi.Bool(true),
			Frequency:   pulumi.Int(900),
			Location:    pulumi.String("South Central US"),
			Locations: []insights.WebTestGeolocationArgs{
				{
					Location: pulumi.String("us-fl-mia-edge"),
				},
			},
			Request: insights.WebTestPropertiesResponseRequest{
				Headers: insights.HeaderFieldArray{
					&insights.HeaderFieldArgs{
						HeaderFieldName:  pulumi.String("Content-Language"),
						HeaderFieldValue: pulumi.String("de-DE"),
					},
					&insights.HeaderFieldArgs{
						HeaderFieldName:  pulumi.String("Accept-Language"),
						HeaderFieldValue: pulumi.String("de-DE"),
					},
				},
				HttpVerb:    pulumi.String("POST"),
				RequestBody: pulumi.String("SGVsbG8gd29ybGQ="),
				RequestUrl:  pulumi.String("https://bing.com"),
			},
			ResourceGroupName:  pulumi.String("my-resource-group"),
			RetryEnabled:       pulumi.Bool(true),
			SyntheticMonitorId: pulumi.String("my-webtest-my-component"),
			Timeout:            pulumi.Int(120),
			ValidationRules: &insights.WebTestPropertiesValidationRulesArgs{
				SSLCertRemainingLifetimeCheck: pulumi.Int(100),
				SSLCheck:                      pulumi.Bool(true),
			},
			WebTestKind: insights.WebTestKindStandard,
			WebTestName: pulumi.String("my-webtest-my-component"),
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
import com.pulumi.azurenative.insights.WebTest;
import com.pulumi.azurenative.insights.WebTestArgs;
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
        var webTest = new WebTest("webTest", WebTestArgs.builder()        
            .description("Ping web test alert for mytestwebapp")
            .enabled(true)
            .frequency(900)
            .location("South Central US")
            .locations(Map.of("location", "us-fl-mia-edge"))
            .request(Map.ofEntries(
                Map.entry("headers",                 
                    Map.ofEntries(
                        Map.entry("headerFieldName", "Content-Language"),
                        Map.entry("headerFieldValue", "de-DE")
                    ),
                    Map.ofEntries(
                        Map.entry("headerFieldName", "Accept-Language"),
                        Map.entry("headerFieldValue", "de-DE")
                    )),
                Map.entry("httpVerb", "POST"),
                Map.entry("requestBody", "SGVsbG8gd29ybGQ="),
                Map.entry("requestUrl", "https://bing.com")
            ))
            .resourceGroupName("my-resource-group")
            .retryEnabled(true)
            .syntheticMonitorId("my-webtest-my-component")
            .timeout(120)
            .validationRules(Map.ofEntries(
                Map.entry("sSLCertRemainingLifetimeCheck", 100),
                Map.entry("sSLCheck", true)
            ))
            .webTestKind("standard")
            .webTestName("my-webtest-my-component")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const webTest = new azure_native.insights.WebTest("webTest", {
    description: "Ping web test alert for mytestwebapp",
    enabled: true,
    frequency: 900,
    location: "South Central US",
    locations: [{
        location: "us-fl-mia-edge",
    }],
    request: {
        headers: [
            {
                headerFieldName: "Content-Language",
                headerFieldValue: "de-DE",
            },
            {
                headerFieldName: "Accept-Language",
                headerFieldValue: "de-DE",
            },
        ],
        httpVerb: "POST",
        requestBody: "SGVsbG8gd29ybGQ=",
        requestUrl: "https://bing.com",
    },
    resourceGroupName: "my-resource-group",
    retryEnabled: true,
    syntheticMonitorId: "my-webtest-my-component",
    timeout: 120,
    validationRules: {
        sSLCertRemainingLifetimeCheck: 100,
        sSLCheck: true,
    },
    webTestKind: azure_native.insights.WebTestKind.Standard,
    webTestName: "my-webtest-my-component",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

web_test = azure_native.insights.WebTest("webTest",
    description="Ping web test alert for mytestwebapp",
    enabled=True,
    frequency=900,
    location="South Central US",
    locations=[azure_native.insights.WebTestGeolocationArgs(
        location="us-fl-mia-edge",
    )],
    request=azure_native.insights.WebTestPropertiesResponseRequestArgs(
        headers=[
            azure_native.insights.HeaderFieldArgs(
                header_field_name="Content-Language",
                header_field_value="de-DE",
            ),
            azure_native.insights.HeaderFieldArgs(
                header_field_name="Accept-Language",
                header_field_value="de-DE",
            ),
        ],
        http_verb="POST",
        request_body="SGVsbG8gd29ybGQ=",
        request_url="https://bing.com",
    ),
    resource_group_name="my-resource-group",
    retry_enabled=True,
    synthetic_monitor_id="my-webtest-my-component",
    timeout=120,
    validation_rules=azure_native.insights.WebTestPropertiesValidationRulesArgs(
        s_sl_cert_remaining_lifetime_check=100,
        s_sl_check=True,
    ),
    web_test_kind=azure_native.insights.WebTestKind.STANDARD,
    web_test_name="my-webtest-my-component")

```

```yaml
resources:
  webTest:
    type: azure-native:insights:WebTest
    properties:
      description: Ping web test alert for mytestwebapp
      enabled: true
      frequency: 900
      location: South Central US
      locations:
        - location: us-fl-mia-edge
      request:
        headers:
          - headerFieldName: Content-Language
            headerFieldValue: de-DE
          - headerFieldName: Accept-Language
            headerFieldValue: de-DE
        httpVerb: POST
        requestBody: SGVsbG8gd29ybGQ=
        requestUrl: https://bing.com
      resourceGroupName: my-resource-group
      retryEnabled: true
      syntheticMonitorId: my-webtest-my-component
      timeout: 120
      validationRules:
        sSLCertRemainingLifetimeCheck: 100
        sSLCheck: true
      webTestKind: standard
      webTestName: my-webtest-my-component

```

{{% /example %}}
{{% example %}}
### webTestUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var webTest = new AzureNative.Insights.WebTest("webTest", new()
    {
        Configuration = new AzureNative.Insights.Inputs.WebTestPropertiesConfigurationArgs
        {
            WebTest = "<WebTest Name=\"my-webtest\" Id=\"678ddf96-1ab8-44c8-9274-123456789abc\" Enabled=\"True\" CssProjectStructure=\"\" CssIteration=\"\" Timeout=\"30\" WorkItemIds=\"\" xmlns=\"http://microsoft.com/schemas/VisualStudio/TeamTest/2010\" Description=\"\" CredentialUserName=\"\" CredentialPassword=\"\" PreAuthenticate=\"True\" Proxy=\"default\" StopOnError=\"False\" RecordedResultFile=\"\" ResultsLocale=\"\" ><Items><Request Method=\"GET\" Guid=\"a4162485-9114-fcfc-e086-123456789abc\" Version=\"1.1\" Url=\"http://my-component.azurewebsites.net\" ThinkTime=\"0\" Timeout=\"30\" ParseDependentRequests=\"True\" FollowRedirects=\"True\" RecordResult=\"True\" Cache=\"False\" ResponseTimeGoal=\"0\" Encoding=\"utf-8\" ExpectedHttpStatusCode=\"200\" ExpectedResponseUrl=\"\" ReportingName=\"\" IgnoreHttpStatusCode=\"False\" /></Items></WebTest>",
        },
        Frequency = 600,
        Kind = AzureNative.Insights.WebTestKind.Ping,
        Location = "South Central US",
        Locations = new[]
        {
            new AzureNative.Insights.Inputs.WebTestGeolocationArgs
            {
                Location = "us-fl-mia-edge",
            },
            new AzureNative.Insights.Inputs.WebTestGeolocationArgs
            {
                Location = "apac-hk-hkn-azr",
            },
        },
        ResourceGroupName = "my-resource-group",
        SyntheticMonitorId = "my-webtest-my-component",
        Timeout = 30,
        WebTestKind = AzureNative.Insights.WebTestKind.Ping,
        WebTestName = "my-webtest-my-component",
    });

});


```

```go
package main

import (
	insights "github.com/pulumi/pulumi-azure-native-sdk/insights"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := insights.NewWebTest(ctx, "webTest", &insights.WebTestArgs{
			Configuration: &insights.WebTestPropertiesConfigurationArgs{
				WebTest: pulumi.String("<WebTest Name=\"my-webtest\" Id=\"678ddf96-1ab8-44c8-9274-123456789abc\" Enabled=\"True\" CssProjectStructure=\"\" CssIteration=\"\" Timeout=\"30\" WorkItemIds=\"\" xmlns=\"http://microsoft.com/schemas/VisualStudio/TeamTest/2010\" Description=\"\" CredentialUserName=\"\" CredentialPassword=\"\" PreAuthenticate=\"True\" Proxy=\"default\" StopOnError=\"False\" RecordedResultFile=\"\" ResultsLocale=\"\" ><Items><Request Method=\"GET\" Guid=\"a4162485-9114-fcfc-e086-123456789abc\" Version=\"1.1\" Url=\"http://my-component.azurewebsites.net\" ThinkTime=\"0\" Timeout=\"30\" ParseDependentRequests=\"True\" FollowRedirects=\"True\" RecordResult=\"True\" Cache=\"False\" ResponseTimeGoal=\"0\" Encoding=\"utf-8\" ExpectedHttpStatusCode=\"200\" ExpectedResponseUrl=\"\" ReportingName=\"\" IgnoreHttpStatusCode=\"False\" /></Items></WebTest>"),
			},
			Frequency: pulumi.Int(600),
			Kind:      insights.WebTestKindPing,
			Location:  pulumi.String("South Central US"),
			Locations: []insights.WebTestGeolocationArgs{
				{
					Location: pulumi.String("us-fl-mia-edge"),
				},
				{
					Location: pulumi.String("apac-hk-hkn-azr"),
				},
			},
			ResourceGroupName:  pulumi.String("my-resource-group"),
			SyntheticMonitorId: pulumi.String("my-webtest-my-component"),
			Timeout:            pulumi.Int(30),
			WebTestKind:        insights.WebTestKindPing,
			WebTestName:        pulumi.String("my-webtest-my-component"),
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
import com.pulumi.azurenative.insights.WebTest;
import com.pulumi.azurenative.insights.WebTestArgs;
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
        var webTest = new WebTest("webTest", WebTestArgs.builder()        
            .configuration(Map.of("webTest", "<WebTest Name=\"my-webtest\" Id=\"678ddf96-1ab8-44c8-9274-123456789abc\" Enabled=\"True\" CssProjectStructure=\"\" CssIteration=\"\" Timeout=\"30\" WorkItemIds=\"\" xmlns=\"http://microsoft.com/schemas/VisualStudio/TeamTest/2010\" Description=\"\" CredentialUserName=\"\" CredentialPassword=\"\" PreAuthenticate=\"True\" Proxy=\"default\" StopOnError=\"False\" RecordedResultFile=\"\" ResultsLocale=\"\" ><Items><Request Method=\"GET\" Guid=\"a4162485-9114-fcfc-e086-123456789abc\" Version=\"1.1\" Url=\"http://my-component.azurewebsites.net\" ThinkTime=\"0\" Timeout=\"30\" ParseDependentRequests=\"True\" FollowRedirects=\"True\" RecordResult=\"True\" Cache=\"False\" ResponseTimeGoal=\"0\" Encoding=\"utf-8\" ExpectedHttpStatusCode=\"200\" ExpectedResponseUrl=\"\" ReportingName=\"\" IgnoreHttpStatusCode=\"False\" /></Items></WebTest>"))
            .frequency(600)
            .kind("ping")
            .location("South Central US")
            .locations(            
                Map.of("location", "us-fl-mia-edge"),
                Map.of("location", "apac-hk-hkn-azr"))
            .resourceGroupName("my-resource-group")
            .syntheticMonitorId("my-webtest-my-component")
            .timeout(30)
            .webTestKind("ping")
            .webTestName("my-webtest-my-component")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const webTest = new azure_native.insights.WebTest("webTest", {
    configuration: {
        webTest: "<WebTest Name=\"my-webtest\" Id=\"678ddf96-1ab8-44c8-9274-123456789abc\" Enabled=\"True\" CssProjectStructure=\"\" CssIteration=\"\" Timeout=\"30\" WorkItemIds=\"\" xmlns=\"http://microsoft.com/schemas/VisualStudio/TeamTest/2010\" Description=\"\" CredentialUserName=\"\" CredentialPassword=\"\" PreAuthenticate=\"True\" Proxy=\"default\" StopOnError=\"False\" RecordedResultFile=\"\" ResultsLocale=\"\" ><Items><Request Method=\"GET\" Guid=\"a4162485-9114-fcfc-e086-123456789abc\" Version=\"1.1\" Url=\"http://my-component.azurewebsites.net\" ThinkTime=\"0\" Timeout=\"30\" ParseDependentRequests=\"True\" FollowRedirects=\"True\" RecordResult=\"True\" Cache=\"False\" ResponseTimeGoal=\"0\" Encoding=\"utf-8\" ExpectedHttpStatusCode=\"200\" ExpectedResponseUrl=\"\" ReportingName=\"\" IgnoreHttpStatusCode=\"False\" /></Items></WebTest>",
    },
    frequency: 600,
    kind: azure_native.insights.WebTestKind.Ping,
    location: "South Central US",
    locations: [
        {
            location: "us-fl-mia-edge",
        },
        {
            location: "apac-hk-hkn-azr",
        },
    ],
    resourceGroupName: "my-resource-group",
    syntheticMonitorId: "my-webtest-my-component",
    timeout: 30,
    webTestKind: azure_native.insights.WebTestKind.Ping,
    webTestName: "my-webtest-my-component",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

web_test = azure_native.insights.WebTest("webTest",
    configuration=azure_native.insights.WebTestPropertiesConfigurationArgs(
        web_test="<WebTest Name=\"my-webtest\" Id=\"678ddf96-1ab8-44c8-9274-123456789abc\" Enabled=\"True\" CssProjectStructure=\"\" CssIteration=\"\" Timeout=\"30\" WorkItemIds=\"\" xmlns=\"http://microsoft.com/schemas/VisualStudio/TeamTest/2010\" Description=\"\" CredentialUserName=\"\" CredentialPassword=\"\" PreAuthenticate=\"True\" Proxy=\"default\" StopOnError=\"False\" RecordedResultFile=\"\" ResultsLocale=\"\" ><Items><Request Method=\"GET\" Guid=\"a4162485-9114-fcfc-e086-123456789abc\" Version=\"1.1\" Url=\"http://my-component.azurewebsites.net\" ThinkTime=\"0\" Timeout=\"30\" ParseDependentRequests=\"True\" FollowRedirects=\"True\" RecordResult=\"True\" Cache=\"False\" ResponseTimeGoal=\"0\" Encoding=\"utf-8\" ExpectedHttpStatusCode=\"200\" ExpectedResponseUrl=\"\" ReportingName=\"\" IgnoreHttpStatusCode=\"False\" /></Items></WebTest>",
    ),
    frequency=600,
    kind=azure_native.insights.WebTestKind.PING,
    location="South Central US",
    locations=[
        azure_native.insights.WebTestGeolocationArgs(
            location="us-fl-mia-edge",
        ),
        azure_native.insights.WebTestGeolocationArgs(
            location="apac-hk-hkn-azr",
        ),
    ],
    resource_group_name="my-resource-group",
    synthetic_monitor_id="my-webtest-my-component",
    timeout=30,
    web_test_kind=azure_native.insights.WebTestKind.PING,
    web_test_name="my-webtest-my-component")

```

```yaml
resources:
  webTest:
    type: azure-native:insights:WebTest
    properties:
      configuration:
        webTest: <WebTest Name="my-webtest" Id="678ddf96-1ab8-44c8-9274-123456789abc" Enabled="True" CssProjectStructure="" CssIteration="" Timeout="30" WorkItemIds="" xmlns="http://microsoft.com/schemas/VisualStudio/TeamTest/2010" Description="" CredentialUserName="" CredentialPassword="" PreAuthenticate="True" Proxy="default" StopOnError="False" RecordedResultFile="" ResultsLocale="" ><Items><Request Method="GET" Guid="a4162485-9114-fcfc-e086-123456789abc" Version="1.1" Url="http://my-component.azurewebsites.net" ThinkTime="0" Timeout="30" ParseDependentRequests="True" FollowRedirects="True" RecordResult="True" Cache="False" ResponseTimeGoal="0" Encoding="utf-8" ExpectedHttpStatusCode="200" ExpectedResponseUrl="" ReportingName="" IgnoreHttpStatusCode="False" /></Items></WebTest>
      frequency: 600
      kind: ping
      location: South Central US
      locations:
        - location: us-fl-mia-edge
        - location: apac-hk-hkn-azr
      resourceGroupName: my-resource-group
      syntheticMonitorId: my-webtest-my-component
      timeout: 30
      webTestKind: ping
      webTestName: my-webtest-my-component

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:insights:WebTest my-webtest-my-component /subscriptions/subid/resourceGroups/my-resource-group/providers/Microsoft.Insights/webtests/my-webtest-my-component 
```
