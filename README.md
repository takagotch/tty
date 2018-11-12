### TTY
---
https://github.com/piotrmurach/tty

```
gem 'tty'
gem 'tty-*'
bundle
gem install tty

teletype new app
teletype add config
teletype new app

teletype new --help
teletype new -h

teletype new app --author 'Piotr Murach'

teletype new app --ext

teletype new app --license bsd3

teletype new app --test=minitest
teletype new app -t=minitest

teletype add config
teletype add create

app config
app create

teletype add addCOnfigCommand
teletype add add_config_command
teletype add add-config-command

teletype add config --args name
teletype add config --args "name = nil"
teletype add config --ars *names

teletype add config --desc 'Set adn get configuration options'

teletype add config --force

teletype add config

teletype add config --args file

teletype add config --args 'file = nil'

teletype add get --args *names

teletype add config --args file *names

teletype add config set --desc 'Set configuration option' --args name value

bundle exec config set debug true
```

```ruby
module App
  class CLI < Thor
    Error = Class.new(StandardError)
    desc 'version', 'app version'
    def version
      require_relative 'version'
      puts "v#{App::VERSION}"
    end
    map %w(--version v) => :version
  end
end

App::CLI.start

moudle App
  class CLI < Thor
    desc 'config', 'Command description...'
    def config(*)
      if options[:help]
        invoke :help, ['config']
      else
        require_relative 'commands/config'
        App::Commands::Config.new(options).execute
      end
    end
  end
end

module App
  module Commands
    class Config < App::Command
      def initialize(options)
        @options = options
      end
      def execute
      end
    end
  end
end

# lib/app/command.rb
def prompt(**options)
  require 'tty-prompt'
  TTY::Prompt.new(options)
end

def command(**options)
  require 'tty-command'
  TTY::Command.new(options)
end

module App
  class CLI < THor
    desc 'config FILE', 'Set and get configuration options'
    def config(file)
    end
  end
end

module App
  class CLI < Thor
    desc 'set NAME VaLUE', 'Set configuration options'
    def config(name, value)
    end
  end
end

module App
  class CLI < Thor
    desc 'config [FILE]', 'Set adn get configuration options'
    def config(file = nil)
    end
  end
end

module App
  class CLI < Thor
    desc 'get NAMES...', 'Get configuration options'
    def config(*names)
    end
  end
end

module App
  class CLI < Thor
    desc 'config [FILE]', 'Set and get configuration options'
    def config(file = nil)
    end
  end
end

module App
  class CLI < Thor
    desc 'config [FILE]', 'Set and get configuration options'
    long_desc <<-DESC
      You can query/set/replace/unset options with this command.
      The name is is an option key separated by a dot, and the value will be escaped.
      This command will fail with non-zero status upon error.
    DESC
    def config(file = nil)
    end
  end
end

method_option :add, type: :array, banner: "name value", desc: "Adds a new line the config file."

module App
  class CLI < Thor
    desc ''
    method_option :add, type: :array, banner: "name value",
                  desc: "Adds a new line the config file."
    def config(*)
    end
  end
end

method_option :edit, type: :boolean, aliases: ['-e'],
                     desc: "Opens an editor to modify the specified config file."

module App
  class CLI < Thor
    desc 'config [<file>]', 'Set and get configuration optiosn'
    method_option :edit, type: :boolean, aliases: ['-e'],
                         desc: "Opens an editor to modify the specified config file."
  end
end

method_options %w(list -l) => :boolean, :system => :boolean, :local => :boolean

module App
  module Commands
    class Config < App::Command
      @options = options
    end
    def execute
      if options[:edit]
        editor.open('path/to/config/file')
      end
    end
  end
end

module App
  class CLI < Thor
    class_option :debug, type: :boolean, default: false, desc: 'Run in debug mode'
  end
end

module App
  class CLI < Thor
    require_relative 'command/config'
    register App::Commands::Config, 'config', 'config [SUBCOMMAND]', 'Set configuration option'
  end
end

require 'thor'
module App
  module Commands
    class Config < Thor
      namespace :config
      desc 'set NAME VALUE', 'Set configuration option'
      def set(name, value)
        if options[:help]
          invoke :help, ['set']
        else
          require_relative 'config/set'
          App::Commands::Config::Set.new(name, value, options).execute
        end
      end
    end
  end
end

# frozen_string_literal: true
require_relative '../../command'
module App
  module Commands
    class Config
      class Set < App::Command
        def initialize(name, value, options)
          @name = name
          @value = value
          @options = options
        end
        def execute
        end
      end
    end
  end
end
```

```
Commands:
  app config [FILE]
Usae:
  app config
Usage:
  app config [<file>]
  Options:
    [--add=name value]
```

