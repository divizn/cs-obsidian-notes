
# Contents

- [About](#about)
- [Sharp et al principles](#sharp%20et%20al%20principles)
- [Accessibility and Inclusivity](#accessibility%20and%20inclusivity)



# About

> Familiarise yourself with Usability Engineering Principles by Don Norman. You should be able to provide a good understanding of UE principles and how they are implemented, as you will need to show this in sketch form in the exam.


### What are design principles?

Design principles are the do's and don't of interaction design.

- Design principles are used by designers to **assist** their thought processes when designing
- Principles are **theory based, common sense** and **experience (consultancy).**
- Not intended to specify **how** to design an interface


# Sharp et al principles

## There are 5 main sharp et al principles:

- Visibility
- Feedback
- Constraints
- Consistency
- Affordance


### Visibility

- Visible functions are how likely users will know what to do next. e.g. controls for a car (headlights, horn, hazards, indicators, etc.). All hand based on what the driver needs them for

Problem examples include sensor technology use. e.g. taps (w/ sensors):
![tap](tap-example.png)
Here you can see that the tap doesn't work with black clothing causing a **usability** issue.


### Feedback

- Feedback is related to visibility
- Imagine submitting coursework and you never receive feedback on how to improve - this is an example of poor feedback. 
- Providing feedback about the action taken will allow the user to continue with the activity

##### There are different types of feedback:
- Audio
- Tactile 
- Verbal 
- Visual
- Combination of these

Example of feedback:
![phone example](feedback-example.png)
Here you can see feedback being provided after a user input - errors for users if they have done something incorrect.

Example of feedback **and** visibility:
![door example](door.png)
Visibility - Handle to show that you are meant to pull, and clear indication for pushing.
Feedback - Door opens/closes


### Constraints

- Determining ways of restricting user interactions at a given time
- Example - deactivate certain menu options in a user interface by shading them grey to restrict users to the actions possible (kind of like visibility). 
- Constraints are designed to apply conventions and make sure the user is using things the right way e.g. external slots on a PC like USB slots are designed to only allow the USB to be entered one way.



### Consistency

- Designing interfaces that have similar elements and components for achieving tasks
- A consistent interface is one that follows rules

Example of consistent design on Instagram:
![insta-example](instagram.png)
Social emails are blue, promotions green, updates are yellow staying **consistent** with the other components


### Affordance

- Affordance is the term used for an attribute of an object that allows people to know how to use it
- For example, a recycle bin icon is used for throwing something away.
- An arrow indicating to go back
- Or a magnifying glass indicating to zoom in/out
- Should be intuitive and allow everyone to understand the purpose of the action

## Others to consider

- **Simplicity/functional minimalism** - keeping it simplistic and straight to the point
- **Cognitive** - reducing cognitive load to understand application (reduce amount of information on screen to highlight what's important) - kind of like abstraction
- **Engagement** - interactively designed - TikTok
- **Perceivability** - another description for affordability - interactive media like showing things happening e.g. dragging a file or loading icon (?)
- **Learnability** - making things easy to learn
- **Mapping** - process that narrows the gap between users or customers' needs and the product

Example of mapping: 
![mapping example](mapping.png)


## Applying Design Principles

- It's challenging to consider more than one principle due to **trade-offs**.
- Try to constrain information results in less visible information
- Implementation of affordances can result in the interface becoming cluttered and difficult to use reducing simplicity
- Consistency can be problematic
- Sometimes inconsistent designs become easier than consistent ones e.g. knives - different uses, but don't all fit in the drawer


# Accessibility and Inclusivity


### Accessible Design vs Universal Design

- Comes down to affordances and context
- Universal design is inherently accessible
- Some designers say that universal design limits creativity
- To design a phone handset intended for both senior citizens and younger customers, you can design for senior citizens' needs first - larger numbers, larger display etc.
- This design approach results in a product that works for only one target group - achieving accessible design, but, not universal design.
- While accessible design is important, it doesn't reach everyone in the same way. So we should logically strive for universal design whenever possible and concentrate on accessible design only when necessary (e.g. when you have a specific target audience).

### Accessible design dilemma

- Video captions, text transcriptions of audio files are **alternatives** to the original content - these are examples of accessible design
- Structural markup is a powerful universal design technique (e.g. html elements - div, h1, h2, p, etc.)
- Organising content logically using meaningful headings - this creates affordance as readers read headings before reading the text and gives readers context.

### Alternative Text

- Many people rely on assistive technology - some people cannot perceive information that is conveyed by images unless a text or audio **alterative** is provided. 
- Having alt text makes sure you are keeping accessible design principles.


##### People who may need alt text

- People who are blind (audio narration for alt text)
- People with cognitive disabilities
- People who rely on assistive technologies
- People with slow internet/limited mobile data plans (less expensive to load alt text than image)
- Search engines (crawler robots or other scrapers)


##### Making good alt text

- Making sure its brief
- Depends on the image context
- Describes content and function of the image
- Should not be redundant or provide same information as the text
- Doesn't use phrases like "image of" or "picture of"
- **Keep it to a maximum of 160 words**

Examples of meaningful alt text:
![examples of good alt text](alt-text.png)


### Principles of accessibility

- If you cannot consider all disabilities, then consider blindness as 80% of accessibility issues are related to blindness. 
-  Create good alt text
- Remember to tag icons so screen readers don't skip over them (e.g. hamburger menu).
- Make sure all important content is accessible by screen readers
- Test for accessibility with real users
- Don't disable zoom in mobile interfaces where possible
- Accessibility is cheaper when it's done up front - and it's easily learnt
- Be aware of visual bias - accessibility doesn't mean ugly design
- Check mobile accessibility separately
- Embrace the all-access attitude (universal design)