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

# Descriptions of Gatekeeper Policy Kinds
# 1. AllowedUsers: 
Controls the user and group IDs of the container and some volumes. Corresponds to the runAsUser, runAsGroup, supplementalGroups, and fsGroup fields in a Policy.
# 2. PAllowPrivilegeEscalationContainer:
Controls restricting escalation to root privileges. Corresponds to the allowPrivilegeEscalation field in a Policy.
# 3. AppArmor:
Configures an allow-list of AppArmor profiles for use by containers. This corresponds to specific annotations applied to a Policy.
# 4. AutomountServiceAccountTokenPod:
Controls the ability of any Pod to enable automountServiceAccountToken.
# 5. BlockEndpointEditDefaultRole:
This ConstraintTemplate forbids the system:aggregate-to-edit ClusterRole from granting permission to create/patch/update Endpoints. \
# 6. BlockLoadBalancer:
Disallows all Services with type LoadBalancer.
# 7. BlockNodePort:
Disallows all Services with type NodePort.
# 8. NoUpdateServiceAccount:
Blocks updating the service account on resources that abstract over Pods.
# 9. BlockWildcardIngress:
Users should not be able to create Ingresses with a blank or wildcard (*) hostname since that would enable them to intercept traffic for other services in the cluster, even if they don't have access to those services.
# 10. Capabilities:
Controls Linux capabilities on containers. Corresponds to the allowedCapabilities and requiredDropCapabilities fields in a Policy.
# 11. ContainerLimits:
Requires containers to have memory and CPU limits set and constrains limits to be within the specified maximum values. 
# 12. ContainerEphemeralStorageLimit:
Requires containers to have an ephemeral storage limit set and constrains the limit to be within the specified maximum values. 
# 13. ContainerRatios:
Sets a maximum ratio for container resource limits to requests.
# 14. ContainerRequests;
Requires containers to have memory and CPU requests set and constrains requests to be within the specified maximum values.
# 15. DisallowAnonymous:
Disallows associating ClusterRole and Role resources to the system:anonymous user and system:unauthenticated group.
# 16. DisallowedTags:
Requires container images to have an image tag different from the ones in the specified list.
# 17. ExternalIPs:
Restricts Service externalIPs to an allowed list of IP addresses.
# 18. FlexVolumes:
Controls the allowlist of FlexVolume drivers. Corresponds to the allowedFlexVolumes field in Policy. 
# 19. FSGroup:
Controls allocating an FSGroup that owns the Pod's volumes. Corresponds to the fsGroup field in a Policy.
# 20. HorizontalPodAutoscaler:
Disallow the following scenarios when deploying HorizontalPodAutoscalers 1. Deployment of HorizontalPodAutoscalers with .spec.minReplicas or .spec.maxReplicas outside the ranges defined in the constraint 2. Deployment of HorizontalPodAutoscalers where the difference between .spec.minReplicas and .spec.maxReplicas is less than the configured minimumReplicaSpread 3. Deployment of HorizontalPodAutoscalers that do not reference a valid scaleTargetRef (e.g. Deployment, ReplicationController, ReplicaSet, StatefulSet).
# 21. HostFilesystem:
Controls usage of the host filesystem. Corresponds to the allowedHostPaths field in a PodSecurityPolicy.
