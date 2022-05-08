# [Carl Gieringer's Github blog](https://carlgieringer.github.io/)

## Development

### Setup

[instructions](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/testing-your-github-pages-site-locally-with-jekyll)

1. Install Ruby [mac instructions](https://www.ruby-lang.org/en/documentation/installation/#homebrew)
    * NOTE: Jekyll [gives](https://jekyllrb.com/docs/installation/macos/#step-2-install-chruby-and-the-latest-ruby-with-ruby-install) contradictory instructions to use Homebrew's `ruby-install` to install Ruby.

1. Install a ruby version manager
    * `RVM` ([mac instructions](https://rvm.io/rvm/install#any-other-system)) or
    * `chruby` (recommended by Jekyll for new installs)

1. Install a 2.x Ruby version

    (Ruby 3+ fails to run jekyll ([details](https://talk.jekyllrb.com/t/running-any-jekyll-command-fails-to-load-jekyll/5704/2)))

    * `RVM`:
      * Run `xcode-select --install` first because installation from source will upgrade Homebrew, which need
        developers' tools.
      * `rvm list known` will list binaries; Google search for the latest Ruby version available
      * `rvm install 2.7.6` to install from source.
      * Set this new Ruby as your default (optional): `rvm use 2.7.6 --default`
1. Create a Gem environment
    * `RVM`: `rvm --create --ruby-version use 2.7.6@gh-blog`
1. Upgrade RubyGems, if necessary: `gem update --system` (RubyGems comes with Ruby.)
1. Install Bundler: `gem install bundler`
1. Install Gems: `bundle install`
    * If Bundler fails to install `eventmachine` with an error like `openssl/ssl.h file not found` then do:

        ```shell
        gem install eventmachine -- --with-cppflags=-I$(brew --prefix openssl)/include
        ```

        And then `bundle install` again.

### Update dependencies

#### Updating RVM

```shell
rvm get stable --auto-dotfiles
```

#### Updating Gems

```shell
bundle update
```

### Running

```shell
bundle exec jekyll serve
```
