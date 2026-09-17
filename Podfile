platform :osx, '15.0'

target 'MultiSoundChanger' do
  # Comment the next line if you don't want to use dynamic frameworks
  use_frameworks!

  pod 'SwiftLint'
  pod 'MediaKeyTap', :git => 'https://github.com/the0neyouseek/MediaKeyTap.git', :branch => 'master'
end

post_install do |installer|
  installer.pods_project.targets.each do |t|
    t.build_configurations.each do |c|
      c.build_settings['MACOSX_DEPLOYMENT_TARGET'] = '15.0'
    end
  end
end
