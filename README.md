<img src="https://github.com/MohiniShinde2103/Image-Steganography-Android-App/blob/main/images/cover.png" height = "500px"/>

# Image Steganography
Steganography is the process of hiding a secret message within a larger one in such a way that someone  cannot know the presence or contents of the hidden message. Although related, Steganography is not to be confused with Encryption, which is the process of making a message unintelligible—Steganography attempts to hide the existence of communication.
The main advantage of steganography algorithm is because of its simple security mechanism. Because the steganographic message is integrated invisibly and covered inside other harmless sources, it is very difficult to detect the message without knowing
the existence and the appropriate encoding scheme .

# Proposed Algorithm
The algorithm is more dedicated towards the algorithm proposed by Rosziati Ibrahim and Teoh Suk Kuan in their [Research Paper](https://arxiv.org/ftp/arxiv/papers/1112/1112.2809.pdf) published on February 25, 2011.
## Encoding Algorithm
- Firstly, the secret message that is extracted is `compressed` as the contents in the compressed string will significantly hard to detect and read, furthermore it reduces the size of string.
- Secondly, the compressed string is `encrypted` with the secret key.
- Finally, `encoding` the encrypted message in the image. It uses `LSB steganographic embedding` to encode data into an image. Once the message is encoded the process stops.
### LSB(Least Significant Bit) Embedding
The LSB is the lowest significant bit in the byte value of the image pixel.
The  LSB  based  image  steganography  embeds  the  secret  in the  least  significant  bits  of  pixel  values  of  the  cover  image (CVR).
The concept of LSB Embedding is simple. It exploits the fact that the level of precision in many image formats is far greater than that perceivable by average human vision. Therefore, an altered image with slight variations in its colors will be indistinguishable from the original by a human being, just by looking at it. In conventional LSB technique, which requires eight bytes of pixels to store 1byte of secret data but in proposed LSB technique, just four bytes of pixels are sufficient to hold one message byte. Rest of the bits in the pixels remains the same.
Following shows the bit level interpretation of the algorithm :  
<div align="center"><img src="/images/lsb1.png"/></div>

## Decoding Algorithm
- Firstly, `decode` the message from the encrypted image using LSB decoding.

- Secondly, `decrypt` the compressed message from the decoded message using the secret key.

- Finally, `decompress` the message to get the original compressed message.   

Consider the following encoding, it is totally undetectable by human eyes.
<div align="center"><img src="/images/original_encoded.png"/></div>


# Documentation

#### ImageSteganography Class

| Java attribute     | Java set methods                | Description                                                  | Default Value |
| :---------------- | :------------------------------ | :----------------------------------------------------------- | :-----------: |
| Message | setMessage(...) , getMessage() | Set the value of message, Get the value of message. | Null      |
| Secret_Key | setSecret_key(...) | Set the value of secret key. | Null      |
| Image  | setImage(...) | Set the value of image.              | Null      |
| Encoded_Image | getEncoded_image() | Get the value of encoded image after text encoding. | Null       |
| Encoded | isEncoded() | Check that the encoding is over or not | false       |
| Decoded | isDecoded() | Check that the decoding is over or not. | false       |
| SecretKeyWrong | isSecretKeyWrong() | Check that the secret key provided was right or wrong but after decoding was done. | true     |



### Example App

There are two options `Encode` and `Decode`. In the encode section you can hide a secret message into an image without making any noticeable changes. In the decode section you can extract the message from the encoded image by inserting the correct key.

**Note** - After pressing the `Save` button, both the original and encoded images are saved at the location ```Android/data/com.ayush.steganography/files/Documents/<UUID>/ ```

|                            Encode                            |                            Decode                            |
| :----------------------------------------------------------: | :----------------------------------------------------------: |
| <img src="https://github.com/MohiniShinde2103/Image-Steganography-Android-App/blob/main/images/encode.gif" height = "500px"/> | <img src="https://github.com/MohiniShinde2103/Image-Steganography-Android-App/blob/main/images/decode.gif" height = "500px"/> |



