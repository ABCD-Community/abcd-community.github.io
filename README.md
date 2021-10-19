# ABCD Documentation Theme


## About this repo

To access this site, click on the link: [https://abcd-community.github.io](https://abcd-community.github.io)

This repository was created to unify all documentation related to the ABCD and to provide a template for multilingual documentation development.

This template can be downloaded and adapted to any kind of documentation.

The basis for this documentation is the book "The abc of ABCD" written by Egbert de Smet, but the examples can be expanded or modified according to each language or need.

The official documentation is produced in English and translations to other languages are required.

To know how to collaborate with the documentation, access [this link](http://localhost:9898/pt/collab/)



## About this Theme
About this topicThis theme is a replica of the theme [Docsy](https://www.docsy.dev/) for [Hugo](https://gohugo.io/), adapted for [Jekyll](https://jekyllrb.com/).

Its starting point was the repository[https://github.com/vsoch/docsy-jekyll](https://github.com/vsoch/docsy-jekyll)

It was made multilingual by @rogercgui.

Also the "homepage" and "about" templates were created to be more similar to the original Docsy.


## Usage

### 1. Get the code

You can clone the repository right to where you want to host the docs:

```bash
git clone https://github.com/ABCD-Community/ABCD-Community.github.io.git ABCD-Community.github.io
cd ABCD-Community.github.io
bundle exec jekyll serve
```
Open URL:
[http://localhost:4000](http://localhost:4000)


If port 4000 is blocked use:


```bash
bundle exec jekyll serve --port 9898
```


### 2. Customize

To edit configuration values, customize the [_config.yml](https://github.com/ABCD-Community/ABCD-Community.github.io/blob/main/_config.yml).
Duplicate the EN folder [en](https://github.com/ABCD-Community/ABCD-Community.github.io/tree/main/en). 
Set the language abbreviation in the header of all .md files
and edit the menu, following the structure that is [_data/toc.myl](https://github.com/ABCD-Community/ABCD-Community.github.io/blob/main/_data/toc.yml).
The top navigation is controlled by [_data/navigation.yml](https://github.com/ABCD-Community/ABCD-Community.github.io/blob/main/_data/navigation.yml)

### 3. Options

Most of the configuration values in the [_config.yml](https://github.com/vsoch/docsy-jekyll/blob/master/_config.yml) are self explanatory,
and for more details, see the [getting started page](https://abcd-community.github.io/en/getting-started)
rendered on the site.

### 4. Serve

Depending on how you installed jekyll:

```bash
jekyll serve
# or
bundle exec jekyll serve
```

or

```bash
bundle exec jekyll serve --port 9898
```


**NOTE:** If the above serve command throws an error saying `require': cannot load such file -- webrick (LoadError)` try to run `bundle add webrick` to automatically add the webrick gem to your Gemfile, or manually add `gem "webrick"` line to the Gemfile and then run the serve command again.


You can then open your browser to [http://localhost:4000](http://localhost:4000)
to see the server running.

> Node : changes `baseurl: ""` in _config.yml  when you are running in local and prod according to the requirement.
