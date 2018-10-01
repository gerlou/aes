# AES-128 and AES-256

Encryption 128-bit key:

We first check the size of the key and see how many bytes we will need to pad it with. We have a method that adds the right amount of padding using CMS padding.
We then take the key and parse it into a 2D array. Once we have that, we calculate all the round keys and store it inside a global variable called roundKeys. 
Then, we go through every 16 bytes in the input and parse them into an array of columns. Before starting the processing rounds, we add the round key to the 
original key. For the first 9 rounds, we do the same thing: subBytes, shiftRows, mixColumns, and then addRoundKey. During the final 10th round, we do everything 
the same, except we don't do the mixColumns step. Once all of this processing is done, we append this to our result bytearray. The whole process is repeated for the next
16 bytes and so on, until we've gone through the whole input. 


Decryption 128-bit key:

This is basically the reverse of what we did for encryption. In the beginning, we do the same thing with the key, where we parse it into a 2D array and then get all of 
the round keys. However, since we want to do a bitwise XOR of the last four words in the key schedule with the ciphertext block before doing any processing rounds, we 
reverse the list of round keys. This way, we can easily get the key we want for each round as we go through the key schedule in reverse order. After we've added 
the round key, we start our processing rounds. The order of operations is the same each round; we do inverseShiftRows, inverseSubBytes, addRoundKey, and then mixColumnsInverse.
In the final round, we do everything the same except we skip out on the inverseMixColumns step. We then remove the padding and append this to our result bytearray.  
