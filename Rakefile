require 'rake/clean'
require 'yaml'
require 'tilt'

SRC = FileList['**/*.*'].exclude(/^\./).ext.exclude(/^README$/)
CLEAN = FileList['*.html']

task default: :build

task build: SRC do
  debugger
end

html = lambda do |f|
  puts Tilt[f].inspect
end
rule '.html' => html
