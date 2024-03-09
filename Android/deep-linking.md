
# Deep Linking

https://developer.android.com/training/app-links/deep-linking

Can be used to intercept links to specific url, and open it in app.
This is how we can have a user open a url from their email, and have our app open to some activity with some data.

```xml
<activity
    android:name="com.example.android.GizmosActivity"
    android:label="@string/title_gizmos" >
    <intent-filter android:label="@string/filter_view_http_gizmos">
        <action android:name="android.intent.action.VIEW" />
        <category android:name="android.intent.category.DEFAULT" />
        <category android:name="android.intent.category.BROWSABLE" />
        <!-- Accepts URIs that begin with "http://www.example.com/gizmos” -->
        <data android:scheme="http"
              android:host="www.example.com"
              android:pathPrefix="/gizmos" />
        <!-- note that the leading "/" is required for pathPrefix-->
    </intent-filter>
    <intent-filter android:label="@string/filter_view_example_gizmos">
        <action android:name="android.intent.action.VIEW" />
        <category android:name="android.intent.category.DEFAULT" />
        <category android:name="android.intent.category.BROWSABLE" />
        <!-- Accepts URIs that begin with "example://gizmos” -->
        <data android:scheme="example"
              android:host="gizmos" />
    </intent-filter>
</activity>
```


## Discovery

https://developer.android.com/training/app-links/verify-android-applinks
I can find out what type of deep linking is supported by a website by appending one of these after their domain.
- `.well-known/assetlinks.json`
- `assetlinks.json`

https://www.youtube.com/.well-known/assetlinks.json
```json
[{
  "relation": ["delegate_permission/common.handle_all_urls"],
  "target": {
    "namespace": "android_app",
    "package_name": "com.google.android.youtube",
    "sha256_cert_fingerprints": [
      "3D:7A:12:23:01:9A:A3:9D:9E:A0:E3:43:6A:B7:C0:89:6B:FB:4F:B6:79:F4:DE:5F:E7:C2:3F:32:6C:8F:99:4A",
      "7F:D2:CE:A3:0C:3A:60:22:EB:29:41:9C:E8:F6:F9:2C:E8:A4:BD:35:B0:CC:87:9E:D3:CC:A6:CB:F5:E9:99:2D"]
  }
},
{
  "relation": ["delegate_permission/common.handle_all_urls"],
  "target": {
    "namespace": "android_app",
    "package_name": "com.google.android.youtube.tv",
    "sha256_cert_fingerprints": [
      "21:19:9D:11:2C:EC:E4:28:C8:2C:B0:DF:22:1D:A2:4F:F8:67:4C:7A:98:2A:83:A1:7A:97:0E:EC:43:30:5B:4A"]
  }
},
{
  "relation": ["delegate_permission/common.handle_all_urls"],
  "target": {
    "namespace": "android_app",
    "package_name": "com.google.android.apps.automotive.youtube",
    "sha256_cert_fingerprints": [
      "AA:AB:5F:1B:60:B7:5C:78:BC:42:56:7F:CA:48:1A:A4:AE:10:01:6C:35:D3:C5:B0:C1:37:3B:64:79:B8:CD:74"]
  }
},
{
  "relation": ["delegate_permission/common.handle_all_urls"],
  "target": {
    "namespace": "android_app",
    "package_name": "com.automotive.test.youtube",
    "sha256_cert_fingerprints": [
      "C1:8C:33:5D:D8:1F:33:36:72:7B:5D:1A:1F:69:F0:A2:D0:D8:F9:3A:42:6A:08:2A:56:58:0F:04:87:D7:5C:A5"]
  }
}]
```

## Related

- [Universal Links](../iOS/universal-links.md#Universal%20Links) for iOS
- [Deep Link into Android App](../adb/deep-link-into-android-app.md#Deep%20Link%20into%20Android%20App): this does not require us to have a domain with `.well-known`