# PRACTICAL NO.: 01
AIM : To understand the concepts of trial, random experiment, sample point, and sample space using Python.
1) Find the sample space of n coins tossed.
2) Find the sample space of n dice tossed.
3) Find the sample space when a coin is tossed followed by a dice.

1) Find the sample space of n coins tossed.
Code :

n = int(input("Enter the number of coins: "))
sample_space = [""]
for i in range(n):
    new_space = []
    for outcome in sample_space:
        new_space.append(outcome + "H")
        new_space.append(outcome + "T")
    sample_space = new_space
print("Sample Space:")
print(sample_space)
print("Number of Outcomes =", len(sample_space))

formula : Number of outcomes for n coins: 2ⁿ

2) Find the sample space of n dice tossed.
Code :

n = int(input("Enter the number of dice: "))
sample_space = [()]
for i in range(n):
    new_space = []
    for outcome in sample_space:
        for face in range(1, 7):
            new_space.append(outcome + (face,))
            sample_space = new_space
print("Sample Space:")
print(sample_space)
print("Number of Outcomes =", len(sample_space))

formula : Number of outcomes for n dice: 6ⁿ
3) Find the sample space when a coin is tossed followed by a dice.
Code : 

sample_space = [(coin, die)
            for coin in ["H", "T"]
            for die in range(1, 7)]
print(sample_space)

formula : Coin followed by a die: 2 × 6 = 12




# PRACTICAL NO.: 02
AIM : To illustrate different types of events using Python.
1)Two dice are thrown.
(a) Find the sample space of the event so that
Code : 

event = []
for die1 in range(1, 7):
    for die2 in range(1, 7):
        if die1 + die2 not in (7, 11):
            event.append((die1, die2))
print("Sample Space:")
print(event)
print("Number of Outcomes =", len(event))


(b) the sum is a perfect square.
Code : 

perfect_square = []
for i in range(1, 7):
    for j in range(1, 7):
        if (i + j) in [4, 9]:
            perfect_square.append((i, j))

print("Event (Sum is a Perfect Square):")
print(perfect_square)
print("Number of outcomes =", len(perfect_square)


(c) the sum is divisible by 3
Code : 

divisible_by_3 = []
for i in range(1, 7):
    for j in range(1, 7):
        if (i + j) % 3 == 0:
            divisible_by_3.append((i, j))

print("Event (Sum is divisible by 3):")
print(divisible_by_3)
print("Number of outcomes =", len(divisible_by_3))

Formula : Probability of an event: P(E) = Number of favourable outcomes / Total number of outcomes

2)Three coins are tossed find the sample point of the event
Sample space  = ["HHH", "HHT", "HTH", "HTT",  "THH", "THT", "TTH", "TTT"]
n(S) = 8

(a) at least 1 heads
Code :

event = [(c1, c2, c3)
         for c1 in ["H", "T"]
         for c2 in ["H", "T"]
         for c3 in ["H", "T"]
         if "H" in (c1, c2, c3)]
print("Event (at least 1 head):")
print(event)
print("Number of outcomes =", len(event))
 formula : At least one Head: P(At least 1 Head) = 1 − P(No Head)

(b) no heads
Code :

event = []
for outcome in sample_space:
    if outcome.count("H") == 0:
        event.append(outcome)
print("No Heads:")
print(event)
print("Number of outcomes =", len(event))

Formula :  No Head in n coin tosses: P(No Head) = (1/2)ⁿ

(c) At the most one head
Code :

event = []
for outcome in sample_space:
    if outcome.count("H") <= 1:
        event.append(outcome)

print("At Most One Head:")
print(event)
print("Number of outcomes =", len(event))

Formula : At most one Head: P(At most 1 Head) = P(0 Head) + P(1 Head)




# PRACTICAL NO.: 03
Aim : Compute probability theoretically and compare with experimental probability.

a) Three coins are tossed simultaneously. Compute the theoretical probability and experimental probability of getting at least one head, and compare the results.
Code : 

import random
n = 1000
favorable = 0
for i in range(n):
c1 = random.choice(['H', 'T'])
c2 = random.choice(['H', 'T'])
c3 = random.choice(['H', 'T'])
if c1 == 'H' or c2 == 'H' or c3 == 'H':
               favorable += 1
experimental_probability = favorable / n
print("Experimental Probability =",
experimental_probability)


b) A die is rolled 200 times. Compute the theoretical and experimental probability of getting an even number and compare the results.
code:-

