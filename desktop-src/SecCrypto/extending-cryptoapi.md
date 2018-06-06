---
Description: CryptoAPI has been designed to be easily extensible. New types and parameters can be defined by any cryptographic service provider (CSP) author to make CryptoAPI bend to the requirements of a wide variety of situations.
ms.assetid: fe87ccb8-16a3-443d-93df-0df02b8787f6
title: Extending CryptoAPI
ms.technology: desktop
ms.prod: windows
ms.author: windowssdkdev
ms.topic: article
ms.date: 05/31/2018
---

# Extending CryptoAPI

[*CryptoAPI*](security.c_gly#-security-cryptoapi-gly) has been designed to be easily extensible. New types and parameters can be defined by any [*cryptographic service provider*](security.c_gly#-security-cryptographic-service-provider-gly) (CSP) author to make CryptoAPI bend to the requirements of a wide variety of situations.



| Extensible items                                                                                                 | Comment                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Provider types<br/>                                                                                        | A provider type represents a particular family or type of cryptographic services. New provider types can be defined, each serving a particular niche.<br/>                                                                                                                                                                                                                                                                                          |
| Provider parameters<br/>                                                                                   | Provider parameters are sent and received using [**CPSetProvParam**](https://www.bing.com/search?q=**CPSetProvParam**) and [**CPGetProvParam**](https://www.bing.com/search?q=**CPGetProvParam**), respectively. New provider parameters could allow a CSP to be configured in ways not foreseen by the CryptoAPI designers.<br/>                                                                                                                                                                 |
| Algorithm identifiers<br/>                                                                                 | The enumeration facilities of [**CPGetProvParam**](https://www.bing.com/search?q=**CPGetProvParam**) allow applications to list algorithm identifiers dynamically. New [*symmetric*](security.s_gly#-security-symmetric-algorithm-gly), [*public key*](security.p_gly#-security-public-key-gly), and [*hash*](security.h_gly#-security-hash-gly) algorithms can be defined at any time.<br/> |
| Public/[*private key*](security.p_gly#-security-private-key-gly) pair types<br/> | While new key pair types can be defined as needed, currently only signature and key [*exchange key pairs*](security.e_gly#-security-exchange-key-pair-gly) are used.<br/>                                                                                                                                                                                                                                           |
| Key BLOB types<br/>                                                                                        | New key [*BLOB*](security.b_gly#-security-blob-gly) types could permit session keys, public keys, and public/private key pairs to be exchanged in a flexible manner using the [**CPExportKey**](https://www.bing.com/search?q=**CPExportKey**) and [**CPImportKey**](https://www.bing.com/search?q=**CPImportKey**) functions.<br/>                                                                                                                                            |
| Key parameters<br/>                                                                                        | Key parameters are sent and retrieved using [**CPSetKeyParam**](https://www.bing.com/search?q=**CPSetKeyParam**) and [**CPGetKeyParam**](https://www.bing.com/search?q=**CPGetKeyParam**). New key parameters could enable support for many different types of keys.<br/>                                                                                                                                                                                                                         |
| Hash object parameters<br/>                                                                                | Hash object parameters are sent and retrieved using [**CPSetHashParam**](https://www.bing.com/search?q=**CPSetHashParam**) and [**CPGetHashParam**](https://www.bing.com/search?q=**CPGetHashParam**). New hash object parameters could enable support for many different types of [*hashes*](security.h_gly#-security-hash-gly).<br/>                                                                                                                                         |
| Flag values<br/>                                                                                           | Most CryptoAPI/CryptoSPI functions have a *dwFlags* parameter. New *dwFlags* values could modify the behavior of functions as necessary.<br/>                                                                                                                                                                                                                                                                                                       |



 

Extensions to CryptoAPI must be made in a responsible manner. Before defining new parameters and algorithm types, a CSP developer should consult Microsoft Corporation, so that:

-   Common CryptoAPI extensions can be identified and placed into the standard Wincrypt.h file.
-   Namespace collisions can be avoided.
-   It can be determined whether the extension is required, or whether a particular operation can be achieved by using the current API.

> [!Note]  
> For a CSP to be compatible with applications developed for the Microsoft Base Cryptographic Provider, it must support all of the preceding items as described in [Base Cryptography Functions](cryptography-functions.md#base-cryptography-functions) and in [Cryptography Service Provider Functions](cryptography-functions.md#service-provider-functions).

 

 

 



