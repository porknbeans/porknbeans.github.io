# A very simple Rakefile for generating static sites. It's essentially Hobix,
# but probably simpler. Every page of the site is a YAML file. The YAML file
# gets compiled into a HTML file with the same basename. The content can be
# wrapped in a layout.
require 'rake/clean'
require 'open-uri'
require 'yaml'
require 'erb'

YML    = FileList['**/*.yml'].exclude(/^[_.]/)
SASS   = FileList['**/*.s[ac]ss'].exclude(/^[_.]/)
COFFEE = FileList['**/*.coffee'].exclude(/^[_.]/)

HTML   = YML.ext('html')
CSS    = SASS.ext('css')
JS     = COFFEE.ext('js')

SITE = HTML + CSS + JS

CLEAN << SITE.existing

task default: :build

task build: SITE

task :serve => :build do
  require 'webrick'
  server = WEBrick::HTTPServer.new :Port => ENV['PORT'] || 3939
  server.mount '/', WEBrick::HTTPServlet::FileHandler, Dir.pwd
  trap('INT') { server.stop }
  server.start
end

rule '.html' => '.yml' do |t|
  page = OpenStruct.new(YAML.load(File.read(t.source)))

  page.layout ||= 'layout.erb'
  page.filter ||= :redcarpet
  page.title  ||= File.basename(t.name, '.html').gsub(/-/, ' ')

  content = FILTERS[page.filter].call(page.body)
  result  = ERB.new(File.read(page.layout)).result(binding)

  open(t.name, 'w') { |f| f.write(result) }
end

rule '.css' => '.scss' do |t|
  require 'sass'
  css = Sass::Engine.new(File.read(t.source), syntax: :scss).render
  open(t.name, 'w') { |f| f.write(css) }
end

rule '.css' => '.sass' do |t|
  require 'sass'
  css = Sass::Engine.new(File.read(t.source)).render
  open(t.name, 'w') { |f| f.write(css) }
end

FILTERS = {
  redcarpet: lambda { |s|
    require 'redcarpet'
    @redcarpet ||= Redcarpet::Markdown.new(Redcarpet::Render::HTML, :autolink => true)
    @redcarpet.render(s)
  }
}