import random
n = 200
favorable = 0
for i in range(n):
roll = random.randint(1, 6)
if roll % 2 == 0:
favorable += 1
experimental_probability = favorable / n
print("Number of favorable outcomes:", favorable)
print("Experimental Probability =",
experimental_probability)

c) A card is drawn from a deck of 52 cards. Compute the theoretical and experimental probability of drawing a heart and compare the results.
Code : 

import random
n = 200
favorable = 0
for i in range(n):
card = random.randint(1, 52)
# Cards numbered 1–13 represent hearts
if 1 <= card <= 13:
favorable += 1
experimental_probability = favorable / n
print("Number of favorable outcomes:", favorable)
print("Experimental Probability =",
experimental_probability)

d) An integer is chosen at random from 200 digits. Compute the theoretical and experimental probability that it is divisible by 6
Code :-

import random
total = 200
count = 0
for i in range(1, total + 1):
    if i % 6 == 0:
        count += 1
theoretical_probability = count / total
print("Numbers divisible by 6:", count)
print("Theoretical Probability =", theoretical_probability)
trials = 10000
success = 0
for i in range(trials):
    num = random.randint(1, 200)
    if num % 6 == 0:
        success += 1
experimental_probability = success / trials
print("Experimental Probability =", experimental_probability)

formula :
1. Theoretical probability: P(E) = Number of favourable outcomes / Total number of outcomes
2. Experimental probability: P(E) = Number of times event occurs / Total number of trials
3. Comparison: Experimental probability ≈ Theoretical probability (for a large number of trials)




# PRACTICAL NO.: 04
Aim : To compute conditional probability and verify independence of events using Python.

1. Given P(A)=0.4, P(B)=0.6 and P(A∩B)=0.24, write a Python program to verify whether the events are independent.
Code :-

P_A = float(input("Enter P(A): "))
P_B = float(input("Enter P(B): "))
P_A_intersection_B = float(input("Enter P(A ∩ B): "))
if P_A_intersection_B == P_A * P_B:
    print("The events A and B are independent.")
else: 
    print("The events A and B are not independent.")

formula : 1. Probability of A: P(A) = Number of outcomes in A / Total outcomes


2. A die is rolled once. Let:
A: Getting an even number
B: Getting a number greater than 3
Code :

sample_space = [1, 2, 3, 4, 5, 6]
A = [2, 4, 6] 
B = [4, 5, 6] 
A_intersection_B = [x for x in A if x in B]
P_A = len(A) / len(sample_space) 
P_B = len(B) / len(sample_space)
P_A_intersection_B = len(A_intersection_B) / len(sample_space) 

P_A_given_B = P_A_intersection_B / P_B 
print("P(A) =", P_A) 
print("P(B) =", P_B) 
print("P(A∩B) =", P_A_intersection_B)
print("P(A|B) =", P_A_given_B)
if P_A_intersection_B == P_A * P_B:
    print("A and B are independent.")
else:
    print("A and B are not independent.")

Formula :  Probability of B: P(B) = Number of outcomes in B / Total outcomes

3.  A card is drawn from a standard deck of 52 cards.
A: Card is a King
B: Card is a Face Card
Code :

total_cards = 52
kings = 4
face_cards = 12
A_intersection_B = 4
P_B = face_cards / total_cards
P_A_intersection_B = A_intersection_B / total_cards
P_A_given_B = P_A_intersection_B / P_B
print("P(B) =", P_B)
print("P(A∩B) =", P_A_intersection_B)
print("P(A|B) =", P_A_given_B)

formula : . Joint probability: P(A ∩ B) = Number of outcomes in A ∩ B / Total outcomes


4. A bag contains 5 red, 3 blue, and 2 green balls. One ball is drawn.
A: Ball is red
B: Ball is not green
Code :

red = int(input("Enter number of red balls: "))
blue = int(input("Enter number of blue balls: "))
green = int(input("Enter number of green balls: "))
total_balls = red + blue + green
not_green = red + blue
P_B = not_green / total_balls
P_A_intersection_B = red / total_balls
P_A_given_B = P_A_intersection_B / P_B
print("P(B) =", P_B)
print("P(A∩B) =", P_A_intersection_B)
print("P(A|B) =", P_A_given_B)

formula : Conditional probability: P(A | B) = P(A ∩ B) / P(B)

