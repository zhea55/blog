 require 'rubygems'
    require 'rake'
    require 'rdoc'
    require 'date'
    require 'yaml'


    desc "Generate and publish blog to master"
    task :publish do
      system "rm -rf D:/zhea55.github.io/*"
      system "cp _site/* D:/zhea55.github.io -rf"
      system "cd D:/zhea55.github.io && git init && git add . && git commit -am 'generated' && git push git@github.com:zhea55/zhea55.github.io.git master --force && cd D:/blog"
      message = "Site updated at #{Time.now.utc}"
      system "echo yolo"
    end

task :default => :publish
