**unifiedKey Suite Overview**

**scriptKey (compatible with Scratch & TurboWarp)**
scriptKey is the most basic kind of key; consisting of 2 sub-keys: username and time signature, with an average length of 25 characters and doesn't have a maximum character limit. 
These 2 sub-keys alone allow for what we classify as "program-level locking", which is the lowest type of key identification, which means that this key cannot be used on other software without some kind of reverse-engineering. This type of key allows for username matching and identification as well as an expiration time, which is up to 2.5 minutes. 

This is the least secure and least accurate type of key, and its only advised to be used for one-time prompts, like activating a piece of software, program-to-program tasks and more.

**activeKey (compatible with TurboWarp. Learn more here)**
activeKey is derived from scriptKey, but allows for what we classify as "software-level locking", which is in the middle of our "locking" ladder. activeKey consists of 3 sub-keys: username, time signature and AAP. 
activeKey allows for what we call the Authorization and Authenticity Protocol (AAP), which allows for key-specific hashing, allowing the system to be able to identify if a key has been altered, even down to the specific Unicode character (preventing a phonograph attack). activeKey also stores the same information as scriptKey, which is username, time signature and now a string of encoded and hashed string to check if the activeKey has been altered. scriptKey and activeKey are not cross-compatible. You cannot use an activeKey on a program that only support a scriptKey and vice versa.

activeKey is meant to be used for handling tasks where software-level locking and high-security standards are required, such as secure enclave compute, secure communications, or any scenario where ensuring the integrity and authenticity of the key is critical.

**tokenKey (compatible with TurboWarp)**
tokenKey is derived from activeKey, which will allow for what we classify as "hardware-level locking" which is the most secure type of unifiedKey; allowing key-identification and association to a group of devices with very specific identifiers (i.e macOS device running Chrome w/ 8 GB of RAM or Windows device running Firefox w/ 16 GB of RAM, with a screen resolution of 1920 by 1080), and can be locked to devices that have the exact same identifier as the device the key was generated on.
The entire key itself is also encoded a number of times, making it very hard, and most importantly, computationally expensive to reverse the encrypted key itself, not even encrypting the main key, which is also encoded a number of times. tokenKey also uses a much more accurate timing algorithm compared to activeKey and scriptKey, which allows the key to be deactivated as soon as 2.5 minutes is over, unlike activeKey and scriptKey, which still have a ~1-30 second buffer after being initiated.
tokenKey is the most secure type of unifedKey yet, and is mostly reserved for low-level system compute (i.e updating software, changing/running code, etc.) or high-risk computes (handling of sensitive data, VVID on scriptOS, etc.)

**unifiedKey Suite Security Statistics**
Note: all of these calculations are an absolute minimum. The actual probability is most likely astronomically lower than what is listed here.

**scriptKey**
Even though scriptKey is still relatively insecure, the approximate chance of a brute force and successfully decoded is ~1 in 11^50 or an approximate 0....9076% ("..." represents 51 zeros between the decimal point and the first non-zero digit) chance of successful a brute force.

**activeKey**
Considering that scriptKey is already incredibly hard to brute force successfully (and that key isn't even hashed), the chance of a successful brute force of an activeKey alone (not fully decoded, just the raw encoded version before the hashing) would be ~1 in 95^88 (~1 in a quindecillion) or an 0...8343% ("..." represents 151 zeros between the decimal point and the first non-zero digit) chance of being brute forced successfully, decrypted the hashed encoded key.

Now, that's just step 1. To further get the actual value of the key, you have to then decrypt it again, and the probability of getting that right is ~0...863617% ("..." represents 84 zeros between the decimal point and the first non-zero digit).

So, the total probability of successfully decrypting an entire activeKey is ~1.20×(10^151).

**tokenKey**
tokenKey is even more secure than activeKey. Since the calculations for tokenKey would be too large to compute, the chance of successfully decrypting a tokenKey, then decrypting the encrypted key again (and again, and again, and again, and so on and so forth), would be at least 1 in a septemdecillion.
