# OAuth 2.0 Proof of Possession Implementation

This code implements a simple version of the OAuth 2.0 Proof of Posession protocol in Node.js. 

`authorizationServer.js` contains the authorization server. It generates random-string access tokens alongside RSA 2048-bit keypairs. The server stores the tokens and public keys in a local NoSQL database. It also provides token introspection to the protected resource for token and key lookup.

`client.js` contains the client. It requests tokens from the authorization server and stores the associated access token and keypair in a local variable. It can create a signed PoP object using JWS that includes the access token as a member and sends this to the protected resource as a header.

`protectedResource.js` contains the protected resource. It parses the signed PoP object out of the header and sends the access token portion to the authorization server for introspection. It then validates the signature using the returned key.

