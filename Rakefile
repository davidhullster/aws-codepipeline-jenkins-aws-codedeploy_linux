#!/usr/bin/env ruby

require 'rake/testtask'
require 'rubygems'
require 'rake'
require 'haml'

# Default task
task default: :compile

# Task to compile HAML files to HTML
task :compile do
  FileList.new('./src/*.html.haml').each do |filename|
    content = File.read(filename) # read the file content once
    # Create the new HTML file
    File.open(filename.sub('.haml', ''), 'w') do |f|
      f.write Haml::Engine.new(content).render
    end
  end
end

task :clean do
  FileUtils.rm_r(Dir.glob("./*.html"), force: true)
end

task :test do 
  Rake::TestTask.new do |t|
    t.test_files = FileList['test/jenkins_sample_test.rb']
  end
end
