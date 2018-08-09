# OCR4iOS

SwiftOCRCamera
SwiftOCRCamera is a fast and simple Tesseract library written in Swift. It uses for image text recognition. As of now, SwiftOCRCamera is optimized for recognizing short, one line long alphanumeric codes (e.g. DI4C9CM). We currently support iOS and OS X.

Features
	•	support of lowercase leters
	•	image preprocessing
	•	speedy text recognition
	•	low light capture text
	•	get text from both album photos and capture image from camera

Prerequisites
	
	•	Xcode 9.x
	•	iOS 11.x
	•	ios device

Installation

To integrate SwiftOCRCamera into your Xcode project using CocoaPods, specify it in your Podfile:

 pod 'TesseractOCRiOS'

Nots :- must add below line in your pod file 
 
post_install do |installer|
      installer.pods_project.targets.each do |target|
          target.build_configurations.each do |config|
              config.build_settings['ENABLE_BITCODE'] = 'NO'
          end
      end
  end

How to use

1)import this two framework in your viewcontroller

import TesseractOCR
import AVFoundation

2) add this function on click button and pass capture image

	// Tesseract Image Recognition

    func performImageRecognition(_ image: UIImage) {
        
        if let tesseract = G8Tesseract(language: "eng") {
            tesseract.engineMode = .tesseractCubeCombined
            tesseract.pageSegmentationMode = .auto
            tesseract.image = image.g8_blackAndWhite()
            tesseract.recognize()
            textView.text = tesseract.recognizedText
        }
     }

![alt text](http://dev.acquaintsoft.com/ocrios.gif)

