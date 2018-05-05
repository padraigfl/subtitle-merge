The goals of this project are to take in two arrays of subtitle objects and pair any which match times within a given range.

This module will depend on another library and external processes to parse the subtitles, so it should be format agnostic provided you can find a means to parse the subtitles into the required format. I may include snippets in here of ways to do that from other modules at a later date.

# Input Format

The structure of subtitle objects attempts to follow the same format as the best subtitles parsing module I could find on npm, subtitles.js, which is as follows

```
{
    start: 123, // time in milleseconds
    end: 456, // same
    text: 'a string', // the displayed subtitles
}
```

# Output Format

Output matches the input but with an added `secondaryText` attribute for paired subtitles, this may be changed at a later date.

# The Matching Algorithm

At the moment it's very primitive and mostly done in a "lets get something the works" mindset with the first set of subtitles being the primary set which the other needs to match with. There is a custom config objected included in the source code which will be expanded up to be the default arguments for selecting which kind of matches can be accepted

# Legacy Stuff

As this is branched off from a previous project that was very SSA focused, there may be some leftover things that look weird. Let me know and I'll resolve them.

# Future plans

- [ ] Implement custom matching arguments
- [ ] Handle overlapping subtitles (e.g. the secondary subtitles have an entry which contains text for the equivalent of several primary subtitles)
- [ ] Filter short subtitles, ones within parentheses, all caps, etc.

# Testing

As written tests for this are rather limited and self-fulfilling in some ways, I've tested these routinely with randomly selected matching pairs of subtitles to ensure major issues are caught