5. Develop a Python program that reads:
Total number of outcomes
Number of outcomes in event A
Number of outcomes in event B
Number of outcomes in A∩B
Code :

total = int(input("Enter total number of outcomes: "))
A = int(input("Enter number of outcomes in A: "))
B = int(input("Enter number of outcomes in B: "))
A_intersection_B = int(input("Enter number of outcomes in A∩B: "))
P_A = A / total
P_B = B / total
P_A_intersection_B = A_intersection_B / total
P_A_given_B = P_A_intersection_B / P_B
P_B_given_A = P_A_intersection_B / P_A
print("P(A) =", P_A)
print("P(B) =", P_B)
print("P(A|B) =", P_A_given_B)
print("P(B|A) =", P_B_given_A)

formula : Conditional probability: P(B | A) = P(A ∩ B) / P(A) 

6. Simulate tossing two coins 10,000 times using Python. Estimate:
P(A): First coin is Head
P(B): Second coin is Head
P(A∩B)
Verify whether the events are independent.
Code :

import random
trials = 10000
count_A = 0
count_B = 0
count_AB = 0
for i in range(trials):
    coin1 = random.choice(["H", "T"])
    coin2 = random.choice(["H", "T"])
    if coin1 == "H":
        count_A += 1
    if coin2 == "H":
        count_B += 1
    if coin1 == "H" and coin2 == "H":
        count_AB += 1
P_A = count_A / trials
P_B = count_B / trials
P_AB = count_AB / trials
print("P(A) =", P_A)
print("P(B) =", P_B)
print("P(A∩B) =", P_AB)
if abs(P_AB - (P_A * P_B)) < 0.01:
    print("The events are independent.")
else:
    print("The events are not independent.")

formula : Independent events: P(A ∩ B) = P(A) × P(B)

7. Generate 100 random integers between 1 and 50 using NumPy. Find:
Probability of obtaining an even number.
Probability of obtaining a multiple of 5.
Conditional probability of an even number given that it is a multiple of 5.
Code :

import numpy as np
numbers = np.random.randint(1, 51, 100)
even = np.sum(numbers % 2 == 0)
multiple5 = np.sum(numbers % 5 == 0)
even_multiple5 = np.sum((numbers % 2 == 0) & (numbers % 5 == 0))
P_even = even / 100
P_multiple5 = multiple5 / 100
P_even_given_multiple5 = even_multiple5 / multiple5
print("Random Numbers:")
print(numbers)
print("P(Even) =", P_even)
print("P(Multiple of 5) =", P_multiple5)
print("P(Even | Multiple of 5) =", P_even_given_multiple5)

formula :  Simulation probability: P(E) = Number of successful outcomes / Number of trials

8. Write a Python program to calculate conditional probability using user-defined functions.
Code :

def probability(event, total):
    return event / total
def conditional_probability(intersection, event):
    return intersection / event
total = int(input("Enter total number of outcomes: "))
A = int(input("Enter number of outcomes in A: "))
B = int(input("Enter number of outcomes in B: "))
A_intersection_B = int(input("Enter number of outcomes in A∩B: "))
P_A = probability(A, total)
P_B = probability(B, total)
P_A_intersection_B = probability(A_intersection_B, total)
P_A_given_B = conditional_probability(P_A_intersection_B, P_B)
print("P(A) =", P_A)
print("P(B) =", P_B)
print("P(A∩B) =", P_A_intersection_B)
print("P(A|B) =", P_A_given_B)



9. Write a Python program to verify the multiplication rule for independent events. 
Code :

P_A = float(input("Enter P(A): "))
P_B = float(input("Enter P(B): "))
P_A_intersection_B = float(input("Enter P(A∩B): "))
product = P_A * P_B
print("P(A) × P(B) =", product)
print("P(A∩B) =", P_A_intersection_B)
if abs(P_A_intersection_B - product) < 1e-9:
    print("Multiplication rule is verified.")
    print("The events are independent.")
else:
    print("Multiplication rule is not verified.")
    print("The events are dependent.")




# PRACTICAL NO.: 05
Aim : To verify important probability theorems using Python.

1. Write a Python program to verify the Addition Theorem of Probability.
Code :

P_A = float(input("Enter P(A): "))
P_B = float(input("Enter P(B): "))
P_A_intersection_B = float(input("Enter P(A ∩ B): "))

P_A_union_B = P_A + P_B - P_A_intersection_B

