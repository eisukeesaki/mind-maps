# public key encryption

```text

public key encryption
    keys
        can be used on messages
            encrypt
            decrypt
    key generator
        generates key pair using one way cryptographic functions
    key pair
        generated for one holder
        public key
            published
            distributed
        private key
            kept as key pair holder's secret
    messages
        message A
            properties
                encrypted with
                    public key
                can be decrypted with
                    private key
            ensures
                data integrity
                    that fact that a message can be decrypted with a private key
                        ensures that the messge has not been tampered with
        message B
            properties
                encrypted with
                    private key
                can be decrypted with
                    public key
            ensures
                authenticity of sender
                    that fact that the message can be decrypted with a public key
                        ensures that the message was sent by the private key holder
        message C
            properties
                encrypted with
                    public key and private key
                can be decrypted with
                    public key and private key
            ensures
                authenticity of sender
                    that fact that the message can be decrypted with a public key
                        ensures that the message was sent by the private key holder
                data integrity
                    that fact that a message can be decrypted with a private key
                        ensures that the messge has not been tampered with
            
```

