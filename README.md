# aes

Encryption 128-bit key

We first check the size of the key and see how many bytes we will need to pad it with. We have a method that adds the right amount of padding using CMS padding.
We then take the key and parse it into a 2D array. Once we have that, we calculate all the round keys and store it inside a global variable called roundKeys. 
Then, we go through every 16 bytes in the input and parse them into an array of columns. Before starting the processing rounds, we add the round key to the 
original key. For the first 9 rounds, we do the same thing: subBytes, shiftRows, mixColumns, and then addRoundKey. During the final 10th round, we do everything 
the same, except we don't do the mixColumns step. Once all of this processing is done, we append this to our result bytearray. The whole process is repeated for the next
16 bytes and so on, until we've gone through the whole input. 



