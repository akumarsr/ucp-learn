   
   ## UCP Architecture Understanding
   UCP, which stands for Unified Control Plane, serves as the central hub for managing and orchestrating an enterprise's service deployment. Within this control plane, essential tasks include establishing configuration baselines, provisioning user and role access, and hosting applications to enable their seamless execution alongside associated services.

   The same framework can also be employed to deploy infrastructure using Crossplane.

   **what is Crossplane?**
   Crossplane is an open source control plane framework supported by the cloud-native community.
   Crossplane has been endorsed by some of the world's best companies and is released under the Apache 2.0 license. 

   [**More detail** :] (https://www.crossplane.io/ "Crossplane Official website")

   **why opt for Crossplane when constructing control planes?**

   **Declarative Configuration**: Crossplane facilitates the creation of control planes with Kubernetes-style declarative and API-driven configuration and management for various resources. This approach ensures that applications and infrastructure managed within your control plane possess inherent self-healing capabilities.

   **Unified Configuration**: Crossplane enables the convergence of application and infrastructure configurations within the same control plane. This simplifies your toolchains and deployment pipelines, reducing complexity.

   **Single Source of Truth**: Control planes constructed using Crossplane seamlessly integrate with CI/CD pipelines. This enables teams to produce, monitor, and approve changes while adhering to GitOps best practices with help of pull base CD tool like Flux and ArgoCD .

   **Automation through Reconciliation**: Your control planes comprise multiple controllers, each responsible for managing the complete lifecycle of a cloud and on-prem resource. These controllers handle provisioning, health monitoring, scaling, failover, and real-time response to external deviations from the desired configuration.

   **High Extensibility**: Crossplane-based control planes leverage well-established Kubernetes design and patterns, making them effortlessly extendable by incorporating custom APIs and controllers. This enhances flexibility and security by embedding policies, quotas, and permissions into custom definitions.

   **Clear Separation of Concerns**: Crossplane allows for the incorporation of organizational concepts and policies at the API level. This grants customers the freedom to self-service within the predefined boundaries of the control plane APIs.

   In summary, Crossplane bridges the gap between open-source capabilities and enterprise-grade control plane needs."

   The **UCP** is structured into distinct layers:
   **Layer 1 - Kubernetes Runtime**:Handles critical functions such as event monitoring, reconciliation, management of Custom Resource Definitions (CRDs), OpenAPI, data persistence (etcd), Ingress handling, RBAC enforcement, and workload execution.
   **Layer 2 - Crossplane Runtime**:Manages interactions with external APIs, encompassing resource creation, updates, and deletions.
   **Layer 3 - Providers**:Establishes connections with cloud APIs to enable the provisioning and management of cloud resources.
   **Layer 4 - Configurations**:Composes customized domain-specific APIs, empowering the management of resources and configurations with fine-grained control.

   **UCP** Leverages **ArgoCD** to continuously observe changes in the infrastructure and assists in seamlessly syncing these changes back to a Git repository.

   Here, the visual representation of **UCP**

   <picture>
      <source media="(prefers-color-scheme: light)" srcset="../images/UCP Architecture Understanding.png">
      <img alt="UCP Architecture Understanding" width="850px" height="350px" src="../images/UCP Architecture Understanding.png">
    </picture> 

   The platform team is responsible for developing XRDs and compositions of managed resources to meet enterprise security and other governance requirements.

