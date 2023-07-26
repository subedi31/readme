# Descriptions of Gatekeeper Policy 
## 1. AllowedUsers: 
The constraint file alloweduser_constraints.yaml controls the user and group IDs of the container and some volumes. User may change the parameter in alloweduser_constraints.yaml file as per the their requirements.
## 2. AllowPrivilegeEscalationContainer:
The constraint allowprivilegeescalationContainer_constraints.yml file Controls restricting escalation to root privileges. Corresponds to the allowPrivilegeEscalation field. User may change the parameter in allowprivilegeescalationContainer_constraints.yml file as per the their requirements.
## 3. AppArmor:
 The constraint file apparmor_constraints.yaml configures an allow-list of AppArmor profiles for use by containers. User may change the parameter in apparmor_constraints.yaml file as per the their requirements.
## 4. AutomountServiceAccountTokenPod:
 The constraint file automountserviceaccounttokenpod_constraints.yaml controls the ability of any Pod to enable automountServiceAccountToken.
## 5. BlockEndpointEditDefaultRole:
 The constraint file blockendpointeditdefaultrole_constraints.yaml forbids the system:aggregate-to-edit ClusterRole from granting permission to create/patch/update Endpoints. 
## 6. BlockLoadBalancer:
 The constraint file blockloadbalancer_constraints.yaml disallows all Services with type LoadBalancer. User may change the parameter in blockloadbalanacer_constraints.yaml file as per the their requirements.
## 7. BlockNodePort:
 The constraint file blocknodeport_constraints.yaml disallows all Services with type NodePort.
## 8. NoUpdateServiceAccount:
 The constraint file updatingserviceaccount_constraints.yaml blocks updating the service account on resources that abstract over Pods.
## 9. BlockWildcardIngress:
 The constraint file blockwildcardingress_constraints.yaml block user to create Ingresses with a blank or wildcard (*) hostname since that would enable them to intercept traffic for other services in the cluster, even if they don't have access to those services.
## 10. Capabilities:
 The constraint file capabilities_constraints.yaml controls Linux capabilities on containers. User may change the parameter in capabilities_constraints.yaml as per the their requirements.
## 11. ContainerLimit 
The constraint file container_limit.yaml applies containers to have memory and CPU limits set and constrains limits to be within the specified maximum values. User need to change parameter as per their need.
## 12. ContainerEphemeralStorageLimit:
The constraint file containerephemeralstoragelimit_limit.yaml requires containers to have an ephemeral storage limit set and constrains the limit to be within the specified maximum values. User may change the parameter as per the their requirements.
## 13. ContainerRatios:
The constraint file containerratios_constraints.yaml sets a maximum ratio for container resource limits to requests. User may change the parameter as per the their requirements.
## 14. ContainerRequests;
The constraint file containerrequests_constraints.yaml requires containers to have memory and CPU requests set and constrains requests to be within the specified maximum values.User may change the parameter as per the their requirements.
## 15. DisallowAnonymous:
The constraint file disallowanonymous_constraints.yaml disallows associating ClusterRole and Role resources to the system:anonymous user and system:unauthenticated group.User may change the parameter as per the their requirements.
## 16. DisallowedTags:
The constraint file disallowed_constraints.yaml requires container images to have an image tag different from the ones in the specified list.User may change the parameter as per the their requirements.
## 17. ExternalIPs:
The constraint file externalips_constraints.yaml restricts service externalIPs to an allowed list of IP addresses.User may change the parameter  as per the their requirements.
## 18. FlexVolumes:
The constraint file cflexvolumes_constraints.yaml controls the allowlist of FlexVolume drivers. Corresponds to the allowedFlexVolumes field. User may change the parameter as per the their requirements.
## 19. FSGroup:
The constraint file fsgroup_constraints.yaml controls allocating an FSGroup that owns the Pod's volumes. Corresponds to the fsGroup.User may change the parameter as per the their requirements.
## 20. HorizontalPodAutoscaler:
The constraint file horizontalpodautoscaler_constraints.yaml disallow the following scenarios when deploying HorizontalPodAutoscalers 1. Deployment of HorizontalPodAutoscalers with .spec.minReplicas or .spec.maxReplicas outside the ranges defined in the constraint 2. Deployment of HorizontalPodAutoscalers where the difference between .spec.minReplicas and .spec.maxReplicas is less than the configured minimumReplicaSpread 3. Deployment of HorizontalPodAutoscalers that do not reference a valid scaleTargetRef (e.g. Deployment, ReplicationController, ReplicaSet, StatefulSet).User may change the parameter as per the their requirements.
## 21. HostFilesystem:
The constraint file hostfilesystem_constraints.yaml controls usage of the host filesystem. Corresponds to the allowedHostPaths field.User may change the parameter as per the their requirements.
## 22. HostNamespace:
The constraint file hostnamespace_constraints.yaml disallows sharing of host PID and IPC namespaces by pod containers. Corresponds to the hostPID and hostIPC fields.User may change the parameter as per the their requirements.
## 23. HostNetworkingPorts:
The constraint file hostnetworkingports_constraints.yaml controls usage of host network namespace by pod containers. Specific ports must be specified. Corresponds to the hostNetwork and hostPorts fields. User may change the parameter as per the their requirements.
## 24. HttpsOnly:
The constraint file httpsonly_constraints.yaml requires Ingress resources to be HTTPS only. Ingress resources must include the kubernetes.io/ingress.allow-http annotation, set to false. By default a valid TLS {} configuration is required, this can be made optional by setting the tlsOptional parameter to true. User may change the parameter as per the their requirements.
## 25. ImageDigests:
The constraint file imagedigests_constraints.yaml requires container images to contain a digest. User may change the parameter as per the their requirements.
## 26 K8sAllowedRepos;
The constraint file k8sallowedrepos_constraints.yaml requires container images to begin with a string from the specified list. User may change the parameter as per the their requirements.
## 27 PodDisruptionBudget:
The constraint file poddisruptionbudget_constraints.yaml disallow the following scenarios when deploying PodDisruptionBudgets or resources that implement the replica subresource (e.g. Deployment, ReplicationController, ReplicaSet, StatefulSet): 1. Deployment of PodDisruptionBudgets with .spec.maxUnavailable == 0 2. Deployment of PodDisruptionBudgets with .spec.minAvailable == .spec.replicas of the resource with replica subresource This will prevent PodDisruptionBudgets from blocking voluntary disruptions such as node draining. User may change the parameter as per the their requirements.
## 28 PrivilegedContainer:
The constraint file privilegedcontainer_constraints.yaml controls the ability of any container to enable privileged mode. Corresponds to the privileged field. 
## 29 ProcMount:
The constraint file procmount_constraints.yaml controls the allowed procMount types for the container. Corresponds to the allowedProcMountTypes field. User may change the parameter as per the their requirements.
## 30 ReadOnlyRootFilesystem:
The constraint file readonlyrootfilesystem_constraints.yaml requires the use of a read-only root file system by pod containers. Corresponds to the readOnlyRootFilesystem field.
## 31 ReplicaLimits:
 The constraint file replicalimits_constraints.yaml requires that objects with the field spec.replicas (Deployments, ReplicaSets, etc.) specify a number of replicas within defined ranges. User may change the parameter as per the their requirements.
