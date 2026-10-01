---
title: Invertible Matrices
subtitle: 
layout: default
date: 2026-09-24
keywords: elementary algebra
published: true
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

### 3. Inverse Matrices and Linear Transformations.
Everyone knows that dividing a nonzero number by itself yields 1. Everyone also knows that dividing is equivalent to multiplying by the reciprocal of that number, so 

$$2 \div 2 = \frac{1}{2}\cdot 2 = 1$$

Effectively, multiplication by $$\frac{1}{2}$$ reverses the action of multiplication by 2 since multiplying by 1 doesn't do anything, so we call $$\frac{1}{2}$$ the (multiplicative) inverse of 2. Similarly, the inverse of a square $$n\times n$$ matrix $$A$$ is a $$n\times n$$ matrix $$A^{-1}$$ such that $$A^{-1}A = I_n$$, where $$I_n$$ denotes the $$n\times n$$ identity matrix. $$I_n$$ takes the place of 1 here since multiplication by $$I_n$$ doesn't do anything. Since matrix multiplication isn't commutative, we also want to specify that $$AA^{-1} = I_n$$ since $$A$$ should be the inverse of $$\inv{A}$$. This takes care of condition 1.

If we specify a basis, then we can interpret multiplication by $$A$$ as the linear transformation $$\phi$$ which takes vectors $$\vec{x}$$ to $$A\vec{x}$$. If $$\inv{A}$$ exists, then multiplying by $$\inv{A}$$ can be interpreted as the linear transformation $$\inv{\phi}$$ taking vectors $$\vec{x}$$ to $$\inv{A}\vec{x}$$. Then obviously, applying the two transformations $$\phi$$ and $$\inv{\phi}$$ in any order results in nothing happening, which means that the two transformations are inverses under function composition. The opposite is true too: $$\phi$$ having an inverse would mean that there's some linear transformation taking $$A\vec{x}$$ back to $$\vec{x}$$, so clearly some matrix that undoes $$A$$ has to exist. This takes care of condition 2.

