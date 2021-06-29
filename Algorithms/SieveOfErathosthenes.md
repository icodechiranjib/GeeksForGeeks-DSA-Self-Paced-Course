
# Sieve Of Eratosthenes

Given a number n, print all primes smaller than or equal to n.

## Example
```
Input : n =10
Output : 2 3 5 7 

Input : n = 20 
Output: 2 3 5 7 11 13 17 19
```   
It is also given that n is a small number. The sieve of Eratosthenes is one of the most efficient ways to find all primes smaller than n when n is smaller than 10 million or so

## Explanation

* Let us take an example when n = 50. So we need to print all prime numbers smaller than or equal to 50.   
* We create a list of all numbers from 2 to 50.   
* According to the algorithm we will mark all the numbers which are divisible by 2 and are greater than or equal to the square of it.   
* Now we move to our next unmarked number 3 and mark all the numbers which are multiples of 3 and are greater than or equal to the square of it.   
* We move to our next unmarked number 5 and mark all multiples of 5 and are greater than or equal to the square of it. 
* We continue this process.

### Time Complexity: O(nlog(log(n)))
 
## Code

```java
import java.util.*;

class Main {
    void simpleSieveOfEratosthenes(int n)
    {
        boolean isPrime[] = new boolean[n + 1];
        
        //initialize all values to true
        Arrays.fill(isPrime, true);
 
        for (int i = 2; i * i <= n; i++){
            if (isPrime[i]){   
                
                //Marking Multiple of PrimeNumbers as False
                for (int j = 2 * i; j <= n; j += i)
                    isPrime[j] = false;
            }
        }
        
        //Display
        for (int i = 2; i <= n; i++){
            if (isPrime[i] == true){
                System.out.print(i + " ");
            }
        }
    }
    
    void optimisedSieveOfErathosthenes(int n){
        
        boolean isPrime[] = new boolean[n+1];
        
        Arrays.fill(isPrime, true);
        
        for(int i=2; i*i <=n; i++){
            if(isPrime[i]){
                //initialize j to i*i
                for(int j=i*i; j<=n;j=j+i){
                    isPrime[j]=false;
                }
            }
        }
        
        //Display
        for (int i = 2; i <= n; i++)
        {
            if (isPrime[i] == true){
                System.out.print(i + " ");
            }
        }
    }
    
    void optimisedShorterSieveOfErathosthenes(int n){
        
        boolean isPrime[] = new boolean[n+1];
        
        Arrays.fill(isPrime, true);
        
        //print and function in one block
        for(int i = 2; i<=n; i++){
            if(isPrime[i]){
                System.out.print(i + " ");
                for(int j=i*i; j<=n;j=j+i){
                    isPrime[j]=false;
                }
            }
        }
    }
    
    public static void main(String args[])
    {
        int n = 50;
        Main g = new Main();
        
        System.out.println("Following are the prime numbers smaller than or equal to " + n);
        g.simpleSieveOfEratosthenes(n);
        System.out.println();
        
        System.out.println("Following are the prime numbers smaller than or equal to " + n);
        g.optimisedSieveOfErathosthenes(n);
        System.out.println();
        
        System.out.println("Following are the prime numbers smaller than or equal to " + n);
        g.optimisedShorterSieveOfErathosthenes(n);
        System.out.println();
    }
}
```

## Reference
[GeeksForGeeks](https://www.geeksforgeeks.org/sieve-of-eratosthenes/)