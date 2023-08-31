# RSA RoCC Accelerator

This is an accelerator that implements the Secure Hash Algorithm 3.
It is mainly meant to be used in the
[Chipyard development environment](https://github.com/ucb-bar/chipyard)
but can be ported to other environments (i.e. plain
[Rocket Chip](https://github.com/chipsalliance/rocket-chip)).
For more information on how the accelerator works, please refer to the
[SHA3 documentation in Chipyard](https://chipyard.readthedocs.io/en/latest/Generators/SHA3.html).

# Software Workloads

See [software/README.md](software/README.md) for more information on building software tests for this
accelerator.

# RSA Algorithm
The RSA Algorithm holds the following features -
 * RSA uses two sets of keys (public and private)
 * exponentiation in a finite field over integers including prime numbers
## RSA Modulus
The initial procedure begins with selection of two prime numbers namely p and q, and then calculating their product N, as shown:
  ```
  N=p*q
  ```
Here, let N be the specified large number.

## Derived number (e) 
Consider the number e as a derived number which should be greater than 1 and less than (p-1) and (q-1). The primary condition will be that there should be no common factor of (p-1) and (q-1) except 1.

## Public key 
The specified pair of numbers n and e forms the RSA public key and it is made public.

## Private Key
Private key d is calculated from the numbers p, q, e. The mathematical relationship between the numbers is as follows - 
ed = 1 mod (p-1) (q-1)
The above formula is the basic formula for Extended Euclidean Algorithm, which takes p and q as the input parameters.

## Encryption Formula 
Consider a sender who sends the plain text message to someone whose public key is (n,e). To encrypt the plain text message in the given scenario, use the following syntax :
```
C = Pe mod n
```

## Decryption Formula
The decryption process is very straightforward and includes analytics for calculation in a systematic approach. Considering receiver C has the private key d, the result modulus will be calculated as :
```
Plaintext = Cd mod n
```


# References

https://people.eecs.berkeley.edu/~kubitron/courses/cs262a-F13/projects/reports/project11_report.pdf
https://www.tutorialspoint.com/cryptography_with_python/cryptography_with_python_understanding_rsa_algorithm.htm
