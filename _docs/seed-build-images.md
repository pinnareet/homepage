---
layout: docs
title: Seed Build Images
---

Seed runs your builds inside a virtual machine and it'll use a build image based on the Lambda runtime of your service. Below is a list of all the images in use:

[**Active Images**](#build-images)
- [General Purpose v3.0](#general-purpose-v30)
- [General Purpose v1.1](#general-purpose-v11)
- [Python 3.6](#python-36)
- [Python 2.7](#python-27)
- [Ruby 2.5](#ruby-25)

[**Deprecated Images**](#deprecated-build-images)
- [General Purpose v2.0](#general-purpose-v20)
- [General Purpose v1.0](#general-purpose-v10)
- [Python 3.7](#python-37)
- [.NET Core 2.1](#net-core-21)

## Changing the Build Image

By default, Seed will automatically select a build image for your service based on the runtime you have set in your `serverless.yml`. However, Seed will not automatically update this when your runtime is updated. This is done to ensure that any scripts in your [build spec]({% link _docs/adding-a-build-spec.md %}) are not affected by the build image change.

If you want to update the build image that a service in your app is using, head over to the service's settings.

![Build image option in service settings](/assets/docs/seed-build-images/build-image-option-in-service-settings.png)

Note that, if a service has not been deployed yet, Seed will not have picked a build image.

You can also check which image was used for a specific build, by heading over to the logs for that build.

![Build image info in build logs](/assets/docs/seed-build-images/build-image-info-in-build-logs.png)

## Package Versions

Seed regularly applies security updates to the build images. This means that the minor versions of the packages in a build image can change.

### Node Versions

However for Node.js, the build images also comes with — [n](https://github.com/tj/n). It allows you to select a specific Node.js version if necessary. For example, to select Node.js v10.21.0 you can run this:

``` bash
$ n 10.21.0
```

And to use it in your Seed builds, update your [build spec]({% link _docs/adding-a-build-spec.md %}) (`seed.yml`) with something like this:

``` yml
before_compile:
  - n 10.21.0
```

## Build Images

Below are the build images that are used and the types of services they are used for. A build image is chosen based on the Lambda runtime of the service.

### General Purpose v3.0

Lambda runtimes: Node.js 12.x, Python 3.8, Go 1.x, Ruby 2.7, Java 11, .NET Core 3.1

OS: Ubuntu 18.04

| Includes        | Version |
|-----------------|:-------:|
| Node.js         | 12      |
| Python          | 3.8     |
| Ruby            | 2.7     |
| Go              | 1.14    |
| .NET Core       | 3.1     |
| Java            | 11      |
| PHP             | 7.4     |
| NPM             | 6.14    |
| YARN            | 1.22    |
| PIP             | 19.3    |
| Docker*         | 19.03   |
| Docker Compose* | 1.24    |

*[Docker and Docker Compose need to be enabled.]({% link _docs/docker-commands-in-your-builds.md %})

### General Purpose v1.1

Lambda runtimes: Node.js 10.x, Python 3.7, Java 8

OS: Ubuntu 18.04

| Includes        | Version |
|-----------------|:-------:|
| Node.js         | 10      |
| Python          | 3.7     |
| Ruby            | 2.6     |
| Go              | 1.13    |
| .NET Core       | 3.1     |
| Java            | 11      |
| PHP             | 7.3     |
| NPM             | 6.14    |
| YARN            | 1.22    |
| PIP             | 19.3    |
| Docker*         | 19.03   |
| Docker Compose* | 1.24    |

*[Docker and Docker Compose need to be enabled.]({% link _docs/docker-commands-in-your-builds.md %})

### Python 3.6

Lambda runtime: Python 3.6

OS: Debian 9

| Includes        | Version |
|-----------------|:-------:|
| Node.js         | 8.15    |
| Python          | 3.6     |
| NPM             | 6.1.0   |
| YARN            | 1.12.3  |
| PIP             | 9.0.1   |

### Python 2.7

Lambda runtime: Python 2.7

OS: Debian 9

| Includes        | Version |
|-----------------|:-------:|
| Node.js         | 8.15    |
| Python          | 2.7     |
| NPM             | 6.1.0   |
| YARN            | 1.12.3  |
| PIP             | 9.0.1   |

### Ruby 2.5

Lambda runtime: Ruby 2.5

OS: Debian 9

| Includes        | Version |
|-----------------|:-------:|
| Node.js         | 8.10    |
| Ruby            | 2.5     |
| NPM             | 6.1.0   |
| YARN            | 1.12.3  |

---

## Deprecated Build Images

The following build images are no longer available for new services but might still be in use for existing services. If your services are still using the ones below, [contact us](mailto:{{ site.email }}) to have them upgraded.

### General Purpose v2.0

Upgrade to: [General Purpose v3.0](#general-purpose-v30)

OS: Ubuntu 18.04

| Includes        | Version |
|-----------------|:-------:|
| Node.js         | 12      |
| Python          | 3.8     |
| Ruby            | 2.6     |
| Go              | 1.13    |
| .NET Core       | 3.0     |
| Java            | 11      |
| PHP             | 7.3     |
| NPM             | 6.13.4  |
| YARN            | 1.12.3  |
| PIP             | 19.3.1  |
| Docker*         | 19.03   |
| Docker Compose* | 1.24    |

*[Docker and Docker Compose need to be enabled.]({% link _docs/docker-commands-in-your-builds.md %})

### General Purpose v1.0

Upgrade to: [General Purpose v1.1](#general-purpose-v11)

OS: Ubuntu 18.04

| Includes        | Version |
|-----------------|:-------:|
| Node.js         | 10      |
| Python          | 3.7     |
| Ruby            | 2.6     |
| Go              | 1.13    |
| .NET Core       | 2.2     |
| Java            | 11      |
| PHP             | 7.3     |
| NPM             | 6.13.4  |
| YARN            | 1.12.3  |
| PIP             | 19.3.1  |
| Docker*         | 18.09   |
| Docker Compose* | 1.24    |

*[Docker and Docker Compose need to be enabled.]({% link _docs/docker-commands-in-your-builds.md %})

### Python 3.7

Upgrade to: [General Purpose v1.0](#general-purpose-v10)

Lambda runtime: Python 3.7

OS: Debian 9

| Includes        | Version |
|-----------------|:-------:|
| Node.js         | 8.15    |
| Python          | 3.7     |
| NPM             | 6.1.0   |
| YARN            | 1.12.3  |
| PIP             | 18.1    |

### .NET Core 2.1

Upgrade to: [General Purpose v1.0](#general-purpose-v10)

Lambda runtime: .NET Core 2.1

OS: Debian 9

| Includes  | Version |
|-----------|:-------:|
| Node.js   | 8.10    |
| .NET Core | 2.1     |
| NPM       | 6.1.0   |
| YARN      | 1.12.3  |
