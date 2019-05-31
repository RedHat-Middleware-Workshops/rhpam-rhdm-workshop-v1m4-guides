# Business central

In this lab we will create _DataSources_ and _DataSets_ in the Business Central workbench that will provide the data for our business reports. To get started, we need to access the Business Central environment:

1. Open the [OpenShift Console]({{ OPENSHIFT_CONSOLE_URL }}) in a web-browser. You've been assigned a username and password by your lab instructor. Use these credentials to login to the console.

2. In your OpenShift Console, you will see a project called "RHPAM - User {x}". Click on this project to open it.

3. In this project you will see an application called `rhpam7-rhpamcentr`. Click on the box of this application to expand it. On the lower right-hand-side of this box you will see a section called `Routes - External Traffic`. Click on either the
`http` or `https` route to access the RHPAM Business Central Workbench.

    ![OpenShift Business Central Route]({% image_path openshift-business-central-route.png %}){:width="600px"}

4. Login to Business Central with the credentials u:`pamAdmin`, p:`redhatpam1!`

    ![Business Central Console]({% image_path business-central-console.png %}){:width="600px"}
