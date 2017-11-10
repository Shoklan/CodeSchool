# Try Android
## Sarah Holderness

## Level 1 [ Cooking Up An App]
- Android is a Mobile OS created by Google.
- *Android Studio* is the official IDE for building Android apps.
- It's free, obviously.
- The Android SDK has standard ways to display data in your app.
- Grandle that is what builds the APK file to run on Android.
- To create a new Emulator:
  1. Hit Play button.
  2. Select *Create New Virtual Device*.
  3. Select Phone.
  4. Download Phone Clone.
- Each screen in our app is called an *activity* and is controlled by a java file and a layout file.
- Activity files use *PascalCase* for naming convention.
- Layout files use *snake_case* for naming convention.
- A layout can contain text, images, buttons, and more.
- The Activity file is for handling events.
- To apply changes, you'd select the lighting bolt button at the top.
- **dp** stands for **Density-independent Pixels**.
- **sp** stands for **Scale-independent Pixels**.
- `wrap_content` means that the view will only be large enough to contain the content.
- You should not use hard coded strings; you should use string values.
- To set this, navigate to res **>** values **>** strings.xml.
- The format looks like:
```
<resources>
  <string name = "variable_name">String Literal Name</string>
</resources>
```
- Then to use your new resource, change it to `@string/variable_name`.

## Level 2 [ Layouts, Views & Images ]

## Level 3 [ListView & Adapters ]

## Level 4 [ EventListeners & Toasts ]
