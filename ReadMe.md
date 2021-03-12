# About This

This is a sample project to demonstrate a build error that appears when using Stripe-iOS in Xcode 12.5. This was mostl recently tested in beta 3.

## To Reproduce

1. Create a new project in Xcode **12.4**. (File > New > Project…)
2. Select the basic iOS "App" template.
3. Create the project.
4. Add Stripe as a Swift Package.
5. In AppDelegate.swift, `import Stripe`
6. In the project's Build Settings, set "Treat Warnings as Errors" to "Yes"
7. Build the app. The app should build successfully.
8. Close Xcode, then open this project in Xcode **12.5**.
9. Build the app.
10. You may need to clean the build (Product > Clean Build Folder) between builds when toggling the warnings setting to see these results.

## Results

With "Treat Warnings as Errors" set to "Yes", the project will fail to build in Xcode 12.5, due to the following errors:

```
.../stripe-ios/Stripe3DS2/Stripe3DS2/include/Stripe3DS2.h:53:1: error: umbrella header for module 'Stripe3DS2' does not include header 'STDSDeviceInformationParameter.h'
.../stripe-ios/Stripe3DS2/Stripe3DS2/include/Stripe3DS2.h:53:1: error: umbrella header for module 'Stripe3DS2' does not include header 'NSString+EmptyChecking.h'
.../stripe-ios/Stripe3DS2/Stripe3DS2/include/Stripe3DS2.h:53:1: error: umbrella header for module 'Stripe3DS2' does not include header 'STDSTransaction+Private.h'
.../stripe-ios/Stripe3DS2/Stripe3DS2/include/Stripe3DS2.h:53:1: error: umbrella header for module 'Stripe3DS2' does not include header 'STDSBrandingView.h'
.../stripe-ios/Stripe3DS2/Stripe3DS2/include/Stripe3DS2.h:53:1: error: umbrella header for module 'Stripe3DS2' does not include header 'STDSChallengeResponseMessageExtension.h'
.../stripe-ios/Stripe3DS2/Stripe3DS2/include/Stripe3DS2.h:53:1: error: umbrella header for module 'Stripe3DS2' does not include header 'STDSDeviceInformationManager.h'
.../stripe-ios/Stripe3DS2/Stripe3DS2/include/Stripe3DS2.h:53:1: error: umbrella header for module 'Stripe3DS2' does not include header 'STDSDirectoryServerCertificate.h'
.../stripe-ios/Stripe3DS2/Stripe3DS2/include/Stripe3DS2.h:53:1: error: umbrella header for module 'Stripe3DS2' does not include header 'STDSImageLoader.h'
.../stripe-ios/Stripe3DS2/Stripe3DS2/include/Stripe3DS2.h:53:1: error: umbrella header for module 'Stripe3DS2' does not include header 'STDSACSNetworkingManager.h'
.../stripe-ios/Stripe3DS2/Stripe3DS2/include/Stripe3DS2.h:53:1: error: umbrella header for module 'Stripe3DS2' does not include header 'STDSDebuggerChecker.h'
.../stripe-ios/Stripe3DS2/Stripe3DS2/include/Stripe3DS2.h:53:1: error: umbrella header for module 'Stripe3DS2' does not include header 'STDSSelectionButton.h'
.../stripe-ios/Stripe3DS2/Stripe3DS2/include/Stripe3DS2.h:53:1: error: umbrella header for module 'Stripe3DS2' does not include header 'STDSChallengeResponseSelectionInfo.h'
.../stripe-ios/Stripe3DS2/Stripe3DS2/include/Stripe3DS2.h:53:1: error: umbrella header for module 'Stripe3DS2' does not include header 'Stripe3DS2-Bridging-Header.h'
.../stripe-ios/Stripe3DS2/Stripe3DS2/include/Stripe3DS2.h:53:1: error: umbrella header for module 'Stripe3DS2' does not include header 'STDSBundleLocator.h'
.../stripe-ios/Stripe3DS2/Stripe3DS2/include/Stripe3DS2.h:53:1: error: umbrella header for module 'Stripe3DS2' does not include header 'STDSSpacerView.h'
.../stripe-ios/Stripe3DS2/Stripe3DS2/include/Stripe3DS2.h:53:1: error: umbrella header for module 'Stripe3DS2' does not include header 'STDSThreeDSProtocolVersion+Private.h'
.../stripe-ios/Stripe3DS2/Stripe3DS2/include/Stripe3DS2.h:53:1: error: umbrella header for module 'Stripe3DS2' does not include header 'STDSChallengeRequestParameters.h'
.../stripe-ios/Stripe3DS2/Stripe3DS2/include/Stripe3DS2.h:53:1: error: umbrella header for module 'Stripe3DS2' does not include header 'STDSWebView.h'
```

These warnings do not appear in Xcode 12.4, but will break the build in 12.5 if a project has "Treat Warnings as Errors" to "Yes".

