Directions
---
This is a step-by-step guide of adding a share-to-Facebook-Messenger functionality into PhotoGallery.

Step 1)
---
Go to to the [Facebook Developer portal](https://developers.facebook.com/quickstarts/?platform=android) and create a new Android project.

Step 2) Add App Id to Strings.xml
---
`<string name="facebook_app_id">529545513865826</string>`

Step 3) Add App Id to AndroidManifest.xml
---
<code>

    ...

    <application
        android:icon="@drawable/ic_launcher"
        android:label="@string/app_name"
        android:theme="@style/AppTheme">

        <meta-data
            android:name="com.facebook.sdk.ApplicationId"
            android:value="@string/facebook_app_id"/>

            ...

<code>

Step 4) Add Facebook SDK Dependency
---
`compile 'com.facebook.android:facebook-android-sdk:4.0.0'`

Step 5) Add New Permission to AndroidManifest.xml
---
`<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>`

Step 6) Add Share Functionality
---
<code>

    Drawable mDrawable = mImageView.getDrawable();
    Bitmap mBitmap = ((BitmapDrawable) mDrawable).getBitmap();
    String path = MediaStore.Images.Media.insertImage(getActivity().getContentResolver(), mBitmap, "Image Description", null);
    Uri uri = Uri.parse(path);

    ShareToMessengerParams shareToMessengerParams = ShareToMessengerParams.newBuilder(
                    uri,
                    "image/*"
    ).build();

    MessengerUtils.shareToMessenger(getActivity(), REQUEST_CODE_SHARE_TO_MESSENGER, shareToMessengerParams);
<code>
