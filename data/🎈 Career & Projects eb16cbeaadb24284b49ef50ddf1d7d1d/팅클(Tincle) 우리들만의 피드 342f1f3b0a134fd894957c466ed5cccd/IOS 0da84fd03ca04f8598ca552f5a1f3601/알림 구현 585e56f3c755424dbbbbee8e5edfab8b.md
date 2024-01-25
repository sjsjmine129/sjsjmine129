# 알림 구현

- 이미지 형태
    
    
    ![IMG_9151.PNG](%E1%84%8B%E1%85%A1%E1%86%AF%E1%84%85%E1%85%B5%E1%86%B7%20%E1%84%80%E1%85%AE%E1%84%92%E1%85%A7%E1%86%AB%20585e56f3c755424dbbbbee8e5edfab8b/IMG_9151.png)
    
    ![IMG_9150.PNG](%E1%84%8B%E1%85%A1%E1%86%AF%E1%84%85%E1%85%B5%E1%86%B7%20%E1%84%80%E1%85%AE%E1%84%92%E1%85%A7%E1%86%AB%20585e56f3c755424dbbbbee8e5edfab8b/IMG_9150.png)
    
    제품 백로그의 “푸시알림/알림창의 알림에는 해당 알림의 내용(댓글 내용, 반응 버튼 종류)이 표시된다.”의  반응 버튼 종류가 위 캡쳐의 앱 아이콘 위치에 들어가야 하는지(구현 필요), 2번째 이미지의 이모지 형태로 text로 들어가도 상관 없는지 
    

