<!-- section start -->
<!-- attr: { class:'slide-title', showInPresentation:true, hasScriptWrapper:true, style:'' } -->
# Combinatorics
##  Brief Overview of Combinations, Permutations and Binary Vectors
<div class="signature">
    <p class="signature-course">Combinatorics</p>
    <p class="signature-initiative">Telerik Software Academy</p>
    <a href="http://academy.telerik.com" class="signature-link">http://academy.telerik.com</a>
</div>

<!-- section start -->
<!-- attr: { showInPresentation:true, hasScriptWrapper:true, style:'' } -->
# Table of Contents
- Definitions in Combinatorics
- Permutations
- Combinations
  - Pascal's Triangle
- Binary Vectors
- Resources

<!-- section start -->
<!-- attr: { class:'slide-section', showInPresentation:true, hasScriptWrapper:true, style:'' } -->
# Definitions in Combinatorics

<!-- attr: { showInPresentation:true, hasScriptWrapper:true, style:'' } -->
# Combinatorics
- `Combinatorics` is a branch of mathematics
  - Concerning the study of finite or countable discrete structures
- Combinatorial problems arise inmany areas of pure mathematics
  - Notably in algebra, probabilitytheory, topology, geometry, physics, chemistry, biology, etc.

<!-- attr: { showInPresentation:true, hasScriptWrapper:true, style:'' } -->
# Combinations
- "My fruit salad is a combination of grapes, strawberries and bananas" 
  - We don't care what order the fruits are in
    - "bananas, grapesand strawberries" or "grapes, bananas andstrawberries" &rarr; it is the same salad
- If the `order doesn't` matter, it is a `combination`

<!-- attr: { showInPresentation:true, hasScriptWrapper:true, style:'' } -->
# Permutations / Variations
- "The combination to the safe is 4385".
  - Now we do care about the `order`
  - "8453" would not work, nor would "4538"
  - It has to be exactly 4-3-8-5
- If the `order does matter` it is a `permutation` / `variation`
  - A permutation / variation is an ordered Combination
- Easy to remember: "Permutation ... Position"

<!-- attr: { showInPresentation:true, hasScriptWrapper:true, style:'' } -->
# Factorial
- The factorial function (`!`) just means to multiply a series of descending natural numbers
  - n! = n × (n - 1)!
    - 0! = 1
    - 1! = 1
    - 4! = 4 × 3 × 2 × 1 = 24
    - 7! = 7 × 6 × 5 × 4 × 3 × 2 × 1 = 5040
    - 20! = 20 x 19 x ... x 2 x 1 = 2432902008176640000

<!-- attr: { showInPresentation:true, style:'font-size:40px' } -->
# Factorial
- Source code
  - Iterative

```cpp
int factorial(int n)
{
    int result = 1;
    for(int i = 2; i <= n; i++)
        result = result * i;
    return result;
}
```
  - Recursive

```cpp
int factorial(int n)
{
    if (n == 0) return 1;
    return factorial(n - 1) * n;
}
```

<!-- section start -->
<!-- attr: { class:'slide-section', showInPresentation:true, hasScriptWrapper:true, style:'' } -->
# Variations

<!-- attr: { showInPresentation:true, hasScriptWrapper:true, style:'' } -->
# Variations
- `Variations (with repetitions)`
  - Easiest to calculate
- When you have `n` things tochoose from ... you have `n` choices each time!
- When choosing k of them,the variations are:
  - `n` × `n` × ... × `n` (k times) = n<sup>k</sup>

<!-- attr: { showInPresentation:true, hasScriptWrapper:true, style:'' } -->
# Variations
- Example: in the lock below, there are 10 numbers to choose from (0, 1, … 9) and you choose 3 of them:
  - 10 × 10 × 10 (3 times) = <code>10<sup>3</sup></code> = 1 000 variations
- All variations from (0, 0, 0) to (9, 9, 9) 

<!-- attr: { showInPresentation:true, hasScriptWrapper:true, style:'' } -->
# Variations
- Generation

