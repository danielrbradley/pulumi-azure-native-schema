An action group resource.
API Version: 2023-01-01.
Previous API Version: 2019-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update an action group
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var actionGroup = new AzureNative.Insights.ActionGroup("actionGroup", new()
    {
        ActionGroupName = "SampleActionGroup",
        ArmRoleReceivers = new[]
        {
            new AzureNative.Insights.Inputs.ArmRoleReceiverArgs
            {
                Name = "Sample armRole",
                RoleId = "8e3af657-a8ff-443c-a75c-2fe8c4bcb635",
                UseCommonAlertSchema = true,
            },
        },
        AutomationRunbookReceivers = new[]
        {
            new AzureNative.Insights.Inputs.AutomationRunbookReceiverArgs
            {
                AutomationAccountId = "/subscriptions/187f412d-1758-44d9-b052-169e2564721d/resourceGroups/runbookTest/providers/Microsoft.Automation/automationAccounts/runbooktest",
                IsGlobalRunbook = false,
                Name = "testRunbook",
                RunbookName = "Sample runbook",
                ServiceUri = "<serviceUri>",
                UseCommonAlertSchema = true,
                WebhookResourceId = "/subscriptions/187f412d-1758-44d9-b052-169e2564721d/resourceGroups/runbookTest/providers/Microsoft.Automation/automationAccounts/runbooktest/webhooks/Alert1510184037084",
            },
        },
        AzureAppPushReceivers = new[]
        {
            new AzureNative.Insights.Inputs.AzureAppPushReceiverArgs
            {
                EmailAddress = "johndoe@email.com",
                Name = "Sample azureAppPush",
            },
        },
        AzureFunctionReceivers = new[]
        {
            new AzureNative.Insights.Inputs.AzureFunctionReceiverArgs
            {
                FunctionAppResourceId = "/subscriptions/5def922a-3ed4-49c1-b9fd-05ec533819a3/resourceGroups/aznsTest/providers/Microsoft.Web/sites/testFunctionApp",
                FunctionName = "HttpTriggerCSharp1",
                HttpTriggerUrl = "http://test.me",
                Name = "Sample azureFunction",
                UseCommonAlertSchema = true,
            },
        },
        EmailReceivers = new[]
        {
            new AzureNative.Insights.Inputs.EmailReceiverArgs
            {
                EmailAddress = "johndoe@email.com",
                Name = "John Doe's email",
                UseCommonAlertSchema = false,
            },
            new AzureNative.Insights.Inputs.EmailReceiverArgs
            {
                EmailAddress = "janesmith@email.com",
                Name = "Jane Smith's email",
                UseCommonAlertSchema = true,
            },
        },
        Enabled = true,
        EventHubReceivers = new[]
        {
            new AzureNative.Insights.Inputs.EventHubReceiverArgs
            {
                EventHubName = "testEventHub",
                EventHubNameSpace = "testEventHubNameSpace",
                Name = "Sample eventHub",
                SubscriptionId = "187f412d-1758-44d9-b052-169e2564721d",
                TenantId = "68a4459a-ccb8-493c-b9da-dd30457d1b84",
            },
        },
        GroupShortName = "sample",
        ItsmReceivers = new[]
        {
            new AzureNative.Insights.Inputs.ItsmReceiverArgs
            {
                ConnectionId = "a3b9076c-ce8e-434e-85b4-aff10cb3c8f1",
                Name = "Sample itsm",
                Region = "westcentralus",
                TicketConfiguration = "{\"PayloadRevision\":0,\"WorkItemType\":\"Incident\",\"UseTemplate\":false,\"WorkItemData\":\"{}\",\"CreateOneWIPerCI\":false}",
                WorkspaceId = "5def922a-3ed4-49c1-b9fd-05ec533819a3|55dfd1f8-7e59-4f89-bf56-4c82f5ace23c",
            },
        },
        Location = "Global",
        LogicAppReceivers = new[]
        {
            new AzureNative.Insights.Inputs.LogicAppReceiverArgs
            {
                CallbackUrl = "https://prod-27.northcentralus.logic.azure.com/workflows/68e572e818e5457ba898763b7db90877/triggers/manual/paths/invoke/azns/test?api-version=2016-10-01&sp=%2Ftriggers%2Fmanual%2Frun&sv=1.0&sig=Abpsb72UYJxPPvmDo937uzofupO5r_vIeWEx7KVHo7w",
                Name = "Sample logicApp",
                ResourceId = "/subscriptions/187f412d-1758-44d9-b052-169e2564721d/resourceGroups/LogicApp/providers/Microsoft.Logic/workflows/testLogicApp",
                UseCommonAlertSchema = false,
            },
        },
        ResourceGroupName = "Default-NotificationRules",
        SmsReceivers = new[]
        {
            new AzureNative.Insights.Inputs.SmsReceiverArgs
            {
                CountryCode = "1",
                Name = "John Doe's mobile",
                PhoneNumber = "1234567890",
            },
            new AzureNative.Insights.Inputs.SmsReceiverArgs
            {
                CountryCode = "1",
                Name = "Jane Smith's mobile",
                PhoneNumber = "0987654321",
            },
        },
        Tags = null,
        VoiceReceivers = new[]
        {
            new AzureNative.Insights.Inputs.VoiceReceiverArgs
            {
                CountryCode = "1",
                Name = "Sample voice",
                PhoneNumber = "1234567890",
            },
        },
        WebhookReceivers = new[]
        {
            new AzureNative.Insights.Inputs.WebhookReceiverArgs
            {
                Name = "Sample webhook 1",
                ServiceUri = "http://www.example.com/webhook1",
                UseCommonAlertSchema = true,
            },
            new AzureNative.Insights.Inputs.WebhookReceiverArgs
            {
                IdentifierUri = "http://someidentifier/d7811ba3-7996-4a93-99b6-6b2f3f355f8a",
                Name = "Sample webhook 2",
                ObjectId = "d3bb868c-fe44-452c-aa26-769a6538c808",
                ServiceUri = "http://www.example.com/webhook2",
                TenantId = "68a4459a-ccb8-493c-b9da-dd30457d1b84",
                UseAadAuth = true,
                UseCommonAlertSchema = true,
            },
        },
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
		_, err := insights.NewActionGroup(ctx, "actionGroup", &insights.ActionGroupArgs{
			ActionGroupName: pulumi.String("SampleActionGroup"),
			ArmRoleReceivers: []insights.ArmRoleReceiverArgs{
				{
					Name:                 pulumi.String("Sample armRole"),
					RoleId:               pulumi.String("8e3af657-a8ff-443c-a75c-2fe8c4bcb635"),
					UseCommonAlertSchema: pulumi.Bool(true),
				},
			},
			AutomationRunbookReceivers: []insights.AutomationRunbookReceiverArgs{
				{
					AutomationAccountId:  pulumi.String("/subscriptions/187f412d-1758-44d9-b052-169e2564721d/resourceGroups/runbookTest/providers/Microsoft.Automation/automationAccounts/runbooktest"),
					IsGlobalRunbook:      pulumi.Bool(false),
					Name:                 pulumi.String("testRunbook"),
					RunbookName:          pulumi.String("Sample runbook"),
					ServiceUri:           pulumi.String("<serviceUri>"),
					UseCommonAlertSchema: pulumi.Bool(true),
					WebhookResourceId:    pulumi.String("/subscriptions/187f412d-1758-44d9-b052-169e2564721d/resourceGroups/runbookTest/providers/Microsoft.Automation/automationAccounts/runbooktest/webhooks/Alert1510184037084"),
				},
			},
			AzureAppPushReceivers: []insights.AzureAppPushReceiverArgs{
				{
					EmailAddress: pulumi.String("johndoe@email.com"),
					Name:         pulumi.String("Sample azureAppPush"),
				},
			},
			AzureFunctionReceivers: []insights.AzureFunctionReceiverArgs{
				{
					FunctionAppResourceId: pulumi.String("/subscriptions/5def922a-3ed4-49c1-b9fd-05ec533819a3/resourceGroups/aznsTest/providers/Microsoft.Web/sites/testFunctionApp"),
					FunctionName:          pulumi.String("HttpTriggerCSharp1"),
					HttpTriggerUrl:        pulumi.String("http://test.me"),
					Name:                  pulumi.String("Sample azureFunction"),
					UseCommonAlertSchema:  pulumi.Bool(true),
				},
			},
			EmailReceivers: []insights.EmailReceiverArgs{
				{
					EmailAddress:         pulumi.String("johndoe@email.com"),
					Name:                 pulumi.String("John Doe's email"),
					UseCommonAlertSchema: pulumi.Bool(false),
				},
				{
					EmailAddress:         pulumi.String("janesmith@email.com"),
					Name:                 pulumi.String("Jane Smith's email"),
					UseCommonAlertSchema: pulumi.Bool(true),
				},
			},
			Enabled: pulumi.Bool(true),
			EventHubReceivers: []insights.EventHubReceiverArgs{
				{
					EventHubName:      pulumi.String("testEventHub"),
					EventHubNameSpace: pulumi.String("testEventHubNameSpace"),
					Name:              pulumi.String("Sample eventHub"),
					SubscriptionId:    pulumi.String("187f412d-1758-44d9-b052-169e2564721d"),
					TenantId:          pulumi.String("68a4459a-ccb8-493c-b9da-dd30457d1b84"),
				},
			},
			GroupShortName: pulumi.String("sample"),
			ItsmReceivers: []insights.ItsmReceiverArgs{
				{
					ConnectionId:        pulumi.String("a3b9076c-ce8e-434e-85b4-aff10cb3c8f1"),
					Name:                pulumi.String("Sample itsm"),
					Region:              pulumi.String("westcentralus"),
					TicketConfiguration: pulumi.String("{\"PayloadRevision\":0,\"WorkItemType\":\"Incident\",\"UseTemplate\":false,\"WorkItemData\":\"{}\",\"CreateOneWIPerCI\":false}"),
					WorkspaceId:         pulumi.String("5def922a-3ed4-49c1-b9fd-05ec533819a3|55dfd1f8-7e59-4f89-bf56-4c82f5ace23c"),
				},
			},
			Location: pulumi.String("Global"),
			LogicAppReceivers: []insights.LogicAppReceiverArgs{
				{
					CallbackUrl:          pulumi.String("https://prod-27.northcentralus.logic.azure.com/workflows/68e572e818e5457ba898763b7db90877/triggers/manual/paths/invoke/azns/test?api-version=2016-10-01&sp=%2Ftriggers%2Fmanual%2Frun&sv=1.0&sig=Abpsb72UYJxPPvmDo937uzofupO5r_vIeWEx7KVHo7w"),
					Name:                 pulumi.String("Sample logicApp"),
					ResourceId:           pulumi.String("/subscriptions/187f412d-1758-44d9-b052-169e2564721d/resourceGroups/LogicApp/providers/Microsoft.Logic/workflows/testLogicApp"),
					UseCommonAlertSchema: pulumi.Bool(false),
				},
			},
			ResourceGroupName: pulumi.String("Default-NotificationRules"),
			SmsReceivers: []insights.SmsReceiverArgs{
				{
					CountryCode: pulumi.String("1"),
					Name:        pulumi.String("John Doe's mobile"),
					PhoneNumber: pulumi.String("1234567890"),
				},
				{
					CountryCode: pulumi.String("1"),
					Name:        pulumi.String("Jane Smith's mobile"),
					PhoneNumber: pulumi.String("0987654321"),
				},
			},
			Tags: nil,
			VoiceReceivers: []insights.VoiceReceiverArgs{
				{
					CountryCode: pulumi.String("1"),
					Name:        pulumi.String("Sample voice"),
					PhoneNumber: pulumi.String("1234567890"),
				},
			},
			WebhookReceivers: []insights.WebhookReceiverArgs{
				{
					Name:                 pulumi.String("Sample webhook 1"),
					ServiceUri:           pulumi.String("http://www.example.com/webhook1"),
					UseCommonAlertSchema: pulumi.Bool(true),
				},
				{
					IdentifierUri:        pulumi.String("http://someidentifier/d7811ba3-7996-4a93-99b6-6b2f3f355f8a"),
					Name:                 pulumi.String("Sample webhook 2"),
					ObjectId:             pulumi.String("d3bb868c-fe44-452c-aa26-769a6538c808"),
					ServiceUri:           pulumi.String("http://www.example.com/webhook2"),
					TenantId:             pulumi.String("68a4459a-ccb8-493c-b9da-dd30457d1b84"),
					UseAadAuth:           pulumi.Bool(true),
					UseCommonAlertSchema: pulumi.Bool(true),
				},
			},
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
import com.pulumi.azurenative.insights.ActionGroup;
import com.pulumi.azurenative.insights.ActionGroupArgs;
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
        var actionGroup = new ActionGroup("actionGroup", ActionGroupArgs.builder()        
            .actionGroupName("SampleActionGroup")
            .armRoleReceivers(Map.ofEntries(
                Map.entry("name", "Sample armRole"),
                Map.entry("roleId", "8e3af657-a8ff-443c-a75c-2fe8c4bcb635"),
                Map.entry("useCommonAlertSchema", true)
            ))
            .automationRunbookReceivers(Map.ofEntries(
                Map.entry("automationAccountId", "/subscriptions/187f412d-1758-44d9-b052-169e2564721d/resourceGroups/runbookTest/providers/Microsoft.Automation/automationAccounts/runbooktest"),
                Map.entry("isGlobalRunbook", false),
                Map.entry("name", "testRunbook"),
                Map.entry("runbookName", "Sample runbook"),
                Map.entry("serviceUri", "<serviceUri>"),
                Map.entry("useCommonAlertSchema", true),
                Map.entry("webhookResourceId", "/subscriptions/187f412d-1758-44d9-b052-169e2564721d/resourceGroups/runbookTest/providers/Microsoft.Automation/automationAccounts/runbooktest/webhooks/Alert1510184037084")
            ))
            .azureAppPushReceivers(Map.ofEntries(
                Map.entry("emailAddress", "johndoe@email.com"),
                Map.entry("name", "Sample azureAppPush")
            ))
            .azureFunctionReceivers(Map.ofEntries(
                Map.entry("functionAppResourceId", "/subscriptions/5def922a-3ed4-49c1-b9fd-05ec533819a3/resourceGroups/aznsTest/providers/Microsoft.Web/sites/testFunctionApp"),
                Map.entry("functionName", "HttpTriggerCSharp1"),
                Map.entry("httpTriggerUrl", "http://test.me"),
                Map.entry("name", "Sample azureFunction"),
                Map.entry("useCommonAlertSchema", true)
            ))
            .emailReceivers(            
                Map.ofEntries(
                    Map.entry("emailAddress", "johndoe@email.com"),
                    Map.entry("name", "John Doe's email"),
                    Map.entry("useCommonAlertSchema", false)
                ),
                Map.ofEntries(
                    Map.entry("emailAddress", "janesmith@email.com"),
                    Map.entry("name", "Jane Smith's email"),
                    Map.entry("useCommonAlertSchema", true)
                ))
            .enabled(true)
            .eventHubReceivers(Map.ofEntries(
                Map.entry("eventHubName", "testEventHub"),
                Map.entry("eventHubNameSpace", "testEventHubNameSpace"),
                Map.entry("name", "Sample eventHub"),
                Map.entry("subscriptionId", "187f412d-1758-44d9-b052-169e2564721d"),
                Map.entry("tenantId", "68a4459a-ccb8-493c-b9da-dd30457d1b84")
            ))
            .groupShortName("sample")
            .itsmReceivers(Map.ofEntries(
                Map.entry("connectionId", "a3b9076c-ce8e-434e-85b4-aff10cb3c8f1"),
                Map.entry("name", "Sample itsm"),
                Map.entry("region", "westcentralus"),
                Map.entry("ticketConfiguration", "{\"PayloadRevision\":0,\"WorkItemType\":\"Incident\",\"UseTemplate\":false,\"WorkItemData\":\"{}\",\"CreateOneWIPerCI\":false}"),
                Map.entry("workspaceId", "5def922a-3ed4-49c1-b9fd-05ec533819a3|55dfd1f8-7e59-4f89-bf56-4c82f5ace23c")
            ))
            .location("Global")
            .logicAppReceivers(Map.ofEntries(
                Map.entry("callbackUrl", "https://prod-27.northcentralus.logic.azure.com/workflows/68e572e818e5457ba898763b7db90877/triggers/manual/paths/invoke/azns/test?api-version=2016-10-01&sp=%2Ftriggers%2Fmanual%2Frun&sv=1.0&sig=Abpsb72UYJxPPvmDo937uzofupO5r_vIeWEx7KVHo7w"),
                Map.entry("name", "Sample logicApp"),
                Map.entry("resourceId", "/subscriptions/187f412d-1758-44d9-b052-169e2564721d/resourceGroups/LogicApp/providers/Microsoft.Logic/workflows/testLogicApp"),
                Map.entry("useCommonAlertSchema", false)
            ))
            .resourceGroupName("Default-NotificationRules")
            .smsReceivers(            
                Map.ofEntries(
                    Map.entry("countryCode", "1"),
                    Map.entry("name", "John Doe's mobile"),
                    Map.entry("phoneNumber", "1234567890")
                ),
                Map.ofEntries(
                    Map.entry("countryCode", "1"),
                    Map.entry("name", "Jane Smith's mobile"),
                    Map.entry("phoneNumber", "0987654321")
                ))
            .tags()
            .voiceReceivers(Map.ofEntries(
                Map.entry("countryCode", "1"),
                Map.entry("name", "Sample voice"),
                Map.entry("phoneNumber", "1234567890")
            ))
            .webhookReceivers(            
                Map.ofEntries(
                    Map.entry("name", "Sample webhook 1"),
                    Map.entry("serviceUri", "http://www.example.com/webhook1"),
                    Map.entry("useCommonAlertSchema", true)
                ),
                Map.ofEntries(
                    Map.entry("identifierUri", "http://someidentifier/d7811ba3-7996-4a93-99b6-6b2f3f355f8a"),
                    Map.entry("name", "Sample webhook 2"),
                    Map.entry("objectId", "d3bb868c-fe44-452c-aa26-769a6538c808"),
                    Map.entry("serviceUri", "http://www.example.com/webhook2"),
                    Map.entry("tenantId", "68a4459a-ccb8-493c-b9da-dd30457d1b84"),
                    Map.entry("useAadAuth", true),
                    Map.entry("useCommonAlertSchema", true)
                ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const actionGroup = new azure_native.insights.ActionGroup("actionGroup", {
    actionGroupName: "SampleActionGroup",
    armRoleReceivers: [{
        name: "Sample armRole",
        roleId: "8e3af657-a8ff-443c-a75c-2fe8c4bcb635",
        useCommonAlertSchema: true,
    }],
    automationRunbookReceivers: [{
        automationAccountId: "/subscriptions/187f412d-1758-44d9-b052-169e2564721d/resourceGroups/runbookTest/providers/Microsoft.Automation/automationAccounts/runbooktest",
        isGlobalRunbook: false,
        name: "testRunbook",
        runbookName: "Sample runbook",
        serviceUri: "<serviceUri>",
        useCommonAlertSchema: true,
        webhookResourceId: "/subscriptions/187f412d-1758-44d9-b052-169e2564721d/resourceGroups/runbookTest/providers/Microsoft.Automation/automationAccounts/runbooktest/webhooks/Alert1510184037084",
    }],
    azureAppPushReceivers: [{
        emailAddress: "johndoe@email.com",
        name: "Sample azureAppPush",
    }],
    azureFunctionReceivers: [{
        functionAppResourceId: "/subscriptions/5def922a-3ed4-49c1-b9fd-05ec533819a3/resourceGroups/aznsTest/providers/Microsoft.Web/sites/testFunctionApp",
        functionName: "HttpTriggerCSharp1",
        httpTriggerUrl: "http://test.me",
        name: "Sample azureFunction",
        useCommonAlertSchema: true,
    }],
    emailReceivers: [
        {
            emailAddress: "johndoe@email.com",
            name: "John Doe's email",
            useCommonAlertSchema: false,
        },
        {
            emailAddress: "janesmith@email.com",
            name: "Jane Smith's email",
            useCommonAlertSchema: true,
        },
    ],
    enabled: true,
    eventHubReceivers: [{
        eventHubName: "testEventHub",
        eventHubNameSpace: "testEventHubNameSpace",
        name: "Sample eventHub",
        subscriptionId: "187f412d-1758-44d9-b052-169e2564721d",
        tenantId: "68a4459a-ccb8-493c-b9da-dd30457d1b84",
    }],
    groupShortName: "sample",
    itsmReceivers: [{
        connectionId: "a3b9076c-ce8e-434e-85b4-aff10cb3c8f1",
        name: "Sample itsm",
        region: "westcentralus",
        ticketConfiguration: "{\"PayloadRevision\":0,\"WorkItemType\":\"Incident\",\"UseTemplate\":false,\"WorkItemData\":\"{}\",\"CreateOneWIPerCI\":false}",
        workspaceId: "5def922a-3ed4-49c1-b9fd-05ec533819a3|55dfd1f8-7e59-4f89-bf56-4c82f5ace23c",
    }],
    location: "Global",
    logicAppReceivers: [{
        callbackUrl: "https://prod-27.northcentralus.logic.azure.com/workflows/68e572e818e5457ba898763b7db90877/triggers/manual/paths/invoke/azns/test?api-version=2016-10-01&sp=%2Ftriggers%2Fmanual%2Frun&sv=1.0&sig=Abpsb72UYJxPPvmDo937uzofupO5r_vIeWEx7KVHo7w",
        name: "Sample logicApp",
        resourceId: "/subscriptions/187f412d-1758-44d9-b052-169e2564721d/resourceGroups/LogicApp/providers/Microsoft.Logic/workflows/testLogicApp",
        useCommonAlertSchema: false,
    }],
    resourceGroupName: "Default-NotificationRules",
    smsReceivers: [
        {
            countryCode: "1",
            name: "John Doe's mobile",
            phoneNumber: "1234567890",
        },
        {
            countryCode: "1",
            name: "Jane Smith's mobile",
            phoneNumber: "0987654321",
        },
    ],
    tags: {},
    voiceReceivers: [{
        countryCode: "1",
        name: "Sample voice",
        phoneNumber: "1234567890",
    }],
    webhookReceivers: [
        {
            name: "Sample webhook 1",
            serviceUri: "http://www.example.com/webhook1",
            useCommonAlertSchema: true,
        },
        {
            identifierUri: "http://someidentifier/d7811ba3-7996-4a93-99b6-6b2f3f355f8a",
            name: "Sample webhook 2",
            objectId: "d3bb868c-fe44-452c-aa26-769a6538c808",
            serviceUri: "http://www.example.com/webhook2",
            tenantId: "68a4459a-ccb8-493c-b9da-dd30457d1b84",
            useAadAuth: true,
            useCommonAlertSchema: true,
        },
    ],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

action_group = azure_native.insights.ActionGroup("actionGroup",
    action_group_name="SampleActionGroup",
    arm_role_receivers=[azure_native.insights.ArmRoleReceiverArgs(
        name="Sample armRole",
        role_id="8e3af657-a8ff-443c-a75c-2fe8c4bcb635",
        use_common_alert_schema=True,
    )],
    automation_runbook_receivers=[azure_native.insights.AutomationRunbookReceiverArgs(
        automation_account_id="/subscriptions/187f412d-1758-44d9-b052-169e2564721d/resourceGroups/runbookTest/providers/Microsoft.Automation/automationAccounts/runbooktest",
        is_global_runbook=False,
        name="testRunbook",
        runbook_name="Sample runbook",
        service_uri="<serviceUri>",
        use_common_alert_schema=True,
        webhook_resource_id="/subscriptions/187f412d-1758-44d9-b052-169e2564721d/resourceGroups/runbookTest/providers/Microsoft.Automation/automationAccounts/runbooktest/webhooks/Alert1510184037084",
    )],
    azure_app_push_receivers=[azure_native.insights.AzureAppPushReceiverArgs(
        email_address="johndoe@email.com",
        name="Sample azureAppPush",
    )],
    azure_function_receivers=[azure_native.insights.AzureFunctionReceiverArgs(
        function_app_resource_id="/subscriptions/5def922a-3ed4-49c1-b9fd-05ec533819a3/resourceGroups/aznsTest/providers/Microsoft.Web/sites/testFunctionApp",
        function_name="HttpTriggerCSharp1",
        http_trigger_url="http://test.me",
        name="Sample azureFunction",
        use_common_alert_schema=True,
    )],
    email_receivers=[
        azure_native.insights.EmailReceiverArgs(
            email_address="johndoe@email.com",
            name="John Doe's email",
            use_common_alert_schema=False,
        ),
        azure_native.insights.EmailReceiverArgs(
            email_address="janesmith@email.com",
            name="Jane Smith's email",
            use_common_alert_schema=True,
        ),
    ],
    enabled=True,
    event_hub_receivers=[azure_native.insights.EventHubReceiverArgs(
        event_hub_name="testEventHub",
        event_hub_name_space="testEventHubNameSpace",
        name="Sample eventHub",
        subscription_id="187f412d-1758-44d9-b052-169e2564721d",
        tenant_id="68a4459a-ccb8-493c-b9da-dd30457d1b84",
    )],
    group_short_name="sample",
    itsm_receivers=[azure_native.insights.ItsmReceiverArgs(
        connection_id="a3b9076c-ce8e-434e-85b4-aff10cb3c8f1",
        name="Sample itsm",
        region="westcentralus",
        ticket_configuration="{\"PayloadRevision\":0,\"WorkItemType\":\"Incident\",\"UseTemplate\":false,\"WorkItemData\":\"{}\",\"CreateOneWIPerCI\":false}",
        workspace_id="5def922a-3ed4-49c1-b9fd-05ec533819a3|55dfd1f8-7e59-4f89-bf56-4c82f5ace23c",
    )],
    location="Global",
    logic_app_receivers=[azure_native.insights.LogicAppReceiverArgs(
        callback_url="https://prod-27.northcentralus.logic.azure.com/workflows/68e572e818e5457ba898763b7db90877/triggers/manual/paths/invoke/azns/test?api-version=2016-10-01&sp=%2Ftriggers%2Fmanual%2Frun&sv=1.0&sig=Abpsb72UYJxPPvmDo937uzofupO5r_vIeWEx7KVHo7w",
        name="Sample logicApp",
        resource_id="/subscriptions/187f412d-1758-44d9-b052-169e2564721d/resourceGroups/LogicApp/providers/Microsoft.Logic/workflows/testLogicApp",
        use_common_alert_schema=False,
    )],
    resource_group_name="Default-NotificationRules",
    sms_receivers=[
        azure_native.insights.SmsReceiverArgs(
            country_code="1",
            name="John Doe's mobile",
            phone_number="1234567890",
        ),
        azure_native.insights.SmsReceiverArgs(
            country_code="1",
            name="Jane Smith's mobile",
            phone_number="0987654321",
        ),
    ],
    tags={},
    voice_receivers=[azure_native.insights.VoiceReceiverArgs(
        country_code="1",
        name="Sample voice",
        phone_number="1234567890",
    )],
    webhook_receivers=[
        azure_native.insights.WebhookReceiverArgs(
            name="Sample webhook 1",
            service_uri="http://www.example.com/webhook1",
            use_common_alert_schema=True,
        ),
        azure_native.insights.WebhookReceiverArgs(
            identifier_uri="http://someidentifier/d7811ba3-7996-4a93-99b6-6b2f3f355f8a",
            name="Sample webhook 2",
            object_id="d3bb868c-fe44-452c-aa26-769a6538c808",
            service_uri="http://www.example.com/webhook2",
            tenant_id="68a4459a-ccb8-493c-b9da-dd30457d1b84",
            use_aad_auth=True,
            use_common_alert_schema=True,
        ),
    ])

```

```yaml
resources:
  actionGroup:
    type: azure-native:insights:ActionGroup
    properties:
      actionGroupName: SampleActionGroup
      armRoleReceivers:
        - name: Sample armRole
          roleId: 8e3af657-a8ff-443c-a75c-2fe8c4bcb635
          useCommonAlertSchema: true
      automationRunbookReceivers:
        - automationAccountId: /subscriptions/187f412d-1758-44d9-b052-169e2564721d/resourceGroups/runbookTest/providers/Microsoft.Automation/automationAccounts/runbooktest
          isGlobalRunbook: false
          name: testRunbook
          runbookName: Sample runbook
          serviceUri: <serviceUri>
          useCommonAlertSchema: true
          webhookResourceId: /subscriptions/187f412d-1758-44d9-b052-169e2564721d/resourceGroups/runbookTest/providers/Microsoft.Automation/automationAccounts/runbooktest/webhooks/Alert1510184037084
      azureAppPushReceivers:
        - emailAddress: johndoe@email.com
          name: Sample azureAppPush
      azureFunctionReceivers:
        - functionAppResourceId: /subscriptions/5def922a-3ed4-49c1-b9fd-05ec533819a3/resourceGroups/aznsTest/providers/Microsoft.Web/sites/testFunctionApp
          functionName: HttpTriggerCSharp1
          httpTriggerUrl: http://test.me
          name: Sample azureFunction
          useCommonAlertSchema: true
      emailReceivers:
        - emailAddress: johndoe@email.com
          name: John Doe's email
          useCommonAlertSchema: false
        - emailAddress: janesmith@email.com
          name: Jane Smith's email
          useCommonAlertSchema: true
      enabled: true
      eventHubReceivers:
        - eventHubName: testEventHub
          eventHubNameSpace: testEventHubNameSpace
          name: Sample eventHub
          subscriptionId: 187f412d-1758-44d9-b052-169e2564721d
          tenantId: 68a4459a-ccb8-493c-b9da-dd30457d1b84
      groupShortName: sample
      itsmReceivers:
        - connectionId: a3b9076c-ce8e-434e-85b4-aff10cb3c8f1
          name: Sample itsm
          region: westcentralus
          ticketConfiguration: '{"PayloadRevision":0,"WorkItemType":"Incident","UseTemplate":false,"WorkItemData":"{}","CreateOneWIPerCI":false}'
          workspaceId: 5def922a-3ed4-49c1-b9fd-05ec533819a3|55dfd1f8-7e59-4f89-bf56-4c82f5ace23c
      location: Global
      logicAppReceivers:
        - callbackUrl: https://prod-27.northcentralus.logic.azure.com/workflows/68e572e818e5457ba898763b7db90877/triggers/manual/paths/invoke/azns/test?api-version=2016-10-01&sp=%2Ftriggers%2Fmanual%2Frun&sv=1.0&sig=Abpsb72UYJxPPvmDo937uzofupO5r_vIeWEx7KVHo7w
          name: Sample logicApp
          resourceId: /subscriptions/187f412d-1758-44d9-b052-169e2564721d/resourceGroups/LogicApp/providers/Microsoft.Logic/workflows/testLogicApp
          useCommonAlertSchema: false
      resourceGroupName: Default-NotificationRules
      smsReceivers:
        - countryCode: '1'
          name: John Doe's mobile
          phoneNumber: '1234567890'
        - countryCode: '1'
          name: Jane Smith's mobile
          phoneNumber: '0987654321'
      tags: {}
      voiceReceivers:
        - countryCode: '1'
          name: Sample voice
          phoneNumber: '1234567890'
      webhookReceivers:
        - name: Sample webhook 1
          serviceUri: http://www.example.com/webhook1
          useCommonAlertSchema: true
        - identifierUri: http://someidentifier/d7811ba3-7996-4a93-99b6-6b2f3f355f8a
          name: Sample webhook 2
          objectId: d3bb868c-fe44-452c-aa26-769a6538c808
          serviceUri: http://www.example.com/webhook2
          tenantId: 68a4459a-ccb8-493c-b9da-dd30457d1b84
          useAadAuth: true
          useCommonAlertSchema: true

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:insights:ActionGroup SampleActionGroup /subscriptions/187f412d-1758-44d9-b052-169e2564721d/resourceGroups/Default-NotificationRules/providers/microsoft.insights/actionGroups/SampleActionGroup 
```
