# Recast.AI documentation

This repository contains the documentation for the [Recast.AI platform](https://recast.ai).
The hosted version is [here](https://recastai.github.io/docs/).

## Installation

Make sure you have bundler installed:
```sh
> gem install bundler
```

Clone the repository and install the dependencies:
```sh
> git clone https://github.com/RecastAI/docs.git
> cd docs
> bundle install
```

If you don't have jekyll installed on your computer:
```sh
> gem install jekyll
```

## Run the project with hot reload

In a terminal, enter:
```sh
> bundle exec jekyll serve --livereload
```

You can now go on http://localhost:4000 to see it live.

## Build the project

```sh
bundle exec jekyll build
```
