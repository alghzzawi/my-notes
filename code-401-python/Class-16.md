# __Cryptography__

#### One of the most punctual encryption techniques is the Caesar Cipher, concocted by Julius Caesar more than two thousand a long time prior to communicate messages to his allies. The Caesar Cipher may be a extraordinary introduction to encryption, decryption, and code cracking, much appreciated to its straightforwardness.

<br>


### __Encrypting a message__

#### Imagine Caesar wants to send this message:

    SECRET MEETING AT THE PALACE

#### Here's what that might look like encrypted:

    YKIXKZ SKKZOTM GZ ZNK VGRGIK

<br>

<br>

#### That looks an horrendously part like gobbledygook at to begin with, but this encrypted message is really exceptionally related to the initial text. The Caesar Cipher may be a simple substitution cipher which replaces each original letter with a diverse letter within the letter set by shifting the letter set by a certain amount. 

#### To make the encrypted message over, I moved the letter set by 6 and utilized this substitution table:

||
| :---------: |
| A	B	C	D	E	F	G	H	I	J	K	L	M	N	O	P	Q	R	S	T	U	V	W	X	Y	Z |
| G	H	I	J	K	L	M	N	O	P	Q	R	S	T	U	V	W	X	Y	Z	A	B	C	D	E	F |

#### S shifts 6 letters over to Y, E shifts 6 letters over to K, etc. Here's the first word and its shifts:

||
| :---------: |
| S	E	C	R	E	T|
| Y	K	I	X	K	Z|

---

<br>

## Decrypting a message

#### According to historical records, Caesar always used a shift of 3. As long as his message recipient knew the shift amount, it was trivial for them to decode the message.

#### Imagine Caesar sends this message to a comrade:

    EHZDUH EUXWXV

#### The comrade uses this substitution table, where the alphabet is shifted by 3:

||
| :---------: |
| A	B	C	D	E	F	G	H	I	J	K	L	M	N	O	P	Q	R	S	T	U	V	W	X	Y	Z|
| D	E	F	G	H	I	J	K	L	M	N	O	P	Q	R	S	T	U	V	W	X	Y	Z	A	B	C|

#### They can then decode the message with certainty. The first letter "E" was shifted by 3 from "B", the second letter "H" was shifted by 3 from "E", etc. The result is this ominous message:

    BEWARE BRUTUS

---

<br>

## Known plaintext

#### Another term for the original unencrypted message is plaintext. If the enemy already knew some part of the plaintext, it will be easier for them to crack the rest of the encrypted version.

#### For example, messages tend to start with similar beginnings. In WWII, encrypted German messages always started with a weather forecast, which ultimately made them easier for British mathematician Alan Turing to crack.

---

<br>

## Encryption, decryption, and cracking

#### Thanks to this exploration of the Caesar Cipher, we now understand the three key aspects of data encryption:

* #### __Encryption__: scrambling the data according to a secret key (in this case, the alphabet shift).

* #### __Decryption__: recovering the original data from scrambled data by using the secret key.

* #### __Code cracking__: uncovering the original data without knowing the secret, by using a variety of clever techniques.