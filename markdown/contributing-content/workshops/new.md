# Creating a new workshop

For all the **content files**, easily accessible (and for copying and pasting) templates are available here:

- [`image.md`](file-templates/image.md)
- [`frontmatter.md`](file-templates/frontmatter.md)
- [`lessons.md`](file-templates/lessons.md)
- [`theory-to-practice.md`](file-templates/theory-to-practice.md)

!!! warning

	**NOTE**: The `README.md` file and `sections` directory are generated using a Python script and should therefore not be edited. To be clear: any content in the `README.md` file or any files in the `sections` directory will be overwritten (without any approval/prompt).

## 1. Navigate to https://github.com/new in order to create a new repository

- **Repository name** (suggestion): name it like we’ve named the other workshops, using a shorthand (i.e. not `introduction-to-javascript` but rather just `javascript`)
- **Description**: No need for description at this point. If you want to, you can fill it out along this format: `@DHRI-Curriculum Session on ______, <Extremely short explanation of the content of the workshop>.`
- **Public**: Keep the visibility as public.
- **Initialize this repository with**: (keep all off)

## 2. Keep the confirmation page open

Keep the confirmation page open. Or you can copy the section `...or push an existing repository from the command line` to keep it handy.

## 3. Open a terminal and navigate to the directory where you want to keep your workshop directory.

In my case, I want it inside my `Repositories` directory in my user folder:

```sh
$ cd ~/Repositories
```

```sh
$ mkdir javascript
```

```sh
$ cd javascript
`

## 4. Add a reference to the GitHub repository

```sh
$ git init
```

Copy the link from the confirmation page:

```sh
$ git remote add origin git@github.com:username/workshop-name.git
```

Switch to the `main` branch:

```sh
$ git branch -M main
```

## 5. Add the `localdjango` component to the workshop

`localdjango` is a little Python program that automatically generates the `README.md` and the `sections` content for each workshop, to make a nice little visible and usable fall-back option, in case the curriculum.dhinstitutes.org site is down, for instance. Or for anyone who comes across our content on GitHub.

First add the submodule:

```sh
$ git submodule add https://github.com/DHRI-Curriculum/localdjango
```

```sh
$ git submodule init
```

Just to make sure, run a submodule update command as well:

```sh
$ git submodule update
```

## 6. Add the basic setup of content files for the workshop.

I like to work in VS Code, so I fire that up by using:

```sh
$ code .
```

In the directory, add the **content files for the workshop**: `frontmatter.md`, `lessons.md`, and `theory-to-practice.md`

## 7. Add the image for the workshop.

In the directory, add the **meta files and directories for the workshop**: `image.md` and the directory `_django-meta`.

In the `image.md` file, add one line on the top of the file, containing the image and the alt-text as follows: `![Header image for the Introduction to JavaScript workshop](https://raw.githubusercontent.com/DHRI-Curriculum/javascript/v2.0/\_django-meta/header%403x.png)`

_Note that you may need to go in and adjust the link to the image after you’ve added the files to your repository, unless you can guess the githubusercontent.com URI from the pattern above._

Inside the `_django-meta` directory, add the PNG file for the header (which will populate the Curriculum site), called `header@3x.png` and of the size 610 x 1994px.

## 8. Time to add the content, starting with `frontmatter.md`

Here, we’ll start with `frontmatter.md` but you can start with any of the files (see point 9 and 10 below)

_Note that there is a template for [`frontmatter.md`](file-templates/frontmatter.md) available to make the following easier to follow._

