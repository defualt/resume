require "rake"

namespace :rst do
  desc "Generate reStructuredText file"
  task :generate do
    puts "Generating reStructuredText file from Markdown"
    system("pandoc -s -w rst resume.markdown -o output/resume.rst")
    puts "Done"
  end
end

namespace :html do
  desc "Compile stylesheet"
  task :styles do
    puts "Compiling CSS file"
    system("compass compile")
  end

  desc "Generate standalone HTML file"
  task :generate => [:styles] do
    puts "Generating standalone HTML file from Markdown"
    system("pandoc -s -S resume.markdown -o output/resume.html -t html5 --self-contained --section-divs --template=templates/html/x.html -T \"Stephen Tudor's Resume\" -c css/main.css")
    system("cp output/resume.html index.html")
    puts "Done"
  end
end

namespace :tex do
  desc "Generate LaTeX file"
  task :generate do
    puts "Generating LaTeX file from Markdown"
    system("pandoc -s -w context resume.markdown -o output/resume.tex")
    puts "Done"
  end
end

namespace :pdf do
  desc "Generate PDF file"
  task :generate do
    puts "Generating PDF file from Markdown"
    system("pandoc -V geometry:margin=1in --template=templates/pdf/x.tex resume.markdown -s -o output/resume.pdf")
    puts "Done"
  end
end

namespace :rtf do
  desc "Generate RTF file"
  task :generate do
    puts "Generating RTF file from Markdown"
    system("pandoc -s -S resume.markdown -o output/resume.rtf")
    puts "Done"
  end
end

namespace :word do
  desc "Generate docx file"
  task :generate do
    puts "Generating docx file from Markdown"
    system("pandoc -s -S resume.markdown -o output/resume.docx --reference-docx=templates/docx/x.docx")
    puts "Done"
  end
end

namespace :odt do
  desc "Generate ODT file"
  task :generate do
    puts "Generating ODT file from Markdown"
    system("pandoc -s -S resume.markdown -o output/resume.odt")
    puts "Done"
  end
end

namespace :epub do
  desc "Generate EPUB file"
  task :generate do
    puts "Generating EPUB file from Markdown"
    system("pandoc -s -S resume.markdown -o output/resume.epub")
    puts "Done"
  end
end

namespace :asciidoc do
  desc "Generate AsciiDoc file"
  task :generate do
    puts "Generating AsciiDoc file from Markdown"
    system("pandoc -s -S resume.markdown -t asciidoc -o output/resume.txt")
    puts "Done"
  end
end

namespace :docbook do
  desc "Generate DocBook file"
  task :generate do
    puts "Generating DocBook file from Markdown"
    system("pandoc -s -S -w docbook resume.markdown -o output/resume.db")
    puts "Done"
  end
end

task :readme do
  desc "Copy resume to README"
  puts "Copying README"
  system("cp resume.markdown README.markdown")
  puts "Done"
end

task :all => [
  "rst:generate",
  "html:generate",
  "pdf:generate",
  "rtf:generate",
  "word:generate",
  "odt:generate",
  "epub:generate",
  "asciidoc:generate",
  "docbook:generate",
  "readme"
]

desc "Transfer resume files to web"
task :web do
  puts "Transferring files to web..."
  path = "smt@s17r.com:s17r.com/public"
  system("scp resume.* index.html #{path}/resume")
  system("scp index.html #{path}")
  puts "Done"
end

desc "Commit change"
task :ci do
  puts "Done"
  system("git checkout master")
  system("git add resume.db resume.docx resume.epub resume.html resume.markdown resume.odt resume.pdf resume.rst resume.rtf resume.tex resume.txt README.markdown index.html")
  system("git commit -m 'Update resume files'")
  puts "Done"
end

desc "Push to GitHub"
task :push => [:ci] do
  system("git checkout gh-pages")
  system("git checkout -f master index.html")
  system("git add index.html")
  system("git commit -m 'Update resume on GitHub Pages'")
  system("git push -f")
  system("git checkout master")
end

task :default => ["html:generate"]
