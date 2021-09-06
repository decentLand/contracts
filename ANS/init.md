# Arweave Names Service

A simple labels contract to make the interacting with Arweave wallets addresses as simple as sending to an e-mail domain through addresses resolving.

# Motivation

Using and adopting names service accross Arweave ecosystem has several benefits:
- faciliate of sharing addresses and sending AR/PSTs
- create an economic cycle through domains financial activities (trading)
- the ability to be used as social profiles contructors in Arweave based social networks (e.g. decent.land users)


## Terminology

- label: equivalent to domain's name in DNS, such as **"decent"** in decent.ar
- owner: the controller of the label
- name: full ANS identifier such as "decent.ar" (label and 'ar' TLD sepperated by a dot)

## Label's string handling

ANS registry contract uses the NFKC (Normalization Form Compatibility Composition) unicode normalization algorithm and case folding to normalize the label's string before comparing its length and allowed unicodes that are predefined in the contract. Then, the label get minted and stored according to its processed format (after normalization), following a Nameprep-like methodology. 

**Allowed unicodes**
The allowed unicode are those of the lowercase alphabetical characters in addition to integers from 0 to 9. Thus, usernames as known as labels are alphanumeric.
The supported UTF-16 code units range from 48 to 57 (0 -> 9) and from 27 to 122 (a -> z).

The usage of the NFKC algorithm allows to reduce the visual security issues like:
- visual spoofing
- reduce visual confuses. [examples](https://util.unicode.org/UnicodeJsps/confusables.jsp)
- Punnycode and Script spoofing

## Available Labels
ANS labels minting is based and limited using the arrangement without repitition of the conditional probability
 
<img src="https://render.githubusercontent.com/render/math?math=%5CHuge%20A_n%5Ep%20%3D%20%7Bn!%7D%2F%7B(n-p)!%7D">

Knowing that `p` is that arbitrary label string entered by the user that may be alphanumerical, and `n` is the total number of allowed characters which is 36 (26 characters from alphabetical characters and 10 characters from the allowed integers).
For a better UX, labels of length equal to one are disallowed and cannot be minted, hence, that total number of labels that can ever exist is more than 43B labels. Breakdown:

| label length  | label supply  |
| :-----------: |:-------------:| 
| 2             | 1260          | 
| 3             | 42,840        | 
| 4             | 1,413,720     |
| 5             | 45,239,040    | 
| 6             | 1,402,410,240 | 
| 7             | 42,072,307,200|

Label scarcity is determined by its length, the lower length it has, the more scarce it is. No renewal fees.

## Possible Minting Models
This section discusses the possible option to be adopted for the label minting process

### Model 1: Free minting

**Pros**
Easier UX, no `$DLT` token is required to mint a label

**Cons**
- limited to 1 label minted per address
- possible Sybil due to labels acquisation
- minted is blockheight limited. unmited labels after a stage's end are sealed forever (6-7 length labels are in an open stage)

### Model 2: minting using $DLT

**Pros**
- no minting limits per address, minting fee is related to the label length
- makes `$DLT` more scarce through burning a percentage of the minting fees
- auto-distribution of a bigger chunk of `$DLT` in-contract for stakers or label owners. Fees can be withdraw'd from the SWC

**Cons**
- a harder UX for new users: owning `$DLT`, depositing DLT tokens in the SWC, additional TXs.
- the need of two tokens (DLT & AR) to make a minting transaction


## Labels marketplace


Labels may be a new asset with new standars not compatible with PSTs or atomic NFTs standards, thus, that requires building a marketplace dedicted for ANS labels.

### characteristics
- main currency: `$DLT`
- create an economical experience and new opportunities
- incentives for `$DLT` holders through marketplace earned fees