[https://jh3786.tistory.com/19](https://jh3786.tistory.com/19)

[https://honeystorage.tistory.com/306](https://honeystorage.tistory.com/306)

[https://www.npmjs.com/package/@react-native-community/push-notification-ios](https://www.npmjs.com/package/@react-native-community/push-notification-ios)

```
yarn add react-native-push-notification
yarn add @react-native-community/push-notification-ios
```

![스크린샷 2023-10-23 오후 6.01.59.png](%E1%84%8B%E1%85%A1%E1%86%AF%E1%84%85%E1%85%B5%E1%86%B7%20%E1%84%80%E1%85%AE%E1%84%92%E1%85%A7%E1%86%AB%20585e56f3c755424dbbbbee8e5edfab8b/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-10-23_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_6.01.59.png)

![스크린샷 2023-10-23 오후 6.02.25.png](%E1%84%8B%E1%85%A1%E1%86%AF%E1%84%85%E1%85%B5%E1%86%B7%20%E1%84%80%E1%85%AE%E1%84%92%E1%85%A7%E1%86%AB%20585e56f3c755424dbbbbee8e5edfab8b/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-10-23_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_6.02.25.png)

왼쪽  ‘+’ 버튼

Background Mode 추가 완료

Push Notification 추가

![스크린샷 2023-10-23 오후 6.03.10.png](%E1%84%8B%E1%85%A1%E1%86%AF%E1%84%85%E1%85%B5%E1%86%B7%20%E1%84%80%E1%85%AE%E1%84%92%E1%85%A7%E1%86%AB%20585e56f3c755424dbbbbee8e5edfab8b/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-10-23_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_6.03.10.png)

x code 에서 진행

![스크린샷 2023-10-23 오후 6.03.37.png](%E1%84%8B%E1%85%A1%E1%86%AF%E1%84%85%E1%85%B5%E1%86%B7%20%E1%84%80%E1%85%AE%E1%84%92%E1%85%A7%E1%86%AB%20585e56f3c755424dbbbbee8e5edfab8b/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-10-23_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_6.03.37.png)

그대로 복붙

![스크린샷 2023-10-23 오후 6.03.52.png](%E1%84%8B%E1%85%A1%E1%86%AF%E1%84%85%E1%85%B5%E1%86%B7%20%E1%84%80%E1%85%AE%E1%84%92%E1%85%A7%E1%86%AB%20585e56f3c755424dbbbbee8e5edfab8b/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-10-23_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_6.03.52.png)

… 있는 부분은 이미 있는 함수의 return 아래에 넣으면 됨

```bash
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions
{
  if ([FIRApp defaultApp] == nil) {
    [FIRApp configure];
  }
  
  self.moduleName = @"tinqle";
  // You can add your custom initial props in the dictionary below.
  // They will be passed down to the ViewController used by React Native.
  self.initialProps = @{};

  return [super application:application didFinishLaunchingWithOptions:launchOptions];
  
  //for notification
  UNUserNotificationCenter *center = [UNUserNotificationCenter currentNotificationCenter];
  center.delegate = self;

  return YES;
}
```

[https://www.npmjs.com/package/react-native-push-notification](https://www.npmjs.com/package/react-native-push-notification)

위에 두줄만 디폴트로 하면 됨

![스크린샷 2023-10-23 오후 6.18.03.png](%E1%84%8B%E1%85%A1%E1%86%AF%E1%84%85%E1%85%B5%E1%86%B7%20%E1%84%80%E1%85%AE%E1%84%92%E1%85%A7%E1%86%AB%20585e56f3c755424dbbbbee8e5edfab8b/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-10-23_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_6.18.03.png)

오류 뜨는 부분 자동으로 고치는 방식으로 해결 - 아래 color 먼저 해야함

![스크린샷 2023-10-23 오후 6.35.03.png](%E1%84%8B%E1%85%A1%E1%86%AF%E1%84%85%E1%85%B5%E1%86%B7%20%E1%84%80%E1%85%AE%E1%84%92%E1%85%A7%E1%86%AB%20585e56f3c755424dbbbbee8e5edfab8b/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-10-23_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_6.35.03.png)

```xml
<manifest xmlns:android="http://schemas.android.com/apk/res/android">

  <uses-permission android:name="android.permission.VIBRATE" />
  <uses-permission android:name="android.permission.RECEIVE_BOOT_COMPLETED"/>

  <uses-permission android:name="android.permission.INTERNET" />
  <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
  <!-- 카메라 권한 -->
  <uses-permission android:name="android.permission.CAMERA" />
  <!-- 저장소 읽기 권한 -->
  <uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
  <!-- 전화번호부 읽기 권한 -->
  <uses-permission android:name="android.permission.READ_CONTACTS" />
  <!-- 저장소 쓰기 권한 -->
  <application android:name=".MainApplication" android:label="@string/app_name" android:icon="@mipmap/ic_launcher" android:roundIcon="@mipmap/ic_launcher_round" android:allowBackup="false" android:theme="@style/AppTheme">
    
    <!-- Change the value to true to enable pop-up for in foreground on receiving remote notifications (for prevent duplicating while showing local notifications set this to false) -->
    <meta-data  android:name="com.dieam.reactnativepushnotification.notification_foreground"
        android:value="false"/>
    <!-- Change the resource name to your App's accent color - or any other color you want -->
    <meta-data  android:name="com.dieam.reactnativepushnotification.notification_color"
        android:resource="@color/white"/> <!-- or @android:color/{name} to use a standard color -->

    <receiver android:name="com.dieam.reactnativepushnotification.modules.RNPushNotificationActions" />
    <receiver android:name="com.dieam.reactnativepushnotification.modules.RNPushNotificationPublisher" />
    <receiver android:name="com.dieam.reactnativepushnotification.modules.RNPushNotificationBootEventReceiver"
        android:exported="true">
      <intent-filter>
        <action android:name="android.intent.action.BOOT_COMPLETED" />
        <action android:name="android.intent.action.QUICKBOOT_POWERON" />
        <action android:name="com.htc.intent.action.QUICKBOOT_POWERON"/>
      </intent-filter>
    </receiver>

    <service
        android:name="com.dieam.reactnativepushnotification.modules.RNPushNotificationListenerService"
        android:exported="false" >
      <intent-filter>
        <action android:name="com.google.firebase.MESSAGING_EVENT" />
      </intent-filter>
    </service>
    
    <activity android:name=".MainActivity" android:label="@string/app_name" android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|screenSize|smallestScreenSize|uiMode" android:launchMode="singleTask" android:windowSoftInputMode="adjustResize" android:exported="true">
      <intent-filter>
        <action android:name="android.intent.action.MAIN" />
        <category android:name="android.intent.category.LAUNCHER" />
      </intent-filter>
      <!-- dynamic links 관련설정 23.10.24 -->
      <intent-filter>
        <action android:name="android.intent.action.VIEW"/>
        <category android:name="android.intent.category.DEFAULT"/>
        <category android:name="android.intent.category.BROWSABLE"/>
        <data android:host="tikkle.lifoli.co.kr" android:scheme="https"/>
      </intent-filter>
      
      <!-- deep link 관련설정 23.10.16 -->
      <intent-filter>
        <action android:name="android.intent.action.VIEW" />
        <category android:name="android.intent.category.DEFAULT" />
        <category android:name="android.intent.category.BROWSABLE" />
        <data android:scheme="tikkle" />
      </intent-filter>

    </activity>
  </application>
</manifest>
```

버전 수정 이미 되어 있음

![스크린샷 2023-10-23 오후 6.45.04.png](%E1%84%8B%E1%85%A1%E1%86%AF%E1%84%85%E1%85%B5%E1%86%B7%20%E1%84%80%E1%85%AE%E1%84%92%E1%85%A7%E1%86%AB%20585e56f3c755424dbbbbee8e5edfab8b/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-10-23_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_6.45.04.png)

둘다 되어 있는 상태 

![스크린샷 2023-10-23 오후 6.46.15.png](%E1%84%8B%E1%85%A1%E1%86%AF%E1%84%85%E1%85%B5%E1%86%B7%20%E1%84%80%E1%85%AE%E1%84%92%E1%85%A7%E1%86%AB%20585e56f3c755424dbbbbee8e5edfab8b/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-10-23_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_6.46.15.png)

추가 (주석 해제)

![스크린샷 2023-10-23 오후 6.47.51.png](%E1%84%8B%E1%85%A1%E1%86%AF%E1%84%85%E1%85%B5%E1%86%B7%20%E1%84%80%E1%85%AE%E1%84%92%E1%85%A7%E1%86%AB%20585e56f3c755424dbbbbee8e5edfab8b/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-10-23_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_6.47.51.png)

android는 설정이 끝남

[https://honeystorage.tistory.com/255](https://honeystorage.tistory.com/255)

IOS 설정

![스크린샷 2023-10-24 오전 11.02.58.png](%E1%84%8B%E1%85%A1%E1%86%AF%E1%84%85%E1%85%B5%E1%86%B7%20%E1%84%80%E1%85%AE%E1%84%92%E1%85%A7%E1%86%AB%20585e56f3c755424dbbbbee8e5edfab8b/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-10-24_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%258C%25E1%2585%25A5%25E1%2586%25AB_11.02.58.png)

![스크린샷 2023-10-24 오전 11.10.32.png](%E1%84%8B%E1%85%A1%E1%86%AF%E1%84%85%E1%85%B5%E1%86%B7%20%E1%84%80%E1%85%AE%E1%84%92%E1%85%A7%E1%86%AB%20585e56f3c755424dbbbbee8e5edfab8b/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-10-24_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%258C%25E1%2585%25A5%25E1%2586%25AB_11.10.32.png)

![스크린샷 2023-10-24 오후 12.11.25.png](%E1%84%8B%E1%85%A1%E1%86%AF%E1%84%85%E1%85%B5%E1%86%B7%20%E1%84%80%E1%85%AE%E1%84%92%E1%85%A7%E1%86%AB%20585e56f3c755424dbbbbee8e5edfab8b/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-10-24_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_12.11.25.png)

디바이스 일단 내꺼 등록함

![스크린샷 2023-10-24 오후 12.25.44.png](%E1%84%8B%E1%85%A1%E1%86%AF%E1%84%85%E1%85%B5%E1%86%B7%20%E1%84%80%E1%85%AE%E1%84%92%E1%85%A7%E1%86%AB%20585e56f3c755424dbbbbee8e5edfab8b/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-10-24_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_12.25.44.png)

![스크린샷 2023-10-24 오후 12.28.18.png](%E1%84%8B%E1%85%A1%E1%86%AF%E1%84%85%E1%85%B5%E1%86%B7%20%E1%84%80%E1%85%AE%E1%84%92%E1%85%A7%E1%86%AB%20585e56f3c755424dbbbbee8e5edfab8b/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-10-24_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_12.28.18.png)

마지막 firebase.json 은 추가 x

설정 완료

podfile

```bash
# delete for react-native-permissions 12/30 sj
# # Resolve react_native_pods.rb with node to allow for hoisting
# require Pod::Executable.execute_command('node', ['-p',
#   'require.resolve(
#     "react-native/scripts/react_native_pods.rb",
#     {paths: [process.argv[1]]},
#   )', __dir__]).strip

# add for react-native-permissions 12/30 sj
def node_require(script)
   # Resolve script with node to allow for hoisting
require Pod::Executable.execute_command('node', ['-p',
  "require.resolve(
    '#{script}',
    {paths: [process.argv[1]]},
  )", __dir__]).strip
end

node_require('react-native/scripts/react_native_pods.rb')
node_require('react-native-permissions/scripts/setup.rb')

platform :ios, min_ios_version_supported
prepare_react_native_project!

# add for react-native-permissions 12/30 sj
# ⬇️ uncomment wanted permissions
setup_permissions([
  # 'AppTrackingTransparency',
  # 'Bluetooth',
  # 'Calendars',
  # 'CalendarsWriteOnly',
  'Camera',
  # 'Contacts',
  # 'FaceID',
  # 'LocationAccuracy',
  # 'LocationAlways',
  # 'LocationWhenInUse',
  # 'MediaLibrary',
  # 'Microphone',
  # 'Motion',
  'Notifications',
  'PhotoLibrary',
  # 'PhotoLibraryAddOnly',
  # 'Reminders',
  # 'Siri',
  # 'SpeechRecognition',
  # 'StoreKit',
])

#firebase 연동 관련 설정 23.10.24
# $RNFirebaseAsStaticFramework = true
# use_frameworks! :linkage => :static
flipper_config = ENV['NO_FLIPPER'] == "1" ? FlipperConfiguration.disabled : FlipperConfiguration.enabled

linkage = ENV['USE_FRAMEWORKS']
if linkage != nil
  Pod::UI.puts "Configuring Pod with #{linkage}ally linked Frameworks".green
  use_frameworks! :linkage => linkage.to_sym
end
# If you are using a `react-native-flipper` your iOS build will fail when `NO_FLIPPER=1` is set.
# because `react-native-flipper` depends on (FlipperKit,...) that will be excluded
#
# To fix this you can also exclude `react-native-flipper` using a `react-native.config.js`
# ```js
# module.exports = {
#   dependencies: {
#     ...(process.env.NO_FLIPPER ? { 'react-native-flipper': { platforms: { ios: null } } } : {}),
# ```

target 'tinqle' do
  config = use_native_modules!
    
  pod 'Firebase', :modular_headers => true
  pod 'FirebaseCoreInternal', :modular_headers => true
  pod 'FirebaseCore', :modular_headers => true
  pod 'FirebaseMessaging', :modular_headers => true
  pod 'GoogleUtilities', :modular_headers => true
  
  # Flags change depending on the env values.
  flags = get_default_flags()

  use_react_native!(
    :path => config[:reactNativePath],
    # Hermes is now enabled by default. Disable by setting this flag to false.
    :hermes_enabled => flags[:hermes_enabled],
    :fabric_enabled => flags[:fabric_enabled],
    # Enables Flipper.
    #
    # Note that if you have use_frameworks! enabled, Flipper will not work and
    # you should disable the next line.
    :flipper_configuration => flipper_config,
    # An absolute path to your application root.
    :app_path => "#{Pod::Config.instance.installation_root}/.."
  )

  target 'tinqleTests' do
    inherit! :complete
    # Pods for testing
  end

  post_install do |installer|
    # https://github.com/facebook/react-native/blob/main/packages/react-native/scripts/react_native_pods.rb#L197-L202
    react_native_post_install(
      installer,
      config[:reactNativePath],
      :mac_catalyst_enabled => false
    )
    __apply_Xcode_12_5_M1_post_install_workaround(installer)
  end
end
```

Flipper와 message 설정과의 충돌로 설정 가이드와는 다르게 코딩함

## ios 앱 내 알림 설정