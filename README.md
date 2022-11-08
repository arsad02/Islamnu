# EPG SDK

**EPG SDK** is a payment gateway, that provides solutions to mobile applications for card payment.

## Features

- The SDK offers a ready-made card payment screen.
- Supporting dark mode.

## Follow the below steps:

1. Contact the EPG team to get the framework.
2. Navigate to the General section of your Target.
3. Drag ```EPG.framework``` file to **Frameworks, Libraries, and Embedded Content section**.

## Usage / Example
Import the `EPG` SDK in your code
```swift
import EPG
```

### Pay with a Card

- Configure your server with EPG
- Get the `authentication_token` from the server
- Get the `transaction_id` from the server
- Get the `merchant_user_name` from the server
- Get the `merchant_password` from the server
- Get the `customer_name` from the server

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
              callBackUrl: "https://www.google.com")

 ``` 

#
### Create an object of ```EPG``` with passing your viewcontroller to navigate.

Pass the `request` initiated above and initiate the payment.

```swift                  
let epg = EPG(controller: self)
epg.initiatePayment(with: request)
```


#
### You are now ready to start payment and handle EPGDelegate

# Delegates
Implement the delegate with your `ViewController` and add the delegate method to recieve the response of payment.

**EPGResult**
- `errorMessage` optional: `Error happend inside execution`
- `success` default: `true/false`
- `transactionId` default: `request transaction id`

```swift
extension ViewController: EPGDelegate {
    func epgPayment(delegate result: EPGResult) {
        if !result.success, let errorMsg = result.errorMessage {
            //Failed
        } else {
           //Success
        }
    }
}
```
#
**Note: EPG SDK only supports Visa, Mastercard, and Amex cards.**
#
