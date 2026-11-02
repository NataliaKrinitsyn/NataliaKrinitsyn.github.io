---
layout: default
title: "Back to Bare Metal Without Giving Up Uptime: How We Built Postgres for Full Independence"
---

# Back to Bare Metal Without Giving Up Uptime: How We Built Postgres for Full Independence

*Nataly Krinitsyn, PhD, CEO of DBInvent · November 2, 2026*

More teams are taking a hard look at their cloud bill and asking a simple question: what are we actually paying for? Some are moving workloads back on-prem. Others are renting bare metal from their cloud provider and running the stack themselves. Either way, the goal is the same: full independence over their own infrastructure, costs and data.

## The numbers behind the move

This isn't just a feeling. Companies that ran the math have published it:

- Ahrefs estimated it saved about $400M over 2.5 years by running 850 servers in its own colocation data center instead of AWS. By its math, the AWS bill would have been larger than the company's revenue for the same period. Source: [How Ahrefs Saved US$400M by NOT Going to the Cloud](https://tech.ahrefs.com/how-ahrefs-saved-us-400m-in-3-years-by-not-going-to-the-cloud-8939dd930af8).
- 37signals (Basecamp, HEY) moved its apps off AWS onto its own Dell servers without growing its ops team. It now projects more than $10M in savings over five years. Sources: [DHH's cloud-exit math](https://world.hey.com/dhh/we-stand-to-save-7m-over-five-years-from-our-cloud-exit-53996caa) and [Ars Technica's update](https://arstechnica.com/information-technology/2024/10/basecamp-maker-37signals-says-its-cloud-exit-will-save-it-10m-over-5-years/).
- a16z found that cloud spend averaged about half the cost of revenue for public software companies, and that bringing workloads in-house typically costs one-third to one-half as much. Source: [The Cost of Cloud, a Trillion Dollar Paradox](https://a16z.com/the-cost-of-cloud-a-trillion-dollar-paradox/).

## "But the comparison isn't fair," say the critics

Critics have pushed back on these numbers. The Register noted that the Ahrefs comparison wasn't apples to apples, and others argue that the cloud's real value is elasticity, managed operations and resilience, not raw server price.

That's a fair point, and it's exactly the gap YT Cluster fills. YT Cluster is the piece that makes the move smart. The resilience and hands-off maintenance people pay the cloud for come built into your own Postgres. Every node is writable, so a node can go down for patching or a major upgrade while the rest keep serving traffic. Capacity grows by adding nodes, not by renting bigger instances.

And it goes further: you can't get this from cloud services. Managed Postgres still makes you plan cutovers and maintenance windows for major upgrades. With YT Cluster, maintenance and major upgrades with no downtime are a core feature, on your own hardware or on cloud bare metal.

So the choice isn't cheap but fragile on-prem versus expensive but safe cloud. With YT Cluster, you get the savings and the uptime.

## The hidden price of "managed" Postgres

Managed cloud Postgres makes it easy to get started. It doesn't make maintenance disappear, though. Major version upgrades still mean planning, testing, cutover windows and some amount of downtime. Cloud providers offer ways around this, like blue/green deployments and replica promotion, but those add extra effort, extra infrastructure and extra risk on every upgrade.

## What changes with YT Cluster

YT Cluster is a multi-master Postgres cluster where every node is writable. That one design choice changes how maintenance works:

- **Maintenance with no downtime.** You take a node out, patch it, bring it back, and the rest of the cluster keeps serving reads and writes.
- **Postgres major upgrades with no downtime.** You upgrade node by node while the application keeps running. You don't need a cutover weekend or a blue/green rebuild.
- **No data migration.** YT Cluster runs on your existing Postgres, so you don't need a new database engine or a rewrite.
- **Consistency you can verify.** YT Cluster is Jepsen-tested for data consistency and ACID, and read-after-write is never stale.

What public cloud offers as an add-on that takes extra effort is a basic core feature for us.

## Why this matters for the move back on-prem

Leaving the cloud shouldn't mean going back to 2 AM maintenance windows. With YT Cluster, on-prem or bare-metal Postgres can be more available than the managed service you left:

- You run it on your hardware, in your data center or on cloud bare metal.
- You control costs, because capacity grows by adding nodes rather than buying ever-larger instances.
- You can maintain and upgrade during business hours, because users don't notice.

That's what full independence should mean: you own the infrastructure, and you don't have to accept downtime as the price of owning it.

## The bottom line

Moving back to on-prem or bare metal is a business decision, and the savings above show why so many teams are making it. Zero-downtime maintenance shouldn't be the reason you hesitate. If your team is weighing that move, or is tired of planning Postgres upgrades around maintenance windows, I'd be happy to compare notes.

Learn more about YT Cluster: [dbinvent.github.io](https://dbinvent.github.io/)

#PostgreSQL #Postgres #CloudRepatriation #CloudExit #OnPrem #BareMetal #CloudCosts #FinOps #HighAvailability #ZeroDowntime #DatabaseEngineering #DevOps #SRE #DBInvent #YTCluster
