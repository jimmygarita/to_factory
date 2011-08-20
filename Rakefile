require 'bundler/gem_tasks'

require 'active_record'
require 'yaml'

namespace :test do
  namespace :db do
    desc "Migrate the database through scripts in db/migrate. Target specific version with VERSION=x"
    task :migrate => :environment do
      ActiveRecord::Migrator.migrate('db/migrate', ENV["VERSION"] ? ENV["VERSION"].to_i : nil )
    end

    task :environment do
      ActiveRecord::Base.establish_connection(YAML::load(File.read('database.yml')))
      ActiveRecord::Base.logger = Logger.new(File.open('database.log', 'a'))
    end
  end
end
