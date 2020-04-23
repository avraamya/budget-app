# budget-app-udemy
Build a code for a budget website

Code app explanations - budget app

what is the code?

The code is from a Udemy course - there are a number of projects we do - this is one of the projects. The project combines HTML, CSS and JavaScript. The project summarizes all the basic material you need to know about JS. Like using objects, DOM, classes. In my opinion this is an important code that summarizes the right way to build a project in JS while emphasizing the important material in JS.

Before we start to write code we need to plan it. For not making unnecessary mistakes - and wasting time. Some of the mistakes can be writing longer, more complicated code, repeating the code several times. Planning is one of the most important parts we need to do.

For Planning - We Want to Build a Budget Website - What Do We Need? How do we do this? What's on a budget website? There is a part of adding - we add a source of income or expense - the source - its name and how much money it is worth. In this section we see that we have a button when we click the button we add. When we add something we see it in another part - if it is a source of income it will be to the right and if a source of expenditure it will be to the left. There is another part above that includes our total budget and expenses and revenue. There are other little things to do with it - but that's the basics.

So what do we have the basics - clicking a button that adds some information - the information appears - and the amount above is updated.



We will try to divide the content we have into groups - that way the code will be much shorter, clear to understand and will be the capsule principle - that the information will not leak - that some function will not have access to what it should not have access to.

Groups: (Modules)
A set of information - memory and calculations. - something active - dynamic that changes.
Calculate a budget
Add an item to a database.
A user interface group (what you see on the screen) - something passive - once and that's it. No calculation needed.
Content revenue - getting the content from the user - it has to do with the interface. There is no calculation. More related to how our design - more to build - HTML.
Add the content to the interface
Update interface.
A management group becomes a schema of what causes what - what function does that function.
The button is part of the interface - but when we press it, we need something. The thing he does is not just about the interface. The design of this button is an interface but clicking on it - triggers actions that need to be done. But not commands of calculating anything. Management operations. It is not information directly - it provides the information to the first group - with the help of the interface. It is a bridge between the two parts. Traveling between the 2 sections - managing them.

All of these are the basics we need to look more deeply into and see what triggers why. A sketch is made of the relationship between the modules and functions:


Once we have the HTML and css code ready - we can start building the js code. Step one we need to realize the principle of modules - divide the code into 3 modules. This has a number of advantages - the code is clearer, more correct and we adhere to the principle of capsulation.

After that, we can build the add button. The add button makes eventlisteners suitable for keypress and click. After clicking the button we will have access to the content.

Because we have a lot of buttons and events, we will build a function that combines all the events. The function is setupEventListeners. In this function we will record the events for pressing a button or keypress of data entry for an item. Another note - we have to put the right selector in it for every event - but what happens if the selector changes? It's not under the control of JS - we can make our code a little more dynamic - wherever all the selectors sent - put them inside an object - will hold all the selectors we need. Because the selectors are UI related - we will define the object within the UI module. And to use it in our management model module - we'll use the getDomStrings function. Another note - for setupEventListener we will use straight at the beginning - we will create an init function that takes care of what needs to run straight with code execution

The data we get from the item will be used by us for many things - building the object of the item, adding the item to the database, adding the item to the html code. So we will do a neat function that will handle all of these cases the function is cntlAddItem:

First you will absorb the data first.
Build an appropriate object. And put it in the database - because we have a lot of items - we will build an array that contains the items. - There will be one array for revenue items and another array for spend items. A more effective way could be if these two arrays are arranged in one object.
The object we built is sent to a function that adds it to HTML.
Another but not necessary option is to clear the data input fields - which each time you click on the fields button will clear.
Another thing we need to do is calculate the budget we have - we'll do it later - right now there are things we need to address.


From our cntladditem function, we will call and use the following functions as described above:

First we will take the information from the fields. We'll build a function that handles this - it's an easy solution - you just have to do an eventlistener with the appropriate selector where we record the information. Again women so you should first register on our UI selectors list.

After we know what content we have about the object - we will build one. Is called the function that builds the object. We will send the function the knowledge we know - its item type, its monetary value, and its description.
If the item is an income type - an income object is built if an expense type is then an expense type is built - this is a simple if condition. Just note that in order to build these objects we must first build a (private) function that builds these objects. We will have 2 simple functions that we will explain soon. Once we have built the desired object. We also need to add the object to our HTML - because we need to add this object to HTML - from the function we asked it to build the object we will also return it - otherwise we will not know which object we are between and what to send to HTML.

