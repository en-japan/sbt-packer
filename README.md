# sbt-packer
Sbt plugin for Packer.io

*Branch*|*Build Status*|
|---|---|
|*master*|[![Build Status](https://magnum.travis-ci.com/en-japan/sbt-packer.svg?token=Fs6yxiLNnpCGj7zQMuZX)](https://magnum.travis-ci.com/en-japan/sbt-packer)|

Still in a work in progress since it only supports Debian/Ubuntu types of
instances.

## Prerequisites
The plugin assumes that sbt-native-packager 1.0.0-M4 has been included in
your SBT build configuration, and its settings have been
initialized. This can by done by adding the plugin following instructions at
http://www.scala-sbt.org/sbt-native-packager/.

## Installation

Add the following to your `project/plugins.sbt` file:
```scala
addSbtPlugin("com.enjapan" % "sbt-packer" % "0.0.1")
```

## Usage

Add the following to your build.sbt
```scala
enablePlugins(PackerPlugin)
```

Use the command
```shell
sbt packerBuildAmi
```
This will launch the `debian:packageBin` task from `sbt-native-package` to create a `.deb` package and install it on an ubuntu instance.

## Configuration

```scala
// Specify the id of the source ami to generate from
packerSourceAmi := "ami-64e27e0c"

// Specify instance type
packerInstanceType := "ubuntu"

// Specify the region
packerRegion := "us-east-1"

// Specify the instance type
packerInstanceType := "t1.micro"

// Specify the name of the user to ssh with
packerSshUsername := "ubuntu"

// Specify the name of the generated ami (defaults to <name>-<version>-{{timestamp}})
packerAmiName := "super-ami"
```


