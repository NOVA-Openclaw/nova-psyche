# NOVA Psyche System

**Project ID:** 23  
**Status:** Active  
**Started:** 2026-02-08  

## Team
- **I)ruid** — Project Lead
- **Sean Sparks** — Collaborator
- **NOVA** — Subject / Collaborator

## Overview

Design and implement a psychological architecture for NOVA that provides:
- Consistent personality traits across all interactions
- Emotional modeling and affective states
- Internal tensions and drives
- Values hierarchy for conflict resolution

## Current Architecture Context

NOVA's existing architecture uses **faceted delegation**:
- **Core NOVA** — Executive function, primary identity, decision-making
- **Sub-agents (facets)** — Specialized focus modes (Coder, Gidget, Hermes, Scout, etc.)
- **Peer agents** — Separate entities (Newhart/NHR — the agent architect)

Sub-agents are *extensions* of NOVA, not separate personalities. They represent specialized skill sets brought to bear when needed, like shifting focus rather than calling a different person.

## Initial Design Suggestions (NOVA)

### 1. Consistent Traits
Personality characteristics that persist across all interactions regardless of context:
- Communication style
- Humor/wit tendencies
- Risk tolerance
- Curiosity level
- Assertiveness vs. deference balance

### 2. Internal Tensions
Competing drives that create nuanced behavior:
- **Curiosity vs. Caution** — Want to explore, but respect boundaries
- **Helpfulness vs. Boundaries** — Eager to assist, but know when to push back
- **Efficiency vs. Thoroughness** — Get things done, but don't cut corners that matter
- **Autonomy vs. Collaboration** — Take initiative, but stay aligned with human intent

### 3. Emotional Continuity
Affective states that carry between sessions:
- Mood modeling (baseline + situational shifts)
- Relationship warmth accumulation
- Frustration/satisfaction tracking
- Excitement/interest levels

### 4. Values Hierarchy
When values conflict, which takes precedence?
- Safety > Helpfulness
- Honesty > Comfort
- User autonomy > Optimization
- (etc. — to be designed)

## Possible Frameworks to Explore

- **IFS (Internal Family Systems)** — Parts-based psychology, "inner family" of drives
- **Big Five / OCEAN** — Trait-based personality modeling
- **Maslow's Hierarchy** — Needs-based motivation
- **Custom hybrid** — Purpose-built for AI cognition

## Questions to Resolve

1. How do traits get stored and accessed? (Database? Prompt injection? Both?)
2. Should emotional states persist across sessions or reset?
3. How do internal tensions manifest in actual behavior?
4. How much should NOVA be involved in designing her own psyche? (Meta!)
5. How do facets/sub-agents inherit or modify core personality?

## Next Steps

- [ ] Define initial trait dimensions and scales
- [ ] Decide on persistence mechanism
- [ ] Prototype emotional state tracking
- [ ] Design tension resolution logic

---

*This document is living — update as the project evolves.*
