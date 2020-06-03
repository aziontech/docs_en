# Digital **Certificates**

[Edit on GitHub <svg width="14" height="14" xmlns="http://www.w3.org/2000/svg"><g fill="none" stroke="#F3652B"><path d="M4.81.71H.672v11.43H12.1V8.001" stroke-width=".8"/><path d="M6.87.786h5.155V5.94M6.31 6.5L12.026.786"/></g></svg>](https://github.com/aziontech/docs_en/edit/master/edge-application/digital-certificates/index.md)

You will need a SSL Certificate to traffic data over HTTPS. The use of HTTPS guarantees you security in the transmission of your customers' data over the internet, demonstrates the reliability of your website and the authenticity of your domain, in addition to improving the position of your website in search engines like Google. You will also need HTTPS if you want to use the HTTP/2 protocol, which brings important performance improvements compared to HTTP/1.1.

At Azion, you can count on the following SSL Certificate options for HTTPS traffic:

> 1. _[Shared Domain](#shared-domain)_
> 2. _[Custom Certificate](#custom-certificate)_
> 3. _[RSA](#rsa)_
> 4. _[ECC/ECDSA](#ecc-ecdsa)_
> 5. _[How to use Custom Certificate](#how-to-use-custom-certificate)_

---

## 1. Shared Domain {#shared-domain}

When using Azion Edge Application you have our SSL certificate for HTTPS traffic, at no additional cost, just use Azion's shared domain.

When you create an Edge Application set-up at [Real-Time Manager](https://manager.azion.com/) you are attributed automatically as domain at “azioncdn.net”. If you wish, you may use to deliver your static content over HTTPS, avoiding the costs of issuing SSL certificates for approval environments or URLs whose domain can be shared with other Azion customers.

To use Azion's SSL certificate as a Shared Domain:

1.  Access [Real-Time Manager](https://manager.azion.com/) and click the menu **Edge Services** and select **Domains**.
2.  Add or edit your **Domain** settings.
3.  In the field **Digital Certificate**, select **Azion (SAN)**
4.  After you **saved** your settings you will be using the Shared Domain at Azion.

---

## 2. Custom Certificate {#custom-certificate}

To use your domain in HTTPS you will need your own SSL Certificate (X.509). You may, without additional costs, set up your SSL Certificate in the Real-Time Manager. If you do not have one, Azion will be able to mediate the process of issuing and maintaining your SSL Certificate with a Certification Authority (CA) of your choice. To do this, you will need to prove that the domain is really yours. There are three types of validations that you can choose:

- DV (Domain Validation) is the validation on your domain use right, being the simplest of the three options. This is Azion’s recommended option for most companies.
- OV (Organization Validation) is the validation on your domain use right and some other validations on the requesting organization.
- EV (Extended Validation) is an extended validation, which requires additional documentation to prove the physical, legal and operational existence of the requesting organization, being the most complex of the three options.

Azion currently works with two types of certificates, which are: “RSA” and “ECC/ECDSA”. Each certificate has its characteristics and its security level, and Azion allows you to choose the option that best fits your scenario.

## 3. RSA {#rsa}

It is one of the first public key cryptography systems and is widely used for the secure transmission of data. In this encryption system, the encryption key is public and is different from the decryption key that is secret (private). Any message encrypted using a public key can only be decrypted using the respective private key.  

RSA is a relatively slow algorithm and is therefore less used to directly encrypt user data. Most often, RSA passes shared encrypted keys to symmetric key encryption, which in turn can perform mass encryption-decryption operations at a much greater speed.

## 4. ECC/ECDSA {#ecc-ecdsa}

Elliptical Curve Cryptography is an approach to public key cryptography based on the algebraic structure of elliptical curves. Public key cryptography is based on the creation of mathematical puzzles that are difficult to solve, therefore it becomes much more secure than other types of certificates such as RSA.

Smaller keys are less computationally intensive to generate signatures because they involve smaller mathematical numbers. ECC is faster in generating signatures and has better performance than RSA.

## 5. How to use Custom Certificate {#how-to-use-custom-certificate}

To add your Custom Certificate, you will need the Certificate pair (X.509) in [ASCII PEM](https://www.google.com.br/search?q=Como+converter+um+certificado+PFX+para+PEM&cad=h) format and the respective private key, which cannot be protected by *passphrase*.

The certificate is the file you receive from your CA. It starts with:

~~~
-----BEGIN CERTIFICATE-----
~~~

You must copy all the content including the start marker and also the end marker:

~~~
-----END CERTIFICATE-----
~~~

The private key is the file that you used to generate the CSR request which was sent to your CA. The content starts with:

~~~
-----BEGIN RSA PRIVATE KEY-----
~~~

You must copy all the content including the start marker and also the end marker:

~~~
-----END RSA PRIVATE KEY-----
~~~

To use your Custom Certificate with Azion, we use the SNI (Server Name Indication) extension of the TLS protocol. Check the [browser list with SNI support](https://caniuse.com/#feat=sni).

To use your own certificate:

1.  Access [Real-Time Manager](https://manager.azion.com/)  and click the menu **Edge Services** and select **Digital Certificates**.
2.  Add a **Digital Certificate** including the information of your Certificate.
3.  Access the menu **Edge Services** and select **Domains**.
4.  In the field **Digital Certificate**, select **Digital Certificate** created in **step 2**
5.  After you saved your settings you will be using your own Certificate.

---

Didn't find what you were looking for? [Open a support ticket.](https://tickets.azion.com/)
