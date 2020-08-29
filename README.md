
This was a small test to show how one might reversibly map each ~1m^2 element
of the globe onto a 3-tuple of words. Check it out [here](https://pballett.github.io/whatfreewords/).

To do this we needed three things:
1. A function which maps metre-accurate (latitude, longitude) pairs into three 5-digit integers below 40k.
2. An ordered list of 40k words which acts as a bijection between integers and words.
3. A scrambling function which can be called in the first function to ensure nearby (latitude,longitude) pairs are mapped to very different integers

Note that all of these functions must be invertible for the mapping to be reversible.  

The scrambling function implemented here is inspired by format preserving encryption: it maps a sequence of 14 digits to another by passing it through a [Feistel network](https://en.wikipedia.org/wiki/Feistel_cipher). There is no need for this encryption to be secure, so the implementation has been simplifed. The point is just to map 14-digits to 14-digits, to exhibit sensitive dependence on the input and to be reversible. 
