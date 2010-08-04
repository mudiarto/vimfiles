require 'rubygems'
require 'erb'

task :default => :install

task :install do
  system("git submodule init")
  system("git submodule update")

  file = "vimrc.erb.vim"
  puts "generating ~/.#{file.sub('.erb', '')}"
  File.open(File.join(ENV['HOME'], ".#{file.sub('.erb.vim', '')}"), 'w') do |new_file|
    new_file.write ERB.new(File.read(file)).result(binding)
  end

  system("rm ~/.vimrc")
  system("ln -s ./vimrc ~/.vimrc")
end
