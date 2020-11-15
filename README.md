# simple-codeartifact-cloudformation
A simple Cloudformation for building a useful Code Artifact for hosting and caching modules.

##  Get Code

```bash
git clone git@github.com:bwinkers/simple-codeartifact-cloudformation.git
```

## Change in the repo directory

```bash
cd simple-codeartifact-cloudformation
```

## Verify the file

```bash
aws cloudformation validate-template --template-body file://template.yaml
{
    "Parameters": []
}
```

## Deploy the stack

```bash
aws cloudformation deploy --template-body file://template.yaml --stack-name private-repo-stack
```

## Get Login instructions from AWS Console

Login to the console and view Code Artifact to see your repos.

![Artifact Console]('docs/../docs/images/view-connection-instructions.png)

Click the big orange button to get connection info fot your package manager.

![Connection info]('docs/../docs/images/view-detailed-instructions.png)

## Auth for Javascript

```bash
aws codeartifact login --tool npm --repository private-repo --domain internal-development --domain-owner xxxxxxxxxx
```

### Logins are valid for 12 hours

```
aws codeartifact login --tool npm --repository private-repo --domain internal-development --domain-owner xxxxxxxxxxxx
Successfully configured npm to use AWS CodeArtifact repository https://internal-development-xxxxxxxxxxxx.d.codeartifact.us-east-1.amazonaws.com/npm/private-repo/
Login expires in 12 hours at 2020-11-15 22:35:00-08:00
```

## Auth for Python

```bash
aws codeartifact login --tool pip --repository private-repo --domain internal-development --domain-owner xxxxxxxxxx
```

## View packages in repo

Install some packages using your package manager.
If the package is found in your internal repo it is used.
If not the package is downloaded from the public repo and stored.

![Packages in repo](docs/images/view-packages-in-console.png)