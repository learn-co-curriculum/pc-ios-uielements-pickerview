## Picker View

Here is a step-by-step guide for implementing UIPicker
![uipicker](http://bencoffman.com/blog/content/binary/iOS%20Simulator.jpg)

###Step 1.### In XCode, select a UIPicker from the object library.  Drag it onto your storyboard.

###Step 2.### Select the Picker, right click, and drag your mouse to the yellow view controller — the left most of the three icons at the top of the phone screen on your storyboard. 

Step 2a: In your ViewContoller file, add UIPickerViewDelegate after your UIViewController class declaration. `class ViewController: UIViewController, UIPickerViewDelegate, UIPickerViewDataSource`

**Explanation:**  This establishes your ViewController as the "Delegate" of your UIPicker.  For more about delegates , read here.  Ultimately, it means that your ViewController has access to all of the methods and behaviors pre-made by Apple to a UIPicker.  We'll use some of these later.

*At this point, you might be getting a few errors.  That's ok — Apple is just waitng for you to add a few methods that will clarify how you want your UIPicker to function.  *

Step 3: Create your picker content array.  In other words, what you want the different rows of your picker to display. `pickerContent = ["Sports", "Geography", "Politics"]`
Step 4: Beneath your `didReceiveMemoryWarning()' function, we are going to add four additional functions:

```swift
func numberOfComponentsInPickerView(pickerView: UIPickerView) -> Int {
        return 1
    }
func pickerView(pickerView: UIPickerView, numberOfRowsInComponent component: Int) -> Int {
        return pickerData.count
    }
    
func pickerView(pickerView: UIPickerView, titleForRow row: Int, forComponent component: Int) -> String? {
        return pickerData[row]
    }
    
func pickerView(pickerView: UIPickerView, didSelectRow row: Int, inComponent component: Int) {
        myLabel.text = factsDict[pickerData[row]]
    }
```
