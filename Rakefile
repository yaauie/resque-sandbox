# encoding: utf-8

require 'resque/tasks'

task 'resque:setup' do
  puts 'setting up...'
  require 'resque'
  
  Resque.redis.ping # ensure connected on parent

  # bail on parent, leave child alive.
  # exit! unless fork
end
