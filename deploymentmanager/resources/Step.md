The resource representation of a rollout step.
API Version: 2019-11-01-preview.
Previous API Version: 2019-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create health check step
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var step = new AzureNative.DeploymentManager.Step("step", new()
    {
        Location = "centralus",
        Properties = new AzureNative.DeploymentManager.Inputs.HealthCheckStepPropertiesArgs
        {
            Attributes = new AzureNative.DeploymentManager.Inputs.RestHealthCheckStepAttributesArgs
            {
                HealthChecks = new[]
                {
                    new AzureNative.DeploymentManager.Inputs.RestHealthCheckArgs
                    {
                        Name = "appHealth",
                        Request = new AzureNative.DeploymentManager.Inputs.RestRequestArgs
                        {
                            Authentication = new AzureNative.DeploymentManager.Inputs.ApiKeyAuthenticationArgs
                            {
                                In = AzureNative.DeploymentManager.RestAuthLocation.Query,
                                Name = "Code",
                                Type = "ApiKey",
                                Value = "NBCapiMOBQyAAbCkeytoPadnvO0eGHmidwFz5rXpappznKp3Jt7LLg==",
                            },
                            Method = AzureNative.DeploymentManager.RestRequestMethod.GET,
                            Uri = "https://resthealth.healthservice.com/api/applications/contosoApp/healthStatus",
                        },
                        Response = new AzureNative.DeploymentManager.Inputs.RestResponseArgs
                        {
                            Regex = new AzureNative.DeploymentManager.Inputs.RestResponseRegexArgs
                            {
                                MatchQuantifier = AzureNative.DeploymentManager.RestMatchQuantifier.All,
                                Matches = new[]
                                {
                                    "(?i)Contoso-App",
                                    @"(?i)""health_status"":((.|
)*)""(green|yellow)""",
                                    "(?mi)^(\"application_host\": 94781052)$",
                                },
                            },
                            SuccessStatusCodes = new[]
                            {
                                "OK",
                            },
                        },
                    },
                    new AzureNative.DeploymentManager.Inputs.RestHealthCheckArgs
                    {
                        Name = "serviceHealth",
                        Request = new AzureNative.DeploymentManager.Inputs.RestRequestArgs
                        {
                            Authentication = new AzureNative.DeploymentManager.Inputs.ApiKeyAuthenticationArgs
                            {
                                In = AzureNative.DeploymentManager.RestAuthLocation.Header,
                                Name = "code",
                                Type = "ApiKey",
                                Value = "NBCapiMOBQyAAbCkeytoPadnvO0eGHmidwFz5rXpappznKp3Jt7LLg==",
                            },
                            Method = AzureNative.DeploymentManager.RestRequestMethod.GET,
                            Uri = "https://resthealth.healthservice.com/api/services/contosoService/healthStatus",
                        },
                        Response = new AzureNative.DeploymentManager.Inputs.RestResponseArgs
                        {
                            Regex = new AzureNative.DeploymentManager.Inputs.RestResponseRegexArgs
                            {
                                MatchQuantifier = AzureNative.DeploymentManager.RestMatchQuantifier.All,
                                Matches = new[]
                                {
                                    "(?i)Contoso-Service-EndToEnd",
                                    @"(?i)""health_status"":((.|
)*)""(green)""",
                                },
                            },
                            SuccessStatusCodes = new[]
                            {
                                "OK",
                            },
                        },
                    },
                },
                HealthyStateDuration = "PT2H",
                MaxElasticDuration = "PT30M",
                Type = "REST",
                WaitDuration = "PT15M",
            },
            StepType = "HealthCheck",
        },
        ResourceGroupName = "myResourceGroup",
        StepName = "healthCheckStep",
        Tags = null,
    });

});


```

```go
package main