2 functions I described in the paragraph above - these are 2 constructor functions. One for an income object and the other for an expense object. Because later on these two objects were different - we will define them in the object separately. What do we need for those objects? What data? First of all we need to know their monetary value, and the description, the type of each object we do not need to keep - because we already know it - before it we build the objects. We said we needed monetary value as well as the description - but we needed something more.

If we have many objects of the same type - we need to keep them - and we also need an identifier for each object - we need to distinguish each object. To save the objects we will use the array as we said before. But in order to confuse the objects, we also need an identifier - that is, an ID. The ID will start with a number according to Incadas running from 0 - and from here we know that in the item set one after the other - so what we do is - we go to the previous organ in the array - take its ID - and update the ID of the new organ with that ID plus 1.
We do not want to use the index of the array itself - because if we delete organs in the array, an index will no longer be correct.

After we have added the item in the data part we will also add it in the part of the UI. In order to add an item to UI we need to know the object of the item - because we need to know the properties of the object:
Description - We can take from reading the fields they performed before
Type - We can take from reading from the fields they performed before
Financial Value - We can take from reading from the fields they performed before
Identification number - For this we will need the object.

We will send all these functions - an economic HTML code is built - in this code DOM manipulation is done - to match it to the values ​​of the object. Substitute values ​​are defined in the HTML code. After that in the appropriate selector - we will add the HTML code we created. There is an option with the DOM command - insertAdjacentHTML command.

We have one last step left on the function that handles the object in the beginning. We are left to do a function to clear the values ​​of the fields. It is a simple code - we will go to the skeleton that wraps the part of the input - and the values ​​filled will be replaced by blank values, ie instead of the values ​​we named women "" -> blank quotes.

We finished everything we needed to finish with a function that handles the item / values ​​input. Now like I said, we can go to the next level. To the phase of updating the data.

What data do we need to update? If we added an item - the current monetary value changed - so we need to update it. Both within the data and within the UI - displayed on the correct budget screen.
Data update: The budget we have - we can find it if we go over the revenue and spend system. And that's how the budget is considered. We can tell a function that passes an array - before the type is sent to it - and it will update the value of the budget. - In order to update the value of the budget we need a place in memory. Note that we have defined a space within the data for the item's arrays - in the same type, the object can add additional fields for the budget we have.
The function will go over the arrays we requested - and will update the value of the new budget in memory. After that, we will ask for another function - a get function that returns these values ​​to us.
Finish the data phase - we are now in the UI stage. That's the simple part - we will build a function that gets the values ​​we updated - and with the help of dom manipulation we showed earlier - we can update the values. Herewith we have completed the whole part concerning the receipt of the item.

Now let's move to the part of the spend - when we spend an item - we have to worry about some things together again - we'll do the same as we did for income - we will compile all the things we need to do in one function - and from that we will call for more functions.

In order to delete an item we need the user to click on a delete button - here we set eventListners in a function that combines all events. The same function will send us to a function that unites and takes care of all the actions that need to be done in the delete. The event tells us that a click was deleted - but that is not enough - we also need to know where it was performed - so within the unifying function - we will need to send us an event about it - so we can know where the click was performed - and find out who the object should be deleted.

When we delete an item we need to do a few things:
Delete it from the data.
Delete it from the ui
Update the percentages - We know there is a difference between an income item and an expense - an expense item also has a percentage. We note that at this point we had to do part of adding an item - we didn't - to avoid any confusion.
Update Budget - Once we have spent spending, the budget has changed.

Before we delete we need to know what we are deleting - this step we can do by event delegation - when we click a button - we know which deletion button we clicked - what item we want to delete - with the help of event delegation. When we click on a button we can get the information about the fathers who wrap the button - those fathers who wrap the fathers - we were concerned about the income stage - which will have the type and ID. So when we click the button we go to his ancestors (as in the tree - we will climb) we will take the part of the father's signature which has the object type and ID.

After that, we are called to an auxiliary function - which performs the deletion - we will send it the ID and type of the object we want to delete. Then - with the ID of his object and type - go to his place in his array - and take it out. This is deletion in data.

In order to delete the item from the UI we need to know its selector - we have the selector in the function that handles deletions. - Sent to a function that deletes the UI from the selector. After that deleting what UI is is very simple. Using DOM manipulation we will use removeChild - before it goes to Dad - and so we deleted the object.

Once we have deleted the item - we have to update the percentages for spend type items - women notice this is a function - that we will call it after we delete an item. This function is exactly the same for women in the section we add - we skipped this step earlier. Now the same function - so we can add it. Another thing, we will also need to update the budget - after deleting it has changed. But we've already built that part. We can use this part - in function - even after removing an item.

