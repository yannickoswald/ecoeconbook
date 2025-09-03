(basics-calculator)=
# Python as a calculator

The first thing we learn is just that you can use a programming language like a pocket calculator. 

This is more important than you think, as there are lots of multiplications throughout all of ecological economics.

In brief, python as all the standard operations that you know since primary school

:::{admonition} Basic operations
- addition +
- subtraction -
- divison /
- multiplication *
- raising a number to an exponent **
:::

you can multiply numbers like in the following code box. 

```python
2 + 2, 10 - 3, 6 * 7, 22 / 7, 22 // 7, 22 % 7, 2 ** 10
```

The ** is raising a number to a power.  So 2*2 = 4 could also be 2**2 because 2 squared is 4. Got it? With this one you need to become really familiar.

Instead of boring stuff like this, let us do some interesting thought experiments to get into the groove: 

The US has a approximately a total primary energy consumption of 100 Exajoule in 2024. This is a unit of energy. A very big unit of energy.

We learn more about this letter. If the USA has 340 million inhabitants that same year we have
(run the following in your Python environment or Notebook)

```python
100 / (340 * 10**6) 
```
Exajoule per person. Since this is a bit cumbersome to read let us convert to Gigajoule (same thing just smaller unit) for which we multiply by 10**9 

```python
100 / (340 * 10**6) * 10**9
```

Wow, the average American consumes roughly 300 GJ energy per person! The global average is only around

```python
592/(8.2*10**9) * 10**9 
```

~72Gigajoule per person. 

First exercise, clarify the above calculation with its respective units. Hint the denominator is global population.

```{dropdown} Solution

The numerator, `592`, represents the total global primary energy consumption in Exajoules (EJ). The denominator, `8.2 * 10**9`, is the global population.

So, the expression `592 / (8.2 * 10**9)` is calculating `(Total Global EJ) / (Global Population) = EJ per person`.

To convert this result from Exajoules to Gigajoules, you multiply by $10^9$, because $1 \text{ Exajoule} = 10^9 \text{ Gigajoules}$.

So, the full calculation is `(EJ per person) * (Gigajoules per Exajoule)`, which gives you the final unit of `Gigajoules per person`.

```

So for the next exercises you conduct simple thought experiments:

1. How much larger would be the total yearly global primary consumption, if everyone lived an American livestyle?
2. How much larger would total yearly $CO_2$ emissions be assuming current average $CO_2$ - intensity of energy (that is the quantity of $CO_2$ emitted per unit of energy - more on this later)?

```{dropdown} Solutions

**Exercise 1: Global Energy Consumption with American Lifestyle**

To solve this, we need to calculate the total energy if the entire global population had the US per capita energy consumption.

* **Global Population:** $8.2 \times 10^9$ people
* **US Energy Consumption per capita:** The average American consumes about $300$ GJ of energy per year. This is equivalent to $\frac{100 \text{ EJ}}{340 \times 10^6 \text{ people}}$.

**Calculation:**
New Global Energy Consumption = (Global Population) $\times$ (US Energy Consumption per capita)
New Global Energy Consumption = $(8.2 \times 10^9 \text{ people}) \times (\frac{100 \text{ EJ}}{340 \times 10^6 \text{ people}})$
New Global Energy Consumption $\approx 2412$ EJ

To find out how much larger this is, we compare it to the current global consumption:
Ratio = $\frac{\text{New Global Energy Consumption}}{\text{Current Global Energy Consumption}}$
Ratio = $\frac{2412 \text{ EJ}}{592 \text{ EJ}} \approx 4.07$

So, the total global primary energy consumption would be about **4.1 times larger** if everyone lived an American lifestyle.

**Exercise 2: Global $CO_2$ Emissions with American Lifestyle**

This problem assumes a constant $CO_2$ intensity of energy, which means the amount of $CO_2$ emitted per unit of energy consumed remains the same.

* Current $CO_2$ Emissions = (Current Energy Consumption) $\times$ ($CO_2$ Intensity)
* New $CO_2$ Emissions = (New Energy Consumption) $\times$ ($CO_2$ Intensity)

Since the $CO_2$ intensity is a constant value in this thought experiment, the ratio of emissions will be the same as the ratio of energy consumption.

Ratio of Emissions = $\frac{\text{New } CO_2 \text{ Emissions}}{\text{Current } CO_2 \text{ Emissions}} = \frac{\text{New Energy Consumption}}{\text{Current Energy Consumption}}$

Based on the calculation from Exercise 1, this ratio is approximately **4.1**. Therefore, total global $CO_2$ emissions would also be about **4.1 times larger**.

```