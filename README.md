# Overview
Demonstration of using [mu](https://github.com/stelligent/mu) to create a CI/CD pipeline with CodePipeline for deploying a simple application on EKS.

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

# kubectl
In order to be able to use `kubectl` with the new EKS cluster, you need to do the following:
* Update `mu.yml` to add your IAM username to the `RBAC:` section to bind your user to the admin role
* Install `aws-iam-authenticator` as per the [EKS User Guide](https://docs.aws.amazon.com/eks/latest/userguide/configure-kubectl.html)
* Create a `kubeconfig` for the EKS cluster as per the [EKS User Guide](https://docs.aws.amazon.com/eks/latest/userguide/create-kubeconfig.html)
