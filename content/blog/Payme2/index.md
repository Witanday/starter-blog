---
title: Lambda Labs Week II/ Payme Application , Building reminders React /Front-End
date: "2019-04-10T09:15:37.121Z"
description: In this topic i will describe how i proceeded to build the front-end and the bacic backend.
---

This post promise to be long and arousing curiosity but i will do my best to keep it interesting , so let describes the 5 most important front-end's building blocks   :
React is Component-Based which means you can build encapsulated components that manage their own state, then compose them to make complex UIs.
[Learn more](https://reactjs.org)

Here is the screenshot :
![bigmodules](https://i.imgur.com/cVhcO0T.jpg)

Before going any further , let me link 3 useful npm packages :

* Simple React component for a search input, providing a filter function [Learn more](https://www.npmjs.com/package/react-search-input)
* A simple and reusable Datepicker component for React [Learn more](https://reactjs.org)
* The Select control for React [Learn more](https://www.npmjs.com/package/react-select)

### I.Search-Invoices
we can set this Search invoice component in 4 simple steps:
1. Get Invoice's data from the server (here localhost:3111/api/reminders/invoices/:idLoggedUser)
![getData](https://i.imgur.com/GAzWaUr.jpg)

2. Based on the shape of data we got from the server , we want to allow user to search invoices by Invoice_Number or by Client Name and the invoices corresponding to the keys will pop up and the user can select the invoice he want to send the reminders for.
![KEYFILTERS](https://i.imgur.com/Cbzurv4.jpg)

3. We plug the Search_term (correspond to any key the user will input in the search bar and this will be matched to the Key_to_filter defined on step 2) and The Key_To_filters into data_Invoice(see step 1) ,the magic will happen : we define an brand new Filtered Invoices
![filterdinvoice](https://i.imgur.com/LYKRdQu.jpg) 

4. SearchInput component will iterate over the Filtered_Invoice Array and returns each time an List of invoice that match the Search Term.
![SearchInput](https://i.imgur.com/vdTKhUr.jpg)

### II. Email and Sms Status SWITCH

This component is designed to render an awesome switch/toggle component , so it will allow User to Send an Email or/and Sms reminders.
![SearchInput](https://i.imgur.com/a6ambeZ.jpg)

The User can Hide or Show up the any reminders 
![Csshide2](https://i.imgur.com/g6eqBSl.jpg)
(when set the className emailfalse/smsfalse this will hide repectively the component)
![Csshide](https://i.imgur.com/0839fgy.jpg)

### III. Date-Time Picker 

Below is a screenshot of how to set the Datepicker . 
![Datepicker](https://i.imgur.com/OOp0p6J.jpg)
We will also need to require the CSS file from this package (or we could provide our own but we are not going to do it just keep it simple with CSS file from this package ).

### IV. Select frequency

It represents a whole new approach to developing powerful React.js components that just work out of the box, while being extremely customisable.
![Seclect](https://i.imgur.com/QlGGeSk.jpg)
 we set first the Options ( which value  tells us how the reminders gonna repeat sending sms/email after the starting date )
![Select Options](https://i.imgur.com/3JaBV48.jpg)

### V. Start Reminders Button

On the section II, i introduced a Switch component witch toggle/hide Sms/Email Forms, we need to set this Start Button to show up at the bottom  of the page each the switch is set On and hide when the switch is Off for both sms/email.
With a simple function component  that takes 2 parameters an returns an button, we can make this works:
![buttonFunc](https://i.imgur.com/qMYZ8AC.jpg)
Last thing to do is wrapper our function with a div and plug isCheckedEmail/isCheckedSms: 
![buttonFunc](https://i.imgur.com/sJuhQ9m.jpg?1)

That's it!!!

### Conclusion
Going through the code, there are a lot of stuff that could be explained and would need more than one post. for more details Please visit the full app version on [github](https://github.com/Lambda-School-Labs/labspt2-pay-me)

In The next post we will tackle the back-end part.
