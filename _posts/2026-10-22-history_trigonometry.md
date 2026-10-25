---
title: Was Trigonometry Really About Triangles?
subtitle: The origins of trigonometry
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
    <caption align="bottom" style="text-align: left; padding-left: 12px"><i>A chord in orange and its corresponding arc in purple at various angles up to 180 degrees.</i></caption>
    <tr><td><img src="/assets/trigonometry images/Chord.webp" alt="A chord." height="250px"></td></tr>
</table>

This correspondence between angles (or arcs) and chords (specifically, the lengths of chords) defines the chord function. We will denote this by $$\crd{\theta}$$, where $$\theta$$ is the central angle corresponding to the chord. The Greeks did not define the chord function for angles over 180 degrees, presumably because it wasn't necessary and there wasn't a natural way to do so.

The Greek astronomer Hipparchus of Rhodes is credited with the making the earliest known chord table. Unfortunately, most of his work has been lost, and the only reason we even know about his chord table is because Claudius Ptolemy referenced it in his *Almagest,* a huge textbook containing all the astronomical knowledge obtained up until that point. Ptolemy improved on Hipparchus's chord table by finding the chord lengths for angles in half-degree increments up to 180 degrees, whereas Hipparchus's table had increments of 7.5 degrees.

To understand how they used $$\crd{}$$ in astronomy, let's look at a problem on page 7-9 from G.J. Toomer's translation of the *Almagest,* which is what he calls a "typical calculation involving trigonometry". I won't be covering the actual context in which the problem appears because it's very involved. Instead, I'll make up my own context which seems plausible enough to me.

#### The Retrograde Motion of Mars

<table align="right" style="padding-left: 10px">
    <caption align="bottom" style="text-align: left; padding-left: 12px"><i>The apparent retrograde motion of Mars. GIF by <a href="https://commons.wikimedia.org/wiki/File:Apparent_retrograde_motion_of_Mars_in_2003.gif">Eugene Alvin Villar (seav)</a>, <a href="https://creativecommons.org/licenses/by-sa/4.0">CC BY-SA 4.0</a>, via Wikimedia Commons</i></caption>
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

**Objective:** Find $$\angle{CEM}$$.
1. Drop an altitude from $$M$$ to $$EC$$. Call the point of intersection $$K$$. Note that $$KM$$ is perpendicular to $$EC$$ by definition.
2. Show that we can construct a circle with diameter $$CM$$ that goes through $$K$$ in the following way:
- Let $$O$$ be the midpoint of $$CM$$.
- Show that $$KO$$ is equal to $$CO$$ and $$OM$$ (not trivial).
- Conclude that $$K$$ is on the circle with diameter $$CM$$.
3. Use the fact that, for a circle with **radius 60,** <br>
$$\crd{60^\circ} = 60$$ to find the length of $$KM$$.
4. Find the length of $$EM$$.
5. Use the result proven in (2) to construct a circle with diameter $$EM$$ that goes through $$K$$.
6. Use the fact that, for a circle with **radius 60,** $$\crd{2.47^\circ} = 2.594$$ find the central angle corresponding to the chord $$KM$$ of the circle constructed in (5).
7. Show that $$\angle{KEM}$$ is exactly half of the angle calculated in (6).