# dicegame
README -  dice game


The agent for the dice game is built using value iteration and relies on the value iteration function covered in the coursework. It works for any number of dices. Thank you again for giving me the 1 week extension, it enabled me to take a proper look at the assignment and give it a good shot.

I will be explaining each function separately, just to portray what my intentions were and how I also managed to pass the extended rules tests.

Function: def calculate_value_for_action

In this function I use the helper function to get the next states for a given action, provided the current state. It returns the reward for each action and what the probabilities are for getting into the next states.

I then align states and probabilities. I loop through the states and the probabilities to find a value for each action. I then want to understand what the reward is for holding - so we then calculate the potential reward for holding that state. I then subtract the cost of rolling the dice (rule agnostic). I then use the value iteration function to calculate the value of the resulting state for this given action. 


Function: def calculate_value_for_state

In this function, I take each action that I can perform on a given state. In case of the dice game, there will always be the same possible actions. I then go through each action and calculate a value for that action. I take the maximum value out of the calculated values for the action.


Function: def __init__(self,game)

Basically, we initiate a while loop that stops when delta reaches a certain point. Based on the formula, delta is the differnce between the value of the subsequent states. Based on the formula, we need to calculate the value of each state, which happens in the for loop. First, I store the value of the previous state in a temporary variable. The next step is that I calculate a value for the current state. The last step is that I calculate the delta and check if it is the largest delta. If it is the largest delta, then I use it. The loop stops when the maximum / biggest delta for all of the states is less than gamma (it converges).

Before the loop, I used state expression tuples as a state values tuple key. In this case, we initialise the states to 0. This is what it looks like visualised:
             (1, 1, 1): 0,
             (1, 1, 2): 0,
             (1, 1 ,3): 0,
             .....
            (6,6,6): 0

For each step, the value, which in the case above is 0, becomes another value, on the next step another value, on the next step another value, and so on. I can then look for the deltas. I have imported the time function to keep track of the time it takes for the construction and for each action. 

Through self.hodl I take the first state from the game, take the length of the elements in that state (I now know how many dices we have), and then using the range, I create an array of the same length of incrementing numbers and then I convert that array to an tuple. The tuple is the state of an action which holds all of the dices and finishes the game (which is why I called it "hodl"). This makes it possible to apply other rules to the game. 


         
