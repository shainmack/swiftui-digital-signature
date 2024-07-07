This is a fork of [@Globulus'](https://github.com/globulus) repo that adds some additional params to set a default color and whether or not a color selector should appear
# SwiftUIDigitalSignature

**Plug'n' play Digital Signatures in SwiftUI**.

## Features

* Freeform signature drawing.
* Selecting signature image.
* Typing signature in oblique font.
* Choose signature color.
* Choose signature font.
* Callback produces `UIImage` that you can save/use.
* iOS 13+ compatible.

![Preview](https://github.com/globulus/swiftui-digital-signature/blob/main/Images/preview.gif?raw=true)

## Installation

This component is distributed as a **Swift package**. Just add the repo URL to your package list:

```text
https://github.com/shainmack/swiftui-digital-signature/
```

## Sample usage

```swift
import SignatureView

struct SignatureViewTest: View {
  @State private var image: UIImage? = nil
    
  var body: some View {
    NavigationView {
      VStack {
        NavigationLink("GO", destination: SignatureView(
          "Your signature here",
          availableTabs: [.draw, .image, .type],
          onSave: { image in
            self.image = image
          }, onCancel: {
                  
          }, color: .red, showColorOptions: true))
        if image != nil {
            Image(uiImage: image!)
        }
      }
    }
  }
}
```

## Parameters

| Parameter | Description                                                                                      |
| :----------------- | :-------------------------------------------------------------------------------------- |
| `placeholder`      | Closure that sets what to do when the cancel button is tapped. *Default = `Signature`*  |
| `onSave`           | Closure that sets what to do when the save button is tapped                             |
| `color`            | SwiftUI Color param for writing color (Color). *Default = `.black`*                     |
| `showColorOptions` | A boolean option to show the color picker (Bool). *Default = `false`*                   |

## Known Issues
* If using multiple `SignatureView`s on a single page, the `Done` button for either will trigger the `signatureCompleted` state on all of them.
* *Workaround:* use an `if` to conditionally show each one, only when the prior has been signed.

## Changelog

* 0.1.6 - added automatic locking states to the `Done` and `Clear` buttons
* 0.1.5 - hotfix
* 0.1.4 - Got rid of onCancel, moved clear button to top, made placeholder text a param
* 0.1.3 - Adds rounded corners, selectable writing color, and choice of showing or hiding color selector
* 0.1.2 - Added `availableTabs` initializer param.
* 0.1.1 - Fixed drawing bounds.
* 0.1.0 - Initial release.

Check out [SwiftUIRecipes.com](https://swiftuirecipes.com) for more SwiftUI solutions, tips and custom components!
