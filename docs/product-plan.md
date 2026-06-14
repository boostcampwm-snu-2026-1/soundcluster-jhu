# SoundCluster Product Plan

## Purpose

SoundCluster is a music exploration tool that analyzes searched songs as emotion vectors and compares their emotional distance in a 3D space.

## Current Product Scope

- iTunes search by song title or artist.
- Track metadata selection from search results.
- LRCLIB lyrics lookup.
- Gemini-based 5D emotion analysis.
- MongoDB Atlas analysis result caching.
- R3F-based 3D emotion-space rendering.
- Emotion axis on/off projection.
- Selected-track nearest/farthest relation calculation.
- Song metadata and emotion values in hover or selected states.
- `nanoid` share URL creation.
- Cluster restoration through shared URLs.

## User Flow

```text
User
  |
  | search by song title or artist
  v
iTunes results
  |
  | click + on a track
  v
Track is added with default emotion values
  |
  | lyrics lookup + Gemini analysis starts
  v
SSE progress animation
  |
  | final 5D JSON is received
  v
Track emotion vector is updated
  |
  | selected axes are applied
  v
3D cluster rerenders
  |
  | select another track
  v
nearest/farthest relation recalculates
  |
  | share
  v
snapshot is stored and short URL is returned
```

## Emotion Vector

The product uses five fixed emotion dimensions.

```text
energy        # intensity and drive
valence       # positive to melancholic tendency
tempoDensity  # rhythmic density
spaceDepth    # wide/deep to intimate spatial feel
tension       # calm to strained emotional pressure
```

Values are produced by Gemini and validated as numbers from `0.0` to `1.0`.
Users do not edit these values directly.
Users only toggle whether each axis participates in the projection.

## Interaction Rules

- Search text is only an iTunes query.
- The `+` button starts extraction for one selected result.
- The selected track is shown in the bottom HUD.
- The selected track can be removed.
- All tracks can be reset after confirmation.
- Hovered tracks show metadata popups.
- Selected, nearest, and farthest tracks remain visually emphasized.
- Nearest relation uses a solid line.
- Farthest relation uses a dashed line.

## Visual Direction

- Dark space background.
- R3F stars rotate only through OrbitControls interaction.
- No CSS star grid pattern.
- Track nodes are small glowing points, not large planets.
- UI panels use dark glass surfaces.
- The right panel is named `Emotions`.
- The left panel is named `Search Results`.
- The 3D scene shows sparse dotted 3D axis lines without text labels.

## Out of Scope For Current Slice

- Spotify API integration.
- User-editable emotion scores.
- Public account system.
- Playlist import.
- Real-time collaboration.
- Server-side 3D projection persistence.
