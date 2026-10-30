---
title: Who Cares About These Ratios Anyway?
subtitle: The origins of trigonometry and where the modern definitions taught in school come from.
layout: default
date: 2026-10-22
keywords: trigonometry
published: true
---

### 1. Introduction
Recently I've been teaching a student the fundamentals of trigonometry. Naturally, I started with introducing sine, cosine, and tangent as ratios of the sides of a right triangle. But as I was doing so, I realized that I had no clue why anyone would think to make those ratios in the first place, and that left me very unsatisfied. It's not really necessary to know these things if you just want to know the math, but it's not very interesting for the learner if it's just like, well here's a thing and you can do some things with it and it's magic basically.... So I like to make up some stories that motivate the math, and although I say "make up", they're usually based on history. It's just that I don't really care about being super accurate if it doesn't make the math feel any more motivated.

I should quickly mention that I will be assuming some level of geometric knowledge, though only basic knowledge that I didn't bother proving when I was researching. At most, I will assume that you know what similar and congruent triangles are and how to tell when triangles are similar or congruent. I will also assume the Pythagorean Theorem.

With that said, let's start investigating the origins of the trigonometric functions that we use so much today.

### 2. Ancient Greek and Roman Astronomy
The origins of the sine function start with the Ancient Greeks in the form of the **chord function.** A **chord** is a line segment with endpoints on a circle. We can associate a central angle of the circle by drawing two radii from the center to the endpoints of the chord. Since this central angle also specifies an arc of the same degree, we can also associate a chord with the arc defined by the chord's endpoints.

<table align="right" style="padding-left: 10px">
    <caption align="bottom" style="text-align: left; padding-left: 13px"><i>A chord in orange and its corresponding arc in purple at various angles up to 180 degrees.</i></caption>
    <tr><td><img src="/assets/trigonometry images/Chord.webp" alt="A chord." height="250px"></td></tr>
</table>

This correspondence between angles (or arcs) and chords (specifically, the lengths of chords) defines the chord function. We will denote this by $$\crd{\theta}$$, where $$\theta$$ is the central angle corresponding to the chord. While the Greeks would've used the degree of an arc instead of the central angle, the formulations are equivalent, so I'm just going to use central angles to make it more familiar. The Greeks did not define the chord function for angles over 180 degrees, presumably because it wasn't necessary and there wasn't a natural way to do so.

The Greek astronomer Hipparchus of Rhodes is credited with the making the earliest known chord table. Unfortunately, most of his work has been lost, and the only reason we even know about his chord table is because Claudius Ptolemy referenced it in his *Almagest,* a huge textbook containing all the astronomical knowledge obtained up until that point. Ptolemy improved on Hipparchus's chord table by finding the chord lengths for angles in half-degree increments up to 180 degrees, whereas Hipparchus's table had increments of 7.5 degrees.

To understand how they used the chord function in astronomy, let's look at a problem on page 7-9 from G.J. Toomer's translation of the *Almagest,* which is what he calls a "typical calculation involving trigonometry". I won't be covering the actual context in which the problem appears because it's very involved. Instead, I'll make up my own context which seems plausible enough to me.

#### The Retrograde Motion of Mars

<table align="right" style="padding-left: 10px">
    <caption align="bottom" style="text-align: left; padding-left: 13px"><i>The apparent retrograde motion of Mars. GIF by <a href="https://commons.wikimedia.org/wiki/File:Apparent_retrograde_motion_of_Mars_in_2003.gif">Eugene Alvin Villar (seav)</a>, <a href="https://creativecommons.org/licenses/by-sa/4.0">CC BY-SA 4.0</a>, via Wikimedia Commons</i></caption>
    <tr><td><img
        src="https://upload.wikimedia.org/wikipedia/commons/7/70/Apparent_retrograde_motion_of_Mars_in_2003.gif?utm_source=commons.wikimedia.org&utm_campaign=index&utm_content=original" 
        alt="Mars doing a loop in the sky." width="250px"></td></tr>
</table>