So we have to build one part - a function that updates the percentages for all items of the spend. There are a number of things that should be done for the percentage update.
Calculate the percentages
Return of the percentages
Display the percentages in the UI.

Let's start with a function that calculates the percentages. In order to calculate the percentages we first need to save the percentages. That's why we made 2 objects - an object for spend items - and for revenue items. For expense items we need to add another thing. We will need to add some memory space to save the percentages. We will add the place in memory to our object - we will add another feature that will save space. (We note that the constructor of the spend object will automatically reset the percentage to minus 1 - because we haven't calculated it yet - and we haven't reached it - as far as the percentage is non-existent - minus 1 is a non-existent definition). Now in terms of memory everything is fine. It remains only to calculate the percentage for each item.

How is the percentage calculated for each item? We will use the function we said in the previous paragraph. This function should ensure that all items recalculate their percentage. There will be a foreach loop here to go over each item. For each item we will need to deal specifically. For each item we need to have a function that calculates the percentage of the item. And this should be a function that will have access to the item's private data. Therefore we add this function to the object itself. The object will have a function that calculates the percentage for the item. The big function that calculates the percentages for all items - will call the function you calculate for an item together. How to Calculate Percentage Per Item? We need to know the part of the item - our expense - from the total amount of revenue. - So we will have to send to the small function - the total income. (The small function has direct access to total revenue - but the small function works full of times - it would be unnecessary and ineffective that at all times it would access total income - the code would be more cumbersome). This means that the total revenue we will have to send from the big function - it will calculate the total revenue once and that is it - and send it to the small function - that counts for each item.

Short explanation of the previous paragraph - we have a function that calculates percentages for all items in the loop. And the function calls for a smaller function that handles each item individually. Just a small note - if our total revenue is 0 - then the percentage is considered undefined - we will format it as 1.
 We are done with the simple calculation part. A function only calculates a percentage - it simply has access to the data. And the function that wraps it only goes in the loop.
 
 Now we are in the return of the data - of the percentages - so we can update the data in the UI. To get the data - the percentages will work in exactly the same way. We will have 2 functions - a large function that goes over all spending items - and return a percentage of value. In order to return a set of percentages - we first need to return a percentage to a single limb. So our second and smallest function is to be a get function. Set a simple get function - which returns a percentage to a single item. In the big function, we will loop - on all items - and return a neat array.

We have the last part related to the percentages. - We still have to update the UI. To see the percentage change made before. What this function should do - it must get from the management function. The set of percentages we calculated earlier. And it will update the percentage for each spend item. How will she do it? It should somehow get the HTML code that shows the percentages. The way to do this is by using queryselectorAll - it passes HTML code - with the sections that contain the percentages. And returns a list - (roughly similar to array). Let's go through the list - in the loop as in the array - and do a sync between our list and the percentage set. First index in this array is the first index in the list - and so on. We will use this principle.

As we said before, we do a loop on the list - there is only one small problem. The list does not have an option to loop - we will need to build a function that does it for a loop. We will do this:
We'll use the function that gets the list passed and passed - like an array forEach. In every interest of the list we get an organ in the list - and we do the action we want - as in forEach.
We will build the function - and send it, the list and another function (callback function - as in real forEach).
The forEach function will take the list - and go through it in a regular loop (there are other ways to solve that we enrolled - it's better to use forEach). For each organ in the list - called the callback function - you will use the organ and its index. We need the index to match the percentage alignment.

Realizing itself - when we use the forEach function and send it our data. On each organ, we go to the content it represents on the screen - the part that the percentages are listed on - and change to our values. For each organ in the list - we go to the section where it represents the content - and in each organ - we put the percentage that belongs to it from the array - using the index.


We've only got some easy parts - improving the UI - in order for the UI to be more organized we can make a few changes - note that we do not present our content cleanly:
When we put a number of thousands - we want to have the semicolon that separates the thousands and we also want the positive numbers to be + and the negatives to be minus:
Whenever we display a number we will use the function - which will make the output number cleaner and cleaner. The function will get the number type - and the number itself.

When we insert an item - we want to add an entry item that the fields will have a blue border, and an expense item that the fields have a red border:
We will use the event that whenever we want to add something positive - the display will be blue. When you want to add something of expense - the display will be red in color.

To be displayed this month and current year at UI:
To display a current month - we will define a simple function that does this. The simple function is called from our init - because we need the month to appear straight at first.


Other important things:
In order for something inside a module to be public - meaning we can access it from outside we will need to register it within a return command.
We will keep the capsule principle - so that we can access content from other modules - we will build a public get function - in order for a function to be public we return in any object module - which will have the public content we want to access.
