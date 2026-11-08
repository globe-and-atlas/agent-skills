# Case notes

Calibration from the first three reviews (November 2026). Add a dated entry after each new review.

## A pixel-art shop game (goal: craft)
- Recent session logs kept ending "unjudged by a human in motion"; two recorded failures were "tests passed, felt bad".
- The project's written purpose was still the unfilled template.
- Advice: write an experience brief, make the player's own play notes the spec, allow one unjudged change at a time, and build variants behind a toggle instead of one big pass.

## Thumbwords, a paid iOS word-puzzle bundle (goal: money)
- The written purpose still described an early desktop web experiment.
- Counting from code showed the paid value sat in two games with over 200 puzzles each, while the free tier was upside down: three games entirely free, the two deep games almost entirely locked.
- Finite content ruled out a subscription; the review supported a one-time unlock at a higher price.
- QC found the uploaded build differed from the source on disk (changes made minutes after the archive), a layout checker that missed the newest game, and a store listing that under-counted the app's own content.
- Fix loop: commit and tag before archiving, bump the build number, archive from the tag.

## Globe & Atlas: Orbits, an iPhone and Apple Watch GNSS app (goal: showcase)
- The written purpose said watch-only with no monetization; neither was still true.
- Trust passed: DOP, coverage angle, meters per degree and RFC 7946 GeoJSON were all correct.
- Sharing failed: the exports a GIS professional would use were behind a paywall, and about 4 in 10 visible sentences were negations ("not a forecast", "not receiver tracking").
- Fixes: free GPX/GeoJSON exports; three source badges (LIVE, PREDICTED, EXAMPLE) so each sentence can say what a view shows; one sources page; caveats that teach kept on screen.
- A satellite-catalog fact-check found no factual errors but found presentation problems: title-cased acronyms, deliberately released objects filed as fragments, and boilerplate stories for famous spacecraft.
- One "done" report from an agent had no commit behind it; check for the commit first.
