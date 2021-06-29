# Keeping up-to-date: Building GitHub backup content

!!! note "When you should follow these instructions"
    The instructions below should be followed _after_ you have made edits to any of the curriculum website's linked repositories.

`localdjango` is a little Python program that automatically generates the `README.md` and the `sections` content for each workshop, to make a nice little visible and usable fall-back option, in case the curriculum.dhinstitutes.org site is down, for instance. Or for anyone who comes across our content on GitHub.

Using the instructions below, you will make sure that the `README.md` file and the `sections` directory are all synchronized with the content for each workshop (which lives in `frontmatter.md`, `lessons.md`, `theory-to-practice.md`, and `image.md` — that's where you make all your edits).

## 1. Navigate to the workshop's local directory

In this example, we will use the `DHRI-Curriculum/python` repository. You can replace this with any other workshop.

```sh
$ cd /path/to/python/
```

## 2. Initiate and check out `localdjango`

If the `localdjango` directory is empty, we need to initiate and check out the so-called "submodule." We can do so by putting both commands on one line for convenience:

```sh
$ git submodule init && git submodule update
```

You should receive a message back from the command prompt that says:

```sh
Submodule path 'localdjango': checked out '0bfdef48ea968121f08122666611b2c4f43b6b81'
```

!!! info
    Note that step 2 might not be necessary if the submodule is already initiated and up to date. It won't hurt to run the commands above, but you will not receive a message back.

## 3. Run `localdjango`

Since your content is in place and up to date (following [step 7–10 of the Creating a new workshop instructions](../contributing-content/workshops/new.md#7-add-the-image-for-the-workshop)), we can run the following command from the repository's root:

```sh
$ python localdjango/setup.py
```

It will ask you some questions, but for the most part, the answers are automatically generated from your content. Once the script finishes, you should have an updated `README.md` file and a `sections` directory in the repository.

## 4. Synchronize with `git`

Since the point is for us to have an up-to-date version of the repository's content live on GitHub, we need to remember to synchronize the repository with `git`.

You can use VS Code's GitHub extension... or run the commands on the command line:

1. `git add *` (for convenience)
2. `git commit -m 'Updating from local files.'`
3. `git push`

For convenience, you can copy and paste these three commands on one line:

```sh
$ git add * && git commit -m 'Updating from local files.' && git push
```
