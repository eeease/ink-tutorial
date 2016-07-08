# ink-tutorial
//This is a modified version of the ink tutorial that I'm using to teach the platform to students who have no prior coding knowledge.



/*
Hello, world!
*	Hello back!
	Nice to hear from you!
*/

//Here's how to comment your 'code'.  Use comments to explain something that might not be clear or to break up your code into sections.  Another method is to use /* and */

/*
//Square brackets can be used if you don't want to print the choice text in the response:
Hello, world!
*	[Hello back!]
	Nice to hear from you!
*/

/*
//Breaking up option content:
"What's going on here?" my friend asked.
*	"An academic moshpit[!"]," I screamed over the sounds of learning.
	"Really," he responded.  "Sounds exciting."
*/

/*
//Multiple choices are created by simply listing different choices with asterisks:
"What's going on here?" my friend asked.
*	"An academic moshpit!"[] I screamed. //note what is separated from choice response to output text.  Yes, comments can be written in line.
	"Really," he responded.  "Sounds exciting."
*	"We're... learning[..."]," I droned.
	"Ugh," he murmured.  "Learning is the worst."
*	"I just got here myself[."]," I replied.
	"Well then, I suppose we're in the same boat!"
*/

/*
//Knots are sections of content, somewhat similar to paragraphs.  They must be written with at least two equals signs on each side.  They must be single words with no spaces (underscores usually = spaces in coding):
=== back_in_hicksville ===
We stumbled into class fifteen minutes late.

//Try compiling that.  What shows up in the console?  Mini-talk about the console (it is the computer's way of communicating with us).  We may want to end the story:

-> END
*/

/*
//Knots divert to knots.  Connect sections of the story using a divert arrow (->).  Diverts happen immediately without user input.
=== back_in_hicksville ===
We stumbled into class fifteen minutes late.
-> teachers_response

=== teachers_response ===
The teacher briefly looked up at us and sighed.
*/

/*
//Diverts can also happen mid-sentence.  This allows us to make modular sentences that we can mix and match according to certain situations:
=== teachers_response ===
The teacher briefly -> looked_and_sighed

=== looked_and_sighed ===
looked up at us and sighed.

=== looked_in_shock ===
looked up at us and dropped his coffee.

=== looked_and_nodded ===
looked up at us and nodded knowingly.
*/

/*
//Glue overrides line-breaks:
=== teachers_response ===
The teacher briefly <>
->looked_up

=== looked_up ===
looked up at us over his coffee
->dropped_mug

=== dropped_mug ===
<> and dropped his mug, the ceramic shattering across the floor.

//Be careful with glue, as it can get sticky.
*/

/*
//Combining knots, options, and diverts will give us the basic structure for a choose-your-own game:
=== paragraph_1 ===
You stand at a fork in the road, breathing heavily.
*	[Look back over your shoulder] -> paragraph_2
*	[Take the left route] -> paragraph_3
*	[Take the right route] -> paragraph_4

=== paragraph_2 ===
You peer back over your shoulder ->with_dread

=== with_dread ===
<>with a feeling of dread.  You might have lost them.
->paragraph_1

=== paragraph_3 ===
You hobble down the left route -> with_dread

=== paragraph_4 ===
You stagger towards the right route -> with_dread

-> END

//We can keep going back to where the story branches.  We can also dynamically change the options and set how many times they can be chosen.
*/

/*
//Stitches are sub-sections of Knots.  If a Knot is an entire scene, a stitch is an event within that scene.
=== the_rundown_house ===
= house_front
Against your mother's advice, you stop by the abandoned Jefferson Estate on the way home from school.
*	[Go around back] ->around_back
*	[Check the front door] ->front_door
*	[Run home] ->run_home //from inside the Stitch, we don't need the full address.  This is the same as "->the_rundown_house.run_home"

= around_back
You walk around to the back of the house.  There is a shed and an overturned canoe.
*	[Shed] ->open_shed
*	[Canoe] ->flip_canoe
*	[Run home] ->run_home

= front_door
You walk up to the front door.  The old wooden stairs creak as you climb them.
*	[Knock]
*	[Run home] ->run_home

= run_home
You scoop up your backpack and take a lively jaunt back to the safety of your home.
->END

=== open_shed ===
You attempt to pull open the door to the shed, but it's stuck.
*	[Lock]
*	[Rock]
*	[Run home] ->the_rundown_house.run_home

=== flip_canoe ===
As you approach the overturned canoe, you are overcome with a rank smell.  You gag, then recompose yourself.
*	[Flip it]
*	[Around front] ->the_rundown_house //diverting to a knot will move to the first stitch.  This is the same as "->the_rundown_house.house_front"
*	[Run home] ->the_rundown_house.run_home
*/

