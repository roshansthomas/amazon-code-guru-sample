# Amazon CodeGuru Reviewer

This lab is provided as part of **[AWS Innovate AI/ML Edition](https://aws.amazon.com/events/aws-innovate/machine-learning/)**, click [here](https://github.com/roshansthomas/aws-innovate-ai-ml-2022) to explore the full list of hands-on labs.

ℹ️ You will run this lab in your own AWS account. Please follow directions at the end of the lab to remove resources to avoid future costs.

## **Overview**
This application is intended as a test case for Amazon CodeGuru Reviewer, a service that uses program analysis and machine learning to detect potential defects in code. The implementation of this example is intentionally suboptimal to demonstrate the ability of CodeGuru Reviewer to provide recommendations. You should not use this example code in production. 

Note: For testing recommendations from different languages please switch to the relevant branch (Example: python).

To get started with CodeGuru Reviewer, follow these steps.
## Try CodeGuru Reviewer

### Step 1: Fork this repo

Log in to GitHub and choose **Fork** to fork this example app to your GitHub account.

![Image of Fork button](images/fork.png)

### Step 2: Associate the forked repo

1. Log in to the [CodeGuru dashboard](https://console.aws.amazon.com/codeguru/home?region=us-east-1).
1. Choose **Repositories** -> **Associate repository and run analysis** from the left navigation pane.
1. Make sure **GitHub** is selected, and then choose **Connect to GitHub or GitHub Enterprise Cloud**.
1. To allow CodeGuru Reviewer to access your account, choose **Authorize aws-codesuite**. If prompted, confirm your GitHub password.
1. Select the **amazon-code-guru-sample** repository, **master** as **Source branch** and then choose **Associate repository and run analysis**.

![Image of Associate view](images/associate.png)

CodeGuru Reviewer is now associated with the repo and listening for pull requests. CodeGuru will run a full analysis on the code base and provide recommendations.

![Full Analysis](images/fullanalysis.png)

![Full Recommendations](images/full-recommendations.png)

### Step 3: Push a change to the code

Clone the forked repo, replacing **USER_ID** in the URL with your actual user ID.

    git clone https://github.com/USER_ID/amazon-codeguru-reviewer-sample-app.git

You can get the URL by choosing **Code**.

![Image of Clone button](images/clone.png)

**Note:** If you access your GitHub repositories using SSH, use the SSH URL instead of the HTTPS URL shown here.

Check out a new branch.

    cd amazon-code-guru-sample
    git checkout -b dev
    
Copy the Java class at **src/main/java/com/shipmentEvents/handlers/EventHandler.java** into **src/main/java/com/shipmentEvents/demo**.

    mkdir src/main/java/com/shipmentEvents/demo/
    cp src/main/java/com/shipmentEvents/handlers/EventHandler.java src/main/java/com/shipmentEvents/demo/

GitHub and CodeGuru Reviewer will treat this as a new file. 

Push your changes.

    git add --all
    git commit -m 'new demo file'
    git push --set-upstream origin dev
    
### Step 4: Create a pull request

1. In your forked GitHub repo, choose **New pull request**.
![Image of New Pull Request](images/newpullrequest.png)
1. On the left side of the comparison (**base**), select **USER_ID/amazon-code-guru-sample**, where `USER_ID` is your GitHub user ID. Leave the branch at **master**.
1. On the right side of the comparison (**compare**), change the branch to **dev**. The branches should be showing as **Able to merge**. ![Image of compare view](images/compare.png)
1. Choose **Create pull request** and, again, **Create pull request**.

### Step 5: Review recommendations

After a few minutes, CodeGuru Reviewer will issue recommendations on the same GitHub page where the pull request was created. You can check the status of the code review in the [Code reviews](https://console.aws.amazon.com/codeguru/reviewer/?region=us-east-1#/codereviews) under **Incremental code reviews** tab of the CodeGuru Reviewer console. It can take a few minutes to complete the review.

![Image of pending status](images/pending.png)

When the code review is complete and the recommendations appear in GitHub, you can provide feedback on the recommendations using the thumbs up or thumbs down icon. Any positive or negative feedback can be used to help improve the performance of CodeGuru Reviewer so that recommendations get better over time. 

![Image of thumbs up/down icons](images/thumbs_icons.png)

### Step 6: Clean up

After you're finished with this demo, clean up your resources.

1. In your GitHub fork of **amazon-code-guru-sample**, go to **Settings**, and then choose **Delete this repository**. Follow the instructions to delete the forked repository.
1. Delete your clone of the forked repository, for example, `rm -rf amazon-code-guru-sample`.
1. In the CodeGuru Reviewer console, select the example repository, choose **Actions**, and then choose **Disassociate repository**.

![Image of disassociate option](images/disassociate.png)

## Learn more

For more information about how to use CodeGuru Reviewer, see the [Amazon CodeGuru Reviewer User Guide](https://docs.aws.amazon.com/codeguru/latest/reviewer-ug/index.html).

## License

This library is licensed under the MIT-0 License. See the LICENSE file.