Mars (and other objects) are subject to a strange phenomenon where they occasionally appear to move move backwards in the sky. This is called **apparent retrograde motion.**

We know now that the Earth revolves around the Sun along with the other planets. Since Mars takes slightly less than twice as long as Earth to complete its orbit, it completes about a quarter of its orbit in the same time that it takes Earth to complete half its orbit. If Mars is at the right position in its orbit, Earth will then pass it by since Earth completes its orbit faster. This makes it look like Mars is lagging behind in the sky. Earth kind of "slows down" at some point because it needs to follow its curved orbit, and Mars is able to catch up and resumes its normal motion in the sky. See the animation for a better idea of what this looks like.

However, the Ancient Greeks did not believe in heliocentrism, and tried to adapt the geocentric model to explain this phenomenon. The theory they came up with was that Mars was actually on a small orbit called an **epicycle,** which itself revolved around the Earth in an orbit called the **deferent.** Ptolemy improved on this model and formalized it in the *Almagest.* This **did** explain the retrograde motion of the planets, but it also eventually became pretty insane and hard to work with. Reducing the number of epicycles was one of the advantages of the Copernican heliocentric model, although apparently he eventually added a bunch of epicycles anyway. Even so, the Ptolemaic model was very accurate at predicting the locations of planets since any orbit shape can be traced out by adding more and more epicycles (essentially a Fourier series).


<table align="center">
    <tr>
        <td style="padding-right: 10px"><img src="/assets/trigonometry images/Epicycles.webp" alt="Since Mars is orbiting on its epicycle, it looks like it's moving backwards from Earth." width="240px"></td>
        <td><img src="/assets/trigonometry images/RetrogradeMars.webp" alt="Changes in viewing angle from Earth trace out a path which doubles back on itself." width="426px"></td>
    </tr>
    <tr>
        <td width="240px"><i>The theory of epicycles explains Mars's backwards motion by putting it on a secondary orbit.</i></td>
        <td width="426px"><i>Heliocentrism explains the phenomenon using changes in viewing angle from Earth. The red line being traced by the dashed line is how we would see the location of Mars from Earth.</i></td>
    </tr>
</table>

If you were an astronomer, something you might want to do is predict where Mars will be in the sky at some time. More specifically, you want to predict how far Mars will lag behind in the sky due to its epicyclic motion. You would know from the model the location of Mars and its epicycle, and what you want to know is the difference in angle between the expected position $$C$$ (the center of the epicycle) and the actual position $$M$$. Suppose at this time, Mars will be 30 degrees to the right of the line $$EC$$, where point $$E$$ is the Earth.

We know that $$EC = 60$$, $$CM = 2.5$$ (marked in green) and $$\angle{ECM} = 30^\circ$$. Note that the length of $$EC$$ is arbitrarily chosen to be 60 because it doesn't matter for our angle calculations as long as everything is scaled accordingly. The number 60 comes from the Babylonians, who used base 60 instead of base 10 like we do. Hipparchus started using circles with radius 60 when he made his chord table, and this became the convention for a long time afterwards.

<table align="right" style="padding-left: 10px">
    <tr><td><img src="/assets/trigonometry images/PtolemyProblem.webp" alt="Figure for chord problem." height="400px"></td></tr>
</table>

Math is something where you only really understand things after getting your hands dirty (figuratively), so I'm going to make this calculation an exercise. I'll write up the full solution at the end, but I recommend you try to do it yourself; it's fun!

**<ins>Exercise 1</ins>**

