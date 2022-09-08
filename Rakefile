# frozen_string_literal: true

require 'bundler/gem_tasks'
require 'rake/testtask'
require 'find'

desc 'Run tests'
task default: :test

Rake::TestTask.new(:test) do |t|
  t.libs << 'test'
  t.pattern = 'test/**/*_test.rb'
  # Equivalent alternative: t.test_files = FileList['test/**/*_test.rb']
end

desc 'List program files'
task :inventory do
  total_size = 0
  file_path_list = []

  Find.find('.') do |path|
    Find.prune if path.include?('/.')

    if FileTest.file?(path)
      file_path_list << path
      total_size += FileTest.size(path)
    end
  end

  puts(file_path_list.map { |path| path[2..] })
  puts '---'
  puts "Size: #{total_size / 1000} KB"
end
