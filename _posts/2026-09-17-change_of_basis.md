---
title: The Change-of-Basis Matrix
subtitle: After several years, I finally understand the change-of-basis matrix.
layout: default
date: 2026-09-17
keywords: linear algebra
published: false
---

I recently came across a linear algebra problem about change of basis, which went something like this:

**Problem:** Let $$B_{old} = \{\left(\begin{smallmatrix}1\\0\end{smallmatrix}\right),\left(\begin{smallmatrix}1\\1\end{smallmatrix}\right)\}$$ and $$B_{new} = \{\left(\begin{smallmatrix}-1\\1\end{smallmatrix}\right),\left(\begin{smallmatrix}0\\1\end{smallmatrix}\right)\}$$ be bases for $$\R^2$$. Find the change of basis matrix from $$B_{old}$$ to $$B_{new}$$.

To be completely honest, I kinda forgot what the change-of-basis matrix was supposed to look like (I'm pretty rusty on my linear algebra). I didn't want to just look it up though, so I tried to figure it out. My thought process went as follows:

**Solution(?):** Changing basis means that if I have some vector expressed in terms of $$B_{old}$$, then I want to figure out how that same vector would be expressed in terms of $$B_{new}$$. What exactly does it mean to express a vector in terms of a basis? Well, every vector has a unique representation as a linear combination of basis vectors. Let's first label the basis vectors of $$B_{old}$$ as $$u_1, u_2$$ and label the basis vectors of $$B_{new}$$ as $$v_1,v_2$$. So in more precise terms, changing basis would mean that if we have a arbitrary vector $$w$$ which is represented in terms of the old basis as $$\left(\begin{smallmatrix}a\\ b\end{smallmatrix}\right)$$, i.e. $$w=au_1+bu_2$$, then I want to translate it into a linear combination of $$v_1,v_2$$ to get the representation of the same object in the new basis.

So how can I do that? Well, I thought that since $$w$$ is a linear combination of $$u_1,u_2$$, then I should first figure out what $$u_1,u_2$$ are as linear combinations of $$v_1,v_2$$, since if $$u_1 = c_1v_1 + c_2v_2$$ and  
$$u_2 = d_1v_1+d_2v_2$$, then

$$\begin{aligned}
w &= au_1+bu_2 \\ 
&= a(c_1v_1+c_2v_2)+b(d_1v_1+d_2v_2) \\ 
&= (ac_1+bd_1)v_1+(ac_2+bd_2)v_2 
\end{aligned}$$

In other words, $$w$$ is represented as $$\left(\begin{smallmatrix}a\\ b\end{smallmatrix}\right)$$ in the old basis, and in the new basis this becomes $$\left(\begin{smallmatrix}ac_1+bd_1\\ ac_2+bc_2\end{smallmatrix}\right)$$.

So now the task has turned into figuring out what the $$c_i$$ and $$d_i$$ are supposed to be. Writing  
$$u_1=c_1v_1+c_2v_2$$ out in terms of the concrete vectors gives us

$$\begin{aligned}
\left(\begin{matrix}1\\0\end{matrix}\right) &= c_1\left(\begin{matrix}-1\\1\end{matrix}\right) + c_2\left(\begin{matrix}0\\1\end{matrix}\right) \\
&= \left(\begin{matrix}-c_1\\ c_1+c_2\end{matrix}\right) \\
&= \left(\begin{matrix}-1&0\\1&1\end{matrix}\right)\left(\begin{matrix}c_1\\ c_2\end{matrix}\right)
\end{aligned}$$

Now we can just solve for $$\left(\begin{smallmatrix}c_1\\ c_2\end{smallmatrix}\right)$$ using basic linear algebra techniques to find that $$c_1=-1$$ and $$c_2=1$$. A similar argument shows that $$d_1=-1$$ and $$d_2=2$$.

Putting everything together, we have that $$w = (-a-b)v_1+(a+2b)v_2$$, giving us the representation of $$w$$ in terms of the new basis, i.e. $$\left(\begin{smallmatrix}-a-b\\ a+2b\end{smallmatrix}\right)$$.

With so many different ways to refer to $$w$$ now, I'm going to formalize it by letting $$w_{old}=\left(\begin{smallmatrix}a\\ b\end{smallmatrix}\right)$$ and $$w_{new} = \left(\begin{smallmatrix}-a-b\\ a+2b\end{smallmatrix}\right)$$. $$w$$ will be reserved for talking about the object itself, independent of any basis. If this sounds redundant, remember that $$w_{old}$$ and $$w_{new}$$ are just **descriptions** of $$w$$. Think of it as $$w$$ being an apple, and $$w_{old}$$ and $$w_{new}$$ being the words "apple" in English and "蘋果" in Chinese. The two words both refer to the same object, the apple, but neither of them are **actually** the apple.

To recap, we started with an arbitrary vector $$w$$'s coordinate representation in terms of the old basis  
($$w_{old}$$) and then did some calculations to obtain $$w$$'s coordinate representation in terms of the new basis ($$w_{new}$$). Now to get the change-of-basis matrix, we need to figure out how to get from $$w_{old}$$ to $$w_{new}$$. This is quite easy, since we can simply use matrix multiplication to decompose $$w_{new}$$ as follows:

$$\left(\begin{matrix}-a-b\\ a+2b\end{matrix}\right) = \left(\begin{matrix}-1&-1\\1&2\end{matrix}\right)\left(\begin{matrix}a\\ b\end{matrix}\right)$$

Let $$A = \left(\begin{smallmatrix}-1&-1\\1&2\end{smallmatrix}\right)$$. Then we have that $$w_{new} = Aw_{old}$$, so $$A$$ must be the change-of-basis matrix. $$\square$$.

Well that wasn't too hard, was it? Except it's **WRONG**!!! I looked on Wikipedia afterwards and found that the actual change-of-basis matrix should be the **inverse** of $$A$$, which would be $$\left(\begin{smallmatrix}-2&-1\\1&1\end{smallmatrix}\right)$$. If we call this matrix $$B$$, then the relationship we obtain is $$w_{old} = Bw_{new}$$.

But doesn't that seem really weird? Like, now we have a vector expressed in terms of the new basis, and after applying the change-of-basis matrix, we get expression of that vector in the old basis. In other words, it seems like we're transitioning from the new basis to the old basis, which should be the **opposite** of what we want. This really confused me, and I'm pretty sure it confused me when I learned about it initially too (which is probably why I couldn't remember how it worked).

Things become clearer if we're transitioning from the standard basis. These basis vectors we've been working with are themselves expressed in terms of the standard basis, which kind of obscures what's going on. So let's do the problem again, but instead we'll transition from the standard basis, $$E = \{\left(\begin{smallmatrix}1\\0\end{smallmatrix}\right),\left(\begin{smallmatrix}0\\1\end{smallmatrix}\right)\}$$ to $$B_{old}$$.

**Solution:** Let $$e_1,e_2$$ denote the standard basis vectors. We'll do this exactly the same way, so we'll first need to find out what the coordinate representations of $$e_1,e_2$$ are in terms of $$B_{old}$$; i.e. figure out what $$c_1,c_2,d_1,d_2$$ are but for this particular case. This can be done pretty easily with some trial and error since the vectors are simple: $$c_1=1,c_2=0,d_1=-1,d_2=1$$. Then for some vector $$w$$ with standard coordinate representation $$\left(\begin{smallmatrix}a\\ b\end{smallmatrix}\right)$$, 