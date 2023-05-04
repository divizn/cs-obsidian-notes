
# Contents

- [About](#about)
- [Evaluation](#evaluation)
- [Heuristic Evaluation](#heuristic%20evaluation)
- [Cognitive Walkthrough](#cognitive%20walkthrough)

# About

> Familiarise yourself with Heuristic Evaluation and Cognitive Walkthrough. You should be able to describe each of these expert evaluation methods, compare and contrast them and know how to use them effectively. Know the pros and cons of each, this will help you.



# Evaluation

### What is evaluation?

Evaluation: a process through which information about the usability of a system is gathered in order to improve the system or to assess a completed interface.”

### Why evaluate?

- Understanding the problem
- Comparing designs
- Checking conformance to a standard
- Engineering towards a target

All centre on asking "how well will the design do its job"

### Why do ***usability*** evaluation

Need to consider how well will the design do the job 
For example:
- will the operator be able to handle emergency calls faster than before?
- is the ticket machine simple enough so that people can use it successfully their first time?
- if this command is used by mistake, how can the user escape from it?
- how many people who try to use the system will continue to use it?
- how will the system be adopted by the organisation - will it change organisational responsibilities? 

### 3 goals for evaluation

1. Assess systems' functionality
2. Assess effect of interface on user - how easy to learn, usability, matches user expectations
3. Identify specific problems with the system - contextual features, -ve features

### 4 key considerations for selecting evaluation approaches

To determine the type and form of evaluative study to carry out, what are the:
1. characteristics of users
2. types of activities users do
3. environment of study
4. nature of thing being evaluated


### 3 main forms of Usability Evaluation

#### Analytical testing
1. **Expert review**
	- based on expert's opinions
	- can be done at different stages of design
2. **Abstract testing**
	- Draw from existing data
	- e.g. cognitive analysis/GOMS/KLM
#### Empirical
3. **User or usability testing**
	- experimental or qualitative studies of use


### Expert review - 'quickfire' approaches

- **Heuristic evaluation**
	- several passes; 'scorecard' approach
	- assessment on conformance to 10 design 'rules'
- **Consistency inspection**
	- terminology, colour, layout, inputs, outputs
	- training materials and help systems
- **Cognitive walkthrough**
	- similar to software engineering 'code walkthrough', but stepping through user actions on the interface to simulate users doing the task (especially for frequent tasks)
- **Formal usability inspection**
	- adversarial courtroom style meeting with moderator
	- present and discuss weaknesses/strengths

### Limitations of expert reviews

- Lacks 'ecological' validity - are they telling us what we want to know?
- Requires knowledge and experience to apply effectively
- May identify more minor issues and fewer major issues
- Subject to the biases and whims of reviewers - which is why you use multiple experts and aggregate their results



# Heuristic Evaluation

An **analytic method** of evaluation

Made by some guy named Jakob Nielsen

- Experts independently evaluate the user interface - whether it conforms to established **usability principles** (heuristics)
- 'Discount usability engineering'
	- Evaluation should last 1 or 2 hours
	- Method can be applied to paper prototypes

###### The output of the evaluation:
- List of usability problems in the interface
- Referring to usability principles that were violated

### Carrying out heuristic evaluation

Best practice - 5 or more experts report a problem using this same format:

1. **Problem description** - a brief description of the problem
2. **Likely/actual difficulties** - the anticipated difficulties that the user will encounter as a consequence of the problem
3. **Specific contexts** - the specific context in which the problem may occur
4. **Assumed causes** - description of the cause(s) of the problem

- The problems found are rated by frequency and impact to assess importance in redesign to decide the priority and need of solving these problems

### The 10 heuristics (assumed causes)

1. **Visibility**
	- For example, state of the program e.g. loading state, interactive state, submitted state, etc.
	- Show the action happening
	- Be as specific as possible e.g. google maps circle on live location indicating the precision and direction of the user
2. **Match between system and real world**
	- systems should speak users language through words user understands e.g. a recycling bin icon on your desktop
3. **User control and freedom**
	- Provide clearly marked exits for users so they don't have to do the thing that the system expected them to do (e.g. accidentally clicking on a link still lets you go back)
	- Strategies:
		- Cancel buttons (for dialogs waiting user input)
		- Universal undo (get back to previous state of system)
		- Interrupt (especially for lengthy operations e.g. downloading)
		- Quit (for leaving the program at any time)
		- Defaults (for restoring a property sheet/start again)
4. **Consistency and standards**
	- People expect systems to be consistent and meet standards
	- Do this by having consistent colours, buttons, interactivity, etc.
5. **Error prevention**
	1. Having a dialog box confirming user input e.g. "Are you sure you want to delete this item?"
	2. Also includes thing like form items are in the right form e.g. email input should expect an email only (include @ and .)
6. **Recognition rather than recall**
	- For example, rather than just having just text for an option, include visuals that people can recognise and remember the option by
7. **Flexibility and efficiency of use**
8. **Aesthetic and minimalist design**
9. **Recognise, diagnose and recover from errors**
10. **Help and documentation**



# Cognitive Walkthrough

An **analytic method** of evaluation

Made by some guy called Polson et al.

- Evaluates how well systems support users learning tasks
	- Usually performed by expert in cognitive psychology
	- expert 'walks through' design to identify potential problems using psychological principles
	- Asks the experts to assess "will the system make sense to the user?" - evaluating the steps to form the task and how meaningful they are to try and uncover mismatches in how users think about the task vs how the developers thinks about the task

## Performing cognitive walkthrough

###### To begin, select a task to be performed and write down all the steps (actions) in the task
For example: creating a customised 'visual' voicemail message on an iPhone:
1. Tap VoiceMail
2. Tap Greeting
3. Tap Custom
4. Tap Record and speak your greeting
5. When you finish, tap Stop
6. To listen to your greeting, tap Play
7. To re-record, repeat steps 4 and 5
8. Tap Save

###### Then for each action in the task, ask these 4 questions:
1. **Will the user try and achieve the right outcome?**
	- *Does the user have the knowledge they need to start the action? Will they understand the need for this action in the task?*
2. **Will the user notice that the correct action is available to them?**
	- *Does the user know what to do next? Is the correct action obvious, or have to be recalled from memory? Is the control visible?*
3. **Will the user associate the correct action with the outcome they expect to achieve?**
	- *Can the user connect the correct action with what he/she is trying to do? Is there a conceptual link between the control and the action?*
4. **If the correct action is performed, will the user see that progress is being made towards their intended outcome?**
	- *Is there feedback? Is the feedback appropriate to indicate action completion? Will the user know if they have made a right or wrong choice?*

- You need to make sure the answer to all 4 questions are yes


