# k8ssec

Securing Kubernetes Workloads Against Common Attack Vectors 

### 1. **Access Control:**
   - **Role-Based Access Control (RBAC):** Implement RBAC to limit access based on users' roles and responsibilities.
   - **Namespace Isolation:** Separate resources and applications using namespaces to reduce the attack surface.

### 2. **Network Policies:**
   - **Firewall Rules:** Implement firewall rules to restrict traffic between pods and external sources.
   - **Ingress/Egress Controls:** Apply policies to control incoming and outgoing traffic.

### 3. **Security Contexts:**
   - **Pod Security:** Assign security contexts to limit pod and container privileges.

### 4. **Secret Management:**
   - **Encryption:** Encrypt sensitive data both at rest and in transit.
   - **Secret Engines:** Utilize secret management tools like HashiCorp Vault or AWS Secrets Manager.

### 5. **Image Security:**
   - **Image Scanning:** Scan container images for vulnerabilities.
   - **Signed Images:** Use signed images to ensure integrity.

### 6. **Runtime Security:**
   - **Anomaly Detection:** Monitor and alert on abnormal behavior.
   - **Security Plugins:** Utilize plugins that enhance runtime security.

### 7. **API Server Security:**
   - **Authentication:** Ensure that only authenticated users can access the API server.
   - **Authorization:** Ensure that users are only able to perform actions they are authorized for.

### 8. **Logging and Monitoring:**
   - **Centralized Logging:** Implement centralized logging to monitor and audit actions.
   - **Alerts:** Create alerts for suspicious and malicious activities.

### 9. **Resource Management:**
   - **Quotas and Limits:** Implement resource quotas and limits to avoid resource exhaustion attacks.

### 10. **Cluster Updates:**
   - **Patching:** Regularly update and patch the Kubernetes cluster to fix known vulnerabilities.
   - **Version Upgrades:** Upgrade to newer versions to benefit from security enhancements.

### 11. **Third-party Security Tools:**
   - **CIS Benchmarks:** Follow the CIS Kubernetes Benchmark for best practices.
   - **Security Software:** Use specialized security software designed for Kubernetes security.

### 12. **Incident Response:**
   - **Plan:** Have an incident response plan in place.
   - **Drills:** Conduct regular drills to ensure the effectiveness of the response plan.


# kubectl commands

### 1. **Access Control:**
   - **RBAC:**
     - Creating a Role: `kubectl create role <role-name> --verb=<verbs> --resource=<resources>`
     - Creating a ClusterRole: `kubectl create clusterrole <role-name> --verb=<verbs> --resource=<resources>`
   - **Namespace Isolation:**
     - Creating a Namespace: `kubectl create namespace <namespace-name>`

### 2. **Network Policies:**
   - **Firewall Rules:** 
     - Apply a Network Policy: `kubectl apply -f <networkpolicy.yaml>`
   - **Ingress/Egress Controls:**
     - Apply Ingress: `kubectl apply -f <ingress.yaml>`

### 3. **Security Contexts:**
   - **Pod Security:** 
     - Apply Security Context: Include security context in the pod’s YAML file and apply using `kubectl apply -f <pod.yaml>`

### 4. **Secret Management:**
   - **Encryption:**
     - Create a Secret: `kubectl create secret generic <secret-name> --from-literal=key=value`
   - **Secret Engines:**
     - No direct `kubectl` commands, usually configured via a UI or API.

### 5. **Image Security:**
   - **Image Scanning:** 
     - While there's no direct `kubectl` command for image scanning, you can integrate image scanning tools like Clair, Trivy, or Anchore into your CI/CD pipeline to automatically scan images during the build and deployment process.
   - **Signed Images:**
     - Utilize Docker Content Trust or a similar tool to sign images during the build phase, then configure your Kubernetes to only pull signed images.

### 6. **Runtime Security:**
   - **Anomaly Detection:** 
     - Implement and configure tools like Falco or Sysdig that are capable of runtime security monitoring. They can be deployed as DaemonSets on Kubernetes clusters.
   - **Security Plugins:**
     - While specific commands depend on the plugin, generally, they are installed and configured via Helm charts, Operators, or YAML files.

### 7. **API Server Security:**
   - **Authentication:** 
     - Configure authentication mechanisms, such as OIDC or token-based authentication, by modifying the API server’s startup parameters or configuration files.
   - **Authorization:** 
     - Implement RBAC and create roles and role bindings to assign permissions, as detailed in the Access Control section.

### 8. **Logging and Monitoring:**
   - **Centralized Logging:** 
     - Deploy logging solutions like the EFK (Elasticsearch, Fluentd, and Kibana) stack or Loki-Stack as a DaemonSet or StatefulSet in your cluster. 
   - **Alerts:** 
     - Use Prometheus with Alertmanager to set up alerts. Deploy them using Helm or applying YAML files and configure alerting rules.

### 9. **Resource Management:**
   - **Quotas and Limits:** 
     - Apply Resource Quota: `kubectl apply -f <resourcequota.yaml>`
     - Apply Limit Range: `kubectl apply -f <limitrange.yaml>`

### 10. **Cluster Updates:**
   - **Patching:** 
     - Depending on the Kubernetes distribution, use package managers like `apt` or `yum`, or use kubeadm: `kubeadm upgrade apply <version>`.
   - **Version Upgrades:**
     - Use the appropriate upgrade procedures for your specific Kubernetes distribution, often involving commands like `kubectl drain <node-name>` for node maintenance and upgrade.

### 11. **Third-party Security Tools:**
   - **CIS Benchmarks:** 
     - Utilize tools like kube-bench that can be run as a job or pod in your cluster to check the configurations against CIS benchmarks.
   - **Security Software:** 
     - Deploy solutions like Aqua Security, Sysdig, or Twistlock as Helm charts, Operators, or via YAML files and configure them as per your security requirements.

### 12. **Incident Response:**
   - **Plan:** 
     - Ensure that written plans and procedures are documented, accessible, and known by the team members. Utilize Kubernetes auditing and logging to gather information during incidents.
   - **Drills:** 
     - Use `kubectl` commands to simulate failure scenarios, like draining nodes or deleting pods, to practice incident responses.
       
### 13. **Backup and Recovery:**
   - **Backup:** 
     - Using Velero: `velero backup create <backup-name> --include-namespaces=<namespaces>`
   - **Disaster Recovery:** 
     - Restoring using Velero: `velero restore create --from-backup <backup-name>`

### 13. **Backup and Recovery:**
   - **Backup:** Regularly backup Kubernetes configuration, applications, and data.
   - **Disaster Recovery:** Have a disaster recovery plan to restore operations after an attack.

