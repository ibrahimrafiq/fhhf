# CSE191               Problem Set 5 Answer Key                  Fall 2013

(1) The statement A to prove is (\forall n)[Sq(n) --> -Sq(n+2)], where Sq is the predicate over Z defined by Sq(n) == (\exists a)[n = a^2].  This is first of all a good example of the difference between proof by contraposition and proof by contradiction.  For if you contrapose the implication, you wind up trying to prove instead the statement A' == (\forall n)[Sq(n+2) --> -Sq(n)], which is equivalent to (\forall n)[Sq(n) --> -Sq(n-2)].  So all this does is change the "+2" to "-2" in the statement, which doesn't make a useful difference.  Proof by contradiction, however, goes this way and works:

1. Assume "for sake of contradiction" that both n and n+2 are perfect squares.
2. "Unpack" what this means---that is, break down Sq(n) && Sq(n+2) into its own definition.
3. Derive a contradiction.
4. Conclude -Sq(n) v -Sq(n+2), which is the same as Sq(n) --> -Sq(n+2).
5. Since n stayed "arbitrary", conclude A by universal generation.

To carry out the second step after doing the first, it means that there exist integers a and b such that n = a^2 and n+2 = b^2.  Then b^2 - a^2 = 2.  By factoring this means (b+a)(b-a) = 2. Now either b+a is odd or b+a is even.  If odd, then b-a is odd too, so (b+a)(b-a) is odd, so it can't equal 2.  If even, then b-a is even too, so (b+a)(b-a) is a multiple of 4.  That means it can't equal 2 either (nor 6 nor 10...).  So we have a contradiction, and we're done.

Another way to reach the contradiction (and the answer I used in a previous year) is to note that since n=0 makes n+2 = 2 which is not a square, we need only consider n > 0.  Then we can take a to be the positive square root, and reason that the positive square root b of n+2 would have to be > a.  The least it can be as an integer is b = a+1.  But (a+1)^2 - a^2 = 2a+1 is a gap of at least 3 in view of a >= 1.  Thus b^2 can't possibly be within 2 of a^2.  So b^2 = n+2 where a^2 = n is a contradiction.


(2) Prove (\forall n)[Even(n) <--> Even(7n+4)], where Even(n) == (\exists k)[n = 2k].  Here unlike problem (1), both sides of the arrow are "positive", and this is conducive to trying direct proofs for each implication.  Fir5st, if n is even, then by existential-instantiation we can write n = 2k.  So 7n+4 = 7*2k + 4 = 14k+4 = 2*(7k+2).  Thus with k' = 7k+2, we have that 7n+4 = 2k'.  So k' is a witness for 7n+4 being even, so we conclude Even(7n+4) directly by existential instantiation.

For the reverse implication we have a choice.  We can do it directly though it may feel a bit "kludgey": By Even(7n+4) we can /take/ k such that 7n+4 = 2k.  Then 7n = 2k-4 = 2*(k-2).  Since 7 has no factor of 2, 7 must divide the k-2 part.  So n = 2*((k-2)/7) is still twice an integer, so it is even.  

The other way to do it is by contraposition.  Recall in this part we are proving Even(7n+4) --> Even(n).  The contrapositive is (-Even(n))-->(-Even(7n+4)), i.e., Odd(n) --> Odd(7n+4).  To prove it, assume Odd(n) (with regard to my lecture last month, this is a "premise you need to pop.")  This means there exists an integer k such that n = 2k+1.  Then 7n+4 = 7*(2k+1) + 4 = 14k + 7 + 4 = 14k + 10 + 1 = 2*(7k+5) + 1.  Hence with k' = 7k+5 we have that 7n+4 = 2*k' + 1.  This means Odd(7n+4), so popping the premise, we have proved Odd(n) --> Odd(7n+4).  This might feel less "kludgey" since you didn't have to argue about division, but it's a matter of taste.  Anyway, this illustrates the "feel" of direct proofs versus contraposition.



(3) Prove that for all real numbers n and m, (m = n or m = -n) <--> m^2 = n^2.  The "-->" part is immediate, since (-n)^2 = n^2.  For the "<--" part, we can do a direct proof: The hypothesis m^2 = n^2 is the same as n^2 - m^2 = 0.  By factoring this is equivalent to (n-m)(n+m) = 0.  By the principle ab = 0 <--> (a = 0 v b = 0), this is <==> to (n-m=0 v n+m=0).  This in turn is equivalent to (n = m v n = -m), which is equivalent to the goal of the "<--" part.  Hence we have proved both implications, so we have proved the equivalence.


