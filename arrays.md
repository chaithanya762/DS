##Shortcuts 

#Hashing
1. Two Sum → "Need = Target - Current"

Clue:

Two numbers

Given target

Find pair

Logic:

need = target - current

If need exists → answer
Otherwise → store current


Java:

int need = target - nums[i];

if (map.containsKey(need)) {
    return new int[]{map.get(need), i};
}

map.put(nums[i], i);


Shortcut:

Two numbers + target → HashMap

Mental phrase:

"I need a partner for this number."

2. Contains Duplicate → "Have I Seen This?"

Clue:

Duplicate

Already seen

Repeated value

Logic:

If already in Set → duplicate
Otherwise → add


Java:

if (set.contains(num)) {
    return true;
}

set.add(num);


Shortcut:

Duplicate / already seen → HashSet

3. Valid Anagram → "Same Frequency?"

Clue:

Anagram

Same characters

Same frequency

Permutation

Logic:

Count characters in S
Subtract characters in T
Everything should end at 0


Java:

count[s.charAt(i) - 'a']++;
count[t.charAt(i) - 'a']--;


Shortcut:

Anagram / permutation / frequency → Counting

4. Group Anagrams → "Same Signature = Same Group"

Clue:

Group anagrams

Group similar strings

Logic:

eat → aet
tea → aet
ate → aet

Same key → same group


Java:

char[] chars = str.toCharArray();
Arrays.sort(chars);

String key = new String(chars);

map.putIfAbsent(key, new ArrayList<>());
map.get(key).add(str);


Shortcut:

Group similar strings → Create a common/canonical key

Day 2 — Arrays
5. Product of Array Except Self → "LEFT × RIGHT"

Clue:

Product of everything except current

Cannot use division

Logic:

answer[i] = everything LEFT × everything RIGHT


Visual:

        i
[ ← LEFT | RIGHT → ]

answer[i] = leftProduct × rightProduct


Shortcut:

Everything except current → Prefix + Suffix

6. Maximum Subarray → "CONTINUE or RESTART?"

Clue:

Maximum sum

Contiguous subarray

Logic:

Should I continue?

currentSum + num

OR

start fresh?

num


Choose the larger:

currentSum = Math.max(num, currentSum + num);


Shortcut:

Maximum contiguous sum → Kadane's Algorithm

Mental phrase:

"If my past is hurting me, throw it away."

7. Best Time to Buy/Sell Stock → "CHEAPEST BEFORE ME"

Clue:

Buy once

Sell later

Maximum profit

Logic:

profit = currentPrice - cheapestPriceSoFar


Then update:

cheapest = min(cheapest, current)


Java:

int profit = price - minPrice;

maxProfit = Math.max(maxProfit, profit);

minPrice = Math.min(minPrice, price);


Shortcut:

Buy cheap → sell high → Running Minimum

8. Majority Element → "CANCEL DIFFERENT"

Clue:

Element appears more than n/2

Majority element

Logic:

Same candidate → +1
Different candidate → -1
count == 0 → choose new candidate


Shortcut:

More than n/2 → Boyer-Moore Voting Algorithm

Mental phrase:

"Cancel different people; the majority survives."

🔥 Master Shortcut Table
Problem Clue	Think
Two numbers + target	HashMap
Duplicate / already seen	HashSet
Anagram / frequency	Counting
Group similar strings	Canonical Key
Everything except current	Prefix + Suffix
Maximum contiguous sum	Kadane
Buy low, sell later	Running Minimum
More than n/2	Boyer-Moore
🧠 The 8 Patterns in One Place
DAY 1 — HASHING

Two Sum
→ Need = Target - Current

Contains Duplicate
→ Have I seen it?

Valid Anagram
→ Same frequency?

Group Anagrams
→ Same key?


DAY 2 — ARRAYS

Product Except Self
→ LEFT × RIGHT

Maximum Subarray
→ KEEP or RESTART

Best Stock
→ MIN SO FAR

Majority Element
→ CANCEL DIFFERENT

When you see a new problem:

                 Problem
                    ↓
              Find the clue
                    ↓
          Identify the pattern
                    ↓
         Choose data structure
                    ↓
                Write code
                    ↓
          Check complexity

Example 1 — Two Sum

"Find two numbers that add to target."

Think:

Two numbers
    ↓
Complement
    ↓
HashMap

Example 2 — Contains Duplicate

"Find duplicate."

Think:

Have I seen this?
    ↓
HashSet

Example 3 — Maximum Subarray

"Find maximum contiguous sum."

Think:

Contiguous + maximum sum
    ↓
Kadane

Example 4 — Product Except Self

"Find product of everything except current."

Think:

Everything except current
    ↓
LEFT × RIGHT
    ↓
Prefix + Suffix

Example 5 — Best Stock

"Find maximum stock profit."

Think:

Buy cheap
    ↓
Minimum price so far
    ↓
Sell at current price

⭐ Golden Rule

Don't start with:

"What code should I write?"

Start with:

"What pattern does this problem belong to?"

Pattern recognition is the main skill we're building through the 100 DSA problems.

📌 Ultra-Short Revision Sheet
1. Two Sum
   → Target - Current
   → HashMap

2. Contains Duplicate
   → Seen before?
   → HashSet

3. Valid Anagram
   → Same frequency?
   → Counting

4. Group Anagrams
   → Same signature?
   → Canonical key + HashMap

5. Product Except Self
   → LEFT × RIGHT
   → Prefix + Suffix

6. Maximum Subarray
   → Continue or restart?
   → Kadane

7. Best Stock
   → Cheapest before me
   → Running Minimum

8. Majority Element
   → Cancel different
   → Boyer-Moore

Core Patterns to Remember
HashMap
→ Need a value / complement / frequency

HashSet
→ Seen before / duplicate

Frequency Array
→ Count characters

Canonical Key
→ Group equivalent items

Prefix + Suffix
→ Everything except current

Kadane
→ Maximum contiguous sum

Running Minimum
→ Buy low / best previous value

Boyer-Moore
→ Majority > n/2
