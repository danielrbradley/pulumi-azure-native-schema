Image template is an ARM resource managed by Microsoft.VirtualMachineImages provider
API Version: 2022-07-01.
Previous API Version: 2020-02-14. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.
## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:virtualmachineimages:VirtualMachineImageTemplate myImageTemplate /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.VirtualMachineImages/imageTemplates/myImageTemplate 
```
