# Commit New Term to GitHub

## Step 1. Commit your changes and synchronize with GitHub.

Press the version control button in your menubar on the left (alternatively, you can choose `SCM` from the `View` menu).  

![Screenshot detail of the SCM button in the left menubar of VS Code](images/vscode-version-control.png)

Next, hover over your newly added term file:

![Screenshot detail of the file in the SCM file list in VS Code](./images/add-file-1.png)

Then, press the `+` button to add the files to your commits. Once you press the `+` button, the file should move from the `Changes` section to the `Staged Changes` section. Once all your files with your terms are in the `Staged Changes` section, you are ready to move on.  

![Screenshot detail of hovering over a file in the SCM file list in VS Code](./images/add-file-2.png)

In the `Message` box above the list, type an instructive message, something along the lines of `Adding terms: <Term 1>, <Term 2>, <Term 3>`

![Screenshot detail of what the commit message looks like in VS Code](./images/commit-message.png)

Then, press the checkmark above the message box (<kbd>✓</kbd>). Alternatively, you can press <kbd>command</kbd> <kbd>enter</kbd>.

Next, you want to synchronize your commit(s) with GitHub, by pressing the icon next to your branch name. If it's your first time, you should press the little cloud with an arrow into it.

![Screenshot detail of what the lower left corner in VS Code looks like before we have committed any changes](./images/sync-with-cloud-1.png)

Otherwise, you should press two arrows forming a circle:

![Screenshot detail of what the lower left corner in VS Code looks like if we have already committed changes before](./images/sync-with-cloud-2.png)

## Step 2. Add a pull request to the `v2.0` branch

Next, we will want to add a pull request to the `v2.0` branch, the current production branch for the DHRI Curriculum's glossary.

Navigate to GitHub's [Compare changes](https://github.com/DHRI-Curriculum/glossary/compare/v2.0...main) page.
   
Ensure that the `base` branch (the one you want to merge your changes _into_) is selected as `v2.0`:

![Screenshot detail of the comparison box in the Pull Request on GitHub](./images/compare-branches.png)

On the `compare` side, you will then want to choose your own branch in the popup menu:

![Screenshot detail of choosing a head ref on GitHub](./images/choose-head-ref.png)

You should see a large, green button that says "Create pull request" and a green checkmark that says that you're able to merge:

![Screenshot detail of what a pull request that's able to merge looks like on GitHub](./images/able-to-merge.png)

Press the "Create pull request" button, and fill out the form that pops up with some important information. _Note: If you filled out the commit above with information about all the terms you added, that should already be the title of your request and this should be an easy step._ Once you're done, press the green "Create pull request" button at the bottom of the form.  

![Screenshot detail of the form where you describe your desired Pull Request](./images/pull-request-form.png)

You're done. Once someone gets around to it, your changes might be merged into the repository.
