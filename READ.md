# First install ( npm i react-native-splash-screen )
# add below code to android/settings.gradle
```gradle
      include ':react-native-splash-screen'   
      project(':react-native-splash-screen').projectDir = new File(rootProject.projectDir, '../node_modules/react-native-splash-screen/android')
```
# add below code to android/app/build.gradle
             implementation project(':react-native-splash-screen')
      
# now goto Mainactivity.java file Up date 
            import android.os.Bundle; // here
      import com.facebook.react.ReactActivity;
      // react-native-splash-screen >= 0.3.1
      import org.devio.rn.splashscreen.SplashScreen; // here
      // react-native-splash-screen < 0.3.1
      //import com.cboy.rn.splashscreen.SplashScreen; // here
      
      public class MainActivity extends ReactActivity {
         @Override//here
          protected void onCreate(Bundle savedInstanceState) { //here
              SplashScreen.show(this);  // here
              super.onCreate(savedInstanceState); //here
          }
    // ...other code
    }

# Create a file called launch_screen.xml in app/src/main/res/layout and paste that code
      <?xml version="1.0" encoding="utf-8"?>
        <RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
            android:orientation="vertical" android:layout_width="match_parent"
            android:layout_height="match_parent">
            <ImageView android:layout_width="match_parent" android:layout_height="match_parent" android:src="@drawable/launch_screen" android:scaleType="centerCrop" />
        </RelativeLayout>


# paste drawable files to ../main/res/

# goto App.tsx and add
      import SplashScreen from 'react-native-splash-screen';
       useEffect(() => {
    if (Platform.OS === 'android') SplashScreen.hide();
  }, [])
