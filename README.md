![hilbert-6](https://github.com/barabo/barabo/assets/4342684/a7ae484f-d97f-4fd8-ad79-0c81ecf35439)


```
 __   ___   ___   ___   ___   _____   ___   ___   ___   ___   _____   ___   ___   ___   ___   __
  _| |_  |_|  _| |_  |_|  _| |_   _| |_  |_|  _| |_  |_|  _| |_   _| |_  |_|  _| |_  |_|  _| |_
 |  _  |  _  |_   _|  _  |  _  | |  _  |  _  |_   _|  _  |  _  | |  _  |  _  |_   _|  _  |  _  |
 |_| |_| | |___| |___| | |_| |_| |_| |_| | |___| |___| | |_| |_| |_| |_| | |___| |___| | |_| |_|
  _   _  |  ___   ___  |  _   _   _   _  |  ___   ___  |  _   _   _   _  |  ___   ___  |  _   _
 | |_| | |_|  _| |_  |_| | |_| | | |_| | |_|  _| |_  |_| | |_| | | |_| | |_|  _| |_  |_| | |_| |
 |_   _|  _  |_   _|  _  |_   _| |_   _|  _  |_   _|  _  |_   _| |_   _|  _  |_   _|  _  |_   _|
  _| |___| |___| |___| |___| |_   _| |___| |___| |___| |___| |_   _| |___| |___| |___| |___| |_
 |  ___   ___   _   ___   ___  | |  ___   ___   _   ___   ___  | |  ___   ___   _   ___   ___  |
 |_|  _| |_  |_| |_|  _| |_  |_| |_|  _| |_  |_| |_|  _| |_  |_| |_|  _| |_  |_| |_|  _| |_  |_|
  _  |_   _|  _   _  |_   _|  _   _  |_   _|  _   _  |_   _|  _   _  |_   _|  _   _  |_   _|  _
 | |___| |___| | | |___| |___| | | |___| |___| | | |___| |___| | | |___| |___| | | |___| |___| |
 |_   _____   _| |_   _____   _| |_   _____   _| |_   _____   _| |_   _____   _| |_   _____   _|
  _| |_   _| |_   _| |_   _| |_   _| |_   _| |_   _| |_   _| |_   _| |_   _| |_   _| |_   _| |_
 |  _  | |  _  | |  _  | |  _  | |  _  | |  _  | |  _  | |  _  | |  _  | |  _  | |  _  | |  _  |
 |_| |_| |_| |_| |_| |_| |_| |_| |_| |_| |_| |_| |_| |_| |_| |_| |_| |_| |_| |_| |_| |_| |_| |_|

```

<details>
 <summary>How many syllables are in a number?</summary>

This code currently only supports numbers up to 1 undecillian - maybe someday I'll solve it generally.

```python
def syllables(n):
    def exp_syllables(power):
        if power > 10:
            raise ValueError("Too large")
        # for million, billion, and trillion (power less than 4)
        # return 2 - all other allowed powers return 3.
        return power < 4 and 2 or 3
    if n == 0:
        return 0
    if n in [1, 2, 3, 4, 5, 6, 8, 9, 10, 12]:
        return 1
    if n in [11, 17, 70]:
        return 3
    if n <= 20 or n in [30, 40, 50, 60, 80, 90]:
        return 2
    if n < 100:
        return syllables(10 * (n // 10)) + syllables(n % 10)
    if n < 1000:
        hundreds = n // 100
        return (hundreds == 7 and 4 or 3) + syllables(n - 100 * hundreds)
    
    exp = int(math.log10(n) // 3)  # thousands, millions, billions, ...
    power = int(math.pow(1000, exp))
    leftmost = n // power
    remainder = n - leftmost * power
    return syllables(leftmost) + exp_syllables(exp) + syllables(remainder)
```

 
</details>

<!--
**barabo/barabo** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
