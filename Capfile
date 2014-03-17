# Load DSL and Setup Up Stages
require 'capistrano/setup'

# Capfile
require 'capistrano/rbenv'
require 'capistrano-resque'

# config/deploy.rb
set :rbenv_type, :user # or :system, depends on your rbenv setup
set :rbenv_ruby, '1.9.3-p448'
set :rbenv_path, `echo $RBENV_ROOT`.chomp
set :rbenv_prefix, "RBENV_ROOT=#{fetch(:rbenv_path)} RBENV_VERSION=#{fetch(:rbenv_ruby)} #{fetch(:rbenv_path)}/bin/rbenv exec"
set :rbenv_map_bins, %w{rake gem bundle ruby}
set :rbenv_roles, :all # default value

# Includes default deployment tasks
require 'capistrano/deploy'
require 'capistrano/bundler'

# Includes tasks from other gems included in your Gemfile
#
# For documentation on these, see for example:
#
#   https://github.com/capistrano/rvm
#   https://github.com/capistrano/rbenv
#   https://github.com/capistrano/chruby
#   https://github.com/capistrano/bundler
#   https://github.com/capistrano/rails
#
# require 'capistrano/rvm'
# require 'capistrano/rbenv'
# require 'capistrano/chruby'
# require 'capistrano/bundler'
# require 'capistrano/rails/assets'
# require 'capistrano/rails/migrations'

# Loads custom tasks from `lib/capistrano/tasks' if you have any defined.
Dir.glob('lib/capistrano/tasks/*.cap').each { |r| import r }

