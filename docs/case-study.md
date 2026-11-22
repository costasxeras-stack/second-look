# Case study: Second Look

## The question

Car parts are one of the hardest search problems in e-commerce: a part is only relevant if it fits the shopper's car. Drivers usually put the car in the query, for example "klocki hamulcowe golf 7" (brake pads for a VW Golf Mk7). I wanted to see how Allegro, the large Polish marketplace, handles that query, measure it rather than describe it, and propose a fix. I work on search for an automotive parts catalogue, so this is close to my day job.

## Approach

I chose one realistic need, brake pads for a common car, and wrote eight variations of the query: a baseline, the car, a non-existent generation, no space, a typo, a front-axle query with Roman numerals, a part number and English. I ran each once, read the offer count, and extracted the titles and promoted labels of page 1 with a small script in the browser. I then scored the experience on six questions and designed a fix for the biggest gap.

## Findings

### 1. The car in the query barely changes the results (confirmed in the test log)

"golf 9", a generation number not on sale at the time of the test, returned 11,517 offers with no warning, more than "golf 7" (10,098). Only 4 of 60 results on page 1 for "golf 7" name the Golf 7. The vehicle filter stays empty.

### 2. Promoted listings titled for other cars sit near the top (confirmed in the test log)

A promoted pad set titled for Golf 5 and 6 and Passat was at position 4 for "golf 7", and at positions 1 and 2 with a typo or "golf 9".

### 3. Position words work (confirmed in the test log)

Adding "przód" (front) moved page 1 from 28 front and 15 rear titles to 37 front and 1 rear.

### 4. Part number search finds the part, then pads the list (confirmed in the test log)

"0986494660" puts the exact part first, then 42 other part numbers on page 1, with a count of 9,419 offers.

### 5. English queries are much less precise (confirmed in the test log)

"brake pads golf 7" returned 56,862 offers, 5.6 times the Polish query.

### 6. Skipping the vehicle filter likely drives wrong-fit returns (hypothesis)

I cannot see Allegro's return data, so the size is [unknown].

## Decisions

### Log queries and count, instead of describing impressions

Most teardowns are opinions with screenshots. A search teardown can be measured.

**Decision:** Run a fixed set of queries, record offer counts, promoted positions and title counts, and publish the log.

Full record: [decisions/0001-measure-not-describe.md](decisions/0001-measure-not-describe.md)

### Use titles as a proxy for visible fitment

I cannot check true fitment for each part without a catalogue.

**Decision:** Count what the shopper can see on the results page: whether the title names the car, front or rear. Say clearly that a title without the car may still fit.

Full record: [decisions/0002-titles-as-proxy.md](decisions/0002-titles-as-proxy.md)

### Placeholder products in the redesign

Real product names with invented fit labels would be false claims about real parts.

**Decision:** Use "brand A, B, C" in the mockup and label it illustrative.

Full record: [decisions/0003-placeholder-mockup.md](decisions/0003-placeholder-mockup.md)

## What I learned as a PM

- A non-existent model is the fastest test of whether search understands an entity
- Strong tools (vehicle filter, VIN entry) do not help if the query does not trigger them
- Ads need relevance rules too: a promoted result that does not fit costs trust

## Limits

- One session, one account, one day
- Titles are a proxy for fitment
- No access to Allegro data, so impact is stated as hypotheses with placeholders

## What I would do next

1. Repeat the log on mobile and signed out, to see how much the account changes results
2. Add 20 more queries across other car makes and part types
3. Test the redesign as a clickable prototype with [number] drivers

## My role

I framed the problem, made the product calls, checked every number and wrote the conclusions. 
