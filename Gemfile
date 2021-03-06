source 'https://rubygems.org'

if Gem::Version.new(Bundler::VERSION) < Gem::Version.new('1.5.0')
  abort "Redmine requires Bundler 1.5.0 or higher (you're using #{Bundler::VERSION}).\nPlease update with 'gem update bundler'."
end

gem "rails", "4.2.4"
gem "addressable", "2.4.0" if RUBY_VERSION < "2.0"
gem "jquery-rails", "~> 4.2.1"
gem "coderay", "~> 1.1.1"
gem "builder", ">= 3.0.4"
gem "request_store", "1.3.2"
gem "mime-types", (RUBY_VERSION >= "2.0" ? "~> 3.0" : "~> 2.99")
gem "protected_attributes"
gem "actionpack-action_caching"
gem "actionpack-xml_parser"
gem "roadie-rails"
gem "mimemagic"
gem 'pg','0.19.0'

gem "nokogiri", "~> 1.6.8"
gem "i18n", "~> 0.7.0"
gem "ffi", "1.9.14", :platforms => :mingw if RUBY_VERSION < "2.0"

# Request at least rails-html-sanitizer 1.0.3 because of security advisories 
gem "rails-html-sanitizer", ">= 1.0.3"

# Windows does not include zoneinfo files, so bundle the tzinfo-data gem
gem 'tzinfo-data', platforms: [:mingw, :x64_mingw, :mswin, :jruby]
gem "rbpdf", "~> 1.19.2"

group :development do
  gem 'capistrano', '~> 3.4.1'
  gem 'capistrano-rails', '~> 1.1.8'
  gem 'capistrano-rbenv', '~> 2.0.4'
  gem 'capistrano-passenger'


end

# Optional gem for LDAP authentication
group :ldap do
  gem "net-ldap", "~> 0.15.0"
end

# Optional gem for OpenID authentication
group :openid do
  gem "ruby-openid", "~> 2.7.0", :require => "openid"
  gem "rack-openid"
end

platforms :mri, :mingw, :x64_mingw do
  # Optional gem for exporting the gantt to a PNG file, not supported with jruby
 # group :rmagick do
  #  gem "rmagick", ">= 2.14.0"
    
 # end

  # Optional Markdown support, not for JRuby
  group :markdown do
    gem "redcarpet", "~> 3.3.2"
  end
end

platforms :jruby do
  # jruby-openssl is bundled with JRuby 1.7.0
  gem "jruby-openssl" if Object.const_defined?(:JRUBY_VERSION) && JRUBY_VERSION < '1.7.0'
  gem "activerecord-jdbc-adapter", "~> 1.3.2"
end

# Include database gems for the adapters found in the database
# configuration file

group :development do
  gem "rdoc", "~> 4.3"
  gem "yard"
end

group :test do
  gem "minitest"
  gem "rails-dom-testing"
  gem "mocha"
  gem "simplecov", "~> 0.9.1", :require => false
  # For running UI tests
  gem "capybara"
  gem "selenium-webdriver", "~> 2.53.4"
end

local_gemfile = File.join(File.dirname(__FILE__), "Gemfile.local")
if File.exists?(local_gemfile)
  eval_gemfile local_gemfile
end

# Load plugins' Gemfiles
Dir.glob File.expand_path("../plugins/*/{Gemfile,PluginGemfile}", __FILE__) do |file|
  eval_gemfile file
end
