# GCMSample
Sample application for communication via [Google Cloud Messaging (GCM)](https://developer.android.com/google/gcm/index.html)

Based on [this tutorial](http://hmkcode.com/android-google-cloud-messaging-tutorial/) but as an [Android Studio](http://developer.android.com/tools/studio/index.html) project.

## Setup
Follow the initial steps in the tutorial that lets you set up a project in the [Google Developer Console (GDC)](https://console.developers.google.com)).
Replace `PROJECT_NUMBER` [here](https://github.com/peralmq/GCMSample/blob/9b177554ac88f01be99f5f72cf7e35b2d83d6b69/app/src/main/java/com/peralmq/gcm/MainActivity.java#L22) with your project number (can be found in the GDC).
Don't run in an emulator, GCM requires a real Google Account when registring.

## Test
Run the app on your device and click the "Get RegId" button to recieve your `<registration_id>`. Then run the following command in your terminal but replace `<server_key>` with your server key (can be found in the GDC) and `<registration_id>`.
```
curl -i -H "Authorization: key=<server_key>" \
--header Content-Type:"application/json" \
https://android.googleapis.com/gcm/send \
-d "{\"registration_ids\":[\"<registration_id>\"], \"data\": {\"title\": \"Toastingly fresh\!\"}}"
```
After a short time the message "Toastingly fresh!" should appear as a toast in the app running on your device.

![](https://cloud.githubusercontent.com/assets/238536/5922923/b29795c6-a64f-11e4-8b94-8a86bcbd0728.png)
