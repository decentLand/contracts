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

<math xmlns="http://www.w3.org/1998/Math/MathML">
  <mstyle displaystyle="true">
    <mrow>
      <msubsup>
        <mi>A</mi>
        <mi>n</mi>
        <mi>p</mi>
      </msubsup>
    </mrow>
    <mo>=</mo>
    <mfrac>
      <mrow>
        <mi>n</mi>
        <mo>!</mo>
      </mrow>
      <mrow>
        <mrow>
          <mo>(</mo>
          <mi>n</mi>
          <mo>&#x2212;</mo>
          <mi>p</mi>
          <mo>)</mo>
        </mrow>
        <mo>!</mo>
      </mrow>
    </mfrac>
  </mstyle>
</math>