print("\nP(A) =", P_A)
print("P(B) =", P_B)
print("P(A ∩ B) =", P_A_intersection_B)
print("P(A ∪ B) =", P_A_union_B)

if P_A_union_B == (P_A + P_B - P_A_intersection_B):
    print("\nAddition Theorem Verified!")
else:
    print("\nAddition Theorem Not Verified!")
    
 formula :  Addition theorem: P(A ∪ B) = P(A) + P(B) − P(A ∩ B)

2. Write a Python program to verify the Multiplication Theorem for independent events.
Code :

P_A = float(input("Enter P(A): "))
P_B = float(input("Enter P(B): "))
P_A_intersection_B = float(input("Enter P(A ∩ B): "))

product = P_A * P_B

print("P(A) × P(B) =", product)
print("P(A ∩ B) =", P_A_intersection_B)

if abs(product - P_A_intersection_B) < 0.0001:
    print("Multiplication Theorem Verified!")
else:
    print("Multiplication Theorem Not Verified!")

formula : Multiplication theorem for independent events: P(A ∩ B) = P(A) × P(B)

3. Write a Python program that computes P(A∪B) using given values of P(A), P(B), and P(A∩B).
Code :

P_A = float(input("Enter P(A): "))
P_B = float(input("Enter P(B): "))
P_A_intersection_B = float(input("Enter P(A ∩ B): "))

P_A_union_B = P_A + P_B - P_A_intersection_B
print("P(A ∪ B) =", P_A_union_B) 



4. Write a Python program to determine whether two events are independent.
Code :
P_A = float(input("Enter P(A): "))
P_B = float(input("Enter P(B): "))
P_A_intersection_B = float(input("Enter P(A ∩ B): "))

if abs(P_A_intersection_B - (P_A * P_B)) < 0.0001:
    print("The events are Independent.")
else:
    print("The events are Dependent.")



5. Roll two dice and verify the Multiplication Theorem for independent outcomes.
Code :

import random
n = int(input("Enter number of trials: "))
count_A = 0
count_B = 0
count_AB = 0
for i in range(n):
    die1 = random.randint(1, 6)
    die2 = random.randint(1, 6)
    if die1 == 4:
        count_A += 1
    if die2 == 5:
        count_B += 1

    if die1 == 4 and die2 == 5:
        count_AB += 1

P_A = count_A / n
P_B = count_B / n
P_AB = count_AB / n
print("\nExperimental P(A) =", P_A)
print("Experimental P(B) =", P_B)
print("Experimental P(A ∩ B) =", P_AB)
print("P(A) × P(B) =", P_A * P_B)

if abs(P_AB - (P_A * P_B)) < 0.01:
    print("\nMultiplication Theorem Verified.")
else:
    print("\nApproximately Verified (difference due to randomness).")



6. A card is drawn from a deck of 52 cards. Verify the Addition Theorem for:
● Event A: Drawing a King
● Event B: Drawing a Heart
Code :

P_A = 4 / 52
P_B = 13 / 52
P_A_intersection_B = 1 / 52

P_A_union_B = P_A + P_B - P_A_intersection_B

print("P(King) =", P_A)
print("P(Heart) =", P_B)
print("P(King and Heart) =", P_A_intersection_B)
print("P(King or Heart) =", P_A_union_B)

if abs(P_A_union_B - (P_A + P_B - P_A_intersection_B)) < 0.0001:
    print("Addition Theorem Verified!")
else:
    print("Addition Theorem Not Verified!")



7. A disease affects 1% of the population.
Probability of having the disease = 0.01
Test sensitivity = 0.99 (positive if disease is present)
False positive rate = 0.05
Code :

P_D = 0.01              
P_not_D = 0.99         
P_pos_given_D = 0.99    
P_pos_given_not_D = 0.05 

P_positive = (P_pos_given_D * P_D) + (P_pos_given_not_D * P_not_D)

P_D_given_positive = (P_pos_given_D * P_D) / P_positive
print("P(Positive) =", P_positive)
print("P(Disease | Positive) =", P_D_given_positive)



Task : Write a Python program to calculate the probability that a person actually has the disease if the test result is positive using Bayes' Theorem.
Code :

P_D = 0.01                 
P_not_D = 0.99             
P_pos_given_D = 0.99      
P_pos_given_not_D = 0.05   

P_positive = (P_pos_given_D * P_D) + (P_pos_given_not_D * P_not_D)

