##count_digits.py

```python

def count_digits(n):
    result = ''
    n = str(n)
    current_digit = None
    total = 0
    for c in n:
        current_digit = current_digit if current_digit else c
        if current_digit != c:
            result += str(total) + current_digit
            current_digit = c
            total = 0
        total += 1
    result += str(total) + current_digit
    return result



if __name__ == '__main__':
    print count_digits(1)
 ```
    
##divide.py

 ```python
def divide(n, div):
    result = 0
    temp = 1

    while div <= n:
        temp = temp << 1
        div = div << 1

    while temp > 1:
        temp = temp >> 1
        div = div >> 1

        if n >= div:
            n -= div
            result += temp
    return result

    print divide(36, 7)
    print divide(32, 7)
    print divide(35, 7)
```

##number_to_word.py


```python
one_to_twenty = {
    1: 'one',
    2: 'two',
    3: 'three',
    4: 'four',
    5: 'five',
    6: 'six',
    7: 'seven',
    8: 'eight',
    9: 'nine',
    10: 'twenty',
    11: 'eleven',
    12: 'twelve',
    13: 'thirteen',
    14: 'fourteen',
    15: 'fifteen',
    16: 'sixteen',
    17: 'seventeen',
    18: 'eighteen',
    19: 'nineteen',
    20: 'twenty',
    30: 'thirty',
    40: 'fourty',
    50: 'fifty',
    60: 'sixty',
    70: 'seventy',
    80: 'eighty',
    90: 'ninety'

}


def three_digits_to_word(n, with_and=False):
    word = ''

    hundred_d = n / 100
    last_two = n % 100

    first_word = ''
    if hundred_d > 0:
        first_word = one_to_twenty[hundred_d]

    last_two_word = ''

    if last_two == 0:
        last_two = ''
    elif last_two in range(1, 21):
        last_two_word = one_to_twenty[last_two]
    else:
        last_two_word += one_to_twenty[(last_two / 10)*10] + ' ' + one_to_twenty[last_two % 10]

    if first_word:
        word += first_word + ' ' + ('hundred' if hundred_d == 1 else 'hundreds')
    if last_two:
        word += (' and ' if (word and with_and) else '') + last_two_word
    return word


def number_to_word(n):
    three_digits = []
    while n:
        if n < 1000:
            three_digits.append(n)
            break
        three_digits.append(n % 1000)
        n = n / 1000
    three_digits.reverse()
    print three_digits
    w = ''
    u = ['', 'thousand', 'million']

    for i in range(len(three_digits)):
        w += ' ' + three_digits_to_word(three_digits[i], True if (w or (i == len(three_digits) - 1)) else False) + u[len(three_digits) - i - 1]

    # n = str(n)
    # w = ''
    # unit = ['', 'thousand', 'million']
    #
    # for i in range(len(n) / 3 + 1):
    #     if n:
    #         w += ' ' + three_digits_to_word(int(n[-3:]), (True if w else False)) + ' ' + unit[i] + ' '
    #     n = n[:-3]
    return w

if __name__ == '__main__':
    test_cases = [1, 13, 98, 100, 102, 123, 199, 500, 1001, 1124, 123456, 11234567]
    for n in test_cases:
        print '%s - %s' % (n, number_to_word(n))
        
```

##phone-keyboard-digits-to-letter.py
```python
digit_map = {
    2: 'abc',
    3: 'def',
    4: 'ghi',
    5: 'jkl',
    6: 'mno',
    7: 'pqrs',
    8: 'tuv',
    9: 'wxyz',
}


def digits_to_word(digits):
    result = ['']
    for d in digits:
        result = [r+c for r in result for c in digit_map[d]]
    return result

if __name__ == '__main__':
    print len(digits_to_word([2, 3, 4, 5]))

```
