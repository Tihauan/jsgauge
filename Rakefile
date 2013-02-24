require 'yaml'

PROJECT_ROOT     = File.expand_path(File.dirname(__FILE__))
PROJECT_SRC_DIR  = File.join(PROJECT_ROOT, 'src')
PROJECT_CONF_DIR = File.join(PROJECT_ROOT, 'cfg')
PROJECT_LIB_DIR  = File.join(PROJECT_ROOT, 'lib')
PROJECT_DIST_DIR = File.join(PROJECT_ROOT, 'build')
PROJECT_PACKAGE_DIR = File.join(PROJECT_ROOT, 'release')

$conf            = YAML.load(IO.read(File.join(PROJECT_CONF_DIR, 'constants.yml')))
PROJECT_VERSION  = $conf['VERSION']
PROJECT_NAME     = $conf['PROJECT_NAME']

desc 'Helper function for placing the copyright message into a file'
def place_copyright(src, dest = src)
	copyright_notice = $conf['COPYRIGHT_NOTICE'].gsub('#{VERSION}', PROJECT_VERSION).
	  gsub('#{PROJECT_NAME}', PROJECT_NAME.capitalize)
	contents = [copyright_notice].concat(IO.readlines(src))
	dest_file = File.open(dest, 'w')
	dest_file.write(contents)
	dest_file.flush()
end

desc 'Helper function for minifying a js file'
def minify(src, dest)
	system `java -jar #{File.join(PROJECT_LIB_DIR, 'yui/yuicompressor-2.4.6.jar')} \
		--type js \
		-o #{dest} \
		#{src}`
	place_copyright(dest)
end

desc 'Minify, add copyright and copy files to the build folder'
task :build => [:clean] do
	puts "== Building #{PROJECT_NAME}-#{PROJECT_VERSION}"

	# copy and minify all source files
	Dir.glob(File.join(PROJECT_SRC_DIR, '*.js')).each do |src|
		base_name = File.basename(src)
		dist_name = File.join(PROJECT_DIST_DIR, base_name)
		system "cp #{src} #{dist_name}"
		place_copyright(dist_name)
		minify(dist_name, File.join(PROJECT_DIST_DIR, base_name.sub(/\.js/, '.min.js')))
	end

	# copy example files
	system "mkdir #{File.join(PROJECT_DIST_DIR, 'example')}"
	system "cp #{File.join(PROJECT_SRC_DIR, 'example/excanvas.js')} #{File.join(PROJECT_DIST_DIR, 'example/excanvas.js')}"
	system "cp #{File.join(PROJECT_SRC_DIR, 'example/gauge.html')} #{File.join(PROJECT_DIST_DIR, 'example/gauge.html')}"
end

desc 'Execute a JSLint test on source file. See cfg/jslint.yml for options.'
task :lint do
	puts "== JSLint #{PROJECT_NAME}-#{PROJECT_VERSION}"

	begin
		require 'jslint/tasks'
	rescue LoadError => e
		puts "\nYou'll need JSLint to build #{PROJECT_NAME}!"
		puts "\nhttps://github.com/psionides/jslint_on_rails"
	end

	JSLint.config_path = File.join(PROJECT_CONF_DIR, 'jslint.yml')
	Rake::Task['jslint'].invoke
end

desc "Copy build and create a release package."
task :release => [:build] do
	puts "== Releasing #{PROJECT_NAME}-#{PROJECT_VERSION}"

	# package
	require 'rake/packagetask'
	Rake::PackageTask.new(PROJECT_NAME, PROJECT_VERSION) do |p|
		p.need_zip = true
		p.package_dir = PROJECT_PACKAGE_DIR
		p.package_files.include("build/**/*")
	end
	Rake::Task['package'].invoke
end

task :clean do
	puts "== Cleaning #{PROJECT_NAME}-#{PROJECT_VERSION}"

	require 'rake/clean'

	# remove build output files and package files
	CLEAN.include(File.join(PROJECT_DIST_DIR, '**'))
	CLEAN.include(File.join(PROJECT_PACKAGE_DIR, "#{PROJECT_NAME}-#{PROJECT_VERSION}**"))
end

task :default => ['clean', 'lint', 'build']
