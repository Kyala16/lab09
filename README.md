# lab09

![Jokes Card](https://readme-jokes.vercel.app/api)

Task about GPG.
We do this step 

```
sudo apt install gpg
gpg --list-secret-keys --keyid-format LONG
gpg --full-generate-key
```
![This is an image](/Pictures/RSA1.png)
```
gpg --list-secret-keys --keyid-format LONG
```
![This is an image](/Pictures/RSA2.png)
```
GPG_KEY_ID=$(gpg --list-secret-keys --keyid-format LONG | grep ssb | tail -1 | awk '{print $2}' | awk -F'/' '{print $2}')
GPG_SEC_KEY_ID=$(gpg --list-secret-keys --keyid-format LONG | grep sec | tail -1 | awk '{print $2}' | awk -F'/' '{print $2}')
gpg --armor --export ${GPG_KEY_ID} | xclip -selection clipboard
xclip -selection clipboard -o
```
![This is an image](/Pictures/RSA3.png)
```
git config user.signingkey ${GPG_SEC_KEY_ID}
git config gpg.program gpg
```
```
git tag -s v0.1.0.0
git tag -v v0.1.0.0
git show v0.1.0.0
git push origin main --tags
```
