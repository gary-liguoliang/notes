
  533  sudo apt-get install ruby-full
  534  sudo gem install bundler
  547  vi Gemfile 
  548  bundle exec jekyll build --safe
  549  sudo gem install jekyll

need ruby 2.0 

guoliang@dev ~/dev/projects/notes $ ruby --version
ruby 1.9.3p484 (2013-11-22 revision 43786) [x86_64-linux]


sudo apt-add-repository ppa:brightbox/ruby-ng
sudo apt-get -y update
guoliang@dev ~/dev/projects/notes $ ruby --version
ruby 2.2.4p230 (2015-12-16 revision 53155) [x86_64-linux-gnu]


guoliang@dev ~/dev/projects/notes $ sudo gem install jekyll
ERROR:  Error installing jekyll:
	ERROR: Failed to build gem native extension.

    /usr/bin/ruby2.2 -r ./siteconf20160308-8449-jm6q7j.rb extconf.rb
mkmf.rb can't find header files for ruby at /usr/lib/ruby/include/ruby.h

extconf failed, exit code 1

Gem files will remain installed in /var/lib/gems/2.2.0/gems/ffi-1.9.10 for inspection.
Results logged to /var/lib/gems/2.2.0/extensions/x86_64-linux/2.2.0/ffi-1.9.10/gem_make.out
