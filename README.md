# DigitalOcean Security

If you have found a security vulnerability in a DigitalOcean product, please submit it via our HackerOne bug bounty program: <https://hackerone.com/digitalocean>.

If you are a partner attempting to report a security concern via embargo, email us at [security@digitalocean.com](mailto:security@digitalocean.com).

If you wish to encrypt your communication, you may do so via encrypting a message to [security@digitalocean.com](mailto:security@digitalocean.com) with either the [Age public key](/age_public_key.txt) or [GPG public key](/GPG_public_key.txt) in this repo.

## Encrypted communications

We recommend you leverage <https://github.com/FiloSottile/age> for encrypted communications.

1. Generate a public-private keypair.
    ```bash
    age-keygen -o secret_key.txt
    ```
1. Encrypt your message with our public key. Ensure your output is PEM-encoded with the --armor` flag.
    ```bash
    age --encrypt -r age12n58x3u8ky5nse8szjusasukdv8k0588raahk8lesvr6zt6nq9fsjkn2kw -o encrypt.txt --armor mymessage.txt
    # or
    age --encrypt -r age12n58x3u8ky5nse8szjusasukdv8k0588raahk8lesvr6zt6nq9fsjkn2kw -o encrypt.txt --armor <<< "My message"
    ```
    
    ![Age encryption](https://user-images.githubusercontent.com/6969296/214439812-7a185afa-cba2-469d-893e-4aed298997ac.png)

1. Email the `encrypt.txt` to us at [security@digitalocean.com](mailto:security@digitalocean.com).
1. We will respond to any encrypted communications with an encrypted response. Decrypt a message with:
    ```bash
    age --decrypt -i secret_key.txt -o plain.txt response.txt
    ```

    ![Age decryption](https://user-images.githubusercontent.com/6969296/214439670-8420d85b-9c82-488a-a2d9-ae689ea01ce4.png)

You may also send us GPG-encrypted communication using the `GPG_public_key.txt` file in this repository.
