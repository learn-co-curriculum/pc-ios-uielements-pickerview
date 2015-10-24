## Picker View##

Here is a step-by-step guide for implementing UIPicker

![uipicker](http://bencoffman.com/blog/content/binary/iOS%20Simulator.jpg)

**Step 1:** In XCode, select a UIPicker from the object library.  Drag it onto your storyboard.

**Step 2.** Select the Picker, right click, and drag your mouse to the yellow view controller — the left most of the three icons at the top of the phone screen on your storyboard. 

*Step 2a:* In your ViewContoller file, add UIPickerViewDelegate after your UIViewController class declaration. 

`class ViewController: UIViewController, UIPickerViewDelegate, UIPickerViewDataSource`

**Explanation:**  This establishes your ViewController as the "Delegate" of your UIPicker.  For more about delegates , read here.  Ultimately, it means that your ViewController has access to all of the methods and behaviors pre-made by Apple to a UIPicker.  We'll use some of these later.

*At this point, you might be getting a few errors.  That's ok — Apple is just waitng for you to add a few methods that will clarify how you want your UIPicker to function.*

**Step 3:** Create your picker content array.  In other words, what you want the different rows of your picker to display. 

`pickerContent = ["Sports", "Geography", "Politics"]`

**Step 4:** Beneath your `didReceiveMemoryWarning()` function, we are going to add four additional functions:

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
**Explanation:** Can you guess what each of these functions are doing?  Let's go through each one.

+ `func numberOfComponentsInPickerView(pickerView: UIPickerView) -> Int {}`

This function sets the number of components in your Picker.  In our SnapFacts App, there will be just one — the fact category.  How many would there be if you wanted your user to select a date?

+`func pickerView(pickerView: UIPickerView, numberOfRowsInComponent component: Int) -> Int {}`
    
  This function specifies the number of rows in your picker.  In other words, how many categories you'll have.  If you wanted your user to select a month of the year, what value would this function return?
  
+ `func pickerView(pickerView: UIPickerView, titleForRow row: Int, forComponent component: Int) -> String? {`

This function specifies the title of each row. In this case, it would be the actual names of your fact categories.  If you wanted you user to select a month, what would these values be?

+ `func pickerView(pickerView: UIPickerView, didSelectRow row: Int, inComponent component: Int) {}`

This function determines what happens when a certain row is selected.  In the case of your Facts App, what do you want to display given the user's category selection?

