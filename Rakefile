#
# Copyright (c) 2015-present, Parse, LLC.
# All rights reserved.
#
# This source code is licensed under the BSD-style license found in the
# LICENSE file in the root directory of this source tree. An additional grant
# of patent rights can be found in the PATENTS file in the same directory.
#

require_relative 'Vendor/xctoolchain/Scripts/xctask/build_task'
require_relative 'Vendor/xctoolchain/Scripts/xctask/build_framework_task'

script_folder = File.expand_path(File.dirname(__FILE__))
build_folder = File.join(script_folder, 'build')
release_folder = File.join(build_folder, 'release')

xcworkspace_name = 'ParseTwitterUtils.xcworkspace'
framework_name = 'ParseTwitterUtils.framework'

namespace :build do
  desc 'Build iOS framework.'
  task :ios do
    task = XCTask::BuildFrameworkTask.new do |t|
      t.directory = script_folder
      t.build_directory = build_folder
      t.framework_type = XCTask::FrameworkType::IOS
      t.framework_name = framework_name

      t.workspace = xcworkspace_name
      t.scheme = 'ParseTwitterUtils-iOS'
      t.configuration = 'Release'
    end
    result = task.execute
    unless result
      puts 'Failed to build iOS Framework.'
      exit(1)
    end
  end
end

namespace :package do
  ios_package_name = 'ParseTwitterUtils-iOS.zip'

  desc 'Build and package all frameworks'
  task :frameworks do
    rm_rf build_folder, :verbose => false
    mkdir_p build_folder, :verbose => false

    Rake::Task['build:ios'].invoke
    ios_framework_path = File.join(build_folder, framework_name)
    make_package(release_folder, [ios_framework_path], ios_package_name)
  end

  def make_package(target_path, items, archive_name)
    temp_folder = File.join(target_path, 'tmp')
    `mkdir -p #{temp_folder}`

    item_list = ''
    items.each do |item|
      `cp -R #{item} #{temp_folder}`

      file_name = File.basename(item)
      item_list << " #{file_name}"
    end

    archive_path = File.join(target_path, archive_name)
    `cd #{temp_folder}; zip -r --symlinks #{archive_path} #{item_list}`
    rm_rf temp_folder
    puts "Release archive created: #{File.join(target_path, archive_name)}"
  end
end
