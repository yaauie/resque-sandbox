# encoding: utf-8

require 'resque/tasks'

def debug_connection(redis_client)
  puts "#{Process.pid}: #{redis_client}(#{redis_client.class})\n" +
       "  connected: #{redis_client.connected?}\n" +
       "  connection_pid: #{redis_client.instance_exec { @pid }}\n"
end

task 'resque:setup' do
  puts 'setting up...'
  require 'resque'
  
  puts "#{Process.pid}: PING->#{Resque.redis.ping}" # ensure connected on parent
  debug_connection(Resque.redis.client)

  # bail on parent, leave child alive.
  if fork
    debug_connection(Resque.redis.client)
    sleep 1
    puts "#{Process.pid}: dies."
    exit!
  end

  debug_connection(Resque.redis.client)
  puts "#{Process.pid}: PING->#{Resque.redis.ping}"
  sleep 1
  debug_connection(Resque.redis.client)
  puts "#{Process.pid}: lives on."
end
