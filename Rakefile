# encoding: utf-8

require 'resque/tasks'

def redis_command(redis, *args)
  $stderr.puts "#{Process.pid}: running #{args.join(', ')}\n"; $stderr.flush
  $stderr.puts "#{Process.pid}: #{redis.client}(#{redis.client.class})\n" +
               "  connected: #{redis.client.connected?}\n" +
               "  connection_pid: #{redis.client.instance_exec { @pid }}\n"

  redis.public_send(*args)
rescue
  $stderr.puts "#{Process.pid}: raised exception #{$!}\n"; $stderr.flush
  raise
end

$attempt ||= 0

task 'resque:setup' do
  require 'resque'
  
  # puts "#{Process.pid}: PING->#{redis_command(Resque.redis, :ping)}" # ensure connected on parent
end
