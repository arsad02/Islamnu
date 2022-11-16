# EPG SDK

**EPG** is a native **iOS SDK**, that allows you accept mobile payment from your customers through multiple payment methods like.

- Card payments (Visa, Mastercard and AMEX).
- Apple pay.
- Samsung pay.
- UAE digital wallets.
- BNPL Providers.
(Currently we are only supports card payments)

## Features

- The SDK offers a ready-made card payment screen.
- Supporting dark mode.

## Requirement

- iOS 13.0
- Swift 5.0
- Xcode 14.0


## Follow the below steps:

1. Contact the EPG team to get the framework.
2. Navigate to the **General** section of your **Target**.
3. Drag ```EPG_v1_0.xcframework``` file to **Frameworks, Libraries, and Embedded Content** and set to **Embed and Sign**.

![App Screenshot](https://github.com/arsad02/Islamnu/blob/master/Screenshot%202022-11-15%20at%2012.08.52%20PM.png)

## Usage / Example
Import the `EPG` SDK in your code
```swift
import EPG
```

### Pay with a Card

##### Configure your server with EPG to get these details:
- `authentication_token`
- `transaction_id`
- `merchant_user_name`
- `merchant_password`
- `customer_name`

#
### Create an object of ```EPGPaymentRequest``` with the parameters and setup the object.
**Optional Parameters**
- `amountToPayText` default: `Amount to Pay`
- `showVat` default: `true`
- `theme` default: `auto`

**Theme has 2 options:**
- theme1
- theme2

```swift
var request = EPGPaymentRequest(
              delegate: self,
              merchantUserName: merchant_user_name,
              merchantPassword: merchant_password,
              transactionId: transactionId,
              authenticationToken: authentication_token,
              customerName: customer_name,
              callBackUrl: "https://www.google.com",
              theme: .auto)

 ``` 

#
### Create an object of ```EPGPayment``` with passing your viewcontroller to navigate.

Pass the `request` initiated above and initiate the payment.

```swift                  
let epg = EPGPayment(controller: self)
epg.initiatePayment(with: request)
```

# Delegates
Implement the delegate with your `ViewController` and add the delegate method to recieve the response of payment.

**EPGResult**
- `errorMessage` optional: `Error happend inside execution`
- `success` default: `true/false`
- `transactionId` default: `request transaction id`

```swift
extension ViewController: EPGDelegate {
    func epgPayment(delegate result: EPGResult?) {
        if !(result?.success ?? false),let errorMsg = result?.errorMessage {
            //Failed
        } else {
           //Success
        }
    }
}
```

#
# Finally after getting the EPGResult from the SDK you must make a server to server call to make sure the transaction has been successfully processed.
#

#
**Note: EPG SDK only supports Visa, Mastercard, and Amex cards.**
#
