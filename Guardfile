require 'asciidoctor'
require 'erb'


#
# OUT OF DATE!
#
# I used to use this as the means to continuously regenerate HTML pages of the manuscript, chapter by chapter.
# I since migrated to running "doc" against either a single chapter (./doc 1) or the index to do it all (./doc index).
#

options = {:attributes => ['allow-uri-read'] }

guard 'shell' do
  watch(/^.*\.adoc$/) {|m|
  	puts "Looking at " << m[0]
		puts "Time to rebuild " << m[0]
		Asciidoctor.convert_file(m[0], :safe => Asciidoctor::SafeMode::UNSAFE, :attributes => {'allow-uri-read' => '', 'copycss' => ''})
  	puts "Time to rebuild the index"
    Asciidoctor.convert_file("my-tech-book-index.adoc", :safe => Asciidoctor::SafeMode::UNSAFE, :attributes => {'allow-uri-read' => '', 'copycss' => ''})
  }
end

guard 'livereload' do
  watch(%r{^.+\.(css|js|html)$})
end