# encoding: utf-8

require 'resque/tasks'

task 'resque:setup' do
  puts 'setting up...'
  require 'resque'
  
  puts Resque.redis.ping # ensure connected on parent

  # bail on parent, leave child alive.
  if fork
    sleep 3
    puts 'parent fork dies'
    exit!
  end
end
