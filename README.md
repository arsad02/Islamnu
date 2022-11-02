# EPG SDK

EPG SDK is a payment gateway, that provides solutions to mobile applications for card payment.

## Features

- The SDK offers a ready-made card payment screen.
- Supporting dark mode.

## Follow the below steps:

1. Contact the EPG team to get the framework.
2. Navigate to the General section of your Target.
3. Drag ```EPG.framework``` file to Frameworks, Libraries, and Embedded Content section.

## Usage / Example
Import the `EPGSDK` in your code
```swift
import EPG
```

### Pay with a Card

- Configure your server with EPG
- Get the `authentication_token` from the server
- Get the `transaction_id` from the server
- Get the `merchant_name` from the server


### Create an object of ```EPG``` with passing your viewcontroller to navigate.

```swift
let epg = EPG(controller: self)
```

Pass the `authentication_token`, `transaction_id`, and `merchant_name`, recieved from your server.

#### Theme has 2 options:
- theme1
- theme2

Setup all the parameters to start the payment

```swift
epg.setupData(
              transactionId: transaction_id,
              authenticationToken: authentication_token,
              customer: merchant_name,
              theme: .theme1,
              delegate: self
              )
```




For an open payment gateway use this.
```swift
epg.openPaymentGateway()
```

#
### You are now ready to start payment and handle EPGDelegate

Delegates
Here you will receive the transaction status and errors.

```swift
extension ViewController: EPGDelegate {
    func epgPayentResponse(_ success: Bool) {
        print("EPG: Success Response")
    }
    
    func epgPaymentResponse(_ error: Error?) {
        print("EPG: Error Response, \(error?.localizedDescription ?? "")")
    }
}
```
#
#### Note: EPG SDK only supports Visa, Mastercard, and Amex cards.
#
