# BaseAuth
Easily set up phone authentication leveraging on different auth platforms (like firebase, sinch and many more to be added) of your choice. With a simple User Interface that can be styled to blend with the theme of your app, you can focus more on other functional requirement of the app other than the authentication process

 [ ![base-fireauth](https://api.bintray.com/packages/kingsmentor/maven/BaseAuth/images/download.svg) ](https://bintray.com/kingsmentor/maven/BaseAuth/_latestVersion)

### Current Support

```gradle
compile 'xyz.belvi.auth:baseauth-firebase:1.0.5'
compile 'xyz.belvi.auth:baseauth-sinch:1.0.5'
compile 'xyz.belvi.auth:baseauth-nexmo:1.0.5'
```

## Sample

<img src="https://github.com/KingsMentor/BaseAuth/blob/master/sample/base_auth_sample.gif"  width="200" height="400" />

## Adding as a dependency

add `jcenter({url "http://dl.bintray.com/kingsmentor/maven"})` to your project / root build.gradle like so:

```gradle
...
allprojects {
    repositories {
        jcenter({url "http://dl.bintray.com/kingsmentor/maven"})
    }
}
...
```

#### Core
*Not Available in 1.0.5*

core provides access to other underlying auth platform. Only use core if you intend to perform phone number authetication using multiple auth providers.
```gradle
dependencies {
    compile 'xyz.belvi.auth:baseauth-core:1.0.3'
}
```

#### Firebase

This module handles phone number authentication using firebase. 
```gradle
dependencies {
    compile 'xyz.belvi.auth:baseauth-firebase:1.0.5'
}
```

#### Sinch

This module handles phone number authentication using sinch. 


```gradle
dependencies {
    compile 'xyz.belvi.auth:baseauth-sinch:1.0.5'
}
```
## Using the Library:

#### As Firebase :

```java
        FireAuthActivity.startFirebasePhoneAuth(this, new FirebaseAuthListener() {
            @Override
            public void authIgnored() {
                // user existed without autheticating
            }

            @Override
            public void helpClicked(Context context) {
                // Help icon is cliced. You might want to do something here.

            }

            @Override
            public void onAuthCompleted(PhoneAuthCredential credential, String phoneNumber) {
                // do something with Firebase PhoneAuthCredential and the autheticated phone number
            }
        }, R.style.BaseAuthStyle);
```
#### As Sinch :

```java
SinchAuthActivity.startSinchAuth(this, new SinchAuthListener() {
            public void onAuthCompleted(String phoneNumber) {

            }

            public void authIgnored() {

            }

            public void helpClicked(Context activity) {

            }
        }, "API_KEY", R.style.BaseAuthStyle);
 ```
 
 #### As Nemo :
 
 ```java
         NexmoAuthActivity.startNexmoAuth(this, new NexmoAuthListener() {
            public void onAuthCompleted(String phoneNumber) {
                Toast.makeText(MainActivity.this, phoneNumber, Toast.LENGTH_LONG).show();
            }

            public void authIgnored() {

            }

            public void helpClicked(Context activity) {

            }
        }, new NexmoAuth("YOUR_API_ID", "YOUR_SHARED_SECRET", PIN_LENGTH), R.style.BaseAuthStyle);
```

#### Styling and Theming 

define style in styles.xml

```xml
    <style name="BaseAuthStyle">
        <item name="ba_show_help">true</item>
    </style>
```

`ba_show_help` determines if the help icon will be shown or not.

layout resources are referenced in corresponding resource xml files.<br/>
you can override any of the resource to suit your need.

##### color.xml

```xml
<resources>
    <color name="ba_colorPrimary">#42a5f5</color>
    <color name="ba_colorPrimaryDark">#253493</color>
    <color name="ba_colorAccent">#FF4081</color>
    <color name="ba_txt_error">#FF4081</color>
    <color name="ba_blue">#42a5f5</color>
    <color name="ba_background">#fcfcfc</color>
    <color name="ba_btn_disabled">#dfdfdf</color>
    <color name="ba_btn_enabled">#ffffff</color>
    <color name="ba_txt_grey">#696969</color>
    <color name="ba_auth_code">#42a5f5</color>
    <color name="ba_white">#FFFFFF</color>
    <color name="ba_country_selector_code_color">#787878</color>
    <color name="ba_country_selector_bg_color">#FFFFFF</color>
    <color name="ba_country_selector_name_color">#000000</color>
</resources>

```

##### strings.xml

```
<resources>
    <string name="app_name">BaseAuth</string>
    <string name="help">Help</string>
    <string name="select_country">Select your country</string>
    <string name="type_in">Please type in the verification code sent to %s</string>
    <string name="verify_number">Verify your number</string>
    <string name="phone_hint">Your phone number</string>
    <string name="cc_hint">Your country code</string>
    <string name="btn_next_title">Next</string>
    <string name="verification_code">Verification Code</string>
    <string name="received_question">Didn\'t receive  code ?</string>
    <string name="wait_field">Please wait</string>
    <string name="help_link">http://www.example.com</string>
    <string name="charges_desc">We will send you a one-off SMS message. Carrier charges may apply.</string>
    <string name="details_desc">Enter your country code and phone number for verification</string>
</resources>
```

##### dimens.xml

```xml
<resources>
    <dimen name="ba_layout_padding">32dp</dimen>
    <dimen name="verification_code_text_size">24sp</dimen>
    <dimen name="vc_txt_size">18sp</dimen>
    <dimen name="type_in_desc_txt_size">16sp</dimen>
    <dimen name="type_in_desc_margin_top">32dp</dimen>
    <dimen name="type_in_desc_margin_bottom">16dp</dimen>
    <dimen name="verification_layout_padding">32dp</dimen>
    <dimen name="verification_code_width">42dp</dimen>
    <dimen name="details_desc">16sp</dimen>
    <dimen name="details_margin_top">16dp</dimen>
    <dimen name="phone_field_text_size">18sp</dimen>
    <dimen name="next_btn_txt_size">14sp</dimen>
    <dimen name="next_btn_padding">16dp</dimen>
    <dimen name="wait_field_txt_size">16sp</dimen>
    <dimen name="wait_field_top_margin">8dp</dimen>
    <dimen name="receive_code_confirmation">14sp</dimen>
    <dimen name="receive_code_confirmation_top_margin">16dp</dimen>
    <dimen name="verification_status_text_size">12sp</dimen>
    <dimen name="verification_status_top_margin">16dp</dimen>
</resources>
```
