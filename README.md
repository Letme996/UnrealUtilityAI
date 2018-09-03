# UnrealUtilityAI
Simple Utility AI implementation for Unreal Engine 4

Utility AI is a pretty opaque definition in the gaming world. At the end is very similiar to what you would have called 'fuzzy logic' in the old days.

At every 'brain' iteration, a series of 'actions' are evaluated. Each evalutation will return a value. This value determines which action to execute. This value defines the 'fuzzyness' of your choice. As an example, you may define a level of 'hunger', with 0 being no-hunger at all, 50 as moderately hungry, and 100 totally in hunger. At the same time you may have another level (well an action) that measure the 'rage' of an agent. Again 0 means no rage at all and 30 means berserk.

Why we choose a max of 100 for hunger and 30 for rage ? Well because being in berserk mode without the energy to fight it would be meaningless. If our UtilityAI chooses the next action to execute based on the highest value, we would know that our agent will never go in berserk mode before having eaten something.

## UUtilityAIAction

This is the C++ class (can be inherited as blueprint too) defining an 'action'.

An action is composed by the following methods/events:

* Spawn (called when the action is instantiated, generally one time per brain)
* Tick (called at every world tick if the action is the currently choosen one)
* CanRun (returns a bool, if true, the default, the action will be taken into account for the final computation)
* Score (returns a float, the score of the action)
* Enter (called whenever the brain switches from another action to this one)
* Exit ((called whenever the brain switches to another action)