P_D_given_positive = (P_pos_given_D * P_D) / P_positive

print("Probability of Positive Test =", P_positive)
print("Probability of Disease given Positive Test =", P_D_given_positive)

formula
3.Bayes' theorem: P(A | B) = [P(B | A) × P(A)] / P(B)
4. Total probability (used in Bayes example): P(B) = P(B | A)P(A) + P(B | Ā)P(Ā)




# PRACTICAL NO.: 06
Aim : To understand the concept of a random variable and probability mass function (p.m.f.) using Python.

1. A bag contains 5 balls numbered 1, 2, 3, 4, and 5. One ball is selected at random.
Let the random variable X denote the number on the selected ball.
Find the Probability Mass Function (PMF) of X.
Verify that the sum of all probabilities is equal to 1.
Calculate the Expected Value E(X).
Code :

balls = [1, 2, 3, 4, 5]
pmf = {x: 1/5 for x in balls}
print("Probability Mass Function (PMF):")
for x, p in pmf.items():
    print(f"P(X={x}) = {p}")
total_probability = sum(pmf.values())
print("\nSum of all probabilities =", total_probability)
expected_value = sum(x * p for x, p in pmf.items())
print("Expected Value E(X) =", expected_value)

pmf formula : PMF condition: Σ P(X = x) = 1
 

2. A fair die is rolled once. Let X be the number appearing on the upper face.
Tasks:
Define the random variable X.
Construct the PMF.
Verify that the sum of probabilities equals 1.
Find the expected value E(X).
Write a Python program to display the PMF.
Code :

outcomes = [1, 2, 3, 4, 5, 6]

pmf = {x: 1/6 for x in outcomes}

print("Probability Mass Function (PMF):")
for x, p in pmf.items():
    print(f"P(X={x}) = {p:.4f}")

total_probability = sum(pmf.values())
print("\nSum of all probabilities =", total_probability)

expected_value = sum(x * p for x, p in pmf.items())
print("Expected Value E(X) =", expected_value)

Expected value / Mean: E(X) = Σ x P(X = x)

3. Two fair coins are tossed simultaneously. Let X be the number of heads obtained.
Tasks:
List the sample space.
Find the PMF.
Verify the probabilities sum to 1.
Calculate the expected value.
Write a Python program to represent the PMF.
Code :

sample_space = ["HH", "HT", "TH", "TT"]
print("Sample Space:")
print(sample_space)
p0 = 1 / 4   # 0 heads
p1 = 2 / 4   # 1 head
p2 = 1 / 4   # 2 heads
print("\nPMF:")
print("P(X = 0) =", p0)
print("P(X = 1) =", p1)
print("P(X = 2) =", p2)
sum_prob = p0 + p1 + p2
print("\nSum of probabilities =", sum_prob)
if sum_prob == 1:
    print("Verified: Sum of probabilities is equal to 1.")
else:
    print("Verification failed!")

E = (0 * p0) + (1 * p1) + (2 * p2)
print("\nExpected Value E(X) =", E)

formula : Expected value / Mean: E(X) = Σ x P(X = x)

4. A box contains 3 red, 4 blue, and 5 green balls.One ball is selected at random.
Define
X=1 for Red
X=2 for Blue
X=3 for Green
Tasks:
Find the PMF.
Verify the probabilities.
Calculate the expected value.
Code :

colors = {
    1: "Red",
    2: "Blue",
    3: "Green"
}

pmf = {
    1: 3/12,  
    2: 4/12,   
    3: 5/12 
}

print("Probability Mass Function (PMF):")
for x, p in pmf.items():
    print(f"X={x} ({colors[x]}) -> P(X={x}) = {p:.4f}")

total_probability = sum(pmf.values())
print("\nSum of all probabilities =", total_probability)

expected_value = sum(x * p for x, p in pmf.items())
print("Expected Value E(X) =", expected_value)


formula : Expected value / Mean: E(X) = Σ x P(X = x)






# PRACTICAL NO.: 07
Aim :  To study the joint and marginal probability function using python.

The following joint probability table represents the probability of students obtaining a particular grade based on attendance.
Attendance        Grade A         Grade B        Grade C
High                0.25            0.15          0.10
Medium              0.10            0.20          0.05
Low                 0.05            0.05          0.05
Tasks:
Create the joint probability table in Python. 
Find the marginal probability of Attendance. 
Find the marginal probability of Grades. 
Code :