```cpp
void GenerateVariations(int index)
{
  if (index >= k)
    Print(arr);
  else
    for (int i = 0; i < n; i++)
    {
      arr[index] = i;
      GenerateVariations(index + 1);
    }
}
```

<!-- attr: { class:'slide-section demo', showInPresentation:true, hasScriptWrapper:true, style:'' } -->
# Variations with Repetitions
##  [Demo]()

<!-- attr: { showInPresentation:true, style:'' } -->
# Variations without Repetition
- Suppose we have 16 billiard balls
  - But maybe you don't want to choose them all, just 3 of them, so that would be only
    - 16 × 15 × 14 = 3360
    - There are 3360 different ways that 3 pool balls could be selected out of 16 balls
  - 16! / 13! = 16 × 15 × 14
- where n is the number of things to choose from, and you choose k of them (No repetition, order matters) 

<!-- attr: { showInPresentation:true, hasScriptWrapper:true, style:'' } -->
# Variations without Repetition
- Example: 
  - How many words of 2 `different` letters can you make with 4 letters { a, b, c, d }?
```
ab, ac, ad, ba, bc, bd, ca, cb, cd, da, db, dc
```
- How to generate variationswithout repetitions?
  - The same way like variations with repetitions
  - Just use each element at most once

<!-- attr: { showInPresentation:true, hasScriptWrapper:true, style:'' } -->
# Variations without Repetitions
- Generation

```cpp
void GenerateVariationsNoReps(int index)
{
  if (index >= k)
    PrintVariations();
  else
    for (int i = 0; i < n; i++)
      if (!used[i])
      {
        used[i] = true;
        arr[index] = i;
        GenerateVariationsNoReps(index + 1);
        used[i] = false;
      }
}

GenerateVariationsNoReps(0);
```

<!-- attr: { class:'slide-section demo', showInPresentation:true, hasScriptWrapper:true, style:'' } -->
# Variations without Repetitions
##  [Demo]()

<!-- section start -->
<!-- attr: { class:'slide-section', showInPresentation:true, hasScriptWrapper:true, style:'' } -->
# Permutations

<!-- attr: { showInPresentation:true, hasScriptWrapper:true, style:'' } -->
# Permutations
- Less number of available choices each time
- What order could `16` pool balls be in?
- After choosing, ball `9` we can't choose the same ball again
  - First choice  = `16` possibilities
  - Second choice = `15` possibilities, etc., etc.
- Total permutations:
  - 16 × 15 × 14 × ... × 2 × 1 = `16!` = 20 922 789 888 000

<!-- attr: { showInPresentation:true, hasScriptWrapper:true, style:'' } -->
# Permutations
- Generation

```cpp
void perm(int arr[], int n, int k)
{
	if (k >= n)
		print(arr);
	else
	{
		perm(arr, k + 1);
		for (int i = k + 1; i < n; i++)
		{
			std::swap(arr[k], arr[i]);
			Perm(arr, k + 1);
			std::swap(arr[k], arr[i]);
		}
	}
}
```

<!-- attr: { class:'slide-section demo', showInPresentation:true, hasScriptWrapper:true, style:'' } -->
# Generating Permutations
##  [Demo]()

<!-- attr: { showInPresentation:true, style:'font-size:40px' } -->
# Permutations with Repetitions
- We have a set of elements, with repetitions
  - E. g. set = { 3, 5, 1, 5, 5 }
- We want to generate all unique permutations (without duplicates):

```
{1, 3, 5, 5, 5} {1, 5, 3, 5, 5} {1, 5, 5, 3, 5} {1, 5, 5, 5, 3}
{3, 1, 5, 5, 5} {3, 5, 1, 5, 5} {3, 5, 5, 1, 5} {3, 5, 5, 5, 1}
{5, 1, 3, 5, 5} {5, 1, 5, 3, 5} {5, 1, 5, 5, 3} {5, 3, 1, 5, 5}
{5, 3, 5, 1, 5} {5, 3, 5, 5, 1} {5, 5, 1, 3, 5} {5, 5, 1, 5, 3}
{5, 5, 3, 1, 5} {5, 5, 3, 5, 1} {5, 5, 5, 1, 3} {5, 5, 5, 3, 1}
```
- We want to efficiently avoid the repeating ones
  - i.e. to work fast for {1, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5}

