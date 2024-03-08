chat_package
Pub Version likes popularity <a href="https://github.com/priyanshu-singh/chat_package" target="_blank">
</a> Pub

This package offers a user-friendly chat UI for your Flutter projects, featuring audio recording and image sending capabilities. It's highly customizable to meet your project requirements.

Developed by Priyanshu Singh
<a href="https://github.com/priyanshu-singh">GitHub</a> <a href="#"> LinkedIn</a> <a href="mailto:your-email@gmail.com"><img src="https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white"></a>

Screenshots
<img src="https://raw.githubusercontent.com/priyanshu-singh/chat_package/main/screenShots/home_screen.png" height="400em"> <img src="https://raw.githubusercontent.com/priyanshu-singh/chat_package/main/screenShots/recording.png" height="400em"> <img src="https://raw.githubusercontent.com/priyanshu-singh/chat_package/main/screenShots/bottom_sheet.png" height="400em"> <img src="https://raw.githubusercontent.com/priyanshu-singh/chat_package/main/screenShots/permission.png" height="400em">

Coming Soon
The next update of this package will add support for recording videos, adding captions to captured or stored images, and many more features.

Usage
Permission Setup
Simply add permissions to your project, and the package will handle the rest. The following permissions are required:

camera
microphone
local storage
Android
Add the following to your "gradle.properties" file:
properties
Copy code
android.useAndroidX=true
android.enableJetifier=true
Set the compileSdkVersion in your "android/app/build.gradle" file to 21 for recording feature:
gradle
Copy code
android {
  compileSdkVersion 21
  ...
}
Replace all android. dependencies with their AndroidX counterparts.
Add permissions to your AndroidManifest.xml file:

xml
Copy code
<uses-permission android:name="android.permission.INTERNET"/>
<uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE"/>
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>
<uses-permission android:name="android.permission.CAMERA"/>
<uses-permission android:name="android.permission.RECORD_AUDIO" />
iOS
Add the following to your "Info.plist" file:

xml
Copy code
<key>NSCameraUsageDescription</key>
<string>camera</string>
<key>NSMicrophoneUsageDescription</key>
<string>microphone</string>
<key>NSPhotoLibraryUsageDescription</key>
<string>photos</string>
Also, add the following to your Podfile:

ruby
Copy code
target.build_configurations.each do |config|
    config.build_settings['GCC_PREPROCESSOR_DEFINITIONS'] ||= [
        '$(inherited)',
        'PERMISSION_CAMERA=1',
        'PERMISSION_MICROPHONE=1',
        'PERMISSION_PHOTOS=1',
    ]
end
Calling
Simply call the ChatScreen widget:

dart
Copy code
ChatScreen(
  scrollController: scrollController,
  messages: messages,
  onSlideToCancelRecord: () {
    log('not sent');
  },
  onTextSubmit: (textMessage) {
    setState(() {
      messages.add(textMessage);
      scrollController
          .jumpTo(scrollController.position.maxScrollExtent + 50);
    });
  },
  handleRecord: (audioMessage, canceled) {
    if (!canceled) {
      setState(() {
        messages.add(audioMessage!);
        scrollController
            .jumpTo(scrollController.position.maxScrollExtent + 90);
      });
    }
  },
  handleImageSelect: (imageMessage) async {
    if (imageMessage != null) {
      setState(() {
        messages.add(imageMessage);
        scrollController
            .jumpTo(scrollController.position.maxScrollExtent + 300);
      });
    }
  },
)
Properties
You can customize almost everything in this package using the following properties:

dart
Copy code
// Customizable properties
final Color? senderColor;
final Color? inActiveAudioSliderColor;
final Color? activeAudioSliderColor;
final ScrollController scrollController;
final Color chatInputFieldColor;
final String sendMessageHintText;
final String imageAttachmentFromGalleryText;
final Icon? imageAttachmentFromGalleryIcon;
final String imageAttachmentFromCameraText;
final Icon? imageAttachmentFromCameraIcon;
final String imageAttachmentCancelText;
final Icon? imageAttachmentCancelIcon;
final TextStyle? imageAttachmentTextStyle;
final String recordingNoteHintText;
final Function(ChatMessage textMessage) onTextSubmit;
final List<ChatMessage> messages;
final Function(ChatMessage? audioMessage, bool canceled) handleRecord;
final Function(ChatMessage? imageMessage) handleImageSelect;
final VoidCallback? onSlideToCancelRecord;
final TextEditingController? textEditingController;
final BoxDecoration? chatInputFieldDecoration;
final bool disableInput;
final EdgeInsets? chatInputFieldPadding;
final TextStyle? messageContainerTextStyle;
final TextStyle? sendDateTextStyle;
final Function(BuildContext context)? attachmentClick;
Found this project useful?
If you found this project useful, please consider giving it a ⭐️ on Github and share it with your friends.

Issues and Feedback
Feel free to open a Github issue to give any suggestions or feedback.