+++
title = "Cross Compiling with Go"
description = ""
tags = [
    "go",
    "golang",
    "development",
]
date = "2014-02-28"
topics = [
    "Development",
    "golang",
]
+++

One of the great features of golang is that you can compile executables
for many different platforms and architectures from a single machine. It’s
really nice to be able to provide executables of
[Hugo](http://hugo.spf13.com) for a bunch of different platforms and
architectures without having to have all these different machines in
a build cluster.

As I’ve been working with Hugo, I’ve wanted to make the experience of
cross compiling as easy and painless as possible. My first attempt was
following the [excellent guide by Dave
Cheney](http://dave.cheney.net/2013/07/09/an-introduction-to-cross-compilation-with-go-1-1).
It provides a bash script that automated the process, but wasn’t very
customizable. I started writing another script to adjust the behavior to
what I needed when I came across [goxc][]. Inspired by Dave’s script,
[goxc][] is a go application that not only cross compiles, but also
can compress the different binaries and package them with the readme and
license. It’s customizable and easy to use.

Here are the necessary steps to be able to cross compile including the
gotchas that are important. 

## Step 1. Prep Go to be able to cross compile

We need to compile go from source to be able to cross compile. While any
host can be used, I use OSX as the host.  If you are on a different
platform or prefer to build go yourself follow the excellent
[documentation on building Go from
source](http://golang.org/doc/install/source). The following instructions
are how I prepare go for cross compilation on OSX.

    brew update
    brew install go --cross-compile-all

If you already have go installed, use 

    brew reinstall go --cross-compile-all

After this step please check your $PATH and make sure it’s setup
correctly.

I also check that `go version` returns the version I’m expecting.

    go version
    go version go1.2 darwin/amd64

I also check that the build happened properly and the system has all the
right file it needs to be able to cross compile. You should see a lot of
platforms and architectures under the /pkg/ directory inside GOROOT.

    ls `go env GOROOT`/pkg
    darwin_386    freebsd_386   freebsd_arm   linux_amd64   netbsd_386    netbsd_arm    openbsd_386   plan9_386     windows_386
    darwin_amd64  freebsd_amd64 linux_386     linux_arm     netbsd_amd64  obj           openbsd_amd64 tool          windows_amd64

If any of these checks return unexpected results then don’t continue.
Please check your steps and make sure that you didn’t miss anything. As
a last resource, carefully building manually from source should resolve
any issues.

## Step 2. Get goxc

    go get github.com/laher/goxc

Then prepare goxc to be able to cross compile.

    goxc -t

## Step 3. Prep the source and dependencies 

I like to start with a clean GOPATH so I have the latest of all dependencies.

    rm -rf ~/.gopath
    mkdir ~/.gopath
    GOPATH=$HOME/.gopath
    go get github.com/spf13/hugo
    go test github.com/spf13/hugo/...

Note, this is not the gopath I use to develop with. I use a temporary
gopath when building to ensure that I have the latest versions of each
library and dependency.

## Step 4. Configuring goxc 

For many people the defaults will work. I customize goxc slightly to fit
my situation. I prefer to provide the version and include that in the
build package. I also like to format the built packages a bit differently. 
We also don’t want to build the plan9 binary due to lack of watcher support for the OS. 

We could use the following command to build each time.

    goxc -d="$HOME/Code/GoBuilds/" -bc="linux windows darwin freebsd netbsd" -pv=0.10 -o="{{.Dest}}{{.PS}}{{.AppName}}{{.PS}}{{.Version}}{{.PS}}{{.AppName}}_{{.Version}}_{{.Os}}_{{.Arch}}{{.Ext}}"

Instead of typing this each and every time, I prefer to use the support
goxc has for a config file.  Creating a configuration file is very
straightforward since goxc does it for you. Type the same line but append
‘-wc’ at the end and it will create a config file with these settings
specific to your project. For me I prefer to leave out the packageversion
setting in the config file. Since I will provide that each time. 

    goxc -d="$HOME/Code/GoBuilds/" -bc="linux windows darwin freebsd netbsd" -o="{{.Dest}}{{.PS}}{{.AppName}}{{.PS}}{{.Version}}{{.PS}}{{.AppName}}_{{.Version}}_{{.Os}}_{{.Arch}}{{.Ext}}"

    cat .goxc.json
    {
        "ArtifactsDest": "/Users/spf13/Code/GoBuilds/",
        "OutPath": "{{.Dest}}{{.PS}}{{.AppName}}{{.PS}}{{.Version}}{{.PS}}{{.AppName}}_{{.Version}}_{{.Os}}_{{.Arch}}{{.Ext}}",
        "BuildConstraints": "linux windows darwin freebsd netbsd",
        "ConfigVersion": "0.9"
    }%

## Step 5. Cross Compiling

With the config file in place, building is as simple as 

    goxc -pv=”0.10”

The goxc program will run for a while first building all dependencies for
each architecture and platform. This will take most of the time. At the
end it will build your application for each arch and os. 

If all goes well the output should resemble the following:

<div class='scrollable'><pre><code>
    [goxc:xc] 2014/03/01 11:11:55 Parallelizing xc for 13 platforms, using max 7 of 8 processors
    [goxc:xc] 2014/03/01 11:11:55 mainDirs : [/Users/spf13/Code/hugo]
    [goxc:xc] 2014/03/01 11:11:55 building hugo for platform {linux 386}.
    [goxc:xc] 2014/03/01 11:11:55 mainDirs : [/Users/spf13/Code/hugo]
    [goxc:xc] 2014/03/01 11:11:55 building hugo for platform {linux amd64}.
    [goxc:xc] 2014/03/01 11:11:55 mainDirs : [/Users/spf13/Code/hugo]
    [goxc:xc] 2014/03/01 11:11:55 building hugo for platform {linux arm}.
    [goxc:xc] 2014/03/01 11:11:55 mainDirs : [/Users/spf13/Code/hugo]
    [goxc:xc] 2014/03/01 11:11:55 building hugo for platform {windows 386}.
    [goxc:xc] 2014/03/01 11:11:55 mainDirs : [/Users/spf13/Code/hugo]
    [goxc:xc] 2014/03/01 11:11:55 building hugo for platform {windows amd64}.
    [goxc:xc] 2014/03/01 11:11:55 mainDirs : [/Users/spf13/Code/hugo]
    [goxc:xc] 2014/03/01 11:11:55 building hugo for platform {darwin 386}.
    [goxc:xc] 2014/03/01 11:11:55 mainDirs : [/Users/spf13/Code/hugo]
    [goxc:xc] 2014/03/01 11:11:55 building hugo for platform {darwin amd64}.
    [goxc:xc] 2014/03/01 11:11:55 mainDirs : [/Users/spf13/Code/hugo]
    [goxc:xc] 2014/03/01 11:11:55 building hugo for platform {freebsd 386}.
    [goxc:xc] 2014/03/01 11:11:55 mainDirs : [/Users/spf13/Code/hugo]
    [goxc:xc] 2014/03/01 11:11:55 building hugo for platform {freebsd amd64}.
    [goxc:xc] 2014/03/01 11:11:55 mainDirs : [/Users/spf13/Code/hugo]
    [goxc:xc] 2014/03/01 11:11:55 building hugo for platform {freebsd arm}.
    [goxc:xc] 2014/03/01 11:11:55 mainDirs : [/Users/spf13/Code/hugo]
    [goxc:xc] 2014/03/01 11:11:55 building hugo for platform {netbsd 386}.
    [goxc:xc] 2014/03/01 11:11:55 mainDirs : [/Users/spf13/Code/hugo]
    [goxc:xc] 2014/03/01 11:11:55 building hugo for platform {netbsd amd64}.
    [goxc:xc] 2014/03/01 11:11:55 mainDirs : [/Users/spf13/Code/hugo]
    [goxc:xc] 2014/03/01 11:11:55 building hugo for platform {netbsd arm}.
    [goxc:xc] 2014/03/01 11:11:55 specified env vars for 'go': [GOOS=linux GOARCH=386]
    [goxc:xc] 2014/03/01 11:11:55 invoking '/usr/local/Cellar/go/1.2/libexec/bin/go build -ldflags " -X main.BUILD_DATE '2014-03-01T11:11:55-05:00' -X main.VERSION '0.10' " -o /Users/spf13/Code/GoBuilds/hugo/0.10/hugo_0.10_linux_386 .' from '/Users/spf13/Code/hugo'
    [goxc:xc] 2014/03/01 11:11:55 specified env vars for 'go': [GOOS=linux GOARCH=amd64]
    [goxc:xc] 2014/03/01 11:11:55 invoking '/usr/local/Cellar/go/1.2/libexec/bin/go build -ldflags " -X main.BUILD_DATE '2014-03-01T11:11:55-05:00' -X main.VERSION '0.10' " -o /Users/spf13/Code/GoBuilds/hugo/0.10/hugo_0.10_linux_amd64 .' from '/Users/spf13/Code/hugo'
    [goxc:xc] 2014/03/01 11:11:55 specified env vars for 'go': [GOOS=windows GOARCH=386]
    [goxc:xc] 2014/03/01 11:11:55 invoking '/usr/local/Cellar/go/1.2/libexec/bin/go build -ldflags " -X main.BUILD_DATE '2014-03-01T11:11:55-05:00' -X main.VERSION '0.10' " -o /Users/spf13/Code/GoBuilds/hugo/0.10/hugo_0.10_windows_386.exe .' from '/Users/spf13/Code/hugo'
    [goxc:xc] 2014/03/01 11:11:55 specified env vars for 'go': [GOOS=windows GOARCH=amd64]
    [goxc:xc] 2014/03/01 11:11:55 invoking '/usr/local/Cellar/go/1.2/libexec/bin/go build -ldflags " -X main.BUILD_DATE '2014-03-01T11:11:55-05:00' -X main.VERSION '0.10' " -o /Users/spf13/Code/GoBuilds/hugo/0.10/hugo_0.10_windows_amd64.exe .' from '/Users/spf13/Code/hugo'
    [goxc:xc] 2014/03/01 11:11:55 specified env vars for 'go': [GOOS=darwin GOARCH=386]
    [goxc:xc] 2014/03/01 11:11:55 invoking '/usr/local/Cellar/go/1.2/libexec/bin/go build -ldflags " -X main.BUILD_DATE '2014-03-01T11:11:55-05:00' -X main.VERSION '0.10' " -o /Users/spf13/Code/GoBuilds/hugo/0.10/hugo_0.10_darwin_386 .' from '/Users/spf13/Code/hugo'
    [goxc:xc] 2014/03/01 11:11:55 specified env vars for 'go': [GOOS=darwin GOARCH=amd64]
    [goxc:xc] 2014/03/01 11:11:55 invoking '/usr/local/Cellar/go/1.2/libexec/bin/go build -ldflags " -X main.BUILD_DATE '2014-03-01T11:11:55-05:00' -X main.VERSION '0.10' " -o /Users/spf13/Code/GoBuilds/hugo/0.10/hugo_0.10_darwin_amd64 .' from '/Users/spf13/Code/hugo'
    [goxc:xc] 2014/03/01 11:11:55 specified env vars for 'go': [GOOS=freebsd GOARCH=386]
    [goxc:xc] 2014/03/01 11:11:55 invoking '/usr/local/Cellar/go/1.2/libexec/bin/go build -ldflags " -X main.BUILD_DATE '2014-03-01T11:11:55-05:00' -X main.VERSION '0.10' " -o /Users/spf13/Code/GoBuilds/hugo/0.10/hugo_0.10_freebsd_386 .' from '/Users/spf13/Code/hugo'
    [goxc:xc] 2014/03/01 11:11:55 specified env vars for 'go': [GOOS=freebsd GOARCH=amd64]
    [goxc:xc] 2014/03/01 11:11:55 invoking '/usr/local/Cellar/go/1.2/libexec/bin/go build -ldflags " -X main.BUILD_DATE '2014-03-01T11:11:55-05:00' -X main.VERSION '0.10' " -o /Users/spf13/Code/GoBuilds/hugo/0.10/hugo_0.10_freebsd_amd64 .' from '/Users/spf13/Code/hugo'
    [goxc:xc] 2014/03/01 11:11:55 specified env vars for 'go': [GOOS=freebsd GOARCH=arm]
    [goxc:xc] 2014/03/01 11:11:55 invoking '/usr/local/Cellar/go/1.2/libexec/bin/go build -ldflags " -X main.BUILD_DATE '2014-03-01T11:11:55-05:00' -X main.VERSION '0.10' " -o /Users/spf13/Code/GoBuilds/hugo/0.10/hugo_0.10_freebsd_arm .' from '/Users/spf13/Code/hugo'
    [goxc:xc] 2014/03/01 11:11:55 specified env vars for 'go': [GOOS=netbsd GOARCH=386]
    [goxc:xc] 2014/03/01 11:11:55 invoking '/usr/local/Cellar/go/1.2/libexec/bin/go build -ldflags " -X main.BUILD_DATE '2014-03-01T11:11:55-05:00' -X main.VERSION '0.10' " -o /Users/spf13/Code/GoBuilds/hugo/0.10/hugo_0.10_netbsd_386 .' from '/Users/spf13/Code/hugo'
    [goxc:xc] 2014/03/01 11:11:55 specified env vars for 'go': [GOOS=netbsd GOARCH=arm]
    [goxc:xc] 2014/03/01 11:11:59 invoking '/usr/local/Cellar/go/1.2/libexec/bin/go build -ldflags " -X main.BUILD_DATE '2014-03-01T11:11:55-05:00' -X main.VERSION '0.10' " -o /Users/spf13/Code/GoBuilds/hugo/0.10/hugo_0.10_netbsd_arm .' from '/Users/spf13/Code/hugo'
    [goxc:xc] 2014/03/01 11:11:55 specified env vars for 'go': [GOOS=linux GOARCH=arm]
    [goxc:xc] 2014/03/01 11:11:59 invoking '/usr/local/Cellar/go/1.2/libexec/bin/go build -ldflags " -X main.BUILD_DATE '2014-03-01T11:11:55-05:00' -X main.VERSION '0.10' " -o /Users/spf13/Code/GoBuilds/hugo/0.10/hugo_0.10_linux_arm .' from '/Users/spf13/Code/hugo'
    [goxc:xc] 2014/03/01 11:11:55 specified env vars for 'go': [GOOS=netbsd GOARCH=amd64]
    [goxc:xc] 2014/03/01 11:11:59 invoking '/usr/local/Cellar/go/1.2/libexec/bin/go build -ldflags " -X main.BUILD_DATE '2014-03-01T11:11:55-05:00' -X main.VERSION '0.10' " -o /Users/spf13/Code/GoBuilds/hugo/0.10/hugo_0.10_netbsd_amd64 .' from '/Users/spf13/Code/hugo'
    [goxc:xc] 2014/03/01 11:12:04 File '/Users/spf13/Code/GoBuilds/hugo/0.10/hugo_0.10_linux_386' is an ELF file (arch: EM_386, osabi: ELFOSABI_NONE)
    [goxc:xc] 2014/03/01 11:12:04 File '/Users/spf13/Code/GoBuilds/hugo/0.10/hugo_0.10_freebsd_386' is an ELF file (arch: EM_386, osabi: ELFOSABI_FREEBSD)
    [goxc:xc] 2014/03/01 11:12:04 File '/Users/spf13/Code/GoBuilds/hugo/0.10/hugo_0.10_darwin_386' is a Mach-O file (arch: Cpu386)
    [goxc:xc] 2014/03/01 11:12:04 File '/Users/spf13/Code/GoBuilds/hugo/0.10/hugo_0.10_windows_386.exe' is a PE file, arch: 332 (332='X86' and 34404='AMD64')
    [goxc:xc] 2014/03/01 11:12:04 File '/Users/spf13/Code/GoBuilds/hugo/0.10/hugo_0.10_linux_amd64' is an ELF file (arch: EM_X86_64, osabi: ELFOSABI_NONE)
    [goxc:xc] 2014/03/01 11:12:04 File '/Users/spf13/Code/GoBuilds/hugo/0.10/hugo_0.10_windows_amd64.exe' is a PE file, arch: 34404 (332='X86' and 34404='AMD64')
    [goxc:xc] 2014/03/01 11:12:04 File '/Users/spf13/Code/GoBuilds/hugo/0.10/hugo_0.10_freebsd_amd64' is an ELF file (arch: EM_X86_64, osabi: ELFOSABI_FREEBSD)
    [goxc:xc] 2014/03/01 11:12:05 File '/Users/spf13/Code/GoBuilds/hugo/0.10/hugo_0.10_darwin_amd64' is a Mach-O file (arch: CpuAmd64)
    [goxc:xc] 2014/03/01 11:12:05 File '/Users/spf13/Code/GoBuilds/hugo/0.10/hugo_0.10_freebsd_arm' is an ELF file (arch: EM_ARM, osabi: ELFOSABI_FREEBSD)
    [goxc:xc] 2014/03/01 11:12:05 File '/Users/spf13/Code/GoBuilds/hugo/0.10/hugo_0.10_netbsd_386' is an ELF file (arch: EM_386, osabi: ELFOSABI_NETBSD)
    [goxc:xc] 2014/03/01 11:12:05 File '/Users/spf13/Code/GoBuilds/hugo/0.10/hugo_0.10_netbsd_amd64' is an ELF file (arch: EM_X86_64, osabi: ELFOSABI_NETBSD)
    [goxc:xc] 2014/03/01 11:12:05 File '/Users/spf13/Code/GoBuilds/hugo/0.10/hugo_0.10_netbsd_arm' is an ELF file (arch: EM_ARM, osabi: ELFOSABI_NETBSD)
    [goxc:xc] 2014/03/01 11:12:05 File '/Users/spf13/Code/GoBuilds/hugo/0.10/hugo_0.10_linux_arm' is an ELF file (arch: EM_ARM, osabi: ELFOSABI_NONE)
    [goxc:xc] 2014/03/01 11:12:05 Task xc succeeded
    [goxc:codesign] 2014/03/01 11:12:05 Task codesign succeeded
    [goxc:copy-resources] 2014/03/01 11:12:05 resources: [README.md LICENSE.md]
    [goxc:copy-resources] 2014/03/01 11:12:05 Copying file /Users/spf13/Code/hugo/README.md to /Users/spf13/Code/GoBuilds/hugo/0.10/README.md
    [goxc:copy-resources] 2014/03/01 11:12:05 Copying file /Users/spf13/Code/hugo/LICENSE.md to /Users/spf13/Code/GoBuilds/hugo/0.10/LICENSE.md
    [goxc:copy-resources] 2014/03/01 11:12:05 Task copy-resources succeeded
    [goxc:archive-zip] 2014/03/01 11:12:05 Parallelizing archive-zip for 10 platforms, using max 7 of 8 processors
    [goxc:archive-zip] 2014/03/01 11:12:11 Artifact(s) archived to /Users/spf13/Code/GoBuilds/hugo/0.10/hugo_0.10_windows_386.zip
    [goxc:archive-zip] 2014/03/01 11:12:11 Artifact(s) archived to /Users/spf13/Code/GoBuilds/hugo/0.10/hugo_0.10_windows_amd64.zip
    [goxc:archive-zip] 2014/03/01 11:12:11 Artifact(s) archived to /Users/spf13/Code/GoBuilds/hugo/0.10/hugo_0.10_darwin_386.zip
    [goxc:archive-zip] 2014/03/01 11:12:11 Artifact(s) archived to /Users/spf13/Code/GoBuilds/hugo/0.10/hugo_0.10_freebsd_386.zip
    [goxc:archive-zip] 2014/03/01 11:12:11 Artifact(s) archived to /Users/spf13/Code/GoBuilds/hugo/0.10/hugo_0.10_netbsd_386.zip
    [goxc:archive-zip] 2014/03/01 11:12:11 Artifact(s) archived to /Users/spf13/Code/GoBuilds/hugo/0.10/hugo_0.10_freebsd_arm.zip
    [goxc:archive-zip] 2014/03/01 11:12:11 Artifact(s) archived to /Users/spf13/Code/GoBuilds/hugo/0.10/hugo_0.10_darwin_amd64.zip
    [goxc:archive-zip] 2014/03/01 11:12:12 Artifact(s) archived to /Users/spf13/Code/GoBuilds/hugo/0.10/hugo_0.10_freebsd_amd64.zip
    [goxc:archive-zip] 2014/03/01 11:12:12 Artifact(s) archived to /Users/spf13/Code/GoBuilds/hugo/0.10/hugo_0.10_netbsd_arm.zip
    [goxc:archive-zip] 2014/03/01 11:12:12 Artifact(s) archived to /Users/spf13/Code/GoBuilds/hugo/0.10/hugo_0.10_netbsd_amd64.zip
    [goxc:archive-zip] 2014/03/01 11:12:12 Task archive-zip succeeded
    [goxc:archive-tar-gz] 2014/03/01 11:12:12 Parallelizing archive-tar-gz for 3 platforms, using max 7 of 8 processors
    [goxc:archive-tar-gz] 2014/03/01 11:12:14 Artifact(s) archived to /Users/spf13/Code/GoBuilds/hugo/0.10/hugo_0.10_linux_386.tar.gz
    [goxc:archive-tar-gz] 2014/03/01 11:12:14 Artifact(s) archived to /Users/spf13/Code/GoBuilds/hugo/0.10/hugo_0.10_linux_arm.tar.gz
    [goxc:archive-tar-gz] 2014/03/01 11:12:15 Artifact(s) archived to /Users/spf13/Code/GoBuilds/hugo/0.10/hugo_0.10_linux_amd64.tar.gz
    [goxc:archive-tar-gz] 2014/03/01 11:12:15 Task archive-tar-gz succeeded
    [goxc:pkg-build] 2014/03/01 11:12:18 Task pkg-build succeeded
    [goxc:rmbin] 2014/03/01 11:12:18 Task rmbin succeeded
    [goxc:downloads-page] 2014/03/01 11:12:18 Task downloads-page succeeded
</code></pre></div>

## Addendum

A few people have commented on [reddit](http://www.reddit.com/r/golang/comments/1zjg2r/cross_compiling_with_go/) with additional information.

Some have reported success using [gox][]. I have yet to play with it
but [Mitchell](http://mitchellh.com) is known for writing excellent
software so I would expect nothing less here. [Gox][] does less than
[goxc][], but that’s the point. 

Cgo has issues when cross compiling. If you depend on cgo then you’re
probably going to be better off building on the native platforms. The go
tool will disable cgo support by default. To explicitly enable cgo, set CGO_ENABLED=1.

[gox]: https://github.com/mitchellh/gox
[goxc]: https://github.com/laher/goxc
