The registration definition.
API Version: 2022-10-01.
Previous API Version: 2019-09-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Put Registration Definition
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var registrationDefinition = new AzureNative.ManagedServices.RegistrationDefinition("registrationDefinition", new()
    {
        Plan = new AzureNative.ManagedServices.Inputs.PlanArgs
        {
            Name = "addesai-plan",
            Product = "test",
            Publisher = "marketplace-test",
            Version = "1.0.0",
        },
        Properties = new AzureNative.ManagedServices.Inputs.RegistrationDefinitionPropertiesArgs
        {
            Authorizations = new[]
            {
                new AzureNative.ManagedServices.Inputs.AuthorizationArgs
                {
                    PrincipalId = "f98d86a2-4cc4-4e9d-ad47-b3e80a1bcdfc",
                    PrincipalIdDisplayName = "Support User",
                    RoleDefinitionId = "acdd72a7-3385-48ef-bd42-f606fba81ae7",
                },
                new AzureNative.ManagedServices.Inputs.AuthorizationArgs
                {
                    DelegatedRoleDefinitionIds = new[]
                    {
                        "b24988ac-6180-42a0-ab88-20f7382dd24c",
                    },
                    PrincipalId = "f98d86a2-4cc4-4e9d-ad47-b3e80a1bcdfc",
                    PrincipalIdDisplayName = "User Access Administrator",
                    RoleDefinitionId = "18d7d88d-d35e-4fb5-a5c3-7773c20a72d9",
                },
            },
            Description = "Tes1t",
            EligibleAuthorizations = new[]
            {
                new AzureNative.ManagedServices.Inputs.EligibleAuthorizationArgs
                {
                    JustInTimeAccessPolicy = new AzureNative.ManagedServices.Inputs.JustInTimeAccessPolicyArgs
                    {
                        ManagedByTenantApprovers = new[]
                        {
                            new AzureNative.ManagedServices.Inputs.EligibleApproverArgs
                            {
                                PrincipalId = "d9b22cd6-6407-43cc-8c60-07c56df0b51a",
                                PrincipalIdDisplayName = "Approver Group",
                            },
                        },
                        MaximumActivationDuration = "PT8H",
                        MultiFactorAuthProvider = "Azure",
                    },
                    PrincipalId = "3e0ed8c6-e902-4fc5-863c-e3ddbb2ae2a2",
                    PrincipalIdDisplayName = "Support User",
                    RoleDefinitionId = "ae349356-3a1b-4a5e-921d-050484c6347e",
                },
            },
            ManagedByTenantId = "83abe5cd-bcc3-441a-bd86-e6a75360cecc",
            RegistrationDefinitionName = "DefinitionName",
        },
        RegistrationDefinitionId = "26c128c2-fefa-4340-9bb1-6e081c90ada2",
        Scope = "subscription/0afefe50-734e-4610-8a82-a144ahf49dea",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.managedservices.RegistrationDefinition;
import com.pulumi.azurenative.managedservices.RegistrationDefinitionArgs;
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
        var registrationDefinition = new RegistrationDefinition("registrationDefinition", RegistrationDefinitionArgs.builder()        
            .plan(Map.ofEntries(
                Map.entry("name", "addesai-plan"),
                Map.entry("product", "test"),
                Map.entry("publisher", "marketplace-test"),
                Map.entry("version", "1.0.0")
            ))
            .properties(Map.ofEntries(
                Map.entry("authorizations",                 
                    Map.ofEntries(
                        Map.entry("principalId", "f98d86a2-4cc4-4e9d-ad47-b3e80a1bcdfc"),
                        Map.entry("principalIdDisplayName", "Support User"),
                        Map.entry("roleDefinitionId", "acdd72a7-3385-48ef-bd42-f606fba81ae7")
                    ),
                    Map.ofEntries(
                        Map.entry("delegatedRoleDefinitionIds", "b24988ac-6180-42a0-ab88-20f7382dd24c"),
                        Map.entry("principalId", "f98d86a2-4cc4-4e9d-ad47-b3e80a1bcdfc"),
                        Map.entry("principalIdDisplayName", "User Access Administrator"),
                        Map.entry("roleDefinitionId", "18d7d88d-d35e-4fb5-a5c3-7773c20a72d9")
                    )),
                Map.entry("description", "Tes1t"),
                Map.entry("eligibleAuthorizations", Map.ofEntries(
                    Map.entry("justInTimeAccessPolicy", Map.ofEntries(
                        Map.entry("managedByTenantApprovers", Map.ofEntries(
                            Map.entry("principalId", "d9b22cd6-6407-43cc-8c60-07c56df0b51a"),
                            Map.entry("principalIdDisplayName", "Approver Group")
                        )),
                        Map.entry("maximumActivationDuration", "PT8H"),
                        Map.entry("multiFactorAuthProvider", "Azure")
                    )),
                    Map.entry("principalId", "3e0ed8c6-e902-4fc5-863c-e3ddbb2ae2a2"),
                    Map.entry("principalIdDisplayName", "Support User"),
                    Map.entry("roleDefinitionId", "ae349356-3a1b-4a5e-921d-050484c6347e")
                )),
                Map.entry("managedByTenantId", "83abe5cd-bcc3-441a-bd86-e6a75360cecc"),
                Map.entry("registrationDefinitionName", "DefinitionName")
            ))
            .registrationDefinitionId("26c128c2-fefa-4340-9bb1-6e081c90ada2")
            .scope("subscription/0afefe50-734e-4610-8a82-a144ahf49dea")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const registrationDefinition = new azure_native.managedservices.RegistrationDefinition("registrationDefinition", {
    plan: {
        name: "addesai-plan",
        product: "test",
        publisher: "marketplace-test",
        version: "1.0.0",
    },
    properties: {
        authorizations: [
            {
                principalId: "f98d86a2-4cc4-4e9d-ad47-b3e80a1bcdfc",
                principalIdDisplayName: "Support User",
                roleDefinitionId: "acdd72a7-3385-48ef-bd42-f606fba81ae7",
            },
            {
                delegatedRoleDefinitionIds: ["b24988ac-6180-42a0-ab88-20f7382dd24c"],
                principalId: "f98d86a2-4cc4-4e9d-ad47-b3e80a1bcdfc",
                principalIdDisplayName: "User Access Administrator",
                roleDefinitionId: "18d7d88d-d35e-4fb5-a5c3-7773c20a72d9",
            },
        ],
        description: "Tes1t",
        eligibleAuthorizations: [{
            justInTimeAccessPolicy: {
                managedByTenantApprovers: [{
                    principalId: "d9b22cd6-6407-43cc-8c60-07c56df0b51a",
                    principalIdDisplayName: "Approver Group",
                }],
                maximumActivationDuration: "PT8H",
                multiFactorAuthProvider: "Azure",
            },
            principalId: "3e0ed8c6-e902-4fc5-863c-e3ddbb2ae2a2",
            principalIdDisplayName: "Support User",
            roleDefinitionId: "ae349356-3a1b-4a5e-921d-050484c6347e",
        }],
        managedByTenantId: "83abe5cd-bcc3-441a-bd86-e6a75360cecc",
        registrationDefinitionName: "DefinitionName",
    },
    registrationDefinitionId: "26c128c2-fefa-4340-9bb1-6e081c90ada2",
    scope: "subscription/0afefe50-734e-4610-8a82-a144ahf49dea",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

registration_definition = azure_native.managedservices.RegistrationDefinition("registrationDefinition",
    plan=azure_native.managedservices.PlanArgs(
        name="addesai-plan",
        product="test",
        publisher="marketplace-test",
        version="1.0.0",
    ),
    properties=azure_native.managedservices.RegistrationDefinitionPropertiesResponseArgs(
        authorizations=[
            azure_native.managedservices.AuthorizationArgs(
                principal_id="f98d86a2-4cc4-4e9d-ad47-b3e80a1bcdfc",
                principal_id_display_name="Support User",
                role_definition_id="acdd72a7-3385-48ef-bd42-f606fba81ae7",
            ),
            azure_native.managedservices.AuthorizationArgs(
                delegated_role_definition_ids=["b24988ac-6180-42a0-ab88-20f7382dd24c"],
                principal_id="f98d86a2-4cc4-4e9d-ad47-b3e80a1bcdfc",
                principal_id_display_name="User Access Administrator",
                role_definition_id="18d7d88d-d35e-4fb5-a5c3-7773c20a72d9",
            ),
        ],
        description="Tes1t",
        eligible_authorizations=[{
            "justInTimeAccessPolicy": {
                "managedByTenantApprovers": [azure_native.managedservices.EligibleApproverArgs(
                    principal_id="d9b22cd6-6407-43cc-8c60-07c56df0b51a",
                    principal_id_display_name="Approver Group",
                )],
                "maximumActivationDuration": "PT8H",
                "multiFactorAuthProvider": "Azure",
            },
            "principalId": "3e0ed8c6-e902-4fc5-863c-e3ddbb2ae2a2",
            "principalIdDisplayName": "Support User",
            "roleDefinitionId": "ae349356-3a1b-4a5e-921d-050484c6347e",
        }],
        managed_by_tenant_id="83abe5cd-bcc3-441a-bd86-e6a75360cecc",
        registration_definition_name="DefinitionName",
    ),
    registration_definition_id="26c128c2-fefa-4340-9bb1-6e081c90ada2",
    scope="subscription/0afefe50-734e-4610-8a82-a144ahf49dea")

```

```yaml
resources:
  registrationDefinition:
    type: azure-native:managedservices:RegistrationDefinition
    properties:
      plan:
        name: addesai-plan
        product: test
        publisher: marketplace-test
        version: 1.0.0
      properties:
        authorizations:
          - principalId: f98d86a2-4cc4-4e9d-ad47-b3e80a1bcdfc
            principalIdDisplayName: Support User
            roleDefinitionId: acdd72a7-3385-48ef-bd42-f606fba81ae7
          - delegatedRoleDefinitionIds:
              - b24988ac-6180-42a0-ab88-20f7382dd24c
            principalId: f98d86a2-4cc4-4e9d-ad47-b3e80a1bcdfc
            principalIdDisplayName: User Access Administrator
            roleDefinitionId: 18d7d88d-d35e-4fb5-a5c3-7773c20a72d9
        description: Tes1t
        eligibleAuthorizations:
          - justInTimeAccessPolicy:
              managedByTenantApprovers:
                - principalId: d9b22cd6-6407-43cc-8c60-07c56df0b51a
                  principalIdDisplayName: Approver Group
              maximumActivationDuration: PT8H
              multiFactorAuthProvider: Azure
            principalId: 3e0ed8c6-e902-4fc5-863c-e3ddbb2ae2a2
            principalIdDisplayName: Support User
            roleDefinitionId: ae349356-3a1b-4a5e-921d-050484c6347e
        managedByTenantId: 83abe5cd-bcc3-441a-bd86-e6a75360cecc
        registrationDefinitionName: DefinitionName
      registrationDefinitionId: 26c128c2-fefa-4340-9bb1-6e081c90ada2
      scope: subscription/0afefe50-734e-4610-8a82-a144ahf49dea

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:managedservices:RegistrationDefinition 26c128c2-fefa-4340-9bb1-6e081c90ada2 /subscriptions/0afefe50-734e-4610-8a82-a144ahf49dea/providers/Microsoft.ManagedServices/registrationDefinitions/26c128c2-fefa-4340-9bb1-6e081c90ada2 
```
