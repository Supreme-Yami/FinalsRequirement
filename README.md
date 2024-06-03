import java.math.BigInteger;
import java.util.ArrayList;
import java.util.List;

/**
 * Class to generate prime numbers within a specified range.
 * 
 * Best Practice: Use of Javadoc comments for public class, providing an overview
 * of the class functionality.
 */
public class JackMidtermReq {

    /**
     * Generates a list of prime numbers between the given start and end values.
     *
     * @param start The starting value of the range.
     * @param end The ending value of the range.
     * @return A list of prime numbers within the specified range.
     * 
     * Best Practice: Use of Javadoc comments for public method, including 
     * descriptions of parameters and return values.
     */
    public static List<BigInteger> generatePrimeNumbers(BigInteger start,
                                                        BigInteger end) {
        // Best Practice: Proper variable naming conventions.
        List<BigInteger> primes = new ArrayList<>();

        // Check if start is less than 2, if so, set it to 2
        if (start.compareTo(BigInteger.valueOf(2)) < 0) {
            start = BigInteger.valueOf(2);
        }

        // Loop through the range from start to end
        // Best Practice: Using braces for control structures, even single statements.
        for (BigInteger i = start; i.compareTo(end) <= 0;
             i = i.add(BigInteger.ONE)) {
            if (isPrime(i)) {
                primes.add(i);
            }
        }

        return primes;
    }

    /**
     * Checks if a BigInteger is a prime number.
     *
     * @param n The number to check.
     * @return True if the number is prime, false otherwise.
     * 
     * Best Practice: Use of Javadoc comments for private method to describe its purpose.
     */
    private static boolean isPrime(BigInteger n) {
        // Check if n is less than 2
        if (n.compareTo(BigInteger.valueOf(2)) < 0) {
            return false;
        }
        // Check if n is divisible by any number less than its square root
        for (BigInteger i = BigInteger.valueOf(2);
             i.multiply(i).compareTo(n) <= 0;
             i = i.add(BigInteger.ONE)) {
            if (n.remainder(i).equals(BigInteger.ZERO)) {
                return false;
            }
        }
        return true;
    }

    /**
     * Main method to execute the prime number generation.
     *
     * @param args Command line arguments.
     * 
     * Best Practice: Use of Javadoc comments for main method.
     */
    public static void main(String[] args) {
        // Best Practice: Proper variable naming conventions.
        BigInteger start = BigInteger.valueOf(10);
        BigInteger end = BigInteger.valueOf(50);

        // Best Practice: Keeping methods short and focused on a single task.
        List<BigInteger> primes = generatePrimeNumbers(start, end);

        // Best Practice: Proper use of println to output results.
        System.out.println("Prime numbers between " + start + " and " + end + ":");
        for (BigInteger prime : primes) {
            System.out.println(prime);
        }
    }
}