>**Objective:** Find $$\angle{CEM}$$. 
>
>**Hint**: In every step, you should try to involve similar triangles somehow. The information gathered from similarity will help you a lot.
>1. Drop an altitude from $$M$$ to $$EC$$. Call the point of intersection $$K$$. Note that $$KM$$ is perpendicular to $$EC$$ by definition.
>2. Show that we can construct a circle with diameter $$CM$$ that goes through $$K$$ in the following way:
>    1. Let $$O$$ be the midpoint of $$CM$$.
>    2. Show that $$KO$$ is equal to $$CO$$ and $$OM$$.
>    3. Conclude that $$K$$ is on the circle with diameter $$CM$$.
>3. Use the fact that, for a circle with **radius 60,** <br>
>$$\crd{60^\circ} = 60$$ to find the length of $$KM$$.
>4. Find the length of $$EM$$ (use the Pythagorean Theorem).
>5. Use the result proven in (2) to construct a circle with diameter $$EM$$ that goes through $$K$$.
>6. Use the fact that, for a circle with **radius 60,** $$\crd{2.47^\circ} = 2.594$$ find the central angle corresponding to the chord $$KM$$ of >the circle constructed in (5).
>7. Show that $$\angle{KEM}$$ (which is the same angle as $$\angle{CEM}$$) is exactly half of the angle calculated in (6).

### 4. The Half-Chord

<table align="left" style="padding-right: 10px">
    <caption align="bottom" style="text-align: left; padding-left: 3px; padding-right: 10px">Jyā, <i>shown in solid orange and</i> koti-jyā, <i>shown in solid grey. The dashed lines show that both are half a chord. The corresponding arcs are colored purple and blue respectively.</i></caption>
    <tr><td><img src="/assets/trigonometry images/Sine.webp" alt="Animation of the half-chord function." width="250px"></td></tr>
</table>

At some point, the Greek and Roman idea of chords made its way to India, where a chord was called *jyā,* which also meant bowstring. They must have decided later that the *ardha-jyā,* or **half-chord** was more useful, as the mathematician and astronomer Aryabhata created a table of half-chords in his work, the *Aryabhatiya.* Eventually, the term *jyā* was used to refer to the half-chord for simplicity, presumably because no one ever used full chords. They also gave a name to the half-chord of the complementary angle, calling it *koti-jyā.*

If you worked through the exercise in the previous section, you may have noticed that using chords is pretty terrible, since we never actually wanted to use full chords or the angles associated with them. Instead, we wanted to know the length of half the chord and the angle associated with half the chord. So it seems fairly natural to move towards using a half-chord function instead of the chord function.

The *jyā* function later was translated to Arabic as *jība,* and when the function got back to Europe, it was misinterpreted as *jaib,* meaning something like "breast pocket", since they are written the same way in Arabic. So it was translated to *sinus* in Latin, meaning the same thing, which became English "sine". Since *koti-jyā* was the sine of the complement angle, it became *complementi sinus,* and from there became "cosine".

It's important to note that at this time, sine was the **length** of the half-chord, which depends on the radius of the circle. I will capitalize the function (i.e. Sine) if it refers to a length from now on to differentiate it from the modern definition.

### 5. Telling Time with Shadows
In the medieval Islamic world, being able to tell the time precisely was a big deal because their religion required them to pray at certain times of the day. To tell the time, they used an instrument called a **gnomon,** which is the part of a sundial that casts a shadow. In it's simplest form, it's just a vertical stick in the ground. Then to go from the length of the shadow to the time of day, they utilized the Sine function, which had made its way over to the Middle East from India. Their techniques are recorded in *The Exhaustive Treatise on Shadows* by Iranian Khwarazmian polymath Abu Reyhan Muhammad ibn Ahmad al-Biruni.

Al-Biruni defined two types of shadows: the **direct shadow** and the **reverse shadow.** The direct shadow is a shadow cast by a vertical gnomon in the ground, while the reverse shadow is the shadow cast below a horizontal gnomon on the wall. Suppose that we had a gnomon casting a direct shadow. How could we use that to tell the time? First, some setup. Imagine you are the gnomon. Point towards the Sun and draw a circle going directly overhead. Then the Sun and the direct shadow are in the same plane as the circle. This circle is called a **circle of altitude.**

We want to know the angle between the horizon plane and the Sun's direction. Because we are only looking for the angle, it doesn't actually matter what the radius of the circle of altitude is. For simplicity, I take the radius of the circle of altitude to be the same length as the gnomon. You will also notice that I center the circle of altitude on the top of the gnomon in the figure and not the ground. That should make sense, because the top of the gnomon determines where the shadow is cast. Therefore, the horizon plane is the horizontal axis of the circle of altitude, and when the Sun reaches this plane the shadow cast is infinitely long. Now, let's actually figure out how to calculate the angle between the Sun and the horizon.

