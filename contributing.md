## Contributing

[pr]: https://github.com/raise-dev/hacktoberfest/compare
[style]: https://github.com/bbatsov/ruby-style-guide

Hi there! We're thrilled that you'd like to contribute to Hacktoberfest. Your help is essential for keeping it great.


## Opening an issue

Thank you for taking the time to open an issue, your feedback helps make Hacktoberfest better.
Before opening an issue, please be sure that your issue hasn't already been asked by using [GitHub search](https://help.github.com/articles/searching-issues/)

Here are a few things that will help us help resolve your issues:

- A descriptive title that gives an idea of what your issue refers to
- A thorough description of the issue, (one word descriptions are very hard to understand)
- Screenshots (if appropriate)
- Links (if appropriate)

## Submitting a pull request

* Clone the repository using :
    ```bash
    git clone --recursive git@github.com:atom-robotics-lab/atom-robotics-lab.github.io.git
    ```
    We need to use the `--recursive` tag since it uses submodules for the themes.
* Our website uses an open-source framework called Hugo. Use this [link](https://gohugo.io/getting-started/quick-start/) to install and use Hugo

* Install git-lfs with  :
  ```bash
     sudo apt-get install git-lfs
  ```

* Refer to the section below if your task requires you to make changes to the theme of the website.

* Fork the repo and Create a new branch: 
   ```bash
    git checkout -b my-branch-name
    ```
* Make changes, commit and Push to your branch. [Submit a Pull Request][pr]
* Wait for your pull request to be reviewed and merged!


## How to make changes to the theme
Follow these guidelines if your tasks requires you to make changes to the theme of the website :

* The theme resides in hugo as submodule in the `themes` directory. If you make changes to the theme and push to this repo they won't be reflected ont the wenbite even though they work locally! Treat the submodule as a separate git repository with a different [remote](https://github.com/atom-robotics-lab/roxo-hugo).
* After making changes to the theme, you need to push your changes to its remote the same way you would do for any other remote.


## Resources

- [Contributing to Open Source on GitHub](https://guides.github.com/activities/contributing-to-open-source/)
- [Using Pull Requests](https://help.github.com/articles/using-pull-requests/)
- [GitHub Help](https://help.github.com)