import (
	deploymentmanager "github.com/pulumi/pulumi-azure-native-sdk/deploymentmanager"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := deploymentmanager.NewStep(ctx, "step", &deploymentmanager.StepArgs{
			Location: pulumi.String("centralus"),
			Properties: deploymentmanager.HealthCheckStepProperties{
				Attributes: deploymentmanager.RestHealthCheckStepAttributes{
					HealthChecks: []deploymentmanager.RestHealthCheck{
						{
							Name: "appHealth",
							Request: {
								Authentication: {
									In:    deploymentmanager.RestAuthLocationQuery,
									Name:  "Code",
									Type:  "ApiKey",
									Value: "NBCapiMOBQyAAbCkeytoPadnvO0eGHmidwFz5rXpappznKp3Jt7LLg==",
								},
								Method: deploymentmanager.RestRequestMethodGET,
								Uri:    "https://resthealth.healthservice.com/api/applications/contosoApp/healthStatus",
							},
							Response: {
								Regex: {
									MatchQuantifier: deploymentmanager.RestMatchQuantifierAll,
									Matches: []string{
										"(?i)Contoso-App",
										"(?i)\"health_status\":((.|\n)*)\"(green|yellow)\"",
										"(?mi)^(\"application_host\": 94781052)$",
									},
								},
								SuccessStatusCodes: []string{
									"OK",
								},
							},
						},
						{
							Name: "serviceHealth",
							Request: {
								Authentication: {
									In:    deploymentmanager.RestAuthLocationHeader,
									Name:  "code",
									Type:  "ApiKey",
									Value: "NBCapiMOBQyAAbCkeytoPadnvO0eGHmidwFz5rXpappznKp3Jt7LLg==",
								},
								Method: deploymentmanager.RestRequestMethodGET,
								Uri:    "https://resthealth.healthservice.com/api/services/contosoService/healthStatus",
							},
							Response: {
								Regex: {
									MatchQuantifier: deploymentmanager.RestMatchQuantifierAll,
									Matches: []string{
										"(?i)Contoso-Service-EndToEnd",
										"(?i)\"health_status\":((.|\n)*)\"(green)\"",
									},
								},
								SuccessStatusCodes: []string{
									"OK",
								},
							},
						},
					},
					HealthyStateDuration: "PT2H",
					MaxElasticDuration:   "PT30M",
					Type:                 "REST",
					WaitDuration:         "PT15M",
				},
				StepType: "HealthCheck",
			},
			ResourceGroupName: pulumi.String("myResourceGroup"),
			StepName:          pulumi.String("healthCheckStep"),
			Tags:              nil,
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
import com.pulumi.azurenative.deploymentmanager.Step;
import com.pulumi.azurenative.deploymentmanager.StepArgs;
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
        var step = new Step("step", StepArgs.builder()        
            .location("centralus")
            .properties(Map.ofEntries(
                Map.entry("attributes", Map.ofEntries(
                    Map.entry("healthChecks",                     
                        Map.ofEntries(
                            Map.entry("name", "appHealth"),
                            Map.entry("request", Map.ofEntries(
                                Map.entry("authentication", Map.ofEntries(
                                    Map.entry("in", "Query"),
                                    Map.entry("name", "Code"),
                                    Map.entry("type", "ApiKey"),
                                    Map.entry("value", "NBCapiMOBQyAAbCkeytoPadnvO0eGHmidwFz5rXpappznKp3Jt7LLg==")
                                )),
                                Map.entry("method", "GET"),
                                Map.entry("uri", "https://resthealth.healthservice.com/api/applications/contosoApp/healthStatus")
                            )),
                            Map.entry("response", Map.ofEntries(
                                Map.entry("regex", Map.ofEntries(
                                    Map.entry("matchQuantifier", "All"),
                                    Map.entry("matches",                                     
                                        "(?i)Contoso-App",
                                        """
(?i)"health_status":((.|
)*)"(green|yellow)"                                        """,
                                        "(?mi)^(\"application_host\": 94781052)$")
                                )),
                                Map.entry("successStatusCodes", "OK")
                            ))
                        ),
                        Map.ofEntries(
                            Map.entry("name", "serviceHealth"),
                            Map.entry("request", Map.ofEntries(
                                Map.entry("authentication", Map.ofEntries(
                                    Map.entry("in", "Header"),
                                    Map.entry("name", "code"),
                                    Map.entry("type", "ApiKey"),
                                    Map.entry("value", "NBCapiMOBQyAAbCkeytoPadnvO0eGHmidwFz5rXpappznKp3Jt7LLg==")
                                )),
                                Map.entry("method", "GET"),
                                Map.entry("uri", "https://resthealth.healthservice.com/api/services/contosoService/healthStatus")
                            )),
                            Map.entry("response", Map.ofEntries(
                                Map.entry("regex", Map.ofEntries(
                                    Map.entry("matchQuantifier", "All"),
                                    Map.entry("matches",                                     
                                        "(?i)Contoso-Service-EndToEnd",
                                        """
(?i)"health_status":((.|
)*)"(green)"                                        """)
                                )),
                                Map.entry("successStatusCodes", "OK")
                            ))
                        )),
                    Map.entry("healthyStateDuration", "PT2H"),
                    Map.entry("maxElasticDuration", "PT30M"),
                    Map.entry("type", "REST"),
                    Map.entry("waitDuration", "PT15M")
                )),
                Map.entry("stepType", "HealthCheck")
            ))
            .resourceGroupName("myResourceGroup")
            .stepName("healthCheckStep")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const step = new azure_native.deploymentmanager.Step("step", {
    location: "centralus",
    properties: {
        attributes: {
            healthChecks: [
                {
                    name: "appHealth",
                    request: {
                        authentication: {
                            "in": azure_native.deploymentmanager.RestAuthLocation.Query,
                            name: "Code",
                            type: "ApiKey",
                            value: "NBCapiMOBQyAAbCkeytoPadnvO0eGHmidwFz5rXpappznKp3Jt7LLg==",
                        },
                        method: azure_native.deploymentmanager.RestRequestMethod.GET,
                        uri: "https://resthealth.healthservice.com/api/applications/contosoApp/healthStatus",
                    },
                    response: {
                        regex: {
                            matchQuantifier: azure_native.deploymentmanager.RestMatchQuantifier.All,
                            matches: [
                                "(?i)Contoso-App",
                                `(?i)"health_status":((.|
)*)"(green|yellow)"`,
                                "(?mi)^(\"application_host\": 94781052)$",
                            ],
                        },
                        successStatusCodes: ["OK"],
                    },
                },
                {
                    name: "serviceHealth",
                    request: {
                        authentication: {
                            "in": azure_native.deploymentmanager.RestAuthLocation.Header,
                            name: "code",
                            type: "ApiKey",
                            value: "NBCapiMOBQyAAbCkeytoPadnvO0eGHmidwFz5rXpappznKp3Jt7LLg==",
                        },
                        method: azure_native.deploymentmanager.RestRequestMethod.GET,
                        uri: "https://resthealth.healthservice.com/api/services/contosoService/healthStatus",
                    },
                    response: {
                        regex: {
                            matchQuantifier: azure_native.deploymentmanager.RestMatchQuantifier.All,
                            matches: [
                                "(?i)Contoso-Service-EndToEnd",
                                `(?i)"health_status":((.|
)*)"(green)"`,
                            ],
                        },
                        successStatusCodes: ["OK"],
                    },
                },
            ],
            healthyStateDuration: "PT2H",
            maxElasticDuration: "PT30M",
            type: "REST",
            waitDuration: "PT15M",
        },
        stepType: "HealthCheck",
    },
    resourceGroupName: "myResourceGroup",
    stepName: "healthCheckStep",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

step = azure_native.deploymentmanager.Step("step",
    location="centralus",
    properties=azure_native.deploymentmanager.HealthCheckStepPropertiesArgs(
        attributes=azure_native.deploymentmanager.RestHealthCheckStepAttributesArgs(
            health_checks=[
                azure_native.deploymentmanager.RestHealthCheckArgs(
                    name="appHealth",
                    request=azure_native.deploymentmanager.RestRequestArgs(
                        authentication=azure_native.deploymentmanager.ApiKeyAuthenticationArgs(
                            in_=azure_native.deploymentmanager.RestAuthLocation.QUERY,
                            name="Code",
                            type="ApiKey",
                            value="NBCapiMOBQyAAbCkeytoPadnvO0eGHmidwFz5rXpappznKp3Jt7LLg==",
                        ),
                        method=azure_native.deploymentmanager.RestRequestMethod.GET,
                        uri="https://resthealth.healthservice.com/api/applications/contosoApp/healthStatus",
                    ),
                    response=azure_native.deploymentmanager.RestResponseArgs(
                        regex=azure_native.deploymentmanager.RestResponseRegexArgs(
                            match_quantifier=azure_native.deploymentmanager.RestMatchQuantifier.ALL,
                            matches=[
                                "(?i)Contoso-App",
                                """(?i)"health_status":((.|
)*)"(green|yellow)"""",
                                "(?mi)^(\"application_host\": 94781052)$",
                            ],
                        ),
                        success_status_codes=["OK"],
                    ),
                ),
                azure_native.deploymentmanager.RestHealthCheckArgs(
                    name="serviceHealth",
                    request=azure_native.deploymentmanager.RestRequestArgs(
                        authentication=azure_native.deploymentmanager.ApiKeyAuthenticationArgs(
                            in_=azure_native.deploymentmanager.RestAuthLocation.HEADER,
                            name="code",
                            type="ApiKey",
                            value="NBCapiMOBQyAAbCkeytoPadnvO0eGHmidwFz5rXpappznKp3Jt7LLg==",
                        ),
                        method=azure_native.deploymentmanager.RestRequestMethod.GET,
                        uri="https://resthealth.healthservice.com/api/services/contosoService/healthStatus",
                    ),
                    response=azure_native.deploymentmanager.RestResponseArgs(
                        regex=azure_native.deploymentmanager.RestResponseRegexArgs(
                            match_quantifier=azure_native.deploymentmanager.RestMatchQuantifier.ALL,
                            matches=[
                                "(?i)Contoso-Service-EndToEnd",
                                """(?i)"health_status":((.|
)*)"(green)"""",
                            ],
                        ),
                        success_status_codes=["OK"],
                    ),
                ),
            ],
            healthy_state_duration="PT2H",
            max_elastic_duration="PT30M",
            type="REST",
            wait_duration="PT15M",
        ),
        step_type="HealthCheck",
    ),
    resource_group_name="myResourceGroup",
    step_name="healthCheckStep",
    tags={})

```

```yaml
resources:
  step:
    type: azure-native:deploymentmanager:Step
    properties:
      location: centralus
      properties:
        attributes:
          healthChecks:
            - name: appHealth
              request:
                authentication:
                  in: Query
                  name: Code
                  type: ApiKey
                  value: NBCapiMOBQyAAbCkeytoPadnvO0eGHmidwFz5rXpappznKp3Jt7LLg==
                method: GET
                uri: https://resthealth.healthservice.com/api/applications/contosoApp/healthStatus
              response:
                regex:
                  matchQuantifier: All
                  matches:
                    - (?i)Contoso-App
                    - |-
                      (?i)"health_status":((.|
                      )*)"(green|yellow)"
                    - '(?mi)^("application_host": 94781052)$'
                successStatusCodes:
                  - OK
            - name: serviceHealth
              request:
                authentication:
                  in: Header
                  name: code
                  type: ApiKey
                  value: NBCapiMOBQyAAbCkeytoPadnvO0eGHmidwFz5rXpappznKp3Jt7LLg==
                method: GET
                uri: https://resthealth.healthservice.com/api/services/contosoService/healthStatus
              response:
                regex:
                  matchQuantifier: All
                  matches:
                    - (?i)Contoso-Service-EndToEnd
                    - |-
                      (?i)"health_status":((.|
                      )*)"(green)"
                successStatusCodes:
                  - OK
          healthyStateDuration: PT2H
          maxElasticDuration: PT30M
          type: REST
          waitDuration: PT15M
        stepType: HealthCheck
      resourceGroupName: myResourceGroup
      stepName: healthCheckStep
      tags: {}

```

{{% /example %}}
{{% example %}}
### Create wait step
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var step = new AzureNative.DeploymentManager.Step("step", new()
    {
        Location = "centralus",
        Properties = new AzureNative.DeploymentManager.Inputs.WaitStepPropertiesArgs
        {
            Attributes = new AzureNative.DeploymentManager.Inputs.WaitStepAttributesArgs
            {
                Duration = "PT20M",
            },
            StepType = "Wait",
        },
        ResourceGroupName = "myResourceGroup",
        StepName = "waitStep",
        Tags = null,
    });

});


```

```go
package main

import (
	deploymentmanager "github.com/pulumi/pulumi-azure-native-sdk/deploymentmanager"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := deploymentmanager.NewStep(ctx, "step", &deploymentmanager.StepArgs{
			Location: pulumi.String("centralus"),
			Properties: deploymentmanager.WaitStepProperties{
				Attributes: deploymentmanager.WaitStepAttributes{
					Duration: "PT20M",
				},
				StepType: "Wait",
			},
			ResourceGroupName: pulumi.String("myResourceGroup"),
			StepName:          pulumi.String("waitStep"),
			Tags:              nil,
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
import com.pulumi.azurenative.deploymentmanager.Step;
import com.pulumi.azurenative.deploymentmanager.StepArgs;
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
        var step = new Step("step", StepArgs.builder()        
            .location("centralus")
            .properties(Map.ofEntries(
                Map.entry("attributes", Map.of("duration", "PT20M")),
                Map.entry("stepType", "Wait")
            ))
            .resourceGroupName("myResourceGroup")
            .stepName("waitStep")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const step = new azure_native.deploymentmanager.Step("step", {
    location: "centralus",
    properties: {
        attributes: {
            duration: "PT20M",
        },
        stepType: "Wait",
    },
    resourceGroupName: "myResourceGroup",
    stepName: "waitStep",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

step = azure_native.deploymentmanager.Step("step",
    location="centralus",
    properties=azure_native.deploymentmanager.WaitStepPropertiesArgs(
        attributes=azure_native.deploymentmanager.WaitStepAttributesArgs(
            duration="PT20M",
        ),
        step_type="Wait",
    ),
    resource_group_name="myResourceGroup",
    step_name="waitStep",
    tags={})

```

```yaml
resources:
  step:
    type: azure-native:deploymentmanager:Step
    properties:
      location: centralus
      properties:
        attributes:
          duration: PT20M
        stepType: Wait
      resourceGroupName: myResourceGroup
      stepName: waitStep
      tags: {}

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:deploymentmanager:Step waitStep /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.DeploymentManager/steps/{stepName} 
```
