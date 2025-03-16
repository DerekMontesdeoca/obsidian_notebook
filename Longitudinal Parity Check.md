Parity check is a very simple type of checksum that consists of deciding on a parity protocol which could be even or odd, and then, breaking the data into byte - 1 sized chunks. After that, the sum of the n - 1 data bytes are added and checked if they are even or odd. The last byte is used to make the data conform to the previosuly established protocol. If any bit is flipped, it means the data is corrupted. 

# Parity Protocol

A parity protocol (odd or even) is chosen. This means that the creator of the checksum and the checker agree that all bytes must be even or odd. 

# Data bits

The data bits are added to check if they are even or odd, and the last bit is used to make the whole byte conform to the previously established protocol. That means that if the even protocol was chosen and the parity is odd, the last bit must be 1 to make it even. If the even protocol was chosen and the parity is even, the last bit must be 0 to keep it even. 

# Checking

When the checker performs the check, it has to make sure that every byte conforms to the parity protocol established.

# Algorithm to Check Parity

The easiest way to do this is to XOR every bit. 

# Caveats

If the message is corrupted on a byte by an odd number of errors, the error is detectable, but if the message is corrupted on a byte by an even number of errors, the error is **not** detectable.
