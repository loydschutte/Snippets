# FizzBuzz for Java

```
class FizzBuzz {
	public static void main(String[] args) {
		for (int i = 1; i <= 100; i++) {
			if (i % 3 == 0 && i % 5 != 0) {
				System.out.print(i + " Fizz\r");
			}
			
			if (i % 5 == 0 && i % 3 != 0) {
				System.out.print(i + " Buzz\r");
			}
			
			if (i % 3 == 0 && i % 5 == 0) {
				System.out.print(i + " Fizzbuzz!!!!\r");
			}
		}
	}
}
```