import pandas as pd
data = {
    "Grade A": [0.25, 0.10, 0.05],
    "Grade B": [0.15, 0.20, 0.05],
    "Grade C": [0.10, 0.05, 0.05]
}
attendance = ["High", "Medium", "Low"]
df = pd.DataFrame(data, index=attendance)
print("Joint Probability Table:")
print(df)
print("\nMarginal Probability of Attendance:")
print(df.sum(axis=1))
print("\nMarginal Probability of Grades:")
print(df.sum(axis=0))


2.
Weather    Light    Moderate    Heavy
Sunny      0.18      0.10       0.02
Cloudy     0.12      0.15       0.08
Rainy      0.05      0.12       0.18

Tasks:
Store the table in Python. 
Calculate row-wise marginal probabilities. 
Calculate column-wise marginal probabilities.
Code :

import pandas as pd
data = {
    "Light": [0.18, 0.12, 0.05],
    "Moderate": [0.10, 0.15, 0.12],
    "Heavy": [0.02, 0.08, 0.18]
}

weather = ["Sunny", "Cloudy", "Rainy"]

df = pd.DataFrame(data, index=weather)
print("Joint Probability Table:")
print(df)
print("\nRow-wise Marginal Probabilities:")
print(df.sum(axis=1))
print("\nColumn-wise Marginal Probabilities:")
print(df.sum(axis=0))


3. Employee Department and Performance Rating
department      excellent     good      average
HR                 0.10       0.08       0.07
Sales              0.12       0.15       0.08
IT                 0.18       0.12       0.10

Tasks:
Find row marginal probabilities. 
Find column marginal probabilities.
Day of Week and Gym Visit
Code :

import pandas as pd
data = {
    "Excellent": [0.10, 0.12, 0.18],
    "Good": [0.08, 0.15, 0.12],
    "Average": [0.07, 0.08, 0.10]
}
department = ["HR", "Sales", "IT"]
df = pd.DataFrame(data, index=department)
print("Joint Probability Table:")
print(df)
print("\nRow-wise Marginal Probabilities:")
print(df.sum(axis=1))
print("\nColumn-wise Marginal Probabilities:")
print(df.sum(axis=0))



 4. Day of Week and Gym Visit
Day         Morining     Evening
weekday      0.30          0.25
weekend      0.20          0.25
Tasks:
Create the joint probability matrix. 
Find marginal probabilities for Day. 
Find marginal probabilities for Time.
Code :

import pandas as pd
data = {
    "Morning": [0.30, 0.20],
    "Evening": [0.25, 0.25]
}
day = ["Weekday", "Weekend"]

df = pd.DataFrame(data, index=day
print("Joint Probability Table:")
print(df)
print("\nMarginal Probability for Day:")
print(df.sum(axis=1))
print("\nMarginal Probability for Time:")
print(df.sum(axis=0))



5. The probabilities are:
Bus & On Time = 0.30 
Bus & Late = 0.10 
Train & On Time = 0.25 
Train & Late = 0.05 
Bike & On Time = 0.20 
Bike & Late = 0.10 
Tasks:
Find the marginal probability of Transport. 
Find the marginal probability of Arrival Time.
Code :

import pandas as pd
data = {
    "On Time": [0.30, 0.25, 0.20],
    "Late": [0.10, 0.05, 0.10]
}
transport = ["Bus", "Train", "Bike"]
df = pd.DataFrame(data, index=transport)
print("Joint Probability Table:")
print(df)
print("\nMarginal Probability of Transport:")
print(df.sum(axis=1))
print("\nMarginal Probability of Arrival Time:")
print(df.sum(axis=0))

formula : 
1. Marginal probability of X: P(X = x) = Σᵧ P(X = x, Y = y)
2. Marginal probability of Y: P(Y = y) = Σₓ P(X = x, Y = y)
3. Row marginal: Marginal row probability = Sum of each row
4. Column marginal: Marginal column probability = Sum of each column





# PRACTICAL NO.: 08
Aim : To compute raw moments, central moments, skewness, and kurtosis for a discrete random variable.

1. A discrete random variable X has values {1,2,3,4} with probabilities 0.1,0.2,0.4and 0.3 respectively.Calculate using python 
E(X),E(X2),E(X3),E(X4)
Code :

X = [1, 2, 3, 4]
P = [0.1, 0.2, 0.4, 0.3]

E_X = sum(x * p for x, p in zip(X, P))
E_X2 = sum(x**2 * p for x, p in zip(X, P))
E_X3 = sum(x**3 * p for x, p in zip(X, P))
E_X4 = sum(x**4 * p for x, p in zip(X, P))

print("E(X)   =", E_X)
print("E(X^2) =", E_X2)
print("E(X^3) =", E_X3)
print("E(X^4) =", E_X4)

formulas : 
1. First raw moment / Mean: μ′₁ = E(X) = Σ xP(x)
2. Second raw moment: μ′₂ = E(X²) = Σ x²P(x)
3. Third raw moment: μ′₃ = E(X³) = Σ x³P(x)
4. Fourth raw moment: μ′₄ = E(X⁴) = Σ x⁴P(x)



2. For the distribution:
x          0       1      2      3
P(x)      0.2     0.3    0.3    0.2 

Write Python code to calculate the first four raw moments.
Code :
X = [0, 1, 2, 3]
P = [0.2, 0.3, 0.3, 0.2]

for r in range(1, 5):
    moment = sum((x**r) * p for x, p in zip(X, P))
    print(f"{r}th Raw Moment =", moment)

formulas : 
1. First raw moment / Mean: μ′₁ = E(X) = Σ xP(x)
2. Second raw moment: μ′₂ = E(X²) = Σ x²P(x)
3. Third raw moment: μ′₃ = E(X³) = Σ x³P(x)
4. Fourth raw moment: μ′₄ = E(X⁴) = Σ x⁴P(x)


3. Write a Python program to calculate the second, third, and fourth central moments for any discrete probability distribution.
Code :

X = [1, 2, 3, 4]
P = [0.1, 0.2, 0.4, 0.3]

mean = sum(x * p for x, p in zip(X, P))

mu2 = sum((x - mean)**2 * p for x, p in zip(X, P))
mu3 = sum((x - mean)**3 * p for x, p in zip(X, P))
mu4 = sum((x - mean)**4 * p for x, p in zip(X, P))

print("Mean =", mean)
print("2nd Central Moment =", mu2)
print("3rd Central Moment =", mu3)
print("4th Central Moment =", mu4)

formulas :
1. Second central moment: μ₂ = Σ (x − μ)²P(x)
2. Third central moment: μ₃ = Σ (x − μ)³P(x)
3. Fourth central moment: μ₄ = Σ (x − μ)⁴P(x)



4. For X ={1,2,3,4,5} with probabilities { 0.05 , 0.15, 0.3,0.4,0.1}, Calculate the skewness and Kurtosis.
Code :

X = [1, 2, 3, 4, 5]
P = [0.05, 0.15, 0.3, 0.4, 0.1]
total = sum(P)
P = [p / total for p in P]
mean = sum(x * p for x, p in zip(X, P))
mu2 = sum((x - mean)**2 * p for x, p in zip(X, P))
mu3 = sum((x - mean)**3 * p for x, p in zip(X, P))
mu4 = sum((x - mean)**4 * p for x, p in zip(X, P))
skewness = mu3 / (mu2 ** 1.5)
kurtosis = mu4 / (mu2 ** 2)
print("Mean =", mean)
print("2nd Central Moment =", mu2)
print("3rd Central Moment =", mu3)
print("4th Central Moment =", mu4)
print("Skewness =", skewness)
print("Kurtosis =", kurtosis)

formula :
1.  Skewness: Skewness = μ₃ / (μ₂)^(3/2)
2.  Kurtosis: Kurtosis = μ₄ / (μ₂)²







# PRACTICAL NO.: 09
Aim :  To study the Binomial and Poisson probability distributions using Python and calculate their probability mass functions (PMFs) 

1. Find the probability of obtaining exactly 4 heads in 10 tosses of a fair coin.
Code :

from math import comb
n = 10
p = 0.5
x = 4
P = comb(n, x) * (p ** x) * ((1 - p) ** (n - x))
print("P(X = 4) =", P)
 formula : Binomial distribution – PMF: P(X = x) = (nCx) pˣ qⁿ⁻ˣ

2. A call center receives an average of 4 calls per minute. Find the probability of receiving exactly 6 calls in one minute using Poisson’s distributions.
Code :

from math import factorial, exp
lam = 4
x = 6
P = (exp(-lam) * lam ** x) / factorial(x)
print("P(X = 6) =", P)

formula :  Poisson distribution – PMF: P(X = x) = e⁻λ λˣ / x!

3. A multiple-choice test contains 10 questions, each with 4 options. If a student guesses every answer, find the probability of getting exactly 3 correct answers.
Code :

from math import comb
n = 10
p = 0.25
x = 3
P = comb(n, x) * (p ** x) * ((1 - p) ** (n - x))
print("P(X = 3) =", P)

formula : Binomial distribution – PMF: P(X = x) = (nCx) pˣ qⁿ⁻ˣ
4. For a Binomial distribution with n = 20 and p = 0.3, use Python to find:
      (i)P(X=5)
     (ii) P(X≤5)
     (iii) P(X≥5)
     (iv) mean
      (v) variance.
Code :

from math import comb

n = 20
p = 0.3
q = 1 - p

# (i) P(X = 5)
P_X5 = comb(n, 5) * (p ** 5) * (q ** 15)

# (ii) P(X <= 5)
P_X_le_5 = 0

for x in range(0, 6):
    P_X_le_5 += comb(n, x) * (p ** x) * (q ** (n - x))

# (iii) P(X >= 5)
P_X_ge_5 = 0

for x in range(5, n + 1):
    P_X_ge_5 += comb(n, x) * (p ** x) * (q ** (n - x))

# (iv) Mean
mean = n * p

# (v) Variance
variance = n * p * q

print("(i)   P(X = 5)  =", P_X5)
print("(ii)  P(X <= 5) =", P_X_le_5)
print("(iii) P(X >= 5) =", P_X_ge_5)
print("(iv)  Mean      =", mean)
print("(v)   Variance  =", variance)

Formula :
Binomial distribution – PMF: P(X = x) = (nCx) pˣ qⁿ⁻ˣ
Mean : E(X)=np
Variance : Var(X)=npq 

5. A website receives an average of 5 complaints per day. Find the probability of receiving exactly 2 complaints on a particular day (Poisson’s distributions)
Code :
from math import factorial, exp
lam = 5
x = 2
P = (exp(-lam) * lam ** x) / factorial(x)
print("P(X = 2) =", P)

Formula : Poisson distribution – PMF: P(X = x) = e⁻λ λˣ / x!






# PRACTICAL NO.: 10 
Aim : To study the Geometric and Hypergeometric probability  distributions using Python and calculate their probability mass functions (PMFs)

1. A fair coin is tossed repeatedly. Find the probability that the first Head occurs on the 4th toss.
Code :

import math
p = 1/2
q = 1 - p
x = 4
probability = (q ** (x - 1)) * p
print("Probability of first Head on 4th toss =", probability)

formula : Geometric distribution : PMF: P(X = x) = q⁽ˣ⁻¹⁾p

2. A die is rolled repeatedly. Find the probability that the first 6 occurs on the 5th roll.
Code :

import math
p = 1/6
q = 1 - p
x = 5
probability = (q ** (x - 1)) * 
print("Probability of first 6 on 5th roll =", probability)

formula : Geometric distribution : PMF: P(X = x) = q⁽ˣ⁻¹⁾p

3. A salesperson has a 20% probability of making a sale on each call. Find the probability that the first sale occurs on the 6th call.
Code :

import math
p = 0.20
q = 1 - p
x = 6
probability = (q ** (x - 1)) * p
print("Probability of first sale on 6th call =", probability)

formula : Geometric distribution : PMF: P(X = x) = q⁽ˣ⁻¹⁾p


4. A box contains 20 products, including 5 defective products. If 4 products are selected without replacement, find the probability of selecting exactly 2 defective products.
Code :

import math
N = 20
K = 5
n = 4
x = 2
probability = (math.comb(K, x) * math.comb(N-K, n-x)) / math.comb(N, n)
print("Probability of exactly 2 defective products =", probability) 

Formula : Combination/coefficient : C(a,b) = a! / [b!(a−b)!]


Formula : Hypergeometric :  PMF: P(X = x) = [(KCx) (N−KCn−x)] / (NCn)
5. A class has 30 students, of which 12 are girls. If 5 students are selected randomly without replacement, find the probability of selecting exactly 3 girls.
Code :

import math
N = 30
K = 12
n = 5
x = 3
probability = (math.comb(K, x) * math.comb(N-K, n-x)) / math.comb(N, n)
print("Probability of exactly 3 girls =", probability)

 Formula : Hypergeometric : PMF: P(X = x) = [(KCx) (N−KCn−x)] / (NCn)
