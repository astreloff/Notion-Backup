# What are (parentheses), [brackets], {curly brackets}, <>, and decimals? : unstable_diffusion

Date [HIDE]: November 9, 2022 3:39 PM
Без разбора: 108 дней
Добавлено: 09.11.2022
Разобрано: No
Ссылка: https://www.reddit.com/r/unstable_diffusion/comments/ykrifx/what_are_parentheses_brackets_curly_brackets_and/
Темы: ../%D0%A2%D0%B0%D0%B1%D0%BB%D0%B8%D1%86%D0%B0%20%E2%80%9C%D0%A2%D0%B5%D0%BC%D1%8B%E2%80%9D%205261d8ac365a4baa890082f78175e751/Stable%20Diffusion%201826c5402bdd451081c322e09681b21a.md

- [] is less emphasis, {} is NAI's "implementation" of (),
- <> is for embeddings,
- decimals specify the number of ()'s so you don't need to type in a bunch.

**(Blue hair) would have more weight than [Blue hair] in the final result, (blue hair:1.4) would increase the blue hair by ~40% more than what it would've normally been, (blue hair:0.6) will increase blue hair by ~40% less than what it would've normally been**

**If using multiple (parenthesis) instead of decimals, is changed by a multiplier of 1.1 with each new parenthesis**

- (n) = (n:1.1)
- ((n)) = (n:1.21)
- (((n))) = (n:1.331)
- ((((n)))) = (n:1.4641)
- (((((n)))) = (n:1.61051)
- ((((((n)))))) = (n:1.771561)

([prompt]:[number less than 1]) = [using this syntax]

- [n] = (n:0.9090909090909091)
- [[n]] = (n:0.8264462809917355)
- [[[n]]] = (n:0.7513148009015778)
- [[[[n]]]] = (n:0.6830134553650707)
- [[[[[n]]]]] = (n:0.6209213230591552)
- [[[[[[n]]]]]] = (n:0.5644739300537775)

*I don't think decimals work with this syntax, it's undocumented in AUTOMATIC's wiki 2 of {} = 1 of (), accurate with a difference of <1%*

exceeding (1.9) , below [0.5] can overcook

![What%20are%20(parentheses),%20%5Bbrackets%5D,%20%7Bcurly%20bracket%202e458091fdb34942b18db25908843d00/v5s7x4il7gy91.png](What%20are%20(parentheses),%20%5Bbrackets%5D,%20%7Bcurly%20bracket%202e458091fdb34942b18db25908843d00/v5s7x4il7gy91.png)