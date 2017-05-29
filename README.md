# Swift 101 - Guard Statement
The supplementary Swift Playground to [Swift 101 - Guard Statement](https://medium.com/pretty-swifty/swift-101-guard-statement-9ff5725d4876).

## Playground source

```swift
/*:
 # Swift 101 - nil
 https://medium.com/pretty-swifty/swift-101-guard-statement-9ff5725d4876
 
 I love working with `guard` statements in my Swift code and you should too, let’s take a closer look…
 */

import UIKit

//Baskets in this example are an array of Items.
typealias Item = String
typealias Basket = [Item]

var basket: Basket = []

func addToBasket(item: Item) {
    guard basket.count < 5 else {
        print("Basket is full, Item: \(item) not added")
        return
    }
    
    basket.append(item)
    print("Item: \(item) added to basket")
}

addToBasket(item: "Apple")
addToBasket(item: "Orange")
addToBasket(item: "Grapes")
addToBasket(item: "Pear")
addToBasket(item: "Banana")
addToBasket(item: "Strawberry") // Will not be added to the basket as it's already full

// How to avoid silly divide by zero errors

func divide(lhs: Int, rhs: Int) {
    guard rhs > 0 else {
        print("Without this guard statement, you would be in a pickle")
        return
    }
    let result = lhs / rhs
    print("Result: \(result)")
}

divide(lhs: 10, rhs: 0)
divide(lhs: 10, rhs: 2)

// Using guards as super charged if-let statements

//Uncomment the line below to see what happens when an input value is optional
let input: Any? = nil

//Uncomment the line below to see what happens when an input value is not optional
//let input: Any? = 1

func guardIfLetExample(optionalValue: Any?) {
    guard let unwrappedValue = optionalValue else {
        print("That optional value was nil")
        return
    }
    print("You can now use unwrappedValue safe in the knowledge that it will never be nil. It was \(unwrappedValue)")
}

guardIfLetExample(optionalValue: input)

// A real world example

var favouriteColour: UIColor? //Because not everyone has a favourite (GB) colour (also GB) you know! Yes, I tend to avoid those people too...
func printColour(_ colour: UIColor?) {
    guard let unwrappedColour = colour else {
        print("Sorry, the colour you provided was nil")
        return
    }
    
    print(unwrappedColour) //unwrappedColour is not nil!
}

printColour(favouriteColour)

```