/*
//Automatic, or Fallback choices, are what gets shown when we run out of choices.  This can be used to build tension around something that definitely has to happen in the story.

=== trash_compactor ===
The walls are closing in, squeezing the garbage surrounding you and your friends.
->not_looking_up

=not_looking_up
Things are not looking up at this very moment.
*	[Steel bar]
You jam a steel bar in between the walls.  It seems to work for a second, then the bar bends like a wet noodle.
->not_looking_up

*	[Bang at the door]
You vigorously bang at the door, but nobody seems to hear... or care.
->not_looking_up

*	[Bad feeling]
You tell your friends you have a bad feeling about this.
->not_looking_up

*	[]  Just as the walls begin to press the breath out of your lungs, your robotic friend hijacks the mainframe and opens the door.  You slip out and breathe the freshest breath in your life.  Smells like rotten banana peels!
*/

/*
//In case you want readers/players to be able to repeatedly choose the same option, you can use Sticky choices:
=== trash_compactor ===
The walls are closing in, squeezing the garbage surrounding you and your friends.
->not_looking_up

=not_looking_up
Things are not looking up at this very moment.
*	[Steel bar]
You jam a steel bar in between the walls.  It seems to work for a second, then the bar bends like a wet noodle.
->not_looking_up

*	[Bang at the door]
You vigorously bang at the door, but nobody seems to hear... or care.
->not_looking_up

+	[Bad feeling]
You tell your friends you have a bad feeling about this.
->not_looking_up

*	[]  Just as the walls begin to press the breath out of your lungs, your robotic friend hijacks the mainframe and opens the door.  You slip out and breathe the freshest breath in your life.  Smells like rotten banana peels!

//The previous example keeps the 'bad feeling' choice available at all times, but also affects the story in another way.  Can you tell how?
*/

/*
//Varying and conditional choices are what non-linear story telling is all about.  For example, if you ask the character the same question over and over, she might have a different response:
=== at_the_dealership ===
=the_offer
Our best offer is
{
-haggling>2:
->too_cheap

-haggling>1:
<> $16,000

-haggling>0:
<> $18,000.

-else:
<> $20,000.
}
 How would you like to pay: Cash or credit?"
->pay_options

=too_cheap
<> for you to leave the dealership and take your business elsewhere.  Good day.
->END

=pay_options
*	[Pay cash]
You make it rain all over the salesperson's desk.  Curiously, nobody else in the office even notices this behavior.
->hop_in_whip

*	[Pay credit]
You swipe your card so fast that smoke begins to rise from the machine.  It's still a bit warm when you return it to your money clip.
->hop_in_whip

+	{haggling<3}[Haggle]
"That's still too much, I'm afraid.  Can't you drop the price just a little bit?" you plead to the salesperson.
->haggling


=hop_in_whip
You hop in your brand new whip and the first thing you do is...
*	[Pump tunes]
While you find it fun to get turnt up in public, the conveniently placed officer finds it a nuisance.  You receive ticket for sound pollution.
->END

*	[Recline]
You lay back in the drivers seat and stare through the sunroof, thinking about how you made it to this very moment.
->END

*	[Skrrrrrt]
You peel out of the dealership and head for the highway.  If you've got it, flaunt it!
->END

=haggling
{
-haggling<3:
"Our manager has just informed me of a deal we are running for new customers.  We can knock $2,000 off the base price."


-else:
"I'm afraid we only offer discounts to customers who intend on paying.  Your frugalness makes us uneasy."
->wishful_departure

}
->the_offer

=wishful_departure
As you skulk out of the dealership, you pass the car you were considering buying.  What would have happened if you weren't so cheap?  Where would you be right now?  You consider what might have been if you had decided to...
->pay_options

*/

//Let's alter or vary some responses in order to make our conversations more natural.  Meet The List.
//Lists are written inside curly brackets, with elements separated by | symbols.  Useful if a piece of content is visited more than once.
=== the_curve_ball ===
The pitcher took to the mound.
->pitches

=pitches
{First pitch - strike | Second pitch - strike | Third pitch - the batter disappeared. | Everyone in the stadium looked around at each other, as if the batter might appear in an adjacent seat for some very logical reason. | The catcher ripped off his mask, scratched his chin, and shrugged his shoulder.  This wasn't the first time he'd seen a batter vanish, it seemed.}
What happened next was...
+	[normal]
->pitches

+	[a bit weird]
->pitches

+	[understandable]
->pitches

+	[possible, I suppose.]
->pitches

//Can you clean up the previous example by using lists?
//There are also cycles that loop (using &); once-only lists that display nothing when they reach the end (!) and shuffles that produce randomised output (~).
//Lists can include blank elements, can be nested, can include divert statements, and can be used inside choice text. (NOTE: You can't start an option with {}, because that's how to mark conditionals).




//INCLUDE statements for multiple files.
