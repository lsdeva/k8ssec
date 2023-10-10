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
     - No direct `kubectl` command, third-party tools are used for image scanning.
   - **Signed Images:**
     - No direct `kubectl` command, images should be signed during the build and push phase.

### 6. **Runtime Security:**
   - **Anomaly Detection:** 
     - No direct `kubectl` command, external tools and systems are needed.
   - **Security Plugins:**
     - Depends on the specific plugins; generally, they are installed and managed through configurations.

### 7. **API Server Security:**
   - **Authentication:** 
     - No specific `kubectl` command, configured within API server settings.
   - **Authorization:** 
     - Same as above.

### 8. **Logging and Monitoring:**
   - **Centralized Logging:** 
     - No direct `kubectl` command, implemented through logging solutions configurations.
   - **Alerts:** 
     - No direct `kubectl` command, alerts are configured in monitoring solutions like Prometheus.

### 9. **Resource Management:**
   - **Quotas and Limits:** 
     - Apply Resource Quota: `kubectl apply -f <resourcequota.yaml>`
     - Apply Limit Range: `kubectl apply -f <limitrange.yaml>`

### 10. **Cluster Updates:**
   - **Patching:** 
     - No direct `kubectl` command, can be handled by package managers or cloud provider tools.
   - **Version Upgrades:**
     - Upgrade command depends on the specific setup, often managed through upgrade scripts or cloud provider consoles.

### 11. **Third-party Security Tools:**
   - **CIS Benchmarks:** 
     - No direct `kubectl` command, involves running audit scripts or third-party tools.
   - **Security Software:** 
     - No direct `kubectl` command, involves installing and configuring third-party software.

### 12. **Incident Response:**
   - **Plan:** 
     - No direct `kubectl` command, it’s about having written plans and procedures.
   - **Drills:** 
     - No direct `kubectl` command, involves testing the incident response plan.

### 13. **Backup and Recovery:**
   - **Backup:** 
     - Using Velero: `velero backup create <backup-name> --include-namespaces=<namespaces>`
   - **Disaster Recovery:** 
     - Restoring using Velero: `velero restore create --from-backup <backup-name>`

### 13. **Backup and Recovery:**
   - **Backup:** Regularly backup Kubernetes configuration, applications, and data.
   - **Disaster Recovery:** Have a disaster recovery plan to restore operations after an attack.

