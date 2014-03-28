require 'bundler'
Bundler::GemHelper.install_tasks

require 'rake'
require 'rake/testtask'
require 'rake/task'

desc 'Default: run unit tests.'
task :default => :test

desc 'Test the acts_as_follower_plus gem.'
Rake::TestTask.new(:test) do |t|
  t.libs << 'lib'
  t.pattern = 'test/**/*_test.rb'
  t.verbose = true
end

desc 'Generate documentation for the acts_as_follower_plus gem.'
Rake::RDocTask.new(:rdoc) do |rdoc|
  rdoc.rdoc_dir = 'rdoc'
  rdoc.title    = 'Acts As Follower Plus'
  rdoc.main     = 'README.rdoc'
  rdoc.options << '--line-numbers' << '--inline-source'
  rdoc.rdoc_files.include('README.rdoc', 'lib/**/*.rb')
end

namespace :rcov do
  desc "Generate a coverage report in coverage/"
  task :gen do
    sh "rcov --output coverage test/*_test.rb --exclude 'gems/*'"
  end

  desc "Remove generated coverage files."
  task :clobber do
    sh "rm -rdf coverage"
  end
end
