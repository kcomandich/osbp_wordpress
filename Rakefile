# Settings
user = 'bridgepdx'
host = 'opensourcebridge.org'
path = '/var/www/wordpress/wp-content/themes/osbp_wordpress_theme_v3/'

# Derived settings
remote = "#{user}@#{host}:#{path}"
# rsync: (v)erbose e(x)clude-other-devices (r)ecursive preserve-sym(l)inks
rsync = 'rsync --checksum -vxrl --progress --exclude=.* --exclude=*~ --exclude=*.swp --exclude=Rakefile --exclude=my_common_styles_url.txt* --exclude=shared_fragments'

desc "Show help"
task :help do
  puts <<-HERE
Tasks:
* deploy => Deploys files to production server
* fetch => Copies files from production server
  HERE
end
task :default => :help

desc "Deploys common style files using rsync"
task :deploy do
  sh "#{rsync} . #{remote}"
end

desc "Copy deployed files from remote into this directory -- will overwrite your files here"
task :fetch do
  sh "#{rsync} #{remote} ."
end
