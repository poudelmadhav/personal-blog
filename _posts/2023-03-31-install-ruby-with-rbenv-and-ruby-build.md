---
title: Install ruby with rbenv and ruby-build
date: 2023-03-31 10:14:28 +0545
layout: post
permalink: install-ruby-with-rbenv-and-ruby-build/
category:
- ruby
meta_description: Install ruby with rbenv and ruby-build
meta_keywords: Install ruby with rbenv and ruby-build, install ruby, install ruby if ruby version is not available on ruby build, ruby build
comments: true
---

To install Ruby using `ruby-build` and `rbenv`, you can follow these steps:

### Step 1
First, make sure you have `ruby-build` and `rbenv` installed on your system. You can check if you have them installed by running the following commands in your terminal:

```shell
which ruby-build
which rbenv
  ```

If either of these commands returns a path, it means that the corresponding tool is already installed on your system. If not, you can follow the installation instructions for your operating system.

### Step 2
Next, check if the version of Ruby you want to install is available in `ruby-build`. You can do this by running the following command:

```shell
ruby-build --definitions | grep <version>
```

Replace `<version>` with the version of Ruby you want to install. If the version is available in `ruby-build`, you can proceed to step 3. Otherwise, you will need to wait for the update to become available in `ruby-build`, or you can try installing Ruby manually.

### Step 3
Install the Ruby version using `rbenv` and `ruby-build`:

```shell
rbenv install <version>
```

Replace `<version>` with the version of Ruby you want to install. This will download the Ruby source code and compile it, which may take some time.

### Step 4
Once the installation is complete, you can set the global version of Ruby to use:

```shell
rbenv global <version>
```

This will set the global version of Ruby to the version you just installed.

### Step 5
Finally, verify that Ruby was installed correctly by running the following command:

```shell
ruby -v
```

This should display the version of Ruby you just installed.

If the version of Ruby you want to install is not available in `ruby-build` yet, but it is available in the official release, you can download the source code from the Ruby website and compile it manually. Once you have the source code, you can use `ruby-build` to compile and install it:

### Step 1
Download the Ruby source code from the official Ruby website: [https://www.ruby-lang.org/en/downloads](https://www.ruby-lang.org/en/downloads){:target="_blank"}

### Step 2
Extract the source code to a directory of your choice.

### Step 3
Use `ruby-build` to compile and install the Ruby version:

```shell
ruby-build <path/to/source/code> <install/path>
```

Replace `<path/to/source/code>` with the path to the directory containing the extracted source code, and `<install/path>` with the path where you want to install Ruby.

### Step 4
Once the installation is complete, you can set the global version of Ruby to use:

```shell
rbenv global <version>
```

### Step 5
Replace `<version>` with the version of Ruby you just installed.

Finally, verify that Ruby was installed correctly by running the following command:

```shell
ruby -v
```

This should display the version of Ruby you just installed.
