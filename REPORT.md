# DP In Practice Assignment

## Part 1: Plain Aggregates & Privacy
### Q1
Most basically, I know that Kinan's music taste can't be any of the options on the form that are not represented in this count. Also (if I didn't know anything about Kinan's music taste), I'd think it's much more likely that he likes Hip Hop or Pop because those are much more common than other genres.

### Q2
I know that Kinan likes rock/metal music (it's probably his favorite), and that he's a fifth year PhD (he probably isn't less than 22 y/o for undergrade + 5 for PhD = 27+), so it's safe to say that he's probably either the 27 year old who likes Rock or the 30 year old who likes Metal. That being said, he also leaked his age at group lunch last week so I know it's 30 & Metal.

### Q3
We can tell that Kinan's favorite color is Black because there's only one person with age 30, so we know that that one person with age 30 and favorite color black must be Kinan.

### Q4
We know that Kinan will be in the 25 and up range, so his favorite sport must be either Soccer or Basketball.

### Q5
Since Kinan would have also been in the 25 and up range, his favorite sport last year must have been either Soccer, American Football or E-Sports. Assuming that his favorite sport didn't change in the last year, this means that it must have been **Soccer** all along.

## Part 2: Implementing Differential Privacy
### Q6
With the starting epsilon of 0.01, the numbers are kind of all over the place and they don't really seem to reflect the original data. The flipside of this is that the data is very private and it would be much more difficult to seperate out a specific person. As the epsilon value increases, the data becomes more and more resemblant of the original data (with more utility), but it becomes a lot less private.

### Q7
The most likely value on the distribution (see [this plot](dp-plot.png)) seems to be 1 which perfectly corresponds to the actual value if we run the unnoised query. For different values of the privacy parameter, the distribution plot becomes more spread out (as you'd expect) which provides more privacy but less accuracy.

## Part 3: Differential Privacy and Composition

### Q8
*From before writing `composition.py`:* Even though each query is noised, running many many times, you can begin to notice that the noised average age of "more than 10 years" is often much greater than the others. Although definitely not conclusive, this would lead me to believe that Kinan has 10+ years of programming experience. This could potentially be wrong if 

*From after:* After running the attack, I'm less confident that Kinan has to have 10+ years of programming experience. It appears that the average age for both 10+ and 8-10 years is both 26, which would lead me to believe Kinan could realisticially be in either group. This assumption could definitely be wrong if Kinan was hiding in one of the lower classes and his average age is just being masked by a bunch of younger people.

### Q9
However, when combining that with the count dataset (in which the # of people w/ 8-10 years appears to be 1 while the # with 10+ appears to be 2), I'm thinking that the one person w/ 8-10 years must be 26, while the 2 with 10+ could very likely be Kinan (30) and some go-getter 22 year old. This gives me high confidence that Kinan has 10+ years of programming experience. 

To summarize, Kinan is 30 years old, he likes Metal, Black & Soccer and he has 10+ years of programming experience.

### Q10
No, my class definitely doesn't keep you from overusing the dataset beyond a certain privacy budget, as it is simply a wrapper around the client that is actually making the queries, so a malicious (or just foolish) developer could bypass the wrapper that makes the DP checks and just go straight for the dataset directly, allowing them to greatly overuse it.

One potential way to block this would be to use cryptography within our budget tracking system to ensure that only a valid instance of the system (that has done the neccessary privacy checks) can decrypt sensitive user data for noising and disclosure, so malicious or falliable developers couldn't bypass those checks.


