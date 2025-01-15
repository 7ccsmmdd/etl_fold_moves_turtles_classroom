## An ETL transformation to fold sequences of move statements

Building on your ETL copy transformation, change the transformation so that it folds sequences of `MoveStatement`s into a single `MoveStatement`. So, for example:

```
forward(20)
forward(10)
```

should become

```
forward(20+10)
```

Similarly, 

```
forward(10+5)
backward(9)
```

should become

```
forward(10+5-9)
```

Remember that ETL makes transformations at the level of the *abstract* syntax. You will need to
 
1. Change the rule that transforms `MoveStatement`s so that it doesn't simply copy every `MoveStatement` but only the first in each sequence;
2. Add code to collect the expressions from all `MoveStatement`s in a given sequence
3. Create a new `Addition` expression that combines all of these expressions together

Again, you will want to test your transformation in the runtime Eclipse. Eventually, save it in the file called `fold_moves.etl` in the `generator` package in the main `turtles` project so that the auto-grader can pick it up.

The auto-grader has a test that checks the basic requirement and some tests that check for corner cases (for example, where the `MoveStatement` is the first or the last in a block of statements).

Eventually, you should get 40/40 from the auto-grader.

### Using the repository

There are two ways to do this activity:

1. You can check out the repository and import the projects into Eclipse, then do the activity there. Commit your changes and push them back to GitHub to trigger the autograding so you can see whether you've correctly implemented the grammar. More information about checking out and editing code in Eclipse can be found on KEATS.
2. You can [do this activity in your browser](https://mdenet-ep.sites.er.kcl.ac.uk/?activities=https://raw.githubusercontent.com/6ccs3mde-7ccsmmdd-2023-24/etl_fold_moves_turtles_classroom/master/activity.json&privaterepo=true). Click on the link and your browser will open the MDENet Education Platform with the activity pre-loaded. Generate the Xtext editor, then you can open a playground view where you can create a model and an ETL transformation and try out what happens when you run the transformation. See the video on KEATS to find out how to do this. **Note that you must save your changes before switching to the generated editor or you will lose them.** Saving your changes will create a commit in your repository, which will also automatically trigger the autograding process -- the transformation is automatically put in the correct place for the autograder to pick it up, no need to copy it across in this case. We have also pre-filled the transformation with the code for the copy transformation so you only need to make edits in appropriate places.
