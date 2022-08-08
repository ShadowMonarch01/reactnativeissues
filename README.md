# reactnativeissues
some of the solutions to certain react native errors

For creating react native or expo project

npx react-native init ChatPro ===> reac-native cli
npx react-native init ChatPro --version 0.68.2
expo init project_name

navigation 5

npm install @react-navigation/native@^5.x

npm install react-native-reanimated react-native-gesture-handler react-native-screens react-native-safe-area-context @react-native-community/masked-view

npm install react-native-reanimated@2.8.0 react-native-gesture-handler@2.2.1 react-native-screens@3.11.1 react-native-safe-area-context@4.2.4 @react-native-community/masked-view

npm install @react-navigation/native@^5.x @react-navigation/stack@^5.x @react-navigation/bottom-tabs@^5.x @react-navigation/drawer@^5.x react-native-vector-icons

EXTRA PACKAGES USED FOR SOME PROJECTS

npm install react-native-document-picker@7.1.1 react-native-fetch-blob@0.10.8 react-native-loading-spinner-overlay react-native-linear-gradient@2.5.6



Fix React native cli icons not showing
//////////////////////////
android/app/build.gradle

apply from: "../../node_modules/react-native-vector-icons/fonts.gradle"
///////////////////////

//////////////////////
android/settings.gradle

rootProject.name = 'MyApp'

include ':app'

// Add these two lines
include ':react-native-vector-icons'
project(':react-native-vector-icons').projectDir = new File(rootProject.projectDir, '../node_modules/react-native-vector-icons/android')
////////////////////////


Resizing images to fit view
<Image
    source={item.img}
    resizeMode={'stretch'}
    style={{ height: 160,width:140, borderRadius: 5,margin:5,alignSelf:'center',aspectRatio:1}}
    />
OTHER RESIZE MODES: contain, cover, repeat, center


#000000 #171717 #2E2E2E #454545


React-Native-Fetch-Blob SETUP
1) install the package
2) go to node_modules/package_name/android/build.gradle

compare
compileSdkVersion 31
    buildToolsVersion "31.0.0"
    defaultConfig {
        minSdkVersion 21
        targetSdkVersion 31
        versionCode 1
        versionName "1.0"
    }

with android/build.gradle and make the necessary changes

3) change
dependencies {
    compile'com.facebook.react:react-native:+'
    //{RNFetchBlob_PRE_0.28_DEPDENDENCY}
}

in node_modules/package_name/android/build.gradle to

dependencies {
    implementation 'com.facebook.react:react-native:+'
    //{RNFetchBlob_PRE_0.28_DEPDENDENCY}
}




REACT NATIVE VIDEO

android\app\build.gradle

implementation project(':react-native-video')


android\settings.gradle

include ':react-native-video'
project(':react-native-video').projectDir = new File(rootProject.projectDir, '../node_modules/react-native-video/android')

android\build.gradle

jcenter(){
            content{
                includeModule("com.yqritc", "android-scalablevideoview")
            }
        }


MainApplication.java

import com.brentvatne.react.ReactVideoPackage;

packages.add(new ReactVideoPackage());


For RNFetchBlob to convert to base64

AndroidManifest.xml

<application
  ...
  android:requestLegacyExternalStorage="true">

