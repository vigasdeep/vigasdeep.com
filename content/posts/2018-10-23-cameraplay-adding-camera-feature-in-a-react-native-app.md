---
title: CameraPlay – adding camera feature in a react-native app.
author: Vigas Deep
type: post
date: 2018-10-23T09:41:06+00:00
url: /2018/10/23/cameraplay-adding-camera-feature-in-a-react-native-app/
featured_image: /wp-content/uploads/2018/10/IMG_6365.jpg
geo_latitude:
  - 30.900965
geo_longitude:
  - 75.8572758
geo_address:
  - Ludhiana, Punjab, India
geo_public:
  - 1
categories:
  - Clicks
  - react-native
  - Tutorial
tags:
  - camera
  - instagram
  - linking
  - react-native

---
I&#8217;m going to play around and embed a camera feature in a mobile app using React Native.

so going ahead and start firing ( in your terminal )

`create-react-native-app CameraPlay`

Since we need to use native modules into the app, we will simply eject the expo part by doing

`npm run eject```

Now run the basic app (depending on your OS, you must have required libraries already setup up) with  
`react-native run-android` or `react-native run-ios`

If above command does not gets the output to your phone/simulator/emulator, then there is no point of moving further. Fix this and follow up next.

So we are going to make this first screen as camera input, after user clicks a photo, we will forward it to next screen to play with the photo.

So lets go ahead and install the **react-native-camera** package by issuing

`npm install react-native-camera --save`

`react-native link react-native-camera`

Only if there is any problem, and app does no compile after this, you need to do the linking manually, follow instructions at <a href="https://github.com/react-native-community/react-native-camera" target="_blank" rel="noopener">React-native-camera github</a>.

I also got some issues while compiling the RNCamera. So I took help from these two comments

<https://github.com/react-native-community/react-native-camera/issues/1530#issuecomment-385752864>

<https://github.com/react-native-community/react-native-camera/issues/1530#issuecomment-386572593>

Now, open the App.js code file and include  
`import { RNCamera } from 'react-native-camera';`  
Now, you can use the RNCamera component inside `return` you must now be able to see the camera inside your application, if not, there might be some problem in linking the module, try again linking.

more to follow, stay tuned in.