- Add header level 1 with the name of the workshop: `# Introduction to JavaScript`
- Add header level 2: `## Abstract` and underneath it, an abstract for the workshop.
- Add header level 2: `## Learning Objectives` and underneath it a bullet point list (`- _____`) of each of the learning objectives. (No need to add any other text here, it will be added automatically under the step below where we run `localdjango`.)
- Add header level 2: `## Estimated time` with content that follows the.format “4 hours” — no need for punctuation.
- Add header level 2: `## Prerequisites` with content in bullet point form (`- _____`) that follows any of the following three examples:
	- Each of the bullet points need to contain either “required” or “recommended” as per the examples below.
	- If you want to add a workshop prerequisite:
		```md
		[Introduction to the Command Line](https://www.github.com/DHRI-Curriculum/command-line) (required) This workshop makes reference to concepts from the Command Line workshop, and having some knowledge about how to use the command line will be central for anyone who wants to learn about ___________.
		```
	- If you want to add a software installation prerequisite:
		```md
		[Visual Studio Code](https://github.com/DHRI-Curriculum/install/blob/v2.0/guides/visual-studio-code.md) (recommended) You can use any plain text editor but for our purposes, Visual Studio Code ("VS Code") will be used.
		```
	- If you want to add an external link prerequisite:
		```md
		[Create a GitHub account](https://github.com/join) (required) You need to have a GitHub account for the purposes of this workshop. It is free to sign up via this link.
		```
	- If you want to add a download from the repository as a prerequisite, you need to use an absolute URI to the githubusercontent.com domain: 
		```md
		[Download the workshop dataset](https://raw.githubusercontent.com/DHRI-Curriculum/data-literacies/v2.0/files/moSmall.csv) (required) The dataset, `moSmall.csv`, will be used throughout the challenges in the workshop. To save the file to your local computer, right click on the "Download the workshop dataset" link and choose `Save Link As...`. Note: It is important to make sure your file is saved as a `.csv` file.
		```
- Add a level 2 header: `## Contexts`
	- Under the “Contexts” header, add a level 3 header: `### Pre-reading suggestions` with any recommended preceding suggestions. All reading suggestions should be added as a bulletpoint list, with a hyperlink with a clear explanatory text as its text element. After the reference, you can also add any other explanatory text that you may want. 
	- Under the “Contexts” header, add a level 3 header: `### Projects that use these skills` with any recommended projects to look at, which use the skills detailed in the workshop. All projects should be added as a bulletpoint list, with a hyperlink with a clear explanatory text as its text element. After the reference, you can also add any other explanatory text that you may want.
	- Under the “Contexts” header, add a level 3 header: `### Ethical Considerations` with any ethical consideration to take into consideration for learners in the workshop. If you want to have a hyperlink, you can do so. Just remember that the hyperlink should have a clear explanatory text as its text element.
	- Under the “Contexts” header, add a level 3 header: `### Datasets` with any datasets that the learner may want to access for the workshop’s purposes. All datasets should be added as a bulletpoint list, with a hyperlink with a clear explanatory text as its text element. After the reference, you can also add any other explanatory text that you may want.
	- Under the “Contexts” header, add a level 3 header: `### Cheat Sheets` with any cheat sheets that the learner may want to access for the workshop’s purposes. All cheat sheets should be added as a bulletpoint list, with a hyperlink with a clear explanatory text as its text element. After the reference, you can also add any other explanatory text that you may want.
- Add a level 2 header: `## Acknowledgements` where you add, as content, each of the current and past contributors to the workshop:
	- Each should be added as a bulletpoint list. Name should be the text hyperlinked (if a hyperlink is added) and the name should be preceded by the category of contribution, whether it’s a “current” or a “past” contribution, followed by a colon. The preference of a hyperlink is to the person’s GitHub profile, but other links are also doable. Some examples:
		```md
		- Current author: [Di Yoong](https://github.com/dyoong)
		- Past contributing author: [Stephen Zweibel](https://github.com/szweibel)
		- Past reviewer: [Stefano Morello](https://github.com/smorello87)
		- Past reviewer: [Filipa Calado](https://github.com/gofilipa)
		- Current editor: [Lisa Rhody](https://github.com/lmrhody)
		- Current editor: [Kalle Westerling](https://github.com/kallewesterling)
		```

## 9. Time to add content to `lessons.md`

_Note that there is a template for [`lessons.md`](file-templates/lessons.md) available to make the following easier to follow._