<table align="center">
    <caption align="bottom" style="text-align: left; padding-left: 3px"><i>$$DE$$ is direct shadow cast by the gnomon $$CD$$.</i></caption>
    <tr><td><img src="/assets/trigonometry images/DirectShadow.webp" alt="Figure of a direct shadow." width="600px"></td></tr>
</table>

**<ins>Exercise 2</ins>**
>**Objective:** Find $$\angle{ACB}$$ using the measurable quantities $$CD$$ and $$DE$$.
>1. Show that $$\triangle{ABC}$$ and $$\triangle{CDE}$$ are similar.
>2. Find the length of $$AB$$.
>3. Justify to yourself that with the appropriate Sine table, knowing the length of $$AB$$ and the length of $$CD$$ is enough to determine $$\angle{ACB}$$.

With this, we have obtained, for a particular gnomon length, a procedure to find the angle between the horizon plane and the Sun (which tells us the time of day) from the length of the direct shadow cast by the gnomon. Notice that we can also reverse the process and find the length of the direct shadow based on the angle between the horizon plane and the Sun. Hence one could pre-calculate the length of the shadow for various angles and produce a table of shadow lengths for a quick reference when trying to tell the time.

Since I made the radius of the circle of altitude the same length as the gnomon, you may notice that the shadow is **tangent** to the circle of altitude, i.e. it touches the circle at exactly one point (tangent comes from Latin *tangere,* meaning "to touch"). Because of this, you might think that the length of the direct shadow would be called the "Tangent" of the angle between the horizon and the Sun (capital "T" since it depends on the radius of the circle). However, because the angle that directly defines the length of the shadow is the angle between the gnomon and the line of sunlight, i.e. $$\angle{DCE}$$, it's more accurate to call it the "Tangent of the complementary angle", or **Cotangent.**

We can also give a name to the length of $$CE$$, the shadow's "hypotenuse". Since it's part of the line of sunlight cutting through the circle, we call it the **Cosecant,** where "secant" comes from Latin *secare*, meaning "to cut". The reason for the "co-" prefix is the same as Cotangent.

For the reverse shadow, we can construct at the following figure in a similar way to the direct shadow:

<table align="center">
    <caption align="bottom" style="text-align: left; padding-left: 3px"><i>$$DE$$ is reverse shadow cast by the gnomon $$CD$$.</i></caption>
    <tr><td><img src="/assets/trigonometry images/ReverseShadow.webp" alt="Figure of a reverse shadow." width="600px"></td></tr>
</table>

We can once again find the angle between the horizon plane and the Sun using the length of the shadow. This isn't worth making into an exercise, but you should convince yourself that this can be done.

Once again, the shadow is tangent to the circle of altitude. However, this time the angle which defines the shadow is equal to the angle between the horizon plane and the Sun. So it makes sense to simply call this the **Tangent.** We can also call the length of $$CE$$ **Secant** for the same reason.

By the 10th century, all six modern trigonometric functions were used. However, they were not yet thought of in terms of right triangles.

### Generalization
With all six trigonometric functions defined, let's turn to the problem of generalization. Currently, there's a lot of baggage associated with our functions which makes them hard to use outside of the context they were originally defined in. For instance, to use the Sine function, you would have to construct the appropriately sized circle for "half-chord" to make any sense. This is not very convenient because, if you recall from Exercise 1 with the chord function, typically we don't really use the circle for anything other than justifying our usage of the function. It would be better if we could come up with an alternate characterization that needs the least amount of context possible.