<!-- attr: { showInPresentation:true, hasScriptWrapper:true, style:'' } -->
# Permutations with Repetitions
- Generation

```cpp
// arr is sorted
void PermuteRep(int arr[], int start, int n)
{
	print(arr);
	for (int left = n - 2; left >= start; left--)
	{
		for (int right = left + 1; right < n; right++)
			if (arr[left] != arr[right])
			{
				std::swap(arr[left], arr[right]);
				permuteRep(arr, left + 1, n);
			}
		var firstElement = arr[left];
		for (int i = left; i < n - 1; i++)
			arr[i] = arr[i + 1];
		arr[n - 1] = firstElement;
	}
}
```

<!-- attr: { class:'slide-section demo', showInPresentation:true, hasScriptWrapper:true, style:'' } -->
# Generating Permutations with Repetitions
##  [Demo]()

<!-- section start -->
<!-- attr: { class:'slide-section', showInPresentation:true, hasScriptWrapper:true, style:'' } -->
# Combinations

<!-- attr: { showInPresentation:true, hasScriptWrapper:true, style:'' } -->
# Combinations
- Order does not matter!
- Two types of combinations:
  - `Repetition is allowed`
    - Coins in your pocket
    - 5, 5, 20, 20, 20, 10, 10
  - `No repetition`
    - Lottery numbers
    - TOTO 6/49, 6/42, 5/35
    - 2, 14, 15, 27, 30, 33

<!-- attr: { showInPresentation:true, style:'' } -->
# Combinations without Repetition
- Back to the 3 of 16 billiard balls
  - Many comb. will be the same
  - We don't care about the order
- Permutations w/o repetitionsreduced by how many ways the objects could be in order:
- This is how lotteries work (TOTO 6/49)
- Often called "n choose k"

<!-- attr: { showInPresentation:true, hasScriptWrapper:true, style:'' } -->
# Combinations without Repetitions
- Generation

```cpp
void combinations(int index, int start)
{
	if (index >= k)
		PrintCombinations();
	else for (int i = start; i < n; i++)
	{
		arr[index] = i;
		Comb(index + 1, i + 1);
	}
}

combinations(0, 0);
```

<!-- attr: { class:'slide-section demo', showInPresentation:true, hasScriptWrapper:true, style:'' } -->
# Combinationswithout Repetitions
##  [Demo]()

<!-- attr: { showInPresentation:true, hasScriptWrapper:true, style:'' } -->
# Pascal's Triangle
- The Pascal's triangle shows you how many combinations of objects withoutrepetition are possible
  - Go down to row "n" (the top row is 0)
  - Move along "k" places
  - The value there is your answer
- Build the triangle: start with "1" atthe top, then continue placingnumbers below it in a triangular pattern

<!-- attr: { showInPresentation:true, hasScriptWrapper:true, style:'' } -->
<!-- # Pascal's Triangle -->
- The triangle is symmetrical
  - Numbers on the left side haveidentical matching numbers onthe right side, like a mirror image
- Diagonals:
  - First diagonal – only “1”s
  - Second diagonal – 1, 2, 3, etc.
  - Third diagonal – triangular numbers
- Horizontal sums: powers of 2

<!-- attr: { showInPresentation:true, style:'font-size:38px' } -->
# Binomial Coefficients
- Calculate using recursion:

```cpp
long long binom(int n, int k) 
{
	if (k > n)
		return 0;
	if (0 == k || k == n)
		return 1;
	return binom(n - 1, k - 1) + binom(n - 1, k);
}
```
- Calculate using dynamic programming:

