The integration account RosettaNet process configuration.
API Version: 2016-06-01.
Previous API Version: 2016-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update an RosettaNetProcessConfiguration
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var rosettaNetProcessConfiguration = new AzureNative.Logic.RosettaNetProcessConfiguration("rosettaNetProcessConfiguration", new()
    {
        ActivitySettings = new AzureNative.Logic.Inputs.RosettaNetPipActivitySettingsArgs
        {
            AcknowledgmentOfReceiptSettings = new AzureNative.Logic.Inputs.RosettaNetPipAcknowledgmentOfReceiptSettingsArgs
            {
                IsNonRepudiationRequired = false,
                TimeToAcknowledgeInSeconds = 600,
            },
            ActivityBehavior = new AzureNative.Logic.Inputs.RosettaNetPipActivityBehaviorArgs
            {
                ActionType = AzureNative.Logic.RosettaNetActionType.DoubleAction,
                IsAuthorizationRequired = false,
                IsSecuredTransportRequired = false,
                NonRepudiationOfOriginAndContent = false,
                PersistentConfidentialityScope = AzureNative.Logic.RosettaNetPipConfidentialityScope.None,
                ResponseType = AzureNative.Logic.RosettaNetResponseType.Async,
                RetryCount = 2,
                TimeToPerformInSeconds = 7200,
            },
            ActivityType = AzureNative.Logic.RosettaNetPipActivityType.RequestResponse,
        },
        Description = "Test description",
        InitiatorRoleSettings = new AzureNative.Logic.Inputs.RosettaNetPipRoleSettingsArgs
        {
            Action = "Purchase Order Request",
            BusinessDocument = new AzureNative.Logic.Inputs.RosettaNetPipBusinessDocumentArgs
            {
                Description = "A request to accept a purchase order for fulfillment..",
                Name = "Purchase Order Request",
                Version = "V02.02.00",
            },
            Description = "This partner role creates a demand for a product or service.",
            Role = "Buyer",
            RoleType = AzureNative.Logic.RosettaNetPipRoleType.Functional,
            Service = "Buyer Service",
            ServiceClassification = "Business Service",
        },
        IntegrationAccountName = "testia123",
        ProcessCode = "3A4",
        ProcessName = "Request Purchase Order",
        ProcessVersion = "V02.02.00",
        ResourceGroupName = "testrg123",
        ResponderRoleSettings = new AzureNative.Logic.Inputs.RosettaNetPipRoleSettingsArgs
        {
            Action = "Purchase Order Confirmation Action",
            BusinessDocument = new AzureNative.Logic.Inputs.RosettaNetPipBusinessDocumentArgs
            {
                Description = "Formally confirms the status of line item(s) in a Purchase Order. A Purchase Order line item may have one of the following states: accepted, rejected, or pending.",
                Name = "Purchase Order Confirmation",
                Version = "V02.02.00",
            },
            Description = "An organization that sells products to partners in the supply chain.",
            Role = "Seller",
            RoleType = AzureNative.Logic.RosettaNetPipRoleType.Organizational,
            Service = "Seller Service",
            ServiceClassification = "Business Service",
        },
        RosettaNetProcessConfigurationName = "3A4",
    });

});


```

```go
package main

