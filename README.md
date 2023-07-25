#### Descriptions of Kubernetes Gatekeeper Policies Kinds ######

# Note: Kubernetes Gatekeeper Policies Kinds can be found in the respective YML files of Templates and Constraints.
# Definitions:
# 1. Templates:
It define a way to validate some set of Kubernetes objects in Gatekeeper’s Kubernetes admission controller. They are made of two main elements:
1. Rego code that defines a policy violation
2. The schema of the accompanying Constraint object, which represents an instantiation of a ConstraintTemplate
# 2. Constraints:
It is a declaration of requirements that a system needs to meet. In another word, Constraints are used to inform Gatekeeper that the admin wants a ConstraintTemplate to be enforced, and how.
# 3. Test-Manifests:
A manifest is used to check the policy whether it is running or not.

# Deployment Steps:
# 1. Install OPA Gatekeeper Agent on the EKS.
# 2. Deploy the Gatekeeper templates on the EKS.
# 3. Deploy the Gatekeeper policy constraints on the EKS. 
# 4. Test the Constraints to be effective using the test-manifest examples.

# Descriptions of Gatekeeper Policy 
## 1. AllowedUsers: 
Controls the user and group IDs of the container and some volumes. Corresponds to the runAsUser, runAsGroup, supplementalGroups, and fsGroup fields.
## 2. AllowPrivilegeEscalationContainer:
Controls restricting escalation to root privileges. Corresponds to the allowPrivilegeEscalation field.
## 3. AppArmor:
Configures an allow-list of AppArmor profiles for use by containers. 
## 4. AutomountServiceAccountTokenPod:
Controls the ability of any Pod to enable automountServiceAccountToken.
## 5. BlockEndpointEditDefaultRole:
This ConstraintTemplate forbids the system:aggregate-to-edit ClusterRole from granting permission to create/patch/update Endpoints. 
## 6. BlockLoadBalancer:
Disallows all Services with type LoadBalancer.
## 7. BlockNodePort:
Disallows all Services with type NodePort.
## 8. NoUpdateServiceAccount:
Blocks updating the service account on resources that abstract over Pods.
## 9. BlockWildcardIngress:
Users should not be able to create Ingresses with a blank or wildcard (*) hostname since that would enable them to intercept traffic for other services in the cluster, even if they don't have access to those services.
## 10. Capabilities:
Controls Linux capabilities on containers. Corresponds to the allowedCapabilities and requiredDropCapabilities fields.
## 11. ContainerLimits:
Requires containers to have memory and CPU limits set and constrains limits to be within the specified maximum values. 
## 12. ContainerEphemeralStorageLimit:
Requires containers to have an ephemeral storage limit set and constrains the limit to be within the specified maximum values. 
## 13. ContainerRatios:
Sets a maximum ratio for container resource limits to requests.
## 14. ContainerRequests;
Requires containers to have memory and CPU requests set and constrains requests to be within the specified maximum values.
## 15. DisallowAnonymous:
Disallows associating ClusterRole and Role resources to the system:anonymous user and system:unauthenticated group.
## 16. DisallowedTags:
Requires container images to have an image tag different from the ones in the specified list.
## 17. ExternalIPs:
Restricts Service externalIPs to an allowed list of IP addresses.
## 18. FlexVolumes:
Controls the allowlist of FlexVolume drivers. Corresponds to the allowedFlexVolumes field. 
## 19. FSGroup:
Controls allocating an FSGroup that owns the Pod's volumes. Corresponds to the fsGroup.
## 20. HorizontalPodAutoscaler:
Disallow the following scenarios when deploying HorizontalPodAutoscalers 1. Deployment of HorizontalPodAutoscalers with .spec.minReplicas or .spec.maxReplicas outside the ranges defined in the constraint 2. Deployment of HorizontalPodAutoscalers where the difference between .spec.minReplicas and .spec.maxReplicas is less than the configured minimumReplicaSpread 3. Deployment of HorizontalPodAutoscalers that do not reference a valid scaleTargetRef (e.g. Deployment, ReplicationController, ReplicaSet, StatefulSet).
## 21. HostFilesystem:
Controls usage of the host filesystem. Corresponds to the allowedHostPaths field.
## 22. HostNamespace:
Disallows sharing of host PID and IPC namespaces by pod containers. Corresponds to the hostPID and hostIPC fields.
## 23. HostNetworkingPorts:
Controls usage of host network namespace by pod containers. Specific ports must be specified. Corresponds to the hostNetwork and hostPorts fields. 
## 24. HttpsOnly:
Requires Ingress resources to be HTTPS only. Ingress resources must include the kubernetes.io/ingress.allow-http annotation, set to false. By default a valid TLS {} configuration is required, this can be made optional by setting the tlsOptional parameter to true.
## 25. ImageDigests:
Requires container images to contain a digest.
## 26 K8sAllowedRepos;
Requires container images to begin with a string from the specified list.
## 27 PodDisruptionBudget:
Disallow the following scenarios when deploying PodDisruptionBudgets or resources that implement the replica subresource (e.g. Deployment, ReplicationController, ReplicaSet, StatefulSet): 1. Deployment of PodDisruptionBudgets with .spec.maxUnavailable == 0 2. Deployment of PodDisruptionBudgets with .spec.minAvailable == .spec.replicas of the resource with replica subresource This will prevent PodDisruptionBudgets from blocking voluntary disruptions such as node draining. 
## 28 PrivilegedContainer:
Controls the ability of any container to enable privileged mode. Corresponds to the privileged field. 
## 29 ProcMount:
Controls the allowed procMount types for the container. Corresponds to the allowedProcMountTypes field.
## 30 ReadOnlyRootFilesystem:
Requires the use of a read-only root file system by pod containers. Corresponds to the readOnlyRootFilesystem field.
## 31 ReplicaLimits:
Requires that objects with the field spec.replicas (Deployments, ReplicaSets, etc.) specify a number of replicas within defined ranges.
## 32 RequiredAnnotations:
Requires resources to contain specified annotations, with values matching provided regular expressions.
## 33 RequiredLabels;
Requires resources to contain specified labels, with values matching provided regular expressions.
## 34 RequiredProbes;
Requires Pods to have readiness and/or liveness probes.
## 35 Seccomp:
Controls the seccomp profile used by containers. Corresponds to the seccomp.security.alpha.kubernetes.io/allowedProfileNames annotation.
## 36 SELinuxV2:
Defines an allow-list of seLinuxOptions configurations for pod containers. Corresponds to a PodSecurityPolicy requiring SELinux configs.
## 37 StorageClass:
Requires storage classes to be specified when used.
## 38 UniqueIngressHost:
Requires all Ingress rule hosts to be unique. Does not handle hostname wildcards:
## 39 UniqueServiceSelector:
Requires Services to have unique selectors within a namespace. Selectors are considered the same if they have identical keys and values. Selectors may share a key/value pair so long as there is at least one distinct key/value pair between them. 
## 40 VerifyDeprecatedAPI:
Verifies deprecated Kubernetes APIs to ensure all the API versions are up to date. This template does not apply to audit as audit looks at the resources which are already present in the cluster with non-deprecated API versions.
## 41 VolumeTypes:
Restricts mountable volume types to those specified by the user. Corresponds to the volumes field.
