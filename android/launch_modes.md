
Launch Modes in Android
--------------------------------------------------------------------------

Launch modes allow us to define how a new instance of an activity is associated with the current task. In order to fully understand Launch Modes, we would need to understand two general terms:

- Tasks: A collection of activities is known as as task. New activities are added to the top of the task.
- Back Stack: Activities are arranged in the order in which each activity is opened, like a stack. So the first activity that is opened will be the first or the root of the stack. When a new activity is opened, it pushes the activity to the top of the stack. When back is clicked, the topmost activity is popped from the stack.

Now let's look at the four different launch modes in Android:

- Standard: It creates a new instance of an activity in the task from which it was started. Multiple instances of the activity can be created and multiple instances can be added to the same or different tasks.
Eg: Suppose there is an activity stack of A -> B -> C.
Now if we launch B again with the launch mode as standard, the new stack will be A -> B -> C -> B.

- SingleTop: It is the same as the standard, except if there is a previous instance of the activity that exists in the top of the stack, then it will not create a new instance but rather send the intent to the existing instance of the activity.
Eg: Suppose there is an activity stack of A -> B
Now if we launch C with the launch mode as singleTop, the new stack will be A -> B -> C as usual.
Suppose now if there is an activity stack of A -> B -> C.
If we launch C again with the launch mode as singleTop, the new stack will still be A -> B -> C

- SingleTask: A new task will always be created and a new instance will be pushed to the task as the root one. So if the activity is already in the task, the intent will be redirected to onNewIntent() else a new instance will be created. At a time only one instance of activity will exist
Eg: Suppose there is an activity stack of A -> B -> C -> D
Now if we launch D with the launch mode as singleTask, the new stack will be A -> B -> C -> D as usual
Now if there is an activity stack of A -> B -> C -> D.
If we launch activity B again with the launch mode as singleTask, the new activity stack will be A -> B. Activities C and D will be destroyed.

- SingleInstance: Same as single task but the system does not launch any activities in the same task as this activity. If new activities are launched, they are done so in a separate task.
Eg: Suppose there is an activity stack of A -> B -> C -> D. If we launch activity B again with the launch mode as singleTask, the new activity stack will be:
Task1:  A -> B -> C
Task2:  D