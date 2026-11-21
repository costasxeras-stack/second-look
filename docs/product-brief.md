# Product brief: Second Look

## Problem

Car parts are one of the hardest search problems in e-commerce: a part is only relevant if it fits the shopper's car. Drivers usually put the car in the query, for example "klocki hamulcowe golf 7" (brake pads for a VW Golf Mk7). I wanted to see how Allegro, the large Polish marketplace, handles that query, measure it rather than describe it, and propose a fix. I work on search for an automotive parts catalogue, so this is close to my day job.

## Users

- Product managers and search teams in marketplaces with fitment-dependent products
- Hiring managers who want to see how I run a teardown: evidence first, then design

## Goals for 0.1.0

- A teardown where every finding traces to logged evidence
- A concrete redesign tied to the biggest gap

## Non-goals for 0.1.0

- Judging Allegro overall
- Estimating Allegro's business metrics

## Success measures

| Measure | Definition | Target |
|---|---|---|
| Vehicle set rate | Share of car parts searches that end with a vehicle selected | [baseline] to [target] |
| Wrong-fit returns | Returns with reason "does not fit" per 1,000 car parts orders | [baseline] down [x]% |
| Search to purchase | Conversion of car parts searches with a vehicle in the query | [target] |
