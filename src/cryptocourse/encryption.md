# Encryption

假设 Alice 和 Bob 共用一个密钥 \\( k \\), Alice 想要向 Bob 发送消息 \\( m \\), 同时避免**窃听**.

- 本章的技术只在对每个消息使用一个密钥的情况下保证安全.  
  若要对多条消息使用相同密钥, 应该使用\[第 5 章\]的技术.
- 本章的技术不保证**消息完整性**. 若要防止消息被篡改, 应该使用\[第 6 章\]的技术.
- 本章没有说明 Alice 和 Bob 如何交换密钥. \[第 21 章\]将会介绍在不可靠信道上交换密钥的协议.

## Shannon ciphers and perfect security

给定<ruby>**密钥**<rp>(</rp><rt>key</rt><rp>)</rp>**空间**<rp>(</rp><rt>space</rt><rp>)</rp></ruby> \\( \mathcal{K} \\), <ruby>**明文**<rp>(</rp><rt>plaintext</rt><rp>)</rp>**空间**<rp>(</rp><rt>space</rt><rp>)</ruby> \\( \mathcal{M} \\), <ruby>**密文空间**<rp>(</rp><rt>ciphertext space</rt><rp>)</rp></ruby> \\( \mathcal{C} \\). 定义<ruby>**香农密码**<rp>(</rp><rt>Shannon cipher</rt><rp>)</rp></ruby>包括<ruby>**加密函数**<rp>(</rp><rt>encryption function</rt><rp>)</rp></ruby> \\( E: \mathcal{K}\times\mathcal{M}\to\mathcal{C} \\) 和<ruby>**解密函数**<rp>(</rp><rt>decryption function</rt><rp>)</rp></ruby> \\( D: \mathcal{K}\times\mathcal{C}\to\mathcal{M} \\), 使得对 \\( k\in\mathcal{K} \\) 和 \\( m\in\mathcal{M} \\) 都有 \\( D(k,E(k,m))=m \\).

设 \\( \mathbf{k} \\) 服从 \\( \mathcal{K} \\) 上的均匀分布, 若对 \\( m\in\mathcal{M} \\) 都有 \\( E(\mathbf{k},m) \\) 的分布相同, 则称 \\( (E,D) \\) 是<ruby>**完美安全**<rp>(</rp><rt>perfectly secure</rt><rp>)</rp></ruby>的.

**定理.** 若 \\( (\mathcal{K},\mathcal{M},\mathcal{C}) \\) 上的密码 \\( (E,D) \\) 是完美安全的, 则 \\( |\mathcal{K}|\ge|\mathcal{M}|\\).

> 怎么回事呢?