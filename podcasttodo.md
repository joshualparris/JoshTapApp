# Podcast Integration TODO

**Decision:** Add as the native Android extension of the shared audio/podcast system.
**Topic bank:** configurable; reuse JoshHub/JoshNFCAudio topic catalogues.

## TODO
- [ ] Add podcast/topic items as a supported library/card type once Media3/NFC playback foundations are complete.
- [ ] Allow NFC tags/cards to open a specific Spotify episode or a curated topic-bank chooser.
- [ ] Add one-tap **different podcast** selection with recent-history persistence and repeat avoidance.
- [ ] Use Spotify app/web deep links; do not assume background/autoplay permissions.
- [ ] Ensure local Media3 playback and Spotify handoff never create competing audio.
- [ ] Keep child-facing card banks parent-curated only.
- [ ] Align topic/episode data with JoshHub/JoshNFCAudio.
- [ ] Add deep-link, NFC, persistence and audio-state tests.

## Shared direction
Treat this as the native Android companion to the **Josh Podcast Dock** ecosystem rather than inventing a separate podcast model.
