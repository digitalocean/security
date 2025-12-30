# DigitalOcean Security

If you have found a security vulnerability in a DigitalOcean product, please submit it via our Intigriti bug bounty program: <https://app.intigriti.com/programs/digitalocean/digitalocean>.

If you are a partner attempting to report a security concern via embargo, email us at [security@digitalocean.com](mailto:security@digitalocean.com).

If you wish to encrypt your communication, you may do so via encrypting a message to [security@digitalocean.com](mailto:security@digitalocean.com) with either the [Age public key](/age_public_key.txt) or [GPG public key](/GPG_public_key.txt) in this repo.

## Encrypted communications

We strongly recommend you leverage <https://github.com/FiloSottile/age> for encrypted communications and [avoid GPG](https://gpg.fail/).

1. Generate a public-private keypair.
    ```bash
    age-keygen -pq -o secret_key.txt
    ```
1. Encrypt your message with our public key. Ensure your output is PEM-encoded with the --armor` flag.
    ```bash
    age -R age_public_key.txt --armor message.txt > message.txt.age
    # or
    age -R age_public_key.txt --armor <<< "My message" > message.txt.age
    ```
2. Email the `message.txt.age` to us at [security@digitalocean.com](mailto:security@digitalocean.com).
3. We will respond to any encrypted communications with an encrypted response. Decrypt a message with:
    ```bash
    age -d -i your_secret_key.txt response.txt.age > message.txt
    ```

    You can also store your private key in a password manager like 1Password and decrypt messages similarly to the following:
    ```bash
    age -d -i <(op read "op://Your Vault/Age keypair/private key") response.txt.age > message.txt
    ```

If you must, you may also send us GPG-encrypted communication using the `GPG_public_key.txt` file in this repository.