import (
	logic "github.com/pulumi/pulumi-azure-native-sdk/logic"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := logic.NewRosettaNetProcessConfiguration(ctx, "rosettaNetProcessConfiguration", &logic.RosettaNetProcessConfigurationArgs{
			ActivitySettings: logic.RosettaNetPipActivitySettingsResponse{
				AcknowledgmentOfReceiptSettings: &logic.RosettaNetPipAcknowledgmentOfReceiptSettingsArgs{
					IsNonRepudiationRequired:   pulumi.Bool(false),
					TimeToAcknowledgeInSeconds: pulumi.Int(600),
				},
				ActivityBehavior: &logic.RosettaNetPipActivityBehaviorArgs{
					ActionType:                       logic.RosettaNetActionTypeDoubleAction,
					IsAuthorizationRequired:          pulumi.Bool(false),
					IsSecuredTransportRequired:       pulumi.Bool(false),
					NonRepudiationOfOriginAndContent: pulumi.Bool(false),
					PersistentConfidentialityScope:   logic.RosettaNetPipConfidentialityScopeNone,
					ResponseType:                     logic.RosettaNetResponseTypeAsync,
					RetryCount:                       pulumi.Int(2),
					TimeToPerformInSeconds:           pulumi.Int(7200),
				},
				ActivityType: logic.RosettaNetPipActivityTypeRequestResponse,
			},
			Description: pulumi.String("Test description"),
			InitiatorRoleSettings: logic.RosettaNetPipRoleSettingsResponse{
				Action: pulumi.String("Purchase Order Request"),
				BusinessDocument: &logic.RosettaNetPipBusinessDocumentArgs{
					Description: pulumi.String("A request to accept a purchase order for fulfillment.."),
					Name:        pulumi.String("Purchase Order Request"),
					Version:     pulumi.String("V02.02.00"),
				},
				Description:           pulumi.String("This partner role creates a demand for a product or service."),
				Role:                  pulumi.String("Buyer"),
				RoleType:              logic.RosettaNetPipRoleTypeFunctional,
				Service:               pulumi.String("Buyer Service"),
				ServiceClassification: pulumi.String("Business Service"),
			},
			IntegrationAccountName: pulumi.String("testia123"),
			ProcessCode:            pulumi.String("3A4"),
			ProcessName:            pulumi.String("Request Purchase Order"),
			ProcessVersion:         pulumi.String("V02.02.00"),
			ResourceGroupName:      pulumi.String("testrg123"),
			ResponderRoleSettings: logic.RosettaNetPipRoleSettingsResponse{
				Action: pulumi.String("Purchase Order Confirmation Action"),
				BusinessDocument: &logic.RosettaNetPipBusinessDocumentArgs{
					Description: pulumi.String("Formally confirms the status of line item(s) in a Purchase Order. A Purchase Order line item may have one of the following states: accepted, rejected, or pending."),
					Name:        pulumi.String("Purchase Order Confirmation"),
					Version:     pulumi.String("V02.02.00"),
				},
				Description:           pulumi.String("An organization that sells products to partners in the supply chain."),
				Role:                  pulumi.String("Seller"),
				RoleType:              logic.RosettaNetPipRoleTypeOrganizational,
				Service:               pulumi.String("Seller Service"),
				ServiceClassification: pulumi.String("Business Service"),
			},
			RosettaNetProcessConfigurationName: pulumi.String("3A4"),
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
import com.pulumi.azurenative.logic.RosettaNetProcessConfiguration;
import com.pulumi.azurenative.logic.RosettaNetProcessConfigurationArgs;
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
        var rosettaNetProcessConfiguration = new RosettaNetProcessConfiguration("rosettaNetProcessConfiguration", RosettaNetProcessConfigurationArgs.builder()        
            .activitySettings(Map.ofEntries(
                Map.entry("acknowledgmentOfReceiptSettings", Map.ofEntries(
                    Map.entry("isNonRepudiationRequired", false),
                    Map.entry("timeToAcknowledgeInSeconds", 600)
                )),
                Map.entry("activityBehavior", Map.ofEntries(
                    Map.entry("actionType", "DoubleAction"),
                    Map.entry("isAuthorizationRequired", false),
                    Map.entry("isSecuredTransportRequired", false),
                    Map.entry("nonRepudiationOfOriginAndContent", false),
                    Map.entry("persistentConfidentialityScope", "None"),
                    Map.entry("responseType", "Async"),
                    Map.entry("retryCount", 2),
                    Map.entry("timeToPerformInSeconds", 7200)
                )),
                Map.entry("activityType", "RequestResponse")
            ))
            .description("Test description")
            .initiatorRoleSettings(Map.ofEntries(
                Map.entry("action", "Purchase Order Request"),
                Map.entry("businessDocument", Map.ofEntries(
                    Map.entry("description", "A request to accept a purchase order for fulfillment.."),
                    Map.entry("name", "Purchase Order Request"),
                    Map.entry("version", "V02.02.00")
                )),
                Map.entry("description", "This partner role creates a demand for a product or service."),
                Map.entry("role", "Buyer"),
                Map.entry("roleType", "Functional"),
                Map.entry("service", "Buyer Service"),
                Map.entry("serviceClassification", "Business Service")
            ))
            .integrationAccountName("testia123")
            .processCode("3A4")
            .processName("Request Purchase Order")
            .processVersion("V02.02.00")
            .resourceGroupName("testrg123")
            .responderRoleSettings(Map.ofEntries(
                Map.entry("action", "Purchase Order Confirmation Action"),
                Map.entry("businessDocument", Map.ofEntries(
                    Map.entry("description", "Formally confirms the status of line item(s) in a Purchase Order. A Purchase Order line item may have one of the following states: accepted, rejected, or pending."),
                    Map.entry("name", "Purchase Order Confirmation"),
                    Map.entry("version", "V02.02.00")
                )),
                Map.entry("description", "An organization that sells products to partners in the supply chain."),
                Map.entry("role", "Seller"),
                Map.entry("roleType", "Organizational"),
                Map.entry("service", "Seller Service"),
                Map.entry("serviceClassification", "Business Service")
            ))
            .rosettaNetProcessConfigurationName("3A4")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const rosettaNetProcessConfiguration = new azure_native.logic.RosettaNetProcessConfiguration("rosettaNetProcessConfiguration", {
    activitySettings: {
        acknowledgmentOfReceiptSettings: {
            isNonRepudiationRequired: false,
            timeToAcknowledgeInSeconds: 600,
        },
        activityBehavior: {
            actionType: azure_native.logic.RosettaNetActionType.DoubleAction,
            isAuthorizationRequired: false,
            isSecuredTransportRequired: false,
            nonRepudiationOfOriginAndContent: false,
            persistentConfidentialityScope: azure_native.logic.RosettaNetPipConfidentialityScope.None,
            responseType: azure_native.logic.RosettaNetResponseType.Async,
            retryCount: 2,
            timeToPerformInSeconds: 7200,
        },
        activityType: azure_native.logic.RosettaNetPipActivityType.RequestResponse,
    },
    description: "Test description",
    initiatorRoleSettings: {
        action: "Purchase Order Request",
        businessDocument: {
            description: "A request to accept a purchase order for fulfillment..",
            name: "Purchase Order Request",
            version: "V02.02.00",
        },
        description: "This partner role creates a demand for a product or service.",
        role: "Buyer",
        roleType: azure_native.logic.RosettaNetPipRoleType.Functional,
        service: "Buyer Service",
        serviceClassification: "Business Service",
    },
    integrationAccountName: "testia123",
    processCode: "3A4",
    processName: "Request Purchase Order",
    processVersion: "V02.02.00",
    resourceGroupName: "testrg123",
    responderRoleSettings: {
        action: "Purchase Order Confirmation Action",
        businessDocument: {
            description: "Formally confirms the status of line item(s) in a Purchase Order. A Purchase Order line item may have one of the following states: accepted, rejected, or pending.",
            name: "Purchase Order Confirmation",
            version: "V02.02.00",
        },
        description: "An organization that sells products to partners in the supply chain.",
        role: "Seller",
        roleType: azure_native.logic.RosettaNetPipRoleType.Organizational,
        service: "Seller Service",
        serviceClassification: "Business Service",
    },
    rosettaNetProcessConfigurationName: "3A4",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

rosetta_net_process_configuration = azure_native.logic.RosettaNetProcessConfiguration("rosettaNetProcessConfiguration",
    activity_settings=azure_native.logic.RosettaNetPipActivitySettingsResponseArgs(
        acknowledgment_of_receipt_settings=azure_native.logic.RosettaNetPipAcknowledgmentOfReceiptSettingsArgs(
            is_non_repudiation_required=False,
            time_to_acknowledge_in_seconds=600,
        ),
        activity_behavior=azure_native.logic.RosettaNetPipActivityBehaviorArgs(
            action_type=azure_native.logic.RosettaNetActionType.DOUBLE_ACTION,
            is_authorization_required=False,
            is_secured_transport_required=False,
            non_repudiation_of_origin_and_content=False,
            persistent_confidentiality_scope=azure_native.logic.RosettaNetPipConfidentialityScope.NONE,
            response_type=azure_native.logic.RosettaNetResponseType.ASYNC_,
            retry_count=2,
            time_to_perform_in_seconds=7200,
        ),
        activity_type=azure_native.logic.RosettaNetPipActivityType.REQUEST_RESPONSE,
    ),
    description="Test description",
    initiator_role_settings=azure_native.logic.RosettaNetPipRoleSettingsResponseArgs(
        action="Purchase Order Request",
        business_document=azure_native.logic.RosettaNetPipBusinessDocumentArgs(
            description="A request to accept a purchase order for fulfillment..",
            name="Purchase Order Request",
            version="V02.02.00",
        ),
        description="This partner role creates a demand for a product or service.",
        role="Buyer",
        role_type=azure_native.logic.RosettaNetPipRoleType.FUNCTIONAL,
        service="Buyer Service",
        service_classification="Business Service",
    ),
    integration_account_name="testia123",
    process_code="3A4",
    process_name="Request Purchase Order",
    process_version="V02.02.00",
    resource_group_name="testrg123",
    responder_role_settings=azure_native.logic.RosettaNetPipRoleSettingsResponseArgs(
        action="Purchase Order Confirmation Action",
        business_document=azure_native.logic.RosettaNetPipBusinessDocumentArgs(
            description="Formally confirms the status of line item(s) in a Purchase Order. A Purchase Order line item may have one of the following states: accepted, rejected, or pending.",
            name="Purchase Order Confirmation",
            version="V02.02.00",
        ),
        description="An organization that sells products to partners in the supply chain.",
        role="Seller",
        role_type=azure_native.logic.RosettaNetPipRoleType.ORGANIZATIONAL,
        service="Seller Service",
        service_classification="Business Service",
    ),
    rosetta_net_process_configuration_name="3A4")

```

```yaml
resources:
  rosettaNetProcessConfiguration:
    type: azure-native:logic:RosettaNetProcessConfiguration
    properties:
      activitySettings:
        acknowledgmentOfReceiptSettings:
          isNonRepudiationRequired: false
          timeToAcknowledgeInSeconds: 600
        activityBehavior:
          actionType: DoubleAction
          isAuthorizationRequired: false
          isSecuredTransportRequired: false
          nonRepudiationOfOriginAndContent: false
          persistentConfidentialityScope: None
          responseType: Async
          retryCount: 2
          timeToPerformInSeconds: 7200
        activityType: RequestResponse
      description: Test description
      initiatorRoleSettings:
        action: Purchase Order Request
        businessDocument:
          description: A request to accept a purchase order for fulfillment..
          name: Purchase Order Request
          version: V02.02.00
        description: This partner role creates a demand for a product or service.
        role: Buyer
        roleType: Functional
        service: Buyer Service
        serviceClassification: Business Service
      integrationAccountName: testia123
      processCode: 3A4
      processName: Request Purchase Order
      processVersion: V02.02.00
      resourceGroupName: testrg123
      responderRoleSettings:
        action: Purchase Order Confirmation Action
        businessDocument:
          description: 'Formally confirms the status of line item(s) in a Purchase Order. A Purchase Order line item may have one of the following states: accepted, rejected, or pending.'
          name: Purchase Order Confirmation
          version: V02.02.00
        description: An organization that sells products to partners in the supply chain.
        role: Seller
        roleType: Organizational
        service: Seller Service
        serviceClassification: Business Service
      rosettaNetProcessConfigurationName: 3A4

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:logic:RosettaNetProcessConfiguration 3A4 /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.Logic/integrationAccounts/testia123/rosettaNetProcessConfigurations/3A4 
```
