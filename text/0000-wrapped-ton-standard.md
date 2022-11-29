- **TEP**: [0](https://github.com/ton-blockchain/TEPs/pull/0) _(don't change)_
- **title**: Wrapped TON standard
- **status**: Draft
- **type**: Contract Interface
- **authors**: [Mark Okhman](https://github.com/markokhman), [Dan Volkov](https://github.com/dvlkv)
- **created**: 29.11.2022
- **replaces**: -
- **replaced by**: -

# Summary

A standard implementation of wrapped TON (further - wTON) that provides DEXs and other interested third parties with unified set of features and security guarantee.

# Motivation

Implementation of a wrapped TON contract doesnt require a lot of effort. As a matter of fact, several implementations already exist. The problem is that numerous different wrapped TONs (wTON, jTON etc) created by different developers bare lots of risks:

**Financial risks: ** there is no guarantee that a particular wTON doesn't hold security vulnerabilities left deliberately or by mistake. Getting security audits and certifications of the same quality for all the many wTONs is unrealistic.
**Ecosystem fragmentation and no single API: **this is a real problem for developers who are building products that will have to use a variety of wTONs. Imagine a wallet developer who wants to correctly display the total amount of wTON, including regular and all kinds of wrapped ones.
**No parity of features: **each wTON will have its own unique set of features, which will lead to additional issues with support.

# Guide

The suggested solution is an implementation of wTON minter along with a standard description that enables developers to use wTON in the most effecient way while building their products.

The public wTON implementation will have no owner and it's address will be trusted and well know source of wTONs.

Because this wTON implementation will be used by all parties, it has to also correspond to usability requirements:

- the default usage scenario performs wTON usage implicitly via DEX's wTON wallets, not involving the end user's wTON wallet. However wTONs can be minted on any address if needed.
- gas price efficient (TODO: elaborate)
- will correspond to TEP-89 standard (disoverable jetton wallets)

Here is a visual preview of the standard usecase when an end user of DEX is purchasing a jetton paying with TONs:

[![](./assets/0000-wrapped-ton-standard/TONtoJetton.png)](https://miro.com/app/board/uXjVP_afLho=/?share_link_id=338884326964)

P.S. DeDust has the closes flow to suggested one (https://dedust.io/)

# Specification

### wTON minter

by DeDust, to be extended

    wrap query_id:uint64 amount:Coins destination:MsgAddress return_gas_to:MsgAddress
                  notify_gas_amount:Coins notify_payload:(Maybe ^Cell) = MsgInBody;

    unwrap query_id:uint64 destination:MsgAddress  = ForwardPayload;

    unwrapped query_id:uint64 = MsgInBody;

### wTON wallet

This section describes your feature formally. It contains requirements, which must be followed in order to implement your TEP. To keep things formal, it is convenient to follow [RFC 2119](https://www.ietf.org/rfc/rfc2119.txt). You should include following text at the beginning of this section:

> The key words “MUST”, “MUST NOT”, “REQUIRED”, “SHALL”, “SHALL NOT”, “SHOULD”, “SHOULD NOT”, “RECOMMENDED”, “MAY”, and “OPTIONAL” in this document are to be interpreted as described in RFC 2119.

# Drawbacks

Why should we _not_ do this?

# Rationale and alternatives

Here we describe the ozys, stonfi (others?)

# Prior art

TODO: Fill in

# Unresolved questions

If there are some questions that have to be discussed during review process or to be solved during implementation of this TEP, write it here.

# Future possibilities

Do you have ideas, which things can be implemented on top of this TEP later? Write possible ideas of new TEPs, which are related to this TEP.
