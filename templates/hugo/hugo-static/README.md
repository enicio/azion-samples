# Hugo Static

This template provides a quickstart to deploy a [Hugo](https://gohugo.io) static website to the Azion edge platform.

##  Deploy Your Own

Deploy your own Hugo project with Azion.

[![Deploy Button](/static/button.png)](https://console.azion.com/create/hugo/hugo-boilerplate "Deploy with Azion")

## Settings

To successfully deploy this template, you must provide the information to configure your Azion application. Fields identified with an asterisk are mandatory.

  * **Application Name***: the name of your edge application on Azion.
  * **GitHub Personal Token***: your GitHub personal token.
    * While generating your GitHub personal token, grant that your scope has the permissions to authorize an OAuth app or a personal token to access to public and private repositories, including read and write access to code. You must also enable the workflow option to allow adding and updating GitHub Actions workflow files.

Note that permissions can be scoped either to a user or an organization or to a repository. Read the [Creating a personal access token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#creating-a-personal-access-token-classic) documentation for more information.

After filling out the form, click the **Next** button to start the deployment process.

Once the template is deployed, you can edit and update your args and code. However, you'll need to declare secrets on your project's GitHub repository first to complete the second build with these changes. When the second build is completed, you can manage your project with a [continuous deployment workflow](#continuous-deployment).

For a more detailed step-by-step on declaring your secrets and using this template, check the [How to deploy edge applications with the Next.js Static Boilerplate](https://www.azion.com/en/documentation/products/guides/nextjs-static-boilerplate/) guide for more details.

## Important

To guarantee the optimal performance of this template, it's necessary to activate the following Azion product:

* [Edge Functions](https://www.azion.com/en/documentation/products/edge-application/edge-functions/#edge-functions-management)

You need to activate the product separately via RTM. Review the [Azion documentation](https://www.azion.com/en/documentation/products/guides/nextjs-static-boilerplate/) to do so.

If this product is activated, the execution of this template could generate usage-related costs. Check the [pricing page](https://www.azion.com/en/pricing/) for more information. 

## Continuous deployment

Once the template is deployed, you can edit it and update it, as well as implement a continuous deployment workflow. However, you'll need first to *declare secrets on your project's GitHub repository* to complete the second build with the changes. When the second build is completed, you'll be able to manage your project with a continuous deployment workflow and edit the args as desired.

To do so, open your repository in GitHub. Then, go to **Settings** > **Secrets and variables** > **Action** to [add your variables](https://docs.github.com/en/actions/security-guides/encrypted-secrets), following these instructions:

1. Add the Azion personal token to the *secrets*:
- Read [how to generate an Azion personal token](https://www.azion.com/en/documentation/products/accounts/personal-tokens/) in the documentation.

```bash
    AZION_PERSONAL_TOKEN=<value>
```

2. Add the environments for use in the action workflow in the **main.yml** file, included in the **.github/workflows** folder of your repository:

```yml
  - name: edge-...
    id: azion_edge
    ...
    with:
        ....
        azionPersonalToken: ${{ secrets.AZION_PERSONAL_TOKEN }}
        ....

```

3. Open a pull request to merge the changes to the main branch and start the automatic deployment.

Now your project is ready to work with a continuous deployment workflow, updating instantly any changes in the application or the repository. 
