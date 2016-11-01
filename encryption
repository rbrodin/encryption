# RSA Encryption/Decryption Algorithm Project - October to November 2016.

# From the built-in library import the greatest common divisor function, part of the Euclidean Algorithm.
from fractions import gcd

def publicKey(p, q):
    
    """
    Defines a function named publicKey with arguments p (integer)m and q (integer). The function will return a list of e (Number relatively prime to j), j (Used later in the code: (p - 1) * (q - 1)), and N (p * q).
    """
    
    # Variable N is initialized, is set to p multiplied by q, the number will always, unless p or q is 2, be an odd number.
    N = p * q
    
    # Variable j is set equal to p-1 multiplied by q-1. This number will always be an even number.
    j = (p - 1) * (q - 1)
    
    # e is an empty list, which will be used to store numbers which are relatively prime to variable j.
    e = []
    
    # A For Loop is used to iterate through all of the numbers in the range of 2 to N. The loop is set from 2 on because in using the GCD function, 1 is the answer we want, so it doesn't make sense to have the loop begin at one.
    for i in range(2, N):
        
        # The GCD function is used to check if two numbers, i, the current iteration in the for loop, and j (p - 1 * q - 1), are relatively prime. If they have no common factors, the function will return one, which means they are relatively prime.
        if gcd(i, j) == 1:
            
            # If the number is relatively prime, then it is appended to the e list.
            e.append(i)
        
        # Otherwise, the loop continues on. N = N is a place holder.    
        else:
            N = N 
            
    # Variable e is flipped, so the larger numbers come first. Meaning that e, the public key, will be more secure, as it will be larger and harder to compute. E will be used to compute d, the private key, which needs to be secure. This is an important reason in why the list is flipped.    
    e = e[::-1]
    
    # The function returns a list of e, the public key, j (p - 1 * q - 1), which will be used in computing the private key, and N, (p * q).
    return [e[0], j, N]
    
def encrypt(e, N, plaintext): 
    
    """
    Function encrypt is set to take the arguments, e (from publicKey function), j (from publicKey function), and plaintext, the message that will be encrypted, it must be a string. The function will return a list M, a list of the ciphertext.
    """
    
    # Variable messagelist is initialized as an empty list, it will be used to store the plaintext.
    messagelist = []
    
    # Variable M is initialized as an empty list. It will be used to store the encrypted text, also known as the ciphertext.
    M = []
    
    # A For Loop is set to iterate through every character given, which then appends each character to a list. This will be used for ease of seperation for the encryption method.
    for i in plaintext:
        messagelist.append(i)
    
    # A For Loop is used to iterate through all of the items in the list, messagelist. For every character, it will be encrypted and appended to the list, M.
    for i in messagelist:
        
        # Variable value is set equal to the ordinal of i, which will return a decimal number.
        value = ord(i)
        
        # The character will finally be encrypted, using the equation, M ^ e (mod N), which will encrypt the character. Value, or the singular value of M, is put to the power of e, modulo N. That value is then converted into a string, for the decryption function (You can't iterate over integers). The string value is then appended to M. This process is repeated for every character provided.
        M.append(str((value ** e) % N))
    
    # List M is returned, which a value such as '50', as a possible list item.
    return M
    
    
def decrypt(e, j, N, M):
    
    """
    Function decrypt takes inputs, e (taken from publicKey function, relatively prime to j), j (taken from publicKey function, p - 1 * q - 1), N (taken from publicKey function, p * q), and M (taken from the encrypt function, the encrypted message/ciphertext. The function will return a string of characters, the plaintext.
    """
    
    # Variable C is initialized as an empty string, it will be used to store the decrypted plaintext.
    C = ""
    
    # List dlist is initialized as an empty list. It will be used to store d, or the private key.
    dlist = []
    
    # A For Loop is set to iterate through all numbers in the range of 2, (if it was a range of one on, the loop would not work correctly, as one is always a factor of any number. The range ends at j, which is, again, p - 1 * q - 1. 
    for i in range(2, j):
        
        # If i multiplied by e, mod j is equal to one, than the d value will work to decrypt the message. The Extended Euclidean Algorithm and inverse Modular arithmetic are used here.
        if (i * e) % j == 1:
            
            # If it is true, i will be appended to list, dlist, and will be used to decrypt the message. The loop will then end, as there is no need to loop through any more numbers.
            dlist.append(i)
            break
        
        # Otherwhise, dlist is set to dlist, a filler.
        else:
            dlist = dlist
    
    # A For Loop is set to iterate through all of the characters in M. The loop is the final step in the decryption algorithm. 
    for i in M:
        
        # Variable char is set equal to the integer i, as the encrypt function returns all items in M as strings, to the power of dlist[0]. dlist[0] is the private key, otherwise known as d. Then, that value will be mod (is there a plural for this?) N (p * q). The value is now decrypted.
        char = ((int(i) ** dlist[0]) % N)
        
        # Variable C is set to the chr(char) function, which will return the character that the value of char correlates to, and added to C. This will be the plaintext.
        C = C + chr(char)
        
    # Finally, C is returned. C is a string.    
    return C

new = publicKey(17, 11)
print decrypt(new[0], new[1], new[2], encrypt(new[0], new[2], "They're going right!"))

