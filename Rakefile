# encoding: utf-8

require 'fileutils'

root = File.expand_path('.')

def replace_figure_markup_in(file)
  content = File.read(file)
  content.gsub!(/Insert\s18333fig\d+\.png\s*\n.*?(\d{1,2})-(\d{1,2})\. (.*)/, '![图 \1-\2：\3](images/\1-\2.png)')
  File.open(file, 'w') do |f|
    f.puts content
  end
end

namespace :copy do
  # Usage: rake copy:markdown [lang='zh']
  desc 'Copy markdown files from progit submodule'
  task :markdown do
    lang = ENV['lang'] || 'zh'
    lang_dir = File.join(root, 'progit', lang)
    abort("rake aborted: #{lang_dir} directory does't exists") unless File.exist? lang_dir

    puts "Copying markdown files from #{lang_dir} ..."
    FileUtils.cd(lang_dir) do
      Dir.glob('*/*.markdown') do |md|
        name = "#{File.basename(md, '.markdown').split('-').last}.txt"
        txt = File.join(root, 'manuscript', "#{name}")
        FileUtils.cp(md, txt)
        puts "    Copied to #{name}"
        replace_figure_markup_in(txt)
        puts "    Replaced figure markup in #{name}"
        puts
      end
    end
    puts "Done!"
  end

  desc "Copy figures, maybe only need run once"
  task :figure do
    from = File.join(root, 'progit', 'figures')
    to   = File.join(root, 'manuscript', 'images')

    puts "Copying figures from #{from} ..."
    FileUtils.cd(from) do
      Dir.glob('18333*.png') do |figure|
        dest = File.join(to, figure.sub(/18333fig0(\d)0?(\d+)\-tn/, '\1-\2'))
        FileUtils.cp(figure, dest)
      end
    end
    puts "Done!"
  end
end
