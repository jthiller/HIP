# Hotspot Onboarding Credit

- Author(s): [@jmarcelino](https://github.com/jmarcelino), Members of the IoT Working Group
- Start Date: <!-- fill me in with today's date, YYYY-MM-DD -->
- Category: Economic, Technical
- Original HIP PR: <!-- leave this empty; maintainer will fill in ID of this pull request -->
- Tracking Issue: <!-- leave this empty; maintainer will create a discussion issue -->
- Vote Requirements: veIOT Holders

## Summary

This HIP introduces a Hotspot credit system that allows owners to either reuse the onboard of their existing Hotspots or transfer it to a new deployment, all while maintaining network security. The Hotspot onboarding and assertion fees are primarily designed to prevent false-hardware attacks on the network. However, the financial burden to restore deployments when Hotspots are damaged, lost, or become nonfunctional can be prohibitive.

## Motivation

While the manufacturing cost of Hotspots has decreased since the genesis of the Helium Network, the onboarding fee remains a significant expense and a barrier for new Hotspot owners. Manufacturers often offer two versions of their LoRaWAN gateways: one with Helium capability and one without. For example, Seeed Studio sells a Helium-enabled Hotspot for $148.99, while a similar non-Helium gateway costs $99. Similarly, RAKwireless prices their Helium-enabled Hotspot at $179, compared to $139 for their non-Helium entry-level gateway.

By allowing Hotspot owners to 'burn' their inactive Hotspot onboard and receive a credit to be applied on a new Hotspot, we can reduce the cost of replacing a Hotspot, thus increasing the number of active Hotspots on the network.

## Stakeholders

This proposal primarily affects Hotspot operators and Hotspot manufacturers.
IOT token holders are affected as the subnetwork emissions are likely to be affected due to changes in allocation via the `a` score of the subnetwork emissions.

## Detailed Explanation
Currently, Hotspot onboarding fees are paid directly using Data Credits. This HIP proposes a new mechanism for managing Hotspot onboardings through the introduction of individual credits, which are backed by Data Credits and specifically designated for onboarding purposes. These onboarding credits will be transferable but restricted solely for use in onboarding a Hotspot.

These onboarding credits can be created in two ways, through the use of tokens, in amounts defined by the IOT Network protocol, or through the 'burning' of an inactive Hotspot. The 'burning' of a Hotspot will be defined as a Hotspot that has not received rewards for 30 days. This will ensure that Hotspots that are active on the network are not 'burned' and that Hotspots blocked from earning due to gaming are not able to rapidly recycle their onboard.

This HIP seeks to ammend HIP19, which mandates that Hotspots sold are done so with an associated onboard. This HIP would change this mandate to allow Hotspot manufacturers to sell Helium-enabled Hotspots with or without an onboard. The hardware key of the Hotspot must be registered with the onboarding server and appropriately flagged as having an onboard or not.

When onboarding a new Hotspot,

Data-only Hotspots may not be onboarded using onboard credits. Their onboards must be paid for using Data Credits.

Furthermore, this credit mechanism can be extended to manufacturers to ensure that Hotspots sold with an included onboard are never left behind when a manufacturer's DC balance is depleted. The onboard credit can be bound to a particular onboarding key at the time of manufacturing, ensuring each Hotspot sold is able to be onboarded to the network. While this mechanism becomes possible via onboarding credits, this HIP does not mandate this behavior.

- for a manufacturer out of DC for onboarding, this credit can be used.
- for manufacturer with DC for onboarding, the maker dc is used. (by detecting the Hotspot in the onboarding server)
- hip 19 amendment to allow manufacturers to sell a helium-enabled Hotspot with no associated onboard.
- 'burn' for credit mechanism only available to hotspots that are inactive on the network – following the same definition as the network, this is 30d of no rewardable activity. Ensure sufficient time to prevent key churn.
- helium wallet would be updated to handle these two paths for hotspot onboard

## Drawbacks

Decreased revenue from onboarding fees.

## Rationale and Alternatives

This is your chance to discuss your proposal in the context of the whole design space. This is
probably the most important section!

- Why is this design the best in the space of possible designs?
- What other designs have been considered and what is the rationale for not choosing them?
- What is the impact of not doing this?

## Unresolved Questions

- What parts of the design do you expect to resolve through the HIP process before this gets merged?
- What parts of the design do you expect to resolve through the implementation of this feature?
- What related issues do you consider out of scope for this HIP that could be addressed in the
  future independently of the solution that comes out of this HIP?
- Are there dependencies, milestones, or dates that need to be met for this HIP to succeed?

## Deployment Impact

Describe how this design will be deployed and any potential impact it may have on current users of
this project.

- How will current users be impacted?
- How will existing documentation/knowledge base need to be supported? Any content to change at
  <http://docs.helium.com>?
- Is this backwards compatible? Can this HIP be undone?
  - If not, what is the procedure to migrate?

## Success Metrics

What metrics can be used to measure the success of this design? Are any new ETL reports needed to
measure the success?

- What should we measure to prove a performance increase?
- What should we measure to prove an improvement in stability?
- What should we measure to prove a reduction in complexity?
- What should we measure to prove an acceptance of this by its users?
```