```cpp
long long m[MAX], i, j;
for (i = 0; i <= n; i++) {
	m[i] = 1;
	if (i > 1) {
		if (k < i - 1) j = k;
		else j = i - 1;
		for (; j >= 1; j--)
			m[j] += m[j - 1];
	}
} // The answer is in m[k]
```

<!-- attr: { showInPresentation:true, hasScriptWrapper:true, style:'' } -->
# Combinations with Repetition
- Ice-cream example
  - 5 flavors of ice-cream: banana,chocolate, lemon, strawberry and vanilla
  - 3 scoops
- How many combinations will there be?
- Let's use letters for the flavors: {b, c, l, s, v}
  - {c, c, c} (3 scoops of chocolate)
  - {b, l, v} (one each of banana, lemon and vanilla)
  - {b, v, v} (one of banana, two of vanilla)

<!-- attr: { showInPresentation:true, hasScriptWrapper:true, style:'' } -->
# Combinations with Repetition
- Ice-cream example
  - n = 5 things to choose from, choose k = 3 of them
  - Order does not matter, and we can repeat
- Think about the ice cream being in boxes
  - arrow means move, circle means scoop
  - {c, c, c} (3 scoops of chocolate)
  - {b, l, v} (banana, lemon, vanilla)
  - {b, v, v} (banana, two of vanilla)

<!-- attr: { showInPresentation:true, style:'' } -->
# Combinations with Repetition
- We have a simpler problem to solve
  - How many different ways can you arrange arrows and circles?
  - 3 circles (3 scoops) and 4 arrows (we need to move 4 times to go from the 1st to 5th container)
  - There are k + (n - 1) positions, and we want to choose k of them to have circles
-  

<!-- attr: { showInPresentation:true, hasScriptWrapper:true, style:'' } -->
# Combinations with Repetitions
-Generation

```cpp
void combinations(int index, int start)
{
	if (index >= k)
		PrintVariations();
	else for (int i = start; i < n; i++)
	{
		arr[index] = i;
		CombReps(index + 1, i);
	}
}

combinations(0, 0);
```

<!-- attr: { class:'slide-section demo', showInPresentation:true, hasScriptWrapper:true, style:'' } -->
# Generating Combinations with Repetitions
##  [Demo]()

<!-- attr: { showInPresentation:true, hasScriptWrapper:true, style:'' } -->
# Combinatorial Formulas
- Calculating the number of permutations, variations, combinations
  - Use the well known formulas:
- Source: http://users.telenet.be/vdmoortel/dirk/Maths/PermVarComb.html

<!-- section start -->
<!-- attr: { class:'slide-section', showInPresentation:true, hasScriptWrapper:true, style:'' } -->
# Binary Vectors

<!-- attr: { showInPresentation:true, hasScriptWrapper:true, style:'' } -->
# Binary Vectors
- Some problems can be reformulated in terms of `binary vectors` – (1, 0, 1, 1, 1, 0, …)
- Combinatorial properties of binary vectors:
  - Number of binary vectors of length n: 2<sup>n</sup>.
  - Number of binary vectors of length `n` and with `k` `1` is C(n, k) (we choose k positions for n `1`)

<!-- attr: { showInPresentation:true, style:'' } -->
# Gray Code
- Gray code (a.k.a. reflected binary code) is a binary numeralsystem where two successive values differ by only one bit

```cpp
int n = 4, a[1000];

void backgray(int k)
{
	if (0 == k)
	{
		print();
		return;
	}
	a[k] = 1;
	forwgray(k - 1);
	a[k] = 0;
	backgray(k - 1);
}
void forwgray(int k)
{
	if (0 == k)
	{
		print();
		return;
	}
	a[k] = 0;
	forwgray(k - 1);
	a[k] = 1;
	backgray(k - 1);
}

forwgray(n);
```

<!-- attr: { class:'slide-section demo', showInPresentation:true, hasScriptWrapper:true, style:'' } -->
# Gray Code
##  [Demo]()

<!-- section start -->
<!-- attr: { id:'questions', class:'slide-section' } -->
# Questions
## Combinatorics
