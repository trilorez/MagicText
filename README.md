# Magic Text
This package provides `UIKit` and `SwiftUI` wrappers around a WebView presenting a [magic 8-ball web app](https://ycsoah4bfq.appflowapp.com/chat).

## Getting Started
To use `MagicText` in your own project, you need to set it up as a package dependency to your `Package.swift` file:
```swift
// swift-tools-version:5.10
import PackageDescription

let package = Package(
  name: "MyPackage",
  dependencies: [
    .package(
      url: "https://github.com/trilorez/MagicText.git",
      .upToNextMajor(from: "1.0.0")
    )
  ],
  targets: [
    .target(
      name: "MyTarget",
      dependencies: [
        .product(name: "MagicText", package: "MagicText")
      ]
    )
  ]
)
```

Or add this package [using Xcode](https://developer.apple.com/documentation/xcode/adding-package-dependencies-to-your-app).

## Compatibility
This package relies on `WKWebView` and requires `iOS 8` or later. `SwiftUI` support requires `iOS 13` or later.

## Usage

### UIKit
`MagicTextView` is a `UIView` subclass. Call it's `refresh` function to load the web app. You can be notified about state updates (loading, loaded, and failure) by setting the `onStateChange` callback.

### SwiftUI
`MagicText` is a `View`. Pass a `shouldRefresh` binding to its initializer to indicate when the web app should load its content. Pass an `onStateChange` callback to its initializer to react to state updates.

## Caching
If loading the web app fails, the library will automatically fall back to a cached version if it is available.