# ToR vs Mass surveillance
- First thing to do is to learn how to use a Windows machine.

## Trivia
- 12T of bandwidth, 6T utilised.
- Lizard Squad dropped a bunch more ToR relays on GCE(?)

## Safety
- Relay diversity.
- User diversity. e.g. 50k+ users in Iran, most are normal citizens getting to
  Facebook.

## Countermeasures
- Address blocking.
   - Bridge relays.

- DPI.
  - ToR uses the DNSSEC prime for DHE.
  - Iran used that as a fingerprint.
  - Connecting to public ToR relays directly in Iran is saddening.

- Syria blocked all SSL.
  - Pluggable transports.
  - Skype 0-day; can we turn every Skype user into a ToR bridge?
  - Obfsproxy.
    - Look like nothing.
  - Look like something expected.

- China
  - Active probing.
  - If you talk ToR, then block you.

- Pluggable transports
  - Flashproxy
  - Fteproxy (http ish output)
  - Stegotorus
  - Skypemorph
  - uProxy
  - Lantern
  - Scramblesuit
  - Telex

- Fronting
  - Meek.
  - Hit GFE, send appengine host header, talk to appengine ToR relay.
    meek-refect.appspot.com

## Pervasive surveillance
- Design changes to improve robustness.
- Internet too centralised.
- End-to-end correlation attacks.
  - Need padding and synchronisation.
- Surveillance and censorship are more related than originally thought.

# SecureDrop
- How does a whistleblower send stuff securely?
- https://freedom.press/securedrop/directory
- Every organisation running securedrop runs their own instance with their own
  hidden service.
- 3rd party principle
- FBI uses Javascript to deanonymise sources.
- Diceware passphrase
- Journalist keep GPG keys on airgapped machines.
- Journalist receives messages from sources encrypted with their public key.

## Future work
- E2E encryption in SD.
  - Simplifies server implementation.
  - Reduce harm of server compromise.
  - Defense in depth.
  - Inherently in conflict with forensic deniability.
  - Where do we store the key?
  - What's Minilock?

## Secure code delivery

# Lightning Talks

# Error prone cryptographic designs - DJB
- Blame standards, not implementers. If the standard leaves room to break
  things, it's a bad standard.
  - Irazoqui-Inci-Eisenbarth-Sunar
- Designs need to lend themselves to simple, fast, verifiable implementations
  which are not vulnerable to timing attacks.
  - Meyer-Somorovsky-Weiss-Schwenk-Schinzel-Tews
  - Bleichenbacher
- OPTLS


# NIST overview
- Hiring more cryptographers.
- [VCAT](http://www.nist.gov/public_affairs/releases/upload/VCAT-Report-on-NIST-Cryptographic-Standards-and-Guidelines-Process.pdf)


# Facebook passwords
- Crypto as a service.
- HMAC via a crypto service for password storage.
- KDC grade bastion hosts. What does that mean?
- Testing pastebin dumps.
  - Tell user to change password on next login.
  - Use other signals (location, datr cookie, etc) to let account continue to
    be enabled.

# Life of a Password - Arvind Mani, LinkedIn.
- Ongoing key rotation of application key fingerprints your database. Lets you
  pinpoint when your database was stolen.
- Password history table (to prevent reuse through invalidation). Make sure you
  use a different application secret.

# In Privacy Enhancing Technologies We Trust
- EHCR art 8, 4th Amendment, applicable only to public authorities, not in
  scope for private entities.
- Problem now is private sector is able to surveill without massive human
  resource cost. (East Germany, Stasi employed 2.5% of the population.)

##  Informational privacy
- Tech oriented. EU: Data Protection Regulation
- Not just privarcy, but minimum standards to enable data economy.
- ToR, Mixmaster, I2P.

# PLAID is not a world class authentication protocol
- PLAID starts in Australian DHS.
- SSR conference
- ISO standard snuck in to the SC17 vs SC27 commitee

# Crypto is for everyone (W3C)
