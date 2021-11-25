# Aritro-Sarkar----Sainya-Ranakshetram-Hackathon-2021-CTF-Solutions 
Solution by Aritro Sarkar (Aritro15)

Assumption:
The following Assumption were taken before developing a solution for the challenge - 
1. The code will run on a remote server and we will use a different machine to connect to the remote server and crash the machine.


Solution: 
A simple python script that takes ip address, port number and attack method as command line inputs and sends data to the application to crash it.

Usage: python3 Buffer_Overflow_Exploit.py -h <ipv4> -p <port> -m <Method (1/2)>')
Examples -
python3 Buffer_Overflow_Exploit.py -h 127.0.0.1 -p 8000 -m 1 (to use method 1)
python3 Buffer_Overflow_Exploit.py -h 127.0.0.1 -p 8000 -m 2 (to use method 2)


Attack Methods - 
The solution uses the following two techniques to crash the application - 
1. Method 1: Utilizes the limit of data type 'int' in C++, 'int' can take input between -2147483648 and 2147483647, passing it an input outside this strict limit will cause it to crash.
2. Method 2: This method is specific to this particular instance of application, it exploits the static size allocation of the array (10 in this case) and no checks while inserting data into the array. If data that is to be inserted in the array is more than the static limit, it will trigger compiler's anti buffer overflow mechanism and terminate the application, thus effectively crashing the application.
