# Ethereum For Dummies by Gavin Wood

[Video: DEVCON1: Ethereum for Dummies - Dr. Gavin Wood](https://www.youtube.com/watch?v=U_LK0t_qaPo)

Transcript for the AI

Actually, *Ethereum for Dummies* wasn’t my original title. The original title was different, but as I worked on the project, my appreciation for exactly what Ethereum is evolved over time. Initially, Ethereum was often described as “Bitcoin with a virtual machine” or “Bitcoin with an extended scripting language.” While that was a cool idea, it didn’t quite capture the full essence of what we were building. At first, the scope of Ethereum’s purpose seemed quite limited — it was basically conceived as an abstraction platform for financial contracts similar to those in the “mass of the coin” style on a blockchain.

As time went on, especially around January 2014 when we all gathered in Miami, I started thinking more deeply. I had little sleep that week but began to wonder if there was a better way to understand Ethereum beyond just Bitcoin with a richer scripting language. My thoughts drifted to crypto finance, and I realized if Bitcoin scripted finance, then Ethereum could be thought of as “crypto law.” In fact, finance is a subset of law in some ways, so Ethereum could be understood as a cryptographic version of law itself. This idea evolved further, and this talk is about a later realization of what Ethereum truly is.

We first answered the “how” — that was reasonably well explained in the original white paper back in November 2013, stemming from the Bitcoin space and decentralization principles. But the “what” — what is Ethereum, really? — has been a harder question. People want it but often don’t truly understand it. In this talk, I’ll avoid technical jargon that explains how Ethereum works but doesn’t capture what it actually is.

For a long time, we simply didn’t know. This might be lost on most, but Ethereum is a computer — just like this old computer from the 1950s, which was thought to be what a home computer would look like by 2004 and ran Fortran. Ethereum *is* a computer, albeit a slow and very expensive one to run. It has the odd property of sometimes being indecisive about its inputs and outputs, but after a little time it converges on certainty. So, at first glance, it may seem like a step backwards, but Ethereum has some fascinating properties I want to share.

First, Ethereum is a **global singleton** computer — possibly one of the first computers that is fundamentally *not localized*. Unlike physical machines or virtual machines running on physical hardware, the Ethereum computer doesn’t reside in any single place on Earth. Yet, there is only one Ethereum computer globally. It has no reset button, no power switch, and cannot be turned off.

Second, it’s **ubiquitous** — accessible by anyone with an internet connection. It is also **multi-user** by nature, with unlimited user accounts simultaneously logged in. Third, it is **natively object-oriented**. Object orientation — where code and data are encapsulated together — is built directly into the Ethereum computer. Each object is strictly separated from others, yet they all coexist in the same environment.

Fourth, Ethereum is remarkably **accessible**. We can interact with it through simple web primitives like JavaScript. Fifth, it is inherently **auditable and verifiable** — every past action can be replayed to yield the same results, making it trustworthy.

Imagine a world map representing the Ethereum computer. Each box on the map represents an account, or an object, which executes within this global, object-oriented environment. External accounts (users) inject messages into this environment, and cryptographic guarantees ensure security. These properties include:

- **Atomicity:** Transactions either fully succeed or fail without partial execution.
- **Synchronous operation:** Objects operate without interfering with each other, eliminating complex issues like threading or shared memory.
- **Provenance:** Every message’s origin can be verified, an unusual feature in object-oriented environments that enhances security.
- **Permanence:** Data and objects persist forever unless explicitly deleted by their own code; no external authority can remove or alter them.
- **Immutability:** The code executed by these objects cannot be changed after deployment.

What do these unique attributes enable? Ethereum is a **commons for innovation** — a shared space where developers can upload code and ideas that seamlessly interoperate without needing permission or complicated contracts between businesses. Unlike traditional servers, which can be barriers to interoperability and foster monopolies, Ethereum encourages openness and collaboration.

Privacy implications are interesting too. While the blockchain is public, making data completely open, this transparency encourages thoughtful data management rather than false reliance on “secure” third-party servers vulnerable to hacking.

Authentication on Ethereum is also different: rather than trusting a server or third party, users authenticate themselves cryptographically by controlling their private keys.

Ethereum is the world’s first **decentralized computer** — a revolutionary concept with no single point of control or failure.

Historically, innovation follows a pattern: starting dispersed and chaotic, then consolidating into centralized power, and eventually decentralizing again as technology matures. We see this in software development, computing infrastructure, and even governments. Ethereum fits into this trend by commoditizing trust and enabling **zero-trust computing** — a platform where parties who don’t trust each other can still interact securely and transparently. It could even serve as the “court of the internet,” a decentralized legal system that arbitrates disputes online.

Ethereum also supports the vision of a **serverless internet** or “Web 3,” offering decentralized infrastructure for multi-user applications that traditionally relied on centralized authorities.

As we develop tools like Ethereum, the users and the culture around them are just as important as the technology itself. Educating people on how to live and operate within these new decentralized systems is a challenge we will continue to face. The hardest transitions may not be technical but social — convincing established organizations and individuals who benefit from the current centralized system to embrace radical change.

Finally, as private blockchains gain popularity, it is crucial that we keep the technology open and share resources to ensure public blockchains like Ethereum remain robust and thriving. Ideally, we will move toward hybrid models where privacy needs and openness coexist seamlessly within a single ecosystem.

That’s my perspective on what Ethereum really is — much more than just a scriptable blockchain environment. It is a global, decentralized computer shaping the future of trust and interaction online.

## Links

- [DEVCON1: Ethereum for Dummies - Dr. Gavin Wood](https://www.youtube.com/watch?v=U_LK0t_qaPo)