- Add each of the lessons, unnumbered, as a level 1 heading, with any subsequent headers as level 2 headers.
	```md
	# Getting to know your browser
	
	What's really nice about JavaScript is that you can get started this very minute. Try it! Go to the `View` menu in the menubar and under the `Developer` submenu, choose "JavaScript Console." You should see `>` which we call a "prompt" and you may have encountered in other workshops here, like our [Python](http://www.github.com/DHRI-Curriculum/python) or [Command Line](http://www.github.com/DHRI-Curriculum/command-line) workshops.
	
	## Playing with the prompt
	
	Let's write `alert("Hello world!")` followed by pressing the `Enter` button on your keyboard.
	```
- For each lesson, add a level 2 section for `## Evaluation`, where you write multiple-choice or open-ended questions on the material in the lesson.
	- An open-ended question should just be on its own line:
		```md
		## Evaluation
		
		How does JavaScript seem different than Python? What do you think the benefits are of learning foundational skills about any given programming language?
		```
	- A multiple-choice question should be formulated on its own line, followed by a bulletpoint list of options, where the correct one(s) are marked with a star directly following the correct answer(s):
		```md
		## Evaluation
		
		Which of the following sentences is correct:
		
		- A prompt is a smiley-face.
		- The prompt helps us perform simple one-line commands.*
		- The prompt can run long program sequences.
		```
 - For each lesson, add a level 2 section for `## Keywords`
	- Start this section with a single-statement on one line: “Do you remember the glossary terms from this section?”
	- Follow this line with a bulletpoint list of all any terms from the lesson that exist in the `glossary` repository’s (branch `v2.0`) [`terms`] directory, where a full bulletpoint looks like this:
		```md
		- [Prompt](https://github.com/DHRI-Curriculum/glossary/blob/v2.0/terms/prompt.md)
		```
- If your lesson has a challenge, add it as a level 2 section: `## Challenge`  If you want to use a subheader, you can do by adding a colon after “Challenge”: `## Challenge: A real challenge for a superuser`
	- In the following paragraph(s), you can use level 3 headers, if you need to, and any styled markdown.
	- If your challenge has a solution, it should follow the same pattern as the challenge above. A level 2-header, that may or may not have a subheader: `## Solution` or `## Solution: We have solved it for you`
	- The solution’s following paragraph(s), cal also use level 3 headers, if you need to, and any styled markdown.

## 10. Time to add content to `theory-to-practice.md`

_Note that there is a template for [`theory-to-practice.md`](file-templates/theory-to-practice.md) available to make the following easier to follow._

- Start with a level 1 heading, `# Theory to Practice` with the following paragraph(s) being a congratulatory message to the learner who has now completed the workshop. It could summarize a bit what the journey has been like, why the skill matters in the world, and where the technology is at right now.
- Add a level 2 header, `## Suggested Further Readings`, with any recommended further readings to look at, which describe the skills detailed in the workshop. All readings should be added as a bulletpoint list, with a hyperlink with a clear explanatory text as its text element. After the reference, you can also add any other explanatory text that you may want.
- Add a level 2 header, `## Other Tutorials`, with any recommended other tutorials the learner may want to look at, which helps them understand the skills detailed in the workshop. All tutorials should be added as a bulletpoint list, with a hyperlink with a clear explanatory text as its text element. After the reference, you can also add any other explanatory text that you may want.
- Add a level 2 header, `## Projects or Challenges to Try`, with any recommended projects or challenges to look at, which use the skills detailed in the workshop. All projects/challenges should be added as a bulletpoint list, with a hyperlink with a clear explanatory text as its text element. After the reference, you can also add any other explanatory text that you may want.
- Add a level 2 header, `Discussion Questions`, which provides some open-ended advanced-level question about how the learner’s research projects might benefit from the skill, what its limits are, pitfalls with using this versus other skills, how they could use it in teaching, etc.

## 11. Run `localdjango`

As it should be initialized in step 5 above, now, after our content is in place (step 7–10), we can follow these steps:

```sh
$ python localdjango/setup.py
```

It will ask you some questions, but for the most part, the answers are automatically generated from your content. Once the script finishes, you should have a `README.md` file and a `sections` directory in the repository.

## 12. Synchronize with git

Now we're ready to synchronize the repository with git.

You can use VS Code and do it using the application's GitHub extension

...or run the commands on the command line:

- `git add *`
- `git commit -m 'Updating from local files.'`
- `git push`
