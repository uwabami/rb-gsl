require File.expand_path(%q{../lib/gsl/version}, __FILE__)

require 'bundler/setup'
require 'rubygems/package_task'
require 'rake/extensiontask'
require 'rake/testtask'

Bundler::GemHelper.install_tasks

Rake::TestTask.new do |t|
  t.libs << 'test'
  t.libs << 'test/gsl'
  t.libs << 'test/gsl/nmatrix_tests'
  t.test_files = FileList[
    'test/*.rb', 
    'test/gsl/*.rb', 
    'test/gsl/nmatrix_tests/nmatrix_gsl_test.rb']
end

spec = eval(IO.read('gsl.gemspec'))
Gem::PackageTask.new(spec).define
Rake::ExtensionTask.new(:gsl_native, spec)

task :default => [:compile, :test]
