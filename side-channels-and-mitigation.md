
# Common side-channel mitigation features present in most of the seure SoC:

- Authentication first: The device authenticates the bitstream before decrypting it. Attackers cannot perform differential attacks on the AES encrypted data without breaking authentication.
- Key update: Limits the amount of encrypted data per key to 1024 bytes.
- Direct key loading: Uses a 256-bit point-to-point key bus to reduce emissions.
- Data scrambling: Scrambles data on long wires within the configuration network on a chip (NoC).

## Links
- https://www.intel.co.jp/content/www/jp/ja/programmable/documentation/ndq1483601370898.html
