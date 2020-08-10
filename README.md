# CoreML-Models.
#### Models you can use them on iOS.

UGATIT_selfie2anime:[Google Drive Link](https://drive.google.com/file/d/1-2IJyaJJFnCm9UUt_2P4wHUJsr1qmRCk/view?usp=sharing)

AnimeGANv2_Hayao:[Google Drive Link](https://drive.google.com/file/d/1i_kwj41BxA1xZNu2B7yX2VVqNF66atMN/view?usp=sharing)

AnimeGANv2_Paprika:[Google Drive Link](https://drive.google.com/file/d/1wuoaVoI8-HOOQ1kUiZkVJ9GWnPbtPnWF/view?usp=sharing)


<img width="517" alt="スクリーンショット 2020-05-19 11 09 03" src="https://user-images.githubusercontent.com/23278992/85667417-881d7d00-b6f8-11ea-8d1c-0d66b2b72de9.png">

<img width="799" alt="スクリーンショット 2020-06-22 4 10 54" src="https://user-images.githubusercontent.com/23278992/85667453-91a6e500-b6f8-11ea-84bf-22853b0995dc.png">

How to use in a xcode project.

```swift:

import Vision
lazy var coreMLRequest:VNCoreMLRequest = {
   let model = try! VNCoreMLModel(for: ugatit().model)
   let request = VNCoreMLRequest(model: model, completionHandler: self.coreMLCompletionHandler0)
   return request
   }()

let handler = VNImageRequestHandler(ciImage: ciimage,options: [:])
   DispatchQueue.global(qos: .userInitiated).async {
   try? handler.perform([coreMLRequest])
}
```

For visualizing multiArray as image, Mr. Hollance’s “CoreML Helpers” are very convenient.
[CoreML Helpers](https://github.com/hollance/CoreMLHelpers)

[Converting from MultiArray to Image with CoreML Helpers.](https://medium.com/@rockyshikoku/converting-from-multiarray-to-image-with-coreml-helpers-59fdc34d80d8)

```swift:
func coreMLCompletionHandler0（request：VNRequest？、error：Error？）{
   let = coreMLRequest.results？.first as！VNCoreMLFeatureValueObservation
   let multiArray = result.featureValue.multiArrayValue
   let cgimage = multiArray？.cgImage（min：-1、max：1、channel：nil、axes：（3,1,2））
```

[P.S. I made an iOS app with UGATIT CoreML model of selfie2anime.](https://apps.apple.com/us/app/animateu/id1513582287)

https://apps.apple.com/us/app/animateu/id1513582287
