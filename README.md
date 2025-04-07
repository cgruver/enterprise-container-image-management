# enterprise-container-image-management
Reference Architecture for managing the consistency of container images across an enterprise

## Managing Container Images

Consider creating a declarative and GitOps driven system to manage container images for your enterprise.

One of the major challenges of any organization is managing dependencies, versions, and CVEs in all of their runtimes - Dev/QA/Prod

A GitOps driven approach to managing container images can greatly reduce the toil that comes with wrangling all of the things running in the enterprise.

The open source project [CeKit](https://cekit.io) offers a declarative means to manage images.  

If you create a tree based approach, where runtime and developer images share common components, then you ensure consistency between Dev/QA/Prod environments.

```bash
Base-Image # my.org.registry/images/common-base:latest - Built from - registry.access.redhat.com/ubi9 + org specific dependencies
|
|-|- Runtime Java 21 # Base + Java 21 Module
  |
  |- Developer Tooling # Base + Java 21 Module + Maven Module + Developer Common Module
```

