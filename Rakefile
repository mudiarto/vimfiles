require 'rubygems'
require 'erb'

task :default => :install

task :install => ['git:submodules', 'generate:vimrc','links', 'install:commandt'] do
end

task :links do
  system("rm ~/.vimrc")
  system("ln -s ~/.vim/vimrc ~/.vimrc")
end

namespace :git do
  task :submodules do
    system("git submodule init")
    system("git submodule update")
  end
end

namespace :generate do
  task :vimrc do
    file = "vimrc.erb.vim"
    File.open("vimrc", 'w') do |new_file|
      new_file.write ERB.new(File.read(file)).result(binding)
    end
  end
end

namespace :install do
  task :commandt do
   system("cd ~/.vim/bundle/vim-commandt/ruby/command-t && ruby extconf.rb && make")
  end
end

