---
layout: docs
title: Configuring Deploy Phases
---

Seed supports [monorepo Serverless Framework apps]({% link _docs/mono-repo-apps-in-seed.md %}). By default, all the services in a monorepo app are deployed concurrently. This means that a new git commit triggers a deployment to all the services in the monorepo app at the same time.

However, there are cases where some services in your monorepo app are dependent on the others. This can happen when you have an _infrastructure_ specific service (that creates your DynamoDB tables) that need to be deployed before your APIs. To do this, Seed gives you a very convenient way to configure your deployment workflow into phases.

### Deploy Phases

Seed has a concept of deployment phases. By default, all your services are deployed concurrently in a single phase. However, you can configure these by hitting **Manage Deploy Phases** from the **Pipeline** tab.

![Click Manage Deploy Phases Button](/assets/docs/configuring-deploy-phases/click-manage-deploy-phases-button.png)

Here you'll be able to manage the deploy phases for your app.

### Add a Deploy Phase

To add a phase, simply hit the **Add a Phase** button

![Click Add a Phases Button](/assets/docs/configuring-deploy-phases/click-add-a-phase-button.png)

And select the service you want deployed in this phase.

![Pick a Service](/assets/docs/configuring-deploy-phases/pick-a-service.png)

And hit **Update Phases**.

Also, if you wanted to add the service back to Phase 1, you can just select it from the dropdown in Phase 1. 

Finally, if you want to run integration tests or a script after all your deploy phases complete; you can [add a post-deploy phase]({% link _docs/adding-a-post-deploy-phase.md %}).

### Deployment Workflow

With these changes, any new deployment will use the phases configured above as a part of the workflow.

![Deployment workflow](/assets/docs/configuring-deploy-phases/deployment-workflow.png)

This means that the service in the second phase will wait for the ones in the first ones to complete.

And that's it. With Deploy Phases you can now manage the dependencies in your services to make sure that they are always deployed in order.
