# flutter_barcode_sdk
![pub.dev](https://img.shields.io/pub/v/flutter_barcode_sdk.svg)

A flutter plugin project for [Dynamsoft Barcode Reader SDK](https://www.dynamsoft.com/barcode-reader/overview/).

## Try example
The example allows users to scan barcodes via the camera video stream in real-time or read barcodes by taking a picture.

```
cd example
flutter run -d <device>
```

Video Scan

![flutter barcode scanner](https://www.dynamsoft.com/codepool/img/2021/flutter-barcode-scanner-camera.gif)

Picture Scan

![flutter barcode reader](https://www.codepool.biz/wp-content/uploads/2019/08/flutter-barcode-plugin.png)

## Current Supported Platforms
- Android

## Supported Barcode Symbologies
- Linear Barcodes (1D)
  - Code 39 (including Code 39 Extended)
  - Code 93
  - Code 128
  - Codabar
  - Interleaved 2 of 5
  - EAN-8
  - EAN-13
  - UPC-A
  - UPC-E
  - Industrial 2 of 5

- 2D Barcodes
  - QR Code (including Micro QR Code and Model 1)
  - Data Matrix
  - PDF417 (including Micro PDF417)
  - Aztec Code
  - MaxiCode (mode 2-5)
  - DotCode

- Patch Code
- GS1 Composite Code
- GS1 DataBar
  - Omnidirectional,
  - Truncated, Stacked, Stacked
  - Omnidirectional, Limited,
  - Expanded, Expanded Stacked

- Postal Codes
  - USPS Intelligent Mail
  - Postnet
  - Planet
  - Australian Post
  - UK Royal Mail


## Usage

- Read barcodes from an image file:

  ```dart
  List<BarcodeResult> results = await _barcodeReader.decodeFile(image-path);
  ```

- Read barcodes from video stream [CameraImage](https://pub.dev/documentation/camera/latest/camera/CameraImage-class.html):

  ```dart
  CameraImage availableImage;
  int format = FlutterBarcodeSdk.IF_UNKNOWN;

  switch (availableImage.format.group) {
    case ImageFormatGroup.yuv420:
      format = FlutterBarcodeSdk.IF_YUV420;
      break;
    case ImageFormatGroup.bgra8888:
      format = FlutterBarcodeSdk.IF_BRGA8888;
      break;
    default:
      format = FlutterBarcodeSdk.IF_UNKNOWN;
  }

  List<BarcodeResult> results = _barcodeReader.decodeImageBuffer(
                availableImage.planes[0].bytes,
                availableImage.width,
                availableImage.height,
                availableImage.planes[0].bytesPerRow,
                format);
  ```

## License Agreement
https://www.dynamsoft.com/Products/barcode-reader-license-agreement.aspx

## Contact Us
support@dynamsoft.com

## TODO
iOS, Windows, Web
