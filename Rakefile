gem_version = File.read("VERSION").strip
gem_name = "instaorganizer"


task :build do
  system "gem build .gemspec"
end

task :release => :build do
  system "gem push #{gem_name}-#{gem_version}.gem"
end

task :install => :build do
  system "gem install --local #{gem_name}-#{gem_version}.gem"
end

task :pry do
  system "pry --gem"
end

task :spec do
  cmd = %w[rspec -fd -c spec]

  if system *%w[which rescue]
    system *(["rescue"]+cmd)
  else
    system *cmd
  end
end

task :default => :spec
