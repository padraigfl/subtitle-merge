# Subtitles Merge

[![Coverage Status](https://coveralls.io/repos/github/padraigfl/subtitle-merge/badge.svg?branch=master)](https://coveralls.io/github/padraigfl/subtitle-merge?branch=master) [![Build Status](https://travis-ci.org/padraigfl/subtitle-merge.svg?branch=master)](https://travis-ci.org/padraigfl/subtitle-merge) [![Maintainability](https://api.codeclimate.com/v1/badges/d30d1df26be3154dff5b/maintainability)](https://codeclimate.com/github/padraigfl/subtitle-ssa/maintainability)

The goals of this project are to take in two arrays of subtitle objects and pair any which match times within a given range.

This module will depend on another library and external processes to parse the subtitles, so it should be format agnostic provided you can find a means to parse the subtitles into the required format. I may include snippets in here of ways to do that from other modules at a later date.

## Usage

## Functions

### `merge(s1, s2, offset) -> Array`

The default export function, this takes in two arrays of subtitle objects (`s1` and `s2`) to pair. `offset` specificies the leniency (in millseconds) for determining matches.

### `default.isInRange(time1, time2, variance) -> Boolean`

Simple comparison function.

### `default.isValidPair(s1, s2, offset) -> String|Boolean`

Takes in two subtitle objects and checks what kind of match (if any, it is). The current range of responses are

```js
  'FULL_MATCH',
  'START_MATCH',
  'END_MATCH',

  'START_LATE_END_EARLY',
  'START_EARLY_END_LATE',

  'START_MATCH_END_EARLY',
  'START_MATCH_END_LATE',

  'START_EARLY_END_MATCH',
  'START_LATE_END_MATCH',
  'START_AFTER_END',
  'END_BEFORE_START',
```

## Testing

- `npm run test`
- `npm run lint`
- `npm run coverage` (runs tests with NYC coverage checks)

## Object structures

### Input Format

The structure of subtitle objects attempts to follow the same format as the best subtitles parsing module I could find on npm, subtitles.js, which is as follows

```js
{
    start: 123, // time in milleseconds
    end: 456, // same
    text: 'a string', // the displayed subtitles
}
```

### Output Format

Output matches the input but with an added `secondaryText` attribute for paired subtitles, this may be changed at a later date.

```js
{
    start: 123, // time in milleseconds
    end: 456, // same
    text: 'a string', // the displayed subtitles
    secondaryText: 'una cuerda(???)',
}
```

## The Matching Algorithm

At the moment it's very primitive and mostly done in a "lets get something the works" mindset with the first set of subtitles being the primary set which the other needs to match with. There is a custom config objected included in the source code which will be expanded up to be the default arguments for selecting which kind of matches can be accepted

## Legacy Stuff

As this is branched off from a previous project that was very SSA focused, there may be some leftover things that look weird. Let me know and I'll resolve them.

## Future plans

- [ ] Implement custom matching arguments
- [ ] Handle overlapping subtitles (e.g. the secondary subtitles have an entry which contains text for the equivalent of several primary subtitles)

As written tests for this are rather limited and self-fulfilling in some ways, I've tested these routinely with randomly selected matching pairs of subtitles to ensure major issues are caught