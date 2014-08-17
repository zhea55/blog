 require 'rubygems'
    require 'rake'
    require 'rdoc'
    require 'date'
    require 'yaml'


    desc "Generate and publish blog to master"
    task :publish do
      system "rm -rf D:/zhea55.github.io/*"
      system "cp _site/* D:/zhea55.github.io -rf"
      system "git init"
      message = "Site updated at #{Time.now.utc}"
      system "git add ."
      system "git commit -am #{message.shellescape}"
      system "git push https://github.com/zhea55/zhea55.github.io.git master --force"
      system "echo yolo"
    end

task :default => :publish