(4) Prove the equivalence of (i) a < b, (ii) (a+b)/2 > a, and (iii) (a+b)/2 < b, for any real numbers a and b.  To show (i) --> (ii), use the definition a < b == (\exists p > 0) a + p = b.  So with regard to (ii), the left-hand side becomes (a+a+p)/2 = (2a+p)/2 = a + p/2, which (since p/2 is still positive) is > a.  For (ii) --> (iii), we can sue the following chain of equivalences:

      (a+b)/2 > a  <-->  a+b > 2a
	               <-->  b > a
				   <-->  2b > a+b
				   <-->  b > (a+b)/2
				   
But notice that since b > a <--> a < b trivially, we actually got (ii) --> (i) and also (i) --> (iii) in the middle of this already.  This suggests that the "circle" isn't really saving us any work.  But anyway to complete it all by showing (iii) --> (i), we just back-up the above: (a+b)/2 < b --> a+b < 2b --> a < b, done.


(5) Prove that for every irrational number r, there is a unique integer n such that |r - n| < 1/2.  First, r cannot equal m + 1/2 for any integer m, because that makes m + 1/2 into a rational number.  Thus there exists an integer n that is less than 1/2 away from r, either by rounding up or by rounding down.  The question is whether n is unique.

For sake of contradiction, suppose n is not unique.  Then there is another integer n' != n such that |n' - r| < 1/2, to go with |n - r| < 1/2.  By the triangle inequality, and the fact that |a - b| = |b - a| always, we get:

|n' - n| <= |n' - r| + |r - n| < 1/2 + 1/2 = 1,    so |n' - n| < 1.

But this is a contradiction of the fact that the distance between any two different integers must be at least 1.  Hence the uniqueness is proved.


(6) p136, 18(d) Show (A \ C) n (C \ B) is always empty.  In Venn diagrams, (A \ C) stays awaw from C, so it stays away from (C \ B) with is within C.  So the intersection is empty graphically.  In Boolean logic, the analogous proposition is (A & -C) & (C & -B), which includes C & -C, so it's always-false, which is the logical sign of the set being empty.  

(e) The Venn diagram for (B \ A) U (C \ A) has all of B that doesn't touch A, plus all of C that doesn't touch A, which is graphically the same as all of B-plus-C that doesn't touch A.  In logic terms, this is asking whether

(B & -A) v (C & -A) <--> (B v C) & -A.

The answer is yes---this is the distributive law tautology since "-A" is a proposition.


(7) Which of these define a valid function from Z into R?  
(a) "f(n) = +-n"?  Not a function: has 2 values.
(b) "f(n) = sqrt(n^2 + 1)": If the radical symbol means the positive square root, then yes, else no---two values.
(c) "f(n) = 1/(n^2 - 4)": No---not defined at the integer n = 2, not to mention n = -2, which cause division by zero.  However, you can "patch" it by excluding these two points, and what's left over is a valid function.  Often that's good enough.  


(8) Show that no function f from a set A can be onto its powerset P(A).  
All we need to do is exhibit a subset D of A that cannot be in Ran(f).
Define D = {a \in A: a is not in the set f(a)}.

Suppose for sake of contradiction (fsoc) that D is in the range of f. Then there exists d in A such that D = f(d).  Now ask the dangerous question: is d in D?  What we can establish about the answer is:

d \in D  <==>  d is in the set f(d), by D = f(d)
         <==>  d is not in the set f(d), by definition of D.

Thus d \in f(d) is equivalent to its negation.  This always evaluates to /false/, and rolls back the proof to deduce the negation of the "fsoc" assumption.  Hence D is not in the range of f, so f is not onto.

This is a "clean and abstract" version of Cantor's "Diagonal Set D" argument.  Notice that it does not care whether A and D are finite or infinite.  Of course for finite sets the conclusion is obvious since 2^n is always > n, but the fact that D gives you a particular set that is not in the range of f is still interesting.  The point is that the proof works also for infinite sets, any sets.  Thus the cardinality of P(A) is always greater than that of A, and |P(P(A))| > |P(A)|, ad-libidum.  That's Latin for "whatever you want", like an "ad-lib" being whatever dialogue you want on the spur of the moment, and tells you there are always higher grades of infinity than any infinity you think you comprehend.
