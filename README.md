# GridPoint

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

GridPoint is a Reston, Virginia clean-technology company, founded in 2003, that builds energy
management and sustainability systems for commercial buildings, enterprises and government
agencies. It pairs its own edge hardware — EC2000 and Edge controllers, submeters, thermostats,
lighting control panels and BACnet/Modbus gateways — with the cloud-based GridPoint Energy Manager
analytics platform, delivering HVAC and lighting automation, equipment-level submetering,
refrigeration monitoring, demand management, grid services and sustainability reporting across
multi-site retail, convenience, restaurant, automotive and public-sector estates.

- https://www.gridpoint.com/

## What this profile found (2026-08-22)

**GridPoint publishes no public API.** There is no developer portal, no API reference, and no
machine-readable contract of any kind — no OpenAPI, AsyncAPI, GraphQL SDL, Protobuf, WSDL, Postman
collection, MCP server or A2A agent card. `developer.gridpoint.com`, `docs.gridpoint.com`,
`api.gridpoint.com` and `apidocs.gridpoint.com` do not resolve in DNS.

An API clearly exists behind the product: the GridPoint Energy Manager application authenticates
against GridPoint's own OAuth 2.0 / OpenID Connect server, which **anonymously advertises the
`client_credentials` grant and partner/system roles** — machine-to-machine integration is a shipped
capability. What is not published is the contract. That makes this a *gated* profile, not an empty
one, and it is the provider's to fix.

What GridPoint does publish, and what is captured here:

| Artifact | What was found |
|---|---|
| `well-known/` | Live OIDC discovery + JWKS on `hydra.`, `identity.` and `ems.gridpoint.com`, saved verbatim. No `security.txt`, `api-catalog` or agent card anywhere. |
| `authentication/` | ORY Hydra authorization server profile read from discovery: four grant types, dynamic client registration, RS256, back/front-channel logout. PKCE is not advertised. |
| `scopes/` | 16 published scopes — coarse `ROLE_*` roles (GridPoint staff / customer / partner / machine), not resource permissions. |
| `lifecycle/` | A real Status.io status page at `status.gridpoint.com`, HTML only — no JSON or RSS feed. No versioning or deprecation policy. |
| `packages/` | Two first-party Elixir libraries on Hex.pm (`plox`, `ostara`). Neither is an API client; **GridPoint ships no SDK**. |
| `conformance/` | OAuth 2.0, OIDC, RFC 7591, HSTS, SPF and DMARC pass. RFC 8414, RFC 9728, PKCE advertisement, DNSSEC and CAA do not. |
| `plans/` | No pricing page — `/pricing/` is a hard 404. Contact-sales only. |
| `rate-limits/` | No documented limits. |

The device layer speaks BACnet and Modbus, but neither is declared in any contract, so no domain
standard is asserted.
