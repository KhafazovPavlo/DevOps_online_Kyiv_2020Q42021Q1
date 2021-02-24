## Task 9.1

## 1. Developing FizzBuzz function 

**FizzBuzz function** for list of inputed range of numbers from 'a' to 'b' (in our case from 1 to 100):

![Image1](screenshots/1.jpg "fizzbuzz")

**Unit test for FizzBuzz function** ( with TestCase classes that include a methods to test for "Fizz", "Buzz", "FizzBuzz" and the numbers aren't divisible by 3 or by 5):

![Image2](screenshots/2.jpg "unit test")

Results:

![Image3](screenshots/3.jpg "funct")

![Image4](screenshots/4.jpg "test")

Test coverage:

![Image5](screenshots/5.jpg "cover")

## 2. Developing function for counting vowels:

User must enter a string and store it in a variable. The count variable is initialized to zero, for loop is used to traverse through the characters in the string, if statement checks if the character is a vowel or not. The count is incremented each time a vowel is encountered. And then the total count of vowels in the string is printed.

![Image6](screenshots/6.jpg "count")

To count consonants:

![Image7](screenshots/7.jpg "count cons")

_I've got a problem when was trying to count consonants because of noletter symbols. To corect this mistake used: converting entire string to lower case to reduce the comparisons, then hecking whether a character is a vowel and reducing counting range exceptionally to letters (from a to z) `elif (str[i] >= 'a' and str[i] <= 'z')`:

![Image8](screenshots/8.jpg "count cons right")





