
# ethereumj-android

This library is an Android-friendly redistribution of [ether.camp's](http://ether.camp) ethereumj. It depends on [SpongyCastle](https://rtyley.github.io/spongycastle/) to provide a comprehensive security implementation suitable for generating and operating on Ethereum-compatible private keys.

## Usage

```java
package your.package.id;

import java.security.Security;
import java.security.SecureRandom;

import org.spongycastle.util.encoders.Hex;
import org.spongycastle.jce.provider.BouncyCastleProvider;

import za.co.io.ethereumj_android.crypto.ECKey;

class YourClass {

    static {
        Security.insertProviderAt(new BouncyCastleProvider(), 1);
    }

    public static void main(String[] args) {
        ECKey eck = new ECKey(Security.getProvider("SC"), new SecureRandom());
        System.out.println("Private key: " + Hex.toHexString(eck.getPrivKeyBytes()));
        System.out.println("Public key: " + Hex.toHexString(eck.getPubKey()));
        System.out.println("Address: " + ("0x" + Hex.toHexString(ECKey.computeAddress(eck.getPubKey()))));
    }

}
```

## Notes

* Shouldn't ethereumj have been named jthereum? :thinking:

## Legal

ethereumj is distributed under the MIT license by ether.camp ([LICENSE](https://github.com/ethereum/ethereumj/blob/develop/LICENSE))