source 'https://rubygems.org'

# Specify your gem's dependencies in pdk.gemspec
gemspec

if RUBY_VERSION < '2.3.0'
  # avoid newer versions that do not support ruby 2.1 anymore
  gem 'cri', '>= 2.10.1', '< 2.11.0'
  gem 'ffi', '1.9.25'
  gem 'nokogiri', '1.7.2'
else
  gem 'nokogiri', '~> 1.10.8'
end

group :development do
  gem 'activesupport', '4.2.9'
  gem 'github_changelog_generator', '~> 1.14'
  if RUBY_VERSION < '2.2.0'
    # pry-byebug >= 3.5.0 requires ruby 2.2.0 or newer
    gem 'pry-byebug', '~> 3.4.0'
    # byebug >= 9.1.0 requires ruby 2.2.0 or newer
    gem 'byebug', '~> 9.0.6'
    # required for github_changelog_generator
    gem 'rack', '~> 1.0'
  elsif RUBY_VERSION < '2.4.0'
    # pry-byebug >= 3.8.0 requires ruby 2.4.0 or newer
    gem 'pry-byebug', '~> 3.7.0'
    # byebug >= 11.1.0 requires ruby 2.4.0 or newer
    gem 'byebug', '~> 11.0.1'
  else
    gem 'pry-byebug', '~> 3.4'
  end
  # ruby-prof >= 1.0 requires Ruby 2.4.0 or newer
  gem 'ruby-prof' if RUBY_VERSION >= '2.4.0'
  gem 'yard'
end

group :test do
  gem 'coveralls'
  gem 'json', '~> 2.2.0'
  gem 'license_finder', '~> 5.4.1'
  if RUBY_VERSION < '2.4'
    # license_finder depends on rubyzip which requires Ruby 2.4 in 2.x
    gem 'rubyzip', '< 2.0.0'
  end
  gem 'parallel', '= 1.13.0'
  gem 'parallel_tests', '~> 2.24.0'
  gem 'parser', '~> 2.5.1.2'
  gem 'rake', '~> 12.3', '>= 12.3.3'
  gem 'rspec', '~> 3.0'
  gem 'rspec-xsd'
  gem 'rubocop', '~> 0.57.2'
  gem 'rubocop-rspec', '~> 1.27.0'
  gem 'simplecov-console'
end

group :acceptance do
  gem 'minitar-cli'
  gem 'serverspec'
end

# Evaluate Gemfile.local and ~/.gemfile if they exist
extra_gemfiles = [
  "#{__FILE__}.local",
  File.join(Dir.home, '.gemfile'),
]

extra_gemfiles.each do |gemfile|
  if File.file?(gemfile) && File.readable?(gemfile)
    eval(File.read(gemfile), binding) # rubocop:disable Security/Eval
  end
end
