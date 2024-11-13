Setup Instructions
.......................................................................................
Step 1: Clone the Repository

bash:
git clone <repository-url>
cd <repository-directory>
.......................................................................................
Step 2: Apply RBAC Configuration
For the staging namespace:
bash: kubectl apply -f rbac-staging.yaml

For the production namespace:
bash: kubectl apply -f rbac-production.yaml
.......................................................................................
Step 3: Apply Secrets
Update secrets-rds.yaml with base64-encoded RDS credentials.
Apply the secrets for both environments:
bash: kubectl apply -f secrets-rds.yaml
.......................................................................................
Step 4: Deploy Applications
For the staging environment:
bash: kubectl apply -f deployment-staging.yaml

For the production environment:
bash: kubectl apply -f deployment-production.yaml
.......................................................................................
Step 5: Validate Configurations
Verify RBAC permissions using kubectl auth can-i:
bash: kubectl auth can-i get pods --as=developer-user -n staging
Test the application's connectivity to the RDS database.

Best Practices

1. RBAC:                            Always grant minimal permissions necessary for each role.
                                    Regularly audit roles and bindings.
2. Secrets:                         Avoid hardcoding sensitive data in manifests or code.
                                    Enable encryption at rest for Kubernetes Secrets.
3. Networking:                      Restrict RDS access using AWS security groups and VPC configurations.
4. Monitoring:                      Enable Kubernetes audit logging to track RBAC and secret access.
5. IAM Authentication (Optional):   Use AWS IAM roles and IRSA (IAM Roles for Service Accounts) for enhanced security.
.......................................................................................
Contribution Guidelines

Feel free to submit pull requests for enhancements or bug fixes. Please follow these steps:

1. Fork the repository.
2. Create a new branch.
3. Commit your changes and push them to your fork.
4. Submit a pull request.
   
.......................................................................................
Contact
For any questions or support, contact Ashish Kumar Banyal at:
📧 ashishkumarbanyal@gmail.com
