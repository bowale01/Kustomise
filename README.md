
Kustomize is a configuration management tool specifically designed for Kubernetes. It provides a way to customize application configurations without modifying the original YAML files, enabling more flexible and reusable Kubernetes deployments. Kustomize works by applying overlays to a set of base resources, allowing you to maintain clean, declarative configuration files while making environment-specific changes.

Here are the key concepts and features of Kustomize:

Key Concepts:
1)  Base Resources:

      - Core YAML manifests that define your Kubernetes resources. They are environment-agnostic and can be reused across different environments (e.g., development, staging, production).
        
2) Overlays:

     - Overlays are additional configurations applied on top of base resources to customize them for specific environments. Overlays can include patches, configuration changes, and additional resources.


3) Kustomization File:

   - Each directory that uses Kustomize must contain a kustomization.yaml file. This file specifies the resources, patches, and configurations that Kustomize should apply.

     
Features:

1) Resource Overlays:

     - Modify existing resources using patches. Patches can be in JSON, YAML, or strategic merge formats.


2) Resource Generators:

     - Generate ConfigMaps and Secrets from files or literals.

3)  Variable Substitution:

    - Substitute variables in configuration files to dynamically adjust resource definitions based on the environment.
  
 
4) Transformers:

     - Apply transformations to resources, such as adding common labels or annotations, modifying image tags, or updating namespace information.
  
       
5) Composition:

     - Combine multiple kustomization.yaml files to build complex configurations from simpler, reusable parts.
  

Example Usage:

Consider you have a base deployment configuration in a base directory:

![image](https://github.com/debolek/Kustomise/assets/37187773/a263caa2-7752-4ee2-946b-4a3982e8aa6d)


A kustomization.yaml file in the base directory:

![image](https://github.com/debolek/Kustomise/assets/37187773/276abb8a-a75f-4c6e-b1ca-62f252b1da8d)



For an overlay in the production environment, you could have:

![image](https://github.com/debolek/Kustomise/assets/37187773/7f5aa2e8-75d7-4eb5-ad9b-4f9bc3f67195)


And the patch file overlays/production/deployment-patch.yaml:

![image](https://github.com/debolek/Kustomise/assets/37187773/a8148cf3-fa00-4bc0-a8b7-da8f473f1d94)



Applying Kustomize:
To apply the customized configuration to your Kubernetes cluster, you can use the kubectl command with the -k flag:


kubectl apply -k overlays/production



This command tells kubectl to apply the resources defined in the kustomization.yaml file in the overlays/production directory, effectively deploying the production version of your application.

Integration with Kubernetes:
Starting with Kubernetes 1.14, kubectl natively supports Kustomize through the -k flag, making it easy to integrate Kustomize into your deployment workflows without needing additional tools.

Kustomize provides a powerful yet simple way to manage Kubernetes configurations, enabling you to maintain clean, reusable base manifests while allowing environment-specific customizations through overlays.







