<-----------------------------Question:1----------------------------->

What is the difference between getElementById, getElementsByClassName, and querySelector / querySelectorAll?
Answer:

i:-- Using getElementById, we can access any element in the HTML document by its ID through JavaScript. (Since ID must be unique, only one element can be accessed using an ID.)

ii:-- Using getElementsByClassName, we can access multiple elements in the HTML document that share the same class.

iii:-- Using querySelector, we can access any element by ID, class, or tag. If selecting a class, we need to use a dot (.), and if selecting an ID, we need to use a hash (#). Note: It selects only the first matching element.

iv:-- Using querySelectorAll, we can also access any element by ID, class, or tag. If selecting a class, use a dot (.), and if selecting an ID, use a hash (#). But using this, we can select all matching elements.

Note:

querySelectorAll →

Returns a NodeList

Does not update automatically if the DOM changes

getElementsByClassName →

Returns an HTMLCollection

Automatically updates if the DOM changes

<-----------------------------Question:2----------------------------->

How do you create and insert a new element into the DOM?
Answer:

i:-- First, in HTML, create an empty container where the newly created element will be added. Note: If you don’t create a separate container, you can also use the parent element where you want to add the new element.

ii:-- Access the empty element you created in HTML and store it in a variable.

iii:-- Use document.createElement() to create any tag you want and store it in a variable.

iv:-- Use variable.innerHTML on the variable created in step iii to add your desired content or code.

v:-- Finally, use appendChild(newVariable) on the variable from step ii to insert the new element.

<-----------------------------Question:3----------------------------->

What is Event Bubbling? And how does it work?
Answer:

Event bubbling allows an event on a child element to propagate up to its parent, then grandparent, and so on, all the way up to the document. Meaning: event → parent → grandparent → document.

Why it is needed: 1: It allows us to easily add an event to a specific element; otherwise, we would have to add multiple events. 2: It allows a single parent element to handle events for multiple child elements.

How it works:

If we want to use one event listener to handle all the buttons with the same class:

Explanation of what happens here:

document.getElementById("parent") accesses the main div or parent first.

addEventListener("click", function(){}) tells the parent what to do when any click happens inside it.

if(event.target.classList.contains("btn")) ensures the event only triggers when a button is clicked; otherwise, any click inside the parent would trigger it.

console.log(event.target.innerText + " clicked") shows the text of the button that was clicked in the console.

Final output: Clicking any of the buttons (Button 1, 2, or 3) will display its name followed by “clicked” in the console.

<-----------------------------Question:4----------------------------->

What is Event Delegation in JavaScript? Why is it useful?
Answer:

Event Delegation allows us to control multiple child elements by adding a single event listener to their parent instead of adding separate event listeners to each child.

Why it is needed: Suppose I have a div container with many buttons inside, and I want to add event listeners to all of them. Without event delegation, if I have 20 buttons, I would need 20 separate event listeners. But if I add the event listener to their parent, the event works for all child elements inside it. Inside the parent’s event listener, I can use event.target.classList.contains() or event.target.closest() to trigger actions on specific child elements. This way, I don’t need to add multiple event listeners to each child individually.

Example:

Explanation: Here, we added an event listener to the parent, and now any child button inside it can trigger the event. This is called event delegation.

<-----------------------------Question:5----------------------------->

What is the difference between preventDefault() and stopPropagation() methods?
preventDefault() → What: The preventDefault() method is used to stop the default behavior of an element.

When needed: This means that the element (like a button, link, or form) will not perform its normal behavior, and only what we define in the event listener will happen. For example, sometimes we want to prevent a link from redirecting, a form from submitting, or a checkbox from checking automatically.

stopPropagation() → What: stopPropagation() is used to stop event bubbling. This means the event will not propagate to the parent or higher-level elements.

When needed: Normally, in event delegation, both child and parent listeners can run when a child is clicked. By using event.stopPropagation(), we can prevent the event from reaching the parent.

Example:

Explanation: Here, clicking the child button will trigger the child’s event listener, but the event will not reach the parent, so the parent’s listener does not run.