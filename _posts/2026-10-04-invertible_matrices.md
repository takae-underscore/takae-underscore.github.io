---
title: Invertible Matrices
subtitle: 
layout: default
date: 2026-10-4
keywords: linear algebra
published: false
---


### 1. Introduction
I remember back when I took my first linear algebra class that half the class was taken up by a theorem called the Invertible Matrix Theorem, which listed many equivalent characterizations of an invertible matrix. At the time, I felt that even though I could see that each condition was equivalent to the others, it all felt very disconnected, which made it hard to remember the whole theorem. It also didn't help that the theorem was spread out over so many weeks. Looking back at it now though, it's very easy for me to see how everything is related, and so I thought it would be fun to write a post about it. Nothing I say here will be particularly formal since I'm just trying to give a broad idea of how things connect together and why they should make sense.

### 2. The Theorem
There are like a billion conditions that are equivalent to invertability, and not all of them are equally important. Wikipedia has a pretty good list of all the important conditions, so I'll state Wikipedia's version of the theorem here.

**Theorem (Invertible Matrix Theorem):** Let $$A$$ be a square $$n \times n$$ matrix over $$\C$$ (or $$\R$$, or any field $$k$$, but if you know what a field is you probably don't need this post). Then the following statements are equivalent:
1. $$A$$ is invertible under matrix multiplication.
2. The linear transformation $$\phi$$ which maps $$\vec{x}$$ to $$A\vec{x}$$ is invertible under function composition.
3. The transpose $$\mtrans{A}$$ is invertible.
4. $$A$$ is row-equivalent to the $$n\times n$$ identity matrix $$I_n$$.
5. $$A$$ is column-equivalent to the $$n\times n$$ identity matrix $$I_n$$.
6. $$A$$ has $$n$$ pivot positions.
7. $$A$$ has full rank.
8. $$A$$ has a trivial kernel.
9. The linear transformation $$\phi$$ as defined above is bijective. In other words, the equation $$A\vec{x} = \vec{b}$$ has a unique solution for every $$\vec{b}$$ in $$\C^n$$.
10. The columns of $$A$$ form a basis of $$\C^n$$. Equivalently, the column space of $$A$$ is $$\C^n$$.
11. The rows of $$A$$ form a basis of $$\C^n$$. Equivalently, the row space of $$A$$ is $$\C^n$$.
12. The determinant of $$A$$ is nonzero.
13. 0 is not an eigenvalue of $$A$$.
14. The matrix $$A$$ can be expressed as a finite product of elementary matrices.

This might seem intimidating and you might not know all the terms that are used here, but don't worry! Things will start to make more sense as we go along.

### 3. Inverse Matrices and Linear Transformations
Everyone knows that dividing a nonzero number by itself yields 1. Everyone also knows that dividing is equivalent to multiplying by the reciprocal of that number, so 

$$2 \div 2 = \frac{1}{2}\cdot 2 = 1$$

Effectively, multiplication by $$\frac{1}{2}$$ reverses the action of multiplication by 2 since multiplying by 1 doesn't do anything, so we call $$\frac{1}{2}$$ the (multiplicative) inverse of 2. Similarly, the inverse of a square $$n\times n$$ matrix $$A$$ is a $$n\times n$$ matrix $$A^{-1}$$ such that $$A^{-1}A = I_n$$, where $$I_n$$ denotes the $$n\times n$$ identity matrix. $$I_n$$ takes the place of 1 here since multiplication by $$I_n$$ doesn't do anything. Since matrix multiplication isn't commutative, we also want to specify that $$AA^{-1} = I_n$$ since $$A$$ should be the inverse of $$\inv{A}$$. This takes care of condition 1.

If we specify a basis, then we can interpret multiplication by $$A$$ as the linear transformation $$\phi$$ which takes vectors $$\vec{x}$$ to $$A\vec{x}$$. If $$\inv{A}$$ exists, then multiplying by $$\inv{A}$$ can be interpreted as the linear transformation $$\inv{\phi}$$ taking vectors $$\vec{x}$$ to $$\inv{A}\vec{x}$$. Then obviously, applying the two transformations $$\phi$$ and $$\inv{\phi}$$ in any order results in nothing happening, which means that the two transformations are inverses under function composition. The converse is true too: $$\phi$$ having an inverse would mean that there's some linear transformation taking $$A\vec{x}$$ back to $$\vec{x}$$, so clearly some matrix that undoes $$A$$ has to exist. This takes care of condition 2.

Now that we've established this strong connection between invertible matrices and invertible linear transformations, we can now talk about what makes a linear transformation invertible instead of directly speaking of matrices.

### 4. Functions
Let's first understand the basic idea of a function, since linear transformations are just a particular kind of function.

Let $$X$$ and $$Y$$ be sets. Assign to each element $$x \in X$$ (the input) exactly one element $$y \in Y$$ (the output). The collection of these assignments is known as a **function** from $$X$$ to $$Y$$ and is written $$f\colon X\to Y$$. If $$x\in X$$, then the element of $$Y$$ assigned to $$x$$ is written $$f(x)$$. The set $$X$$ is called the **domain** of $$f$$ and $$Y$$ is called the **codomain** of $$f$$.

If you don't know what a set is, it's a list of elements where only distinct elements are considered. Therefore, $$\{1,2,3\} = \{1,3,2\} = \{1,1,2,3\}$$.

In simpler terms, a function is a machine where each input in the domain has exactly one output. This condition **only applies to the domain,** so it's not required for each element in the codomain to be the output of some input, and it's also okay for two inputs to both have the same output.

Examples and non-examples:
- $$f\colon \R \to \R$$, defined by $$f(x)=x$$ is a function.
- $$f\colon \R \to \R$$, defined by $$f(x)=x^2$$ is a function. Notice that the function never gives negative outputs, and multiple real numbers have the same square.
- $$f\colon \R \to \R$$, defined by $$f(x)=\sqrt{x}$$ is not a function because negative numbers don't have square roots. However, restricting the domain to only nonnegative real numbers would fix this problem.

#### Invertible Functions
To create a function from the set $$\{1,2,3\}$$ to the set $$\{4,5,6\}$$, I need to assign an element of $$\{4,5,6\}$$ to each element of $$\{1,2,3\}$$. The particular assignment is chosen by me. For instance, I could define a function $$f\colon \{1,2,3\} \to \{4,5,6\}$$ such that $$f(1) = 6$$, $$f(2)=4$$, and $$f(3) = 5$$. [INSERT PICTURE HERE]

I can also define a function $$\inv{f}\colon \{4,5,6\} \to \{1,2,3\}$$ such that $$\inv{f}(4)=2$$, $$\inv{f}(5)=3$$, and $$\inv{f}(6)=1$$. You will notice that applying $$f$$ and then applying $$\inv{f}$$ brings me back to where I started, and if I apply the two functions in the opposite order, I also return to where I started. (Side note:$$\inv{f}$$ is pronounced f-inverse).[INSERT IMAGE HERE]

Hence $$f$$ and $$\inv{f}$$ reverse each other's effects. We call these **inverse functions,** and both $$f$$ and $$\inv{f}$$ are considered **invertible.** Not every function is invertible, though. You'll notice that $$f$$ has an interesting property: elements in the domain and codomain are paired together with no overlap between pairs. In fact, this property is **equivalent** to invertability. The reason for this is somewhat technical and not really worth talking about now. Essentially, it comes from the requirement that every input in the domain needs to have an output, and that the "reversing" should go both ways (i.e. $$\inv{f}$$ must reverse the effects of $$f$$, and $$f$$ must also reverse the effects of $$\inv{f}$$ for $$f$$ and $$\inv{f}$$ to be considered inverses). I'm not going to prove this because it doesn't really matter, but it's not that hard to do it yourself, so give it a try if you're interested. I think it's fairly understandable though, each input in the domain is sent to exactly one output, and the inverse function needs to send that output back to the input and only that input because of the definition of a function. This needs to be true for every element in both the domain and the codomain (which is the domain of the inverse function) again because of the requirements in the function definition, which effectively pairs up elements of the domain with elements in the codomain.

Anyway, the point is that we now don't need to explicitly find an inverse function to be able to tell if a function is invertible. We just need to know whether our function pairs up elements of the domain and codomain properly (i.e. with no overlap). How can we tell if this is the case? We can use two tests:
1. Does the function take more than input to the same output?
2. Is every element in the codomain hit by the function?
If Test 1 fails, then we would obviously have overlap between pairs. If Test 2 fails, then some element in the codomain has nothing to pair with. [INSERT IMAGE HERE]

If the function passes Test 1, then it's called **injective** or **1-1 (one-to-one).** If the function passes Test 2, then the function it's called **surjective** or **onto.** A function which is both injective and surjective is **bijective.** We can also call the function a **1-1 correspondence.** A more compact way to refer to injective, surjective, or bijective functions is to call them **injections, surjections, or bijections** respectively. With this terminology, we can now say that bijectivity is equivalent to invertibility.

#### Surjectivity and Images
I'd like to quickly mention an alternate way of viewing surjectivity which will be helpful later on. If $$f$$ is a function, then the set of elements that $$f$$ reaches in the codomain is called the **image** of $$f$$, written $$\ima{f}$$. You may also recognize this as being the **range** of $$f$$ instead. Since surjectivity requires every element of the codomain to be hit by $$f$$, this means that $$\ima{f}$$ must equal the codomain.

### 5. Invertible Linear Transformations
A linear transformation is invertible if it's invertible as a function. Since invertible functions are bijective functions, a linear transformation is invertible if it's bijective. It might just seem like I've replaced one word for another, but this is actually huge. With invertibility, we had to construct an inverse linear transformation despite not knowing if one even existed. Now, we can just check injectivity and surjectivity, which we have many ways of checking (as you will soon find out).

I'd like to now point out that a function with a domain and codomain that are different sizes can't possibly be bijective, since you wouldn't be able to get a partner for every element in either the domain or codomain. There just wouldn't be enough elements to make that possible. With vector spaces, "size" translates to dimension. So any non-square $$m\times n$$ matrix $$M$$ would instantly be disqualified from invertability since the associated linear transformation which takes $$\vec{x}$$ to $$M\vec{x}$$ would have domain $$\C^m$$ but codomain $$\C^n$$. These have different dimensions, so this linear transformation could not possibly be bijective.

Our discussion of bijective functions almost takes care of condition 9. Remember that we established that invertability of a $$n\times n$$ matrix $$A$$ was the same as invertability of the linear transformation $$\phi \colon \C^n \to \C^n$$ which takes $$\vec{x}$$ to $$A\vec{x}$$ (this requires specifying a basis to be defined, standard basis is usually assumed). $$\phi$$ being invertible is the same as $$\phi$$ being bijective, so that's the first part done. The second part is almost obvious, since solving $$\phi(\vec{x})=A\vec{x}=\vec{b}$$ for $$\vec{x}$$ amounts to finding the partner of $$\vec{b}$$, which can only be one vector by bijectivity. So this equation has a unique solution for any $$\vec{b}$$.

### 6. Injectivity and Surjectivity
So far we've reduced the question of invertibility to checking injectivity and surjectivity. But what if I told you that you only had to check one? It turns out that, since we're only considering linear transformations with domain and codomain of the same dimension, being injective automatically means that it's surjective too, and vice versa. To convince ourselves of this, let's think about a linear transformation $$\phi \colon \R^2 \to \R^2$$. Recall that we only need to know what $$\phi$$ does to the basis, since the action of $$\phi$$ on any other vector can be deduced from its action on the basis. If $$\phi$$ is injective, then it must take the two basis vectors to linearly independent vectors, or else you'd have some vectors being squashed together [INSERT IMAGE HERE]. The span of these transformed vectors, which is equivalent to $$\ima{\phi}$$ (this is true because $$\phi$$ preserves linear combinations), is all of $$\R^2$$, so $$\phi$$ is surjective.

On the other hand, if $$\phi$$ was surjective, then $$\ima{\phi}$$ must span all of $$\R^2$$, which means that our two independent directions must have been preserved by $$\phi$$. Since the action of $$\phi$$ on other vectors emulates the action of $$\phi$$ on the basis vectors, the fact that we haven't squashed any basis vectors together means that $$\phi$$ shouldn't have squashed anything else together either, so $$\phi$$ should also be injective.

Where does this leave us? Starting with a square matrix $$n\times n$$ matrix $$A$$, we know that it's invertible if, after choosing a basis, the associated linear transformation $$\phi \colon \C^n \to \C^n$$ is invertible, which is the same as bijectivity, which is the same as injectivity or surjectivity. Surjectivity is simple to check: since the span of the transformed basis vectors is $$\ima{\phi}$$, we just need to know what those transformed vectors are and whether they span the codomain ($$\C^n$$). Luckily, the columns of $$A$$ tell us where the basis vectors were sent to. The span of these columns is known as the column space of $$A$$, and if they span $$\C^n$$, then $$\phi$$ is surjective and therefore $$A$$ is invertible. This takes care of condition 10.

The dimension of the column space is called the **rank** of $$A$$, written $$\operatorname{rank}{A}$$. If the rank is equal to the dimension of the codomain, then we say $$A$$ has **full rank.** $$A$$ having full rank means that the column space of $$A$$ is $$n$$-dimensional, which means that the column space of $$A$$ is $$\C^n$$. This takes care of condition 7.

As for injectivity, we also have a simple but powerful way to check it. First, if $$\phi$$ is injective, then we shouldn't have any nonzero vectors going to 0; i.e. the only vector that is sent to 0 by $$\phi$$ should be 0. We can say this in a different way by first defining the **kernel** of $$\phi$$, denoted $$\ker{\phi}$$, to be the subspace of the domain which is sent to 0. You may recognize this as the **null space** instead. Then we can say that $$\ker{\phi}=\{0\}$$ if $$\phi$$ is injective. This much is obvious, but the cool part is that the other way is actually true as well: if $$\ker{\phi}={0}$$, then $$\phi$$ is injective. Somehow, injectivity for the 0 vector somehow translates to injectivity for everything, and I'm not going to prove it because it doesn't really teach us anything. If the kernel only contains 0, then we consider the kernel to be trivial because 0 is always in there anyway (i.e. no "nontrivial" elements). If we define $$\ker{A}$$ to mean $$\ker{\phi}$$, then if $$\ker{A}$$ is trivial, then $$\phi$$ is injective and thus bijective, so $$A$$ is invertible. This takes care of condition 8.

The image I want you have in your mind when thinking about all this is that if our linear transformation squashes vectors together, then it's not invertible. The things we've been talking about so far are precise ways to tell if this happens. We still have a couple more conditions to go, so keep this image in mind for those.

### Other Ways to Know If Vectors are Squashed Together
Assume that any linear transformation mentioned from now on is from $$\C^n$$ to $$\C^n$$.

One tool we can use to determine if vectors are squashed together is the **determinant.** The determinant of a matrix (more or less) tells you how the parallelogram (parallelepiped in higher dimensions) formed by the basis vectors is scaled by the linear transformation associated with the matrix. If this is 0, then this must mean that the transformed basis vectors are squashed together, so the linear transformation is not invertible. This takes care of condition 12.

Another tool we can use is **eigenvalues.** Sometimes a linear transformation will hold some (nonzero) vectors still and only scale them. Such a vector is called an **eigenvector,** and the amount it's scaled is its associated eigenvalue. It's possible that one eigenvalue will be associated with more than one eigenvector. Anyway, this is useful to us because if the linear transformation has 0 as an eigenvalue, that means that some nonzero vector was scaled down to 0, which makes the kernel nontrivial. Therefore, the linear transformation is not injective, so it's not invertible. This takes care of condition 13.

### 7. Systems of Equations
Recall that a matrix equation $$A\vec{x}=\vec{b}$$ can be interpreted as a system of equations. For example, for a $$2\times 2$$ matrix, we have

$$\pmat{A_{11}&A_{12}\\ A_{21}&A_{22}}\pmat{x\\ y} = \pmat{b_1\\ b_2}$$

which, after expansion, leaves us with the following system of equations:

$$\begin{cases}
  A_{11}x+A_{12}y=b_1 \\
  A_{21}x+A_{22}y=b_2
  \end{cases}$$

If $$A$$ is invertible, then $$A\vec{x}=\vec{b}$$ has a unique solution, so the system of equations also has a unique solution. You may recall that we can use **Gaussian elimination**, also known as **row reduction**, to solve the system of equations. I will illustrate the process with a simple example. Take $$A=\spmat{1&2\\ 3&1}$$ and  
$$\vec{b}=\spmat{4\\2}$$. Then to perform row reduction, I first construct the augmented matrix representing this system:

$$\amat{cc}{c}{1&2&4\\3&1&2}$$

Next, I can start applying the three elementary row operations to get a 1 in each of the diagonal entries and 0 everywhere else. Recall that the elementary row operations are:
1. Swapping rows
2. Multiplying a row by a scalar
3. Adding a multiple of one row to another

These row operations don't affect the solution of the system of equations, so applying them to my augmented matrix gives me another augmented matrix which is Basically the Same&trade;. The two augmented matrices are then considered **row equivalent.**
For this example, this process would play out like this:

$$\begin{aligned}
\amat{cc}{c}{1&2&4\\3&1&2} \xrightarrow{-3R_1+R_2} &\amat{cc}{c}{1&2&4\\0&-5&-10} \\
\xrightarrow{-{\tfrac{1}{5}}R_2} &\amat{cc}{c}{1&2&4\\0&1&2} \\
\xrightarrow{-2R_2+R_1} &\amat{cc}{c}{1&0&0\\0&1&2}
\end{aligned}$$

Bringing back the variables, then this augmented matrix tells us that our system is Basically the Same&trade; as the system 

$$\begin{cases}
x=0 \\
y=2
\end{cases}$$

Since this system obviously can't have any other solutions, that means that $$\vec{x} = \spmat{0\\2}$$ is the unique solution to our original matrix equation. This doesn't yet mean that $$A$$ is invertible though, since we need a unique solution for every $$\vec{b}$$. Let's choose another $$\vec{b}$$ and see what happens. Let $$\vec{b}=\spmat{1\\5}$$. Then row reduction plays out like this:

$$\begin{aligned}
\amat{cc}{c}{1&2&1\\3&1&8} \xrightarrow{-3R_1+R_2} &\amat{cc}{c}{1&2&1\\0&-5&5} \\
\xrightarrow{-{\tfrac{1}{5}}R_2} &\amat{cc}{c}{1&2&1\\0&1&-1} \\
\xrightarrow{-2R_2+R_1} &\amat{cc}{c}{1&0&3\\0&1&-1}
\end{aligned}$$

The system we end up with once again has a unique solution, so our original system did too. Therefore, $$\vec{x}=\spmat{3\\-1}$$ is the unique solution to this equation. You'll notice that I did exactly the same row operations to arrive at the solution even though the actual system I was solving was different. This actually makes sense, since by condition 9, unique solutions for every equation $$A\vec{x}=\vec{b}$$ is dependent on the invertibility of $$A$$, and has nothing to do with $$\vec{b}$$. That means that we can just completely ignore $$\vec{b}$$ and just work with the matrix $$A$$ itself.

So what is it about the matrix $$A$$ that we've been working with forces unique solutions? Well, row reduction turns our original system into a system that directly tells you what the variables have to be. It's this resulting system that determines if there's a unique solution or not. What if this resulting system just didn't force one of the variables to be one specific number? In the two-variable case, this could look one of two ways: either one variable just isn't involved at all, or the two variables are in a dependent relationship. More explicitly, we could have have a system like this:

$$\begin{cases}
x=5
\end{cases}$$

or we could have a system like this:

$$\begin{cases}
x+y=2
\end{cases}$$

Neither of those are really a system at all... they're just both one equation. As augmented matrices (with two rows), the first system looks like this:

$$\amat{cc}{c}{1&0&5\\0&0&0}$$

and the second system looks like this:

$$\amat{cc}{c}{1&1&2\\0&0&0}$$

You can verify that when expanded, these matrices do represent their respective systems, both with an extra condition that $$0+0=0$$, but this is obviously always true and hence imposes no restriction on the variables. We can conclude from this that if a matrix forces unique solutions, then it is row-equivalent to a matrix with 1's along the diagonal, which specify what values each variable should take. On the other hand, a matrix that doesn't force unique solutions ends up with at least one row of all zeroes. Of course, the matrix with 1's along the diagonal is none other than the identity matrix.

Putting everything together, we have that an $$n\times n$$ matrix $$A$$ is invertible if it is row-equivalent to the $$n\times n$$ identity matrix $$I_n$$, which takes care of condition 4.

#### Pivot Positions
The pivot positions are the positions of the first 1 in each row after row reduction. If there are no 1's in a row, then that row doesn't have a pivot position. If an $$n\times n$$ matrix doesn't have $$n$$ pivot positions, then at least one row is all zeroes and therefore the matrix is not invertible. On the flipside, if it does have all $$n$$ pivot positions, then the matrix is row-equivalent to the identity matrix, so it is invertible. This takes care of condition 6.

### 8. Transpose Matrices
The **transpose** of a matrix $$A$$ is the matrix where all the entries are reflected along the diagonal (i.e. rows become columns and columns become rows) and is denoted $$\mtrans{A}$$. This part is kind of weird because there's not really any nice interpretation of the transpose I know of that's also not super involved. I'd honestly just think of it as something people got just from messing around with matrices, since turning rows into columns isn't particularly hard to come up with. Then a natural thing to explore would be whether the invertibility of a matrix is connected with the invertibility of its transpose. There are definitely other ways to go about doing this than what I'm going to do (which is just brute force proving it), but I don't think those other approaches makes anything easier or more enlightnening, so I'm just going to go with this.

If a matrix $$A$$ was invertible, then you might expect its transpose to be invertible too, just because it seems like it should be. A natural guess for this inverse would be the transpose of $$\inv{A}$$. So let's see if this is true. We want to show that $$\mtrans{(\inv{A})}\mtrans{A} = \mtrans{A}\mtrans{(\inv{A})} = I_n$$.

At this moment, you might think that it would be nice if we could combine the transposes, like you can do with exponentials with the same power ($$a^2b^2=(ab)^2$$). 

**If that were true**, then we could say

$$\mtrans{(\inv{A})}\mtrans{A}=\mtrans{(\inv{A}A)}=\mtrans{I_n}=I_n \\
\mtrans{A}\mtrans{(\inv{A})}=\mtrans{(A\inv{A})}=\mtrans{I_n}=I_n$$

and we would be done. So let's see if this transpose-combining property is true. We want to show that for matrices $$A$$ and $$B$$, $$\mtrans{(AB)} = \mtrans{A}\mtrans{B}$$. Recall that the entry of $$A$$ in the $$i$$th row and $$j$$th column is given by $$A_{ij}$$.

$$\begin{aligned}
(\mtrans{A}\mtrans{B})_{ij} &= \sum\limits_{k=1}^n\mtrans{A}_{ik}\mtrans{B}_{kj} && \text{by definition of matrix multiplication}\\
&= \sum\limits_{k=1}^nA_{ki}B_{jk} && \text{by definition of transpose}\\
&= \sum\limits_{k=1}^nB_{jk}A_{ki} \\
&= (BA)_{ji} = \left(\mtrans{(BA)}\right)_{ij}
\end{aligned}$$

So $$\mtrans{(AB)} = \mtrans{B}\mtrans{A}$$. Oh no! It turns out we were wrong! But have no fear, almost nothing changes for us. Simply swapping $$A$$ and $$\inv{A}$$ a couple times will give us our result:

$$\mtrans{(\inv{A})}\mtrans{A}=\mtrans{(A\inv{A})}=\mtrans{I_n}=I_n \\
\mtrans{A}\mtrans{(\inv{A})}=\mtrans{(\inv{A})A}=\mtrans{I_n}=I_n$$

Therefore, if $$A$$ is invertible, then $$\mtrans{A}$$ is invertible. Moreover, $$\inv{(\mtrans{A})}=\mtrans{(\inv{A})}$$ On the other hand, if $$\mtrans{A}$$ is invertible, then since $$\mtrans{(\mtrans{A})} = A$$, the transpose of $$\mtrans{A}$$ (which is $$A$$) is invertible. This takes care of condition 3.

With this, we can also get conditions 5 and 11 for free. If $$A$$ is invertible, then $$\mtrans{A}$$ is invertible, so $$\mtrans{A}$$ is row-equivalent to the identity. Applying row operations to the transpose is the same as applying column operations to $$A$$, since transposing swaps rows and columns. Therefore, $$A$$ becomes column-equivalent to the identity. Similarly, the column space of the transpose is the same as the row space of $$A$$, so since $$\mtrans{A}$$ is invertible, the column space is $$\C^n$$ and so the row space of $$A$$ is $$\C^n$$.

### 9. The Final Condition
Finally, we arrive at condition 14. An **elementary matrix** is a matrix which encodes the action of an elementary row operation. For instance, the matrix $$\spmat{0&1\\1&0}$$ swaps the two rows of a $$2\times 2$$ matrix. Condition 14 is then quite obvious, since a matrix is invertible if it's row-equivalent to the identity. Then, we can work backwards from the identity, reversing each step by applying the appropriate elementary matrix until we get back to our original matrix. Multiplying by the identity is equivalent to doing nothing at all, so we're left with a product of elementary matrices, and this product is finite since row reduction is a finite process.

### 10. Conclusion
With that, we've gone through all the conditions of the Invertible Matrix Theorem. Who knows if that even helps lmao