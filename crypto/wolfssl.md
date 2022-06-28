
# Init-Update-Final Transformation Model

This model is used for implementation of crupto functions that accepts arbitrary large inputs in an interative way. For embedded device with low momery footprint, it is not feasible to load the entire input data into RAM to process together. In this context, the init-update-final approach is very useful. Init-update-final approach is used in implementation of various crypto libraries like OpenSSL and Wolfssl. 

Steps of init-update-final model for hash functions are given below:
- **Init.** Create an context of crypto module and initialize its parameters.
- **Update.** Append the input data into internal buffer which is empty initially. If the buffer has data chuncks whose size equal to block size of hash function, the it is processed in this step. Rest of the tail-end data bytes are kept in the buffer.
- **Final.** In this step rest of buffer data, which are not processed in update step, are processed along with alogorithm specific paadded bytes.

# Linux Kernel Crypto API
https://kernel.readthedocs.io/en/sphinx-samples/crypto-API.html