## 32 RequiredAnnotations:
The constraint file requiredannotations_constraints.yaml requires resources to contain specified annotations, with values matching provided regular expressions. User may change the parameter as per the their requirements.
## 33 RequiredLabels;
The constraint file requiredlabels_constraints.yaml requires resources to contain specified labels, with values matching provided regular expressions. User may change the parameter as per the their requirements.
## 34 RequiredProbes;
The constraint file required_constraints.yaml requires Pods to have readiness and/or liveness probes. User may change the parameter as per the their requirements.
## 35 Seccomp:
The constraint file seccomp_constraints.yaml controls the seccomp profile used by containers. Corresponds to the seccomp.security.alpha.kubernetes.io/allowedProfileNames annotation. User may change the parameter as per the their requirements. 
## 36 SELinuxV2:
The constraint file selinuxv2_constraints.yaml defines an allow-list of seLinuxOptions configurations for pod containers. Corresponds to a PodSecurityPolicy requiring SELinux configs. User may change the parameter as per the their requirements.
## 37 StorageClass:
The constraint file storageclass_constraints.yaml requires storage classes to be specified when used. User may change the parameter as per the their requirements.
## 38 UniqueIngressHost:
The constraint file uniqueingresshost_constraints.yaml requires all Ingress rule hosts to be unique. Does not handle hostname wildcards:
## 39 UniqueServiceSelector:
The constraint file uniqueserviceselector_constraints.yaml requires Services to have unique selectors within a namespace. Selectors are considered the same if they have identical keys and values. Selectors may share a key/value pair so long as there is at least one distinct key/value pair between them.  
## 40 VerifyDeprecatedAPI:
The constraint file verifydeprecatedapi_constraints.yaml verifies deprecated Kubernetes APIs to ensure all the API versions are up to date. This template does not apply to audit as audit looks at the resources which are already present in the cluster with non-deprecated API versions. User may change the parameter as per the their requirements.
## 41 VolumeTypes:
The constraint file volumetypes_constraints.yaml restricts mountable volume types to those specified by the user. Corresponds to the volumes field in a Pod. User may change the parameter in volumetypes_constraints.yaml as per the their requirements.
