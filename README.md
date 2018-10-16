# Overview
Demonstration of using [mu](https://github.com/stelligent/mu) to create a CI/CD pipeline with CodePipeline for managing the provisioning of an EKS environment and deploying a simple application to it. 

# Fork and clone this repo
```
git clone git@github.com:cplee/hello-eks.git
```

# Install mu
```
curl -s https://getmu.io/install.sh | sh
```

# Create the pipeline
```
mu pipeline up
```

You can watch the pipeline deploy through the AWS CodePipeline console or via:

```
mu svc show -w
```

# Test the application
Once deployment is complete, grab the `Base URL` and open in your browser:

```
mu env show acceptance
```

# Using kubectl
In order to be able to use `kubectl` with the new EKS cluster, you need to do the following:
* Update `mu.yml` to add your IAM username to the `rbac:` section to bind your user to the admin role and push the change to allow mu to deploy the new role bindings.
* Install `aws-iam-authenticator` as per the [EKS User Guide](https://docs.aws.amazon.com/eks/latest/userguide/configure-kubectl.html) 
* Create a `kubeconfig` for the EKS cluster as per the [EKS User Guide](https://docs.aws.amazon.com/eks/latest/userguide/create-kubeconfig.html)

# Cleanup
To cleanup all the stacks that mu creates, just run:

```
mu purge
```
