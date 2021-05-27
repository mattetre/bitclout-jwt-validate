# bitclout-jwt-validate

This project is a simple javascript/node.js example to help validate & decode a BitClout JWT token using a BitClout public key

This was created based on the BitClout identity docs example of how to validate a JWT token (https://docs.bitclout.com/devs/identity-api#validation-in-go). I struggled to get validation working solely based on the docs so I thought this example might help others.

Feel free to reach out to [@mattetre](https://bitclout.com/u/mattetre) from [@bithunt](https://bitclout.com/u/bithunt)

## BitClout public key info

What I found in my testing is that the BitClout public key is not the public key that you get from the original keypair that is used to sign the your JWT. It has been manipulated to add in a "prefix" and then base58 encoded. If you want to validate your JWT you need to decode your public key and then remove the prefix to obtain the original public key. This removal of the prefix was not obvious for me looking at the BitClout identity docs.

See for more info: `privateKeyToBitcloutPublicKey` in https://github.com/bitclout/identity/blob/main/src/app/crypto.service.ts#L128

## Running the code

### Setup

install dependencies

```shell
npm install
```

### Running

```shell
node index.js --publicKey BITCLOUT_PUBLIC_KEY --jwt JWT_TOKEN
```

```shell
node index.js -p BITCLOUT_PUBLIC_KEY -j JWT_TOKEN
```

example:

```shell
node.js index.js --publicKey abc123 --jwt 321xyz
```

## Credits:

Thanks [@mubashariqbal](https://bitclout.com/u/mubashariqbal) and [@transhumanist](https://bitclout.com/u/transhumanist) for your code getting BitClout identiy working on web!
