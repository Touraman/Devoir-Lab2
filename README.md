# Devoir-Lab2
#include <iostream>
using namespace std;

int main() {
    int a, b;
    int temp;

    int somme_d_a = 0; // Sum of divisors of a
    int nums_d_a = 0;  // Number of divisors of a
    int prod_odd_div_a = 1;  // Product of odd divisors of a


    int somme_d_b = 0; // Sum of divisors of b
    int nums_d_b = 0;  // Number of divisors of b
    int prod_even_div_b = 1;  // Product of even divisors of b

    // Input for the two numbers
    cout << "Enter the first number: ";
    cin >> a;
    cout << "Enter the second number: ";
    cin >> b;

    // Validation of input numbers
    if (a >= 10 && a <= 1000 && b >= 10 && b <= 1000) {
        
        // Store original values for display after PGCD calculation
        int original_a = a;
        int original_b = b;

        // Calculate sum and count of divisors of 'a'
        for (int i = 1; i <= a; i++) {
            if (a % i == 0) {
                somme_d_a += i;
                nums_d_a++;
                if (i % 2 != 0) {  // If the divisor is odd
                    prod_odd_div_a *= i;
                }
            }
        }

        // Calculate sum and count of divisors of 'b'
        for (int j = 1; j <= b; j++) {
            if (b % j == 0) {
                somme_d_b += j;
                nums_d_b++;
                if (j % 2 == 0) {  // If the divisor is even
                    prod_even_div_b *= j;
                }
            }
        }

        // Ensure a > b for the PGCD calculation
        if (a < b) {
            swap(a, b);
        }

        // Calculate PGCD 
        while (b != 0) {
            temp = a % b;
            a = b;
            b = temp;
        }

        // PGCD is now in 'a'
        int pgcd = a;

        // Display results
        cout << "Sum of divisors of " << original_a << " and " << original_b << " is: " << somme_d_a + somme_d_b << endl;
        cout << "Product of the number of divisors of " << original_a << " and " << original_b << " is: " << nums_d_a * nums_d_b << endl;
        cout << "Product of odd divisors of " << original_a << " and even divisors of " << original_b << " is: " << prod_odd_div_a * prod_even_div_b << endl;
        cout << "The greatest common divisor (GCD) of " << original_a << " and " << original_b << " is: " << pgcd << endl;
        
    } else {
        cout << "The numbers should be between [10, 1000]" << endl;
    }

    return 0;
}
