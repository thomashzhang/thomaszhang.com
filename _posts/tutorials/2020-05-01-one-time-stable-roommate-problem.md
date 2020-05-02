---
layout: post
current: post
cover: assets/images/tutorials/cover.jpg
navigation: True
title: Algorithmically and Fairly Split Housing Costs With Roommates
date: 2020-05-01 7:53:00
tags: tutorial, algorithm
class: post-template
subclass: 'post'
author: thomas
---

How would you like to set the price of how much you'd like to pay for your room, and then pay less than what you've asked to for? Plus all of your roommates get to do this as well! 

This is probably one of best and quickest utility driven ways to split housing costs with your roommates and ensures everyone is satisfied!

That sounds like an enticing algorithm, but does it work and do you have proof? Yes and yes! Before we jump right into the algorithm, I can share in brief the outcome of running this algorithm with my current roommates.
- I said that I was willing to pay *$900* for my room, but am only paying **$833.33**
- John was willing to pay *$1150* for his room, but he is only paying **$1066.67**
- Ian was willing to pay *$1400* for his room and is only paying **$1250**
 
How is the possible, does that cover all of the rent? Yes - Read on!

## The Basics Step By Step

Here are the basics of how fairly split the room costs using the one time stable roommate algorithm so you can use it right away practically. If you'd like to see a much more algorithmic version along with some proofs and simulations, please see [The Formal Algorithm and Proofs](#proofs)

1. Decide and order the general utility of each room as a group. For example, if there are 3 rooms, *A*, *B* and *C*, the group needs to agree on an ordering where *Utility(A) < Utility(B) < Utility(C)*. Essentially decide which rooms are generally more preferable than the others.
   - Don't go away! This is actually the trickiest step and the rest is pretty easy - if there are any disagreements, the square footage of the room should take precedence.
2. Each roommate will write down on a piece of paper how much they'd be willing to pay for each room. They need to ensure the following:
   - The sum of how much they are willing to pay for each room adds up to the total cost of the house
      - If the house costs *$3150* and there are 3 rooms, *A*, *B* and *C*, then *Cost(A) + Cost(B) + Cost(C) = $3150*
   - The order of utility must be followed.
      - For example, if there are 3 rooms, *A*, *B* and *C*, and the group decided *Utility(A) < Utility(B) < Utility(C)*, then *Cost(A) < Cost(B) < Cost(C)*.
   - Equally crucial, each roommate's paper must be private to all other roommates until **every** roommate is finished, otherwise other roommates may be able to game the system.
3. When all the roommates are done assigning how much they'd be willing to pay for each room, order the results for who would be willing to pay the highest for each room (see [Example Outcome](#example)).
4. The roommate that bids the highest for each room will receive that room for the mean price of all the other roommate cost assignments
   - Ties are rare as perceived utility is generally different per person, but can be broken using an coin or otherwise an *n* results probability device where n is the number of roommates
     - For example, if two roommates both picked *$1000* for the highest utility room, then a coin would determine which roommate actually gets the room
     - If three roommates all picked *$1400* for the highest utility room, then a dice split where 2 numbers are assigned to each roommate would determine which roommate gets the room.

#### Example Outcome <a name="example"></a>

|               | Room A (Small) | Room B (Medium) | Room C (Large)|
| :------------ |:-----:| :-----:| :-----:|
| Thomas   | $900  |  $1075 |  $1175 |
| John   | $825  |  $1150 |  $1175 |
| Ian   | $775  |  $975  |  $1400 |

Using the example outcome (which is actually a real life example that I used to split rooming costs with two other roommates), we can see the following assignment as a result of running through steps 1-3:
- The total cost of the 3 bedroom apartment is `$3150`, and the decided utility is `Utility(A) < Utility(B) < Utility(C)`.
- Thomas gets `Room A` for `$833.33` which is `AVG($900, $825, $775)`. This is amazing because Thomas was willing to pay `$900` for the room, but is actually only going to pay `$833.33`
- John gets `Room B` for `$1066.67` which is `AVG($1075, $1150, $975)`. This is equally amazing because John was willing to pay `$1150` for the room, but will actually be paying `$1066.67`
- Ian gets `Room C` for `$1250` which is `AVG($1175, $1175, $1400)`. It seemed like Ian really wanted the biggest room as he bid a high `$1400` for the room, but will only be paying `$1250` for it.
- Any one last sanity check to make sure we're not somehow paying less rent `833.33 + 1066.67 + 1250 = 3150`. Yes, combined, we are still paying the full rent!

Why is this better?
1. Each person will only pay *what they want or less* for the room they choose
2. Utility based

There are obviously other methods out there to split roommate costs, but each one of them is flawed in one way or another. But let's take a look at some of the current methods:
1. Equal split - divide costs equally across 
2. Split depending on square footage
3. Using the [Stable Roommate Algorithm](https://en.wikipedia.org/wiki/Stable_roommates_problem)

## An Example

## The Formal Algorithm and Proofs <a name="proofs"></a>

Let's define a couple of terms
- `t` is the total cost of the house
- `r` is the number of rooms and thus the number of roommates
- `$c_r$` is the 


<script async
  src="//mathjax.rstudio.com/latest/MathJax.js?config=TeX-MML-AM_CHTML">
</script>
$$T^{\mu\nu}=\begin{pmatrix}
\varepsilon&0&0&0\\
0&\varepsilon/3&0&0\\
0&0&\varepsilon/3&0\\
0&0&0&\varepsilon/3
\end{pmatrix},$$

### Simulation Runs

### 