# Многострочные строки | Multiline Strings

### Определение

**Многострочные строки (Multiline Strings)** — строки состоящие из нескольких строк с переносами.

### Описание

- Для переноса строки можно использовать тройные кавычки (`"""` или `'''`).
- Внутри multi-line строки можно переносить текст без использования конструкции перевода строки `\n`.
- Не нужно экранировать одинарные кавычки `'` и двойные `"`.

### Пример синтаксиса

```python
text = '''Пример текста,
состоящего из
нескольких строк'''
```