{
	"Title": "Hugo: A fast and flexible static site generator built in GoLang",
	"Description": "",
	"Keywords": [
		"Development",
		"golang",
		"Blogging",
        "profiling"
	],
	"Tags": [
		"Development",
		"golang",
		"Blogging"
	],
	"Pubdate": "2013-07-04",
	"Topics": [
		"Development",
		"Blogging",
		"GoLang"
	],
	"Slug": "hugo",
    "project_url": "http://github.com/spf13/hugo"
    "project_name": "Hugo"
    "project_description": "A fast and flexible static site generator written in go"
    "official_url": "http://hugo.spf13.com"
    "download_url": "http://github.com/spf13/hugo/releases"
    "version": "0.9"
    "release_date": "2013-11-15"
}

{{% img src="/media/hugo.png" class="hid" caption="Hugo Website" %}}

Hugo is a static site generator written in GoLang. It is optimized for 
speed, easy use and configurability. Hugo takes a directory with content and
templates and renders them into a full html website.

Hugo makes use of markdown files with front matter for meta data.  
Written in GoLang for speed, Hugo is significantly faster than most
other static site generators.

A typical website of moderate size can be
rendered in a fraction of a second. A good rule of thumb is that Hugo
takes around 1 millisecond for each piece of content.
It's so fast that it will render the site in 
less time than it takes to switch to your browser and reload.

Hugo is made to be very flexible. Define your own content types. Define
your own indexes. Build your own templates, shortcodes and more.
It is written to work well with any
kind of website including blogs, tumbles and docs.

**[Hugo has his own site](http://hugo.spf13.com).**

## Installing Hugo

Hugo is written in GoLang with support for Windows, Linux, FreeBSD and OSX.

The latest release can be found at [hugo releases](https://github.com/spf13/hugo/releases).
We currently build for Windows, Linux, FreeBSD and OS X for x64
and 386 architectures.

Installation is very easy. Simply download the appropriate version for your
platform from [hugo releases](https://github.com/spf13/hugo/releases).
Once downloaded it can be run from anywhere. You don't need to install
it into a global location. This works well for shared hosts and other systems
where you don't have a privileged account.

Ideally you should install it somewhere in your path for easy use. `/usr/local/bin` 
is the most probable location.

*The Hugo executible has no external dependencies.*

## Installing from source

### Dependencies

* Git
* Go 1.1+
* Mercurial
* Bazaar

### Clone locally (for contributors):

    git clone https://github.com/spf13/hugo
    cd hugo
    go get

Because go expects all of your libraries to be found in either $GOROOT or $GOPATH,
it's helpful to symlink the project to one of the following paths:

 * ln -s /path/to/your/hugo $GOPATH/src/github.com/spf13/hugo
 * ln -s /path/to/your/hugo $GOROOT/src/pkg/github.com/spf13/hugo

### Get directly from Github:

If you only want to build from source, it's even easier.

    go get github.com/spf13/hugo

### Building Hugo

    cd /path/to/hugo
    go build -o hugo main.go
    mv hugo /usr/local/bin/

### Running Hugo

    cd /path/to/hugo
    go install github.com/spf13/hugo/hugolibs
    go run main.go


**Complete documentation is available at [Hugo Documentation](http://hugo.spf13.com).**

## License

Hugo is released under the Simple Public License. See [LICENSE.md](https://github.com/spf13/hugo/blob/master/LICENSE.md).
