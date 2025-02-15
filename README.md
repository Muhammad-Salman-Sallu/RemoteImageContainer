# RemoteImageContainer

RemoteImageContainer loads the remote image and cache it for best user experience.

## Requirements
- Xcode 12.0 or later
- iOS 11.0 or later
- Swift 5.0 or later

## Installation
### Cocoapods
1. This framework is available through [CocoaPods](http://cocoapods.org). 
2. Include RemoteImageContainer in your `Pod File`:

```
pod 'RemoteImageContainer'
```
   
## Usage
### RemoteImageContainer
RemoteImageContainer provides a helper UIView to show any image. To get any image:

1. Import following in your desired swift file.

```swift
import RemoteImageContainer
```

2. Open your Storyboard or .XIB file, select your superview, drag a UIView and set it's Custom Class name to **RemoteImageContainer**.
3. Create and attach an outlet for our **RemoteImageContainer** view.

```swift
@IBOutlet weak var imageContainerView: RemoteImageContainer!
```

4. Use **setImage** method of **RemoteImageContainer** class to set details of image to be downloaded.

```swift
imageContainerView.setImage(url: URL, overLay: Bool, overLayWithOpacity: CGFloat)
```

- `url` URL of image.
- `overLay` To add black overLay above the image. By default, its value is false.
- `overLayWithOpacity` To set the opacity of black overLay. Bye default, its value is 0.4.

### Download Image/Audio
RemoteImageContainer provides a method for downloading media i.e. image, audio. To download any media:

1. Import following in your desired swift file.

```swift
import RemoteImageContainer
```

2. Send request for download using following method:
```swift
RRDownloadManager.shared().addDownloadOperation(url: URL) { (error) in
}
```

## Observers
### Subscribe
```swift
let observerClient = RRDownloadManager.shared().addObserver(observer: self)
```

After subscribing for observer, you can listen for following delegate functions:
```swift
extension ViewController: RRDownloadManagerObserver {
        
    func didFinishedDownload(url: URL) {
    }

}
```

### Unsubscribe
```swift
RRDownloadManager.shared().removeObserver(client: observerClient)
```
