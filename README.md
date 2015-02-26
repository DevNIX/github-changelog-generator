
[![Gem Version](https://badge.fury.io/rb/github_changelog_generator.svg)](http://badge.fury.io/rb/github_changelog_generator)
[![Build Status](https://travis-ci.org/skywinder/Github-Changelog-Generator.svg?branch=master)](https://travis-ci.org/skywinder/Github-Changelog-Generator)

GitHub Changelog Generator
==================

  - [Installation](#installation)
  - [Output example](#output-example)
  - [Usage](#usage)
    - [Params](#params)
    - [GitHub token](#github-token)
  - [Features and advantages of this project](#features-and-advantages-of-this-project)
    - [Alternatives](#alternatives)
    - [Projects using this library](#projects-using-this-library)
  - [Am I missed some essential feature?](#am-i-missed-some-essential-feature)
  - [Contributing](#contributing)
  - [License](#license)

 
Changelog generation has never been so easy.

**Fully automate changelog generation** - This gem generate change log file based on tags, issues and merged pull requests from **Github issue tracker**. This generator complies all [change log format guidelines](http://keepachangelog.com/).

## Installation

	[sudo] gem install github_changelog_generator

## Output example

- Look at **[CHANGELOG.md](https://github.com/skywinder/Github-Changelog-Generator/blob/master/CHANGELOG.md)** for this project
- [ActionSheetPicker-3.0/CHANGELOG.md](https://github.com/skywinder/ActionSheetPicker-3.0/blob/master/CHANGELOG.md)  was generated by command:

		github_changelog_generator -u skywinder -p ActionSheetPicker-3.0

- In general it looks like this:

> ## [1.3.10](https://github.com/skywinder/ActionSheetPicker-3.0/tree/1.3.10)
> #### 09/01/15
> - *Merged pull-request:* add header file to public [\#115](https://github.com/skywinder/ActionSheetPicker-3.0/pull/115)
> ([skywinder](https://github.com/skywinder))
> 
> - *Merged pull-request:* Fix bad interaction with Git submodules.
> [\#112](https://github.com/skywinder/ActionSheetPicker-3.0/pull/112)
> ([JimDabell](https://github.com/JimDabell))
> 
> - *Implemented enhancement:* Should have minimum/maximum date property exposed
> [\#97](https://github.com/skywinder/ActionSheetPicker-3.0/issues/97)
> 
> ## [1.3.9](https://github.com/skywinder/ActionSheetPicker-3.0/tree/1.3.9)
> #### 11/12/14
> - *Closed issue:* Bad interaction with submodules [\#111](https://github.com/skywinder/ActionSheetPicker-3.0/issues/111)
> 
> - *Closed issue:* No "cancel" button [\#122](https://github.com/skywinder/ActionSheetPicker-3.0/issues/122)


## Usage
**It's really simple**: 

- If your **git remote** `origin` refer to your GitHub repo, then just go to your project folder and run:

		github_changelog_generator

-  or from anywhere:

		github_changelog_generator -u github_username -p github_project
     
As output you will get `CHANGELOG.md` file with pretty *Markdown-formatted* changelog.

### Params
Type `github_changelog_generator --help` for detailed usage.

    Usage: changelog_generator [options]
    -u, --user [USER]                Username of the owner of target GitHub repo
    -p, --project [PROJECT]          Name of project on GitHub
    -t, --token [TOKEN]              To make more than 50 requests per hour your GitHub token required. You can generate it here: https://github.com/settings/tokens/new
    -f, --date-format [FORMAT]       Date format. Default is %d/%m/%y
    -o, --output [NAME]              Output file. Default is CHANGELOG.md
        --[no-]verbose               Run verbosely. Default is true
        --[no-]issues                Include closed issues to changelog. Default is true
        --[no-]issues-wo-labels      Include closed issues without labels to changelog. Default is true
        --[no-]pr-wo-labels          Include pull requests without labels to changelog. Default is true
        --[no-]pull-requests         Include pull-requests to changelog. Default is true
        --[no-]filter-by-milestone   Use milestone to detect when issue was resolved. Default is true
        --[no-]author                Add author of pull-request in the end. Default is true
        --unreleased-only            Generate log from unreleased closed issues only.
        --[no-]unreleased            Add to log unreleased closed issues. Default is true
        --[no-]compare-link          Include compare link between older version and newer version. Default is true
        --include-labels  x,y,z      Issues only with that labels will be included to changelog. Default is 'bug,enhancement'
        --exclude-labels  x,y,z      Issues with that labels will be always excluded from changelog. Default is 'duplicate,question,invalid,wontfix'
        --github-site [URL]          The Enterprise Github site on which your project is hosted.
        --github-api [URL]           The enterprise endpoint to use for your Github API.
    -v, --version                    Print version number
    -h, --help                       Displays Help


### GitHub token

Since GitHub allow to make only 50 requests without authentication it's recommended to run this script with token

**You can easily [generate it here](https://github.com/settings/applications)**.

And:

- Run with key `-t [your-16-digit-token]` 
- Or set environment variable `CHANGELOG_GITHUB_TOKEN` and specify there your token. 
 		
	i.e. add to your `~/.bash_profile` or `~/.zshrc` or any other place to load ENV variables string :

        export CHANGELOG_GITHUB_TOKEN="your-40-digit-github-token"

So, if you got error like this:
>! /Library/Ruby/Gems/2.0.0/gems/github_api-0.12.2/lib/github_api/response/raise_error.rb:14:in `on_complete'

It's time to create this token or wait for 1 hour before GitHub reset the counter for your IP.

##Features and advantages of this project
- Generate canonical change log file, followed by [keepachangelog.com guidlines](http://keepachangelog.com/)
- Simply add links for all closed issues and merged pull requests
- Possible to generate **Unreleased** changes (closed issues that have not released yet)
- Flexible format customisation:
    - Customize issues, that should be added to changelog
    - Custom date format supported 
    - Ability to manually specify in which version issue was fixed (in case, when closed date is not match) by setting `milestone` of issue the same name as tag of  required version
    - Ability to exclude specific issues from change log (by labels)
        - Automatically exclude "questions" - issues marked as `question` labels (and other issues, that shouldn't be in change log file: with `duplicate invalid wontfix` labels)
- Distinguish bug fixes, enchantments, and closed issues according labels.
    - 	**Issues** (closed issues w/o any labels)
    - **Merged pull-requests** (all merged pull-requests)
    - **Bug-fixes** (by label `bug` in issue)
    - **Enhancements** (by label `enhancement` in issue)

###Alternatives
Here is a [wikipage list of alternatives](https://github.com/skywinder/Github-Changelog-Generator/wiki/Alternatives), that I found. But no one was satisfy my requirements.

*If you know other projects - feel free to edit this Wiki page!*


### Projects using this library
[Wikipage with list of projects](https://github.com/skywinder/Github-Changelog-Generator/wiki/Projects-using-Github-Changelog-Generator) 

*If you are using `github_changelog_generator` for generation change log in your project or know of project that uses it, please add it to [this] (https://github.com/skywinder/Github-Changelog-Generator/wiki/Projects-using-Github-Changelog-Generator) list.*

## Am I missed some essential feature?

**Nothing is impossible!** 

Open an [issue](https://github.com/skywinder/Github-Changelog-Generator/issues/new) and let's make generator better together!

*Bug reports, feature requests, patches, well-wishes are always welcome!*

## Contributing

1. Create an issue to discuss about your idea
2. [Fork it] (https://github.com/skywinder/Github-Changelog-Generator/fork)
3. Create your feature branch (`git checkout -b my-new-feature`)
4. Commit your changes (`git commit -am 'Add some feature'`)
5. Push to the branch (`git push origin my-new-feature`)
6. Create a new Pull Request

## License

Github Changelog Generator is released under the [MIT License](http://www.opensource.org/licenses/MIT).
