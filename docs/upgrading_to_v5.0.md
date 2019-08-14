# Upgrading to v5.0

The v5.0 release of *kubernetes-engine* is a backwards incompatible
release.

## Migration Instructions

### Service Account creation

Previously, if you explicitly specified a Service Account using the `service_account` variable on the module this was sufficient to force that Service Account to be used.

Now, an additional `create_service_account` has been added with a default value of `true`. If you would like to use an explicitly created Service Account from outside the module, you will need to set `create_service_account` to `false` (in addition to passing in the Service Account email).

No action is needed if you use the module's default service account.

```diff
 module "kubernetes_engine_private_cluster" {
   source  = "terraform-google-modules/kubernetes-engine/google"
-  version = "~> 4.0"
+  version = "~> 5.0"

   service_account        = "project-service-account@my-project.iam.gserviceaccount.com"
+  create_service_account = true
   # ...
 }
```