A common way to do this in math is to base our definitions on properties we want to have. For example, applying the Pythagorean Theorem to $$\triangle{CDE}$$ in the figure of the reverse shadow gives us that, for a specified gnomon length (radius) $$r$$, $$r^2 + \operatorname{Tan^2}{\theta} = \operatorname{Sec^2}{\theta}$$. Then, if we have a right triangle with an interior angle of $$\theta$$ and the leg adjacent to $$\theta$$ is length $$r$$, then this triangle is congruent to $$\triangle{CDE}$$ by the ASA congruence theorem. To satisfy the Pythagorean identity above, the other leg must be length $$\operatorname{Tan}{\theta}$$ and the hypotenuse must be length $$\operatorname{Sec}{\theta}$$. In this way, the constraint imposed by this Pythagorean identity completely determines the values of $$\operatorname{Tan}{\theta}$$ and $$\operatorname{Sec}{\theta}$$. This means that we can use this condition equivalently to the original definition of the two functions.

The definition of $$\operatorname{Tan}{\theta}$$ would then look like:
> **Definition:** Suppose we have a right triangle with an interior angle $$\theta$$ such that the length of the leg adjacent to $$\theta$$ has length $$r$$. Then we call the length of the leg opposite to $$\theta$$ the **Tangent** of $$\theta$$.

We can redefine the other functions similarly for a specified radius $$r$$ by using the Pythagorean identities $$\operatorname{Sin^2}{\theta} + \operatorname{Cos^2}{\theta} = r^2$$ and $$\operatorname{Cot^2}{\theta} + r^2 = \operatorname{Csc^2}{\theta}$$. For Sine and Cosine, we didn't directly involve right triangles originally, but it should be trivial to prove that the Pythagorean identity is true. Thus, we obtain the following presentation:

<table align="center">
    <caption align="bottom" style="text-align: left; padding-left: 3px"><i>The side lengths of these three triangles define the six trigonometric functions.</i></caption>
    <tr><td><img src="/assets/trigonometry images/Triangles.webp" alt="Three triangles which define trigonometric functions." width="600px"></td></tr>
</table>

#### So Where Do Ratios Come In?
At this point, we're still defining the trigonometric functions in terms of length. So why did they come to represent ratios? I couldn't find that much information about this, but it seems to naturally come from using $$r=1$$ to calculate trigonometric tables. Let's see how this could be the case.

Looking back at Exercise 1 again, something annoying we had to deal with was that the chord table was calculated for a circle of radius 60. This made it so that in Step 3 we had to scale down the result from the chord table by the appropriate factor, which we had to do an extra calculation to find. To simplify things, we could instead calculate chord tables using radius 1, which makes the scaling factor equal to the radius of our circle (this can be shown easily using the properties of similar triangles).

In Step 6, we wanted to find the central angle corresponding to the chord $$KM$$. To do this, we had to scale up our circle by the appropriate scaling factor to obtain a circle of radius 60 so that we could use the chord table. With a chord table calculated for a radius of 1, we would instead simply divide the length of $$KM$$ by the radius of the circle to find the right length to reference the chord table with, i.e. we would use the entry which says $$\crd{2.47^\circ} = \frac{KM}{EM/2}$$. It's not hard to see how $$\crd{}$$ could be seen as a ratio of the chord and radius lengths, rather than a chord length of a circle with radius 1.

Similarly, it's easy to imagine that calculating trigonometric tables for $$r = 1$$ would lead to the trigonometric functions being seen as ratios of the sides of right triangles.

In history, it was Georg Joachim Rheticus, Copernicus's only student, who introduced this formulation of trigonometric functions. This was quite a big change for the people of his time, since they had been using arcs of the circle instead of central angles like we've been doing. Thus, discarding the circle entirely would've been pretty foreign for them since it was fundamentally tied to the concept of trigonometric functions. In our case, I've been using angles the whole time so it was pretty easy.

### The Modern Era
Currently, none of our functions are defined for any angles more than 90 degrees. You might recall that the values of $$\sin$$, $$\cos$$, etc. for other angles may end up negative. But of course, neither lengths nor ratios of lengths can be negative! To extend the definition of these functions, we would have to stop thinking about trigonometry geometrically, and instead think about it more abstractly so that concepts like "negative length" can make sense.