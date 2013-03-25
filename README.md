LBReadingTime
=============

UIScrollView indicator's panel showing the remaing reading time.
![image](https://raw.github.com/lukabernardi/LBReadingTime/master/screenshot_remaining_time.png)

This component is inspired by [iA blog](http://informationarchitects.net/blog/) and use some code from the [Florian Mielke's article about scroll indicator panel](http://blog.madefm.com/post/13817640556/ios-devcorner-attaching-an-info-panel-to-a)


Usage
=====

This componet is made up of two main classes namely `UITextView+ReadingTime` and `LBReadingTimeScrollPanel`. 

The first one is a UITextView's category that enable the count of remaining reading time. It can be used independently for programmatically obtain the reading time. This category swizzle a UITextView method in order to know when the text changes and add some associated object, this is done at `+load:` but for actually start the counting you should set the property `enableReadingTime` to `YES`. This is done because counting the word introduce a slight overhead, therefor be sure to enable it only if you need it.
You can also customize the value of Words per Minute via the property `wordsPerMinute`, by default this value is set to 200 words per minute (According to [http://en.wikipedia.org/wiki/Words_per_minute](http://en.wikipedia.org/wiki/Words_per_minute)).

`LBReadingTimeScrollPanel`, instead, is the view that is attached to the `UIScrollView`'s indicator. In order to work correctly you should set this view as your `UITextView` delegate or also forward the delegate call to the view. This view resize itself automatically to match the label width.

The usage is pretty simple:

1. Instantiate the `LBReadingTimeScrollPanel` (hold it in a strong property since it's repeatedly added and removed as subview)
2. Enable the reading time in the `UITextView`
3. Set the scoll panel as `UITextView` delegate

		self.scrollPanel = [[LBReadingTimeScrollPanel alloc] initWithFrame:CGRectZero];
		self.textView.enableReadingTime = YES;
		self.textView.delegate = self.scrollPanel;
    
    
 If you need to localize or change the message in your .string file make an entry for the string `NSLocalizedString(@"%d min left", nil)`.
 
Stay in touch
============

Tweet me [@luka_bernardi](https://twitter.com/luka_bernardi) if you use this code or simply want to tell me what you think about it.

License
============
LBReadingTime is available under the MIT license. See the LICENSE file for more info.