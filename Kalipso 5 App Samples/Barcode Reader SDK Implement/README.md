# Kalipso-Samples
All our samples are identified by a name, made in what version and their intent.

***************************************************************
MyPlugin.zip -> Android Studio Project

There are 2 classes there for you to use:
RFIDInterface and ScanInterface.

These classes have the methods created, but they are throwing "Not Implemented" exceptions, so you need to implement those methods.
You also need to import their SDK library into the project

For example, for Barcode, according to the PDF you sent, in the ScanInterface class in the Connect() method you should call something similar to :
barcodeReader = new BarcodeReader(ctx);

//Also you should declare a class variable like this:
BarcodeReader barcodeReader =null;

The PDF also says you will receive keycodes for the scanner, so in the onKeyDown() you should have something like:
if((keyCode == SCAN) || (keyCode == SIDE_LEFT) || (keyCode == SIDE_RIGHT)) { barcodeReader.start(new BarcodeCallback() { @Override public void onBarcodeRead(String barcode) { String detectedBarcode = barcode;

// Send scan to Kalipso
mEventsInterface.BarcodeScanned(detectedBarcode , 0, ""); } }); }


And on the onKeyUp() something like:
if((keyCode == SCAN) || (keyCode == SIDE_LEFT) || (keyCode == SIDE_RIGHT)) { barcodeReader.stop(); }


Then build your APK and put it in Files To Send folder.
If your APK is named MyPlugin.apk, then in Kalipso you would call:
Barcode Connect  (External API; PFOLDER + "\MyPlugin.apk"; "com.sysdevmobile.myplugin.ScanInterface"; "")

Note, the file names are case sensitive.

External API option allows you to implement an interface with a barcode scanner SDK and use standard Kalipso Barcode... actions to interact with it.
You can find the android java library containing the interfaces in Designer folder under "Plugins\Android\libs"
You should create a class that implements the KExternalScannerAPI interface. Then you pass in the path to the JAR/APK file you created and you must pass the name of the class that implements this interface. Kalipso will create an instance of this class, and any call to Kalipso Barcode... actions will be translated into a call to the corresponding Interface method.
The KExternalEventsInterface that you will receive in the Connect() call allow you to send barcode scan events and other additional events to Kalipso to App Notifed events in Kalipso forms and to register callbacks for some events to be sent to you from Kalipso. See RunJar.

***************************************************************
