# Villagers Reborn - Development Roadmap

## Version 1.0: The Actors (Personality & Dialogue System)
**Focus:** Establish villager personality and dialogue foundation
**Effort:** Easiest to implement, content-heavy but low mental load

### Core Implementation
- [ ] Dialogue system code (4-step pipeline)
  - Prefix quirks (20% chance)
  - Core dialogue selection (weighted distribution)
  - Tonal modifications (personality/mood interjections)
  - Suffix quirks (20% chance)
- [ ] Mood system (0-10 scale with three groups)
  - Negative (0-3): unhappy, worried, irritable
  - Neutral (4-6): pensive (wistful tone), content (positive tone), nostalgic (bittersweet tone),  tired(slightly negative tone)
  - Positive (7-10): energetic, prideful, playful, grateful
- [ ] Mood transitions (cross-threshold randomization at 3→4 and 6→7)
- [ ] Main personality groups (6 types)
  - Hermit (rational + introvert)
  - Professional (rational + extrovert)
  - Dreamer (idealistic + introvert)
  - Performer (idealistic + extrovert)
  - Recluse (pessimistic + introvert)
  - Cynic (pessimistic + extrovert)
- [ ] Secondary traits (initially 6, expandable)
  - Friendly, Witty, Greedy, Wise, Romantic, Brave
- [ ] Quirks of speech (prefix/suffix, assigned at villager creation)
- [ ] Memory tracking
  - First trade and frequency
  - First gift (positive/negative)
  - Total interactions
  - Weather at first meeting
  - Global achievements

### Content Population
- [ ] ~10 base lines per mood
- [ ] ~5 lines per mood + job combination
- [ ] ~5 lines per mood + personality combination
- [ ] Tonal markers (speech_quirks/tonalmarks.json)
- [ ] Speech prefix/suffix quirks
- [ ] Main personality dialogue (40% weight)
- [ ] Job-specific dialogue (20% weight)
- [ ] Secondary personality dialogue (10% each, two slots)
- [ ] Event dialogue (10% weight)

### Skins Feature (Trivial, Include in v1)
- [ ] Command to change villager skin via image link
- [ ] Skin validity checking
- [ ] Skin tracking and assignment storage

### Bug Fixes
- [ ] Fix zombie villager spawning/behavior

---

## Version 2.0: The Roles (Job System)
**Focus:** Give villagers profession-based abilities and depth
**Effort:** Second easiest to implement, major gameplay feature (1/3 of mod)
**Prerequisite:** v1 dialogue system (jobs inform dialogue selection)

### Vanilla Job Enhancements
- [ ] Cleric
  - Heal nearby players and tamed creatures passively
  - Healing/humming SFX
  - Marriage/matchmaking capability
- [ ] Blacksmith
  - Outfit guards with tools/armor
  - Repair tools (with cost)
- [ ] Librarian
  - Enchant items with clearer UI than vanilla
  - Option to enchant above vanilla level limits (for cost)
- [ ] Farmer/Chef
  - Create custom food beyond vanilla saturation limits
  - Custom enchant implementation
- [ ] Cartographer
  - Generate maps to other villages, ruins, End fortress

### Combat/Defense
- [ ] Guard job replaces nitwit
  - Fight mobs profession-appropriately
  - Put out fires
  - Attack villager-attackers
  - Defend against fires
  - Give quests as job feature
- [ ] Profession-appropriate defensive abilities (non-job)
  - Each profession fights in its own way if attacked

### Breeding System Overhaul
- [ ] Remove vanilla villager breeding
- [ ] Replace with migration system where NPCs simply spawn in empty houses (beds >> population)
    - Check for jobs not already in town, otherwise become guards
- [ ] Simplify babies to single growth stage
- [ ] Track parentage for special dialogue

### Secret/Mob Villager Jobs
- [ ] Creeper variant
  - Glassworker trade
  - Demolitionist secret job (rectangular prism explosions with markers)
- [ ] Zombie/Skeleton variant
  - Grave keeper job
  - Trade mob drops
  - Revive registered creatures or city villagers
  - Require ghast tears and levels
- [ ] Enderman variant
  - Trade random blocks
  - Fast travel between villages (teleportation)
  - Random daily found items
- [ ] Witch variant
  - Sell potions
  - Spawn rare animals (secret job, with cost)
  - Cure zombified villagers in presence
- [ ] Reformed Illager
  - Sell weapons
  - Tamed mercenary secret job
  - Evoker variant spawns allays (for price)
- [ ] Spawn conditions
  - Big cities or migrations
  - Hidden condition triggers
  - Separate skin folder

### Reformed Boss Mobs (Optional, High Effort)
- [ ] Ender Dragon (female, one per world)
  - POI: Dragon egg
  - Teleport to End cities (bypass stronghold)
- [ ] Wither (either gender, farming wither can allow multiple)
  - Degrade items to components
  - Sell nether materials
- [ ] Elder Guardian (either gender, farming can allow multiple)
  - Grant buff reversing boss fight debuff
  - Water breathing
  - Sell ocean temple materials
- [ ] Warden (either gender, farming can allow multiple)
  - Sell skulk items for experience
  - Wander at night, beat up noise-making mobs
  - Add a drop when killing ordinary warden to make POI
  - Experience used to regenerate health

---

## Version 3.0: The Stage (Settlement Generation)
**Focus:** Create believable village/town/city structures and context
**Effort:** Massive scope, practically a separate mod (1/3 effort but decorative until v2 is solid)
**Prerequisite:** v1 & v2 (dialogue and jobs provide context for settlements)

### Settlement Types & Spawning
- [ ] Three settlement tiers: Village → Town → City
  - Village: Small, no guaranteed landmarks
  - Town: Medium, 1 max landmark
  - City: Large, 2 landmarks guaranteed
- [ ] Settlement spawning
  - Cities naturally spawn 2-3 towns nearby
  - Towns spawn 1-2 villages nearby (adjacent biomes, chunk limit)
  - Player spawn at first city generation (avoid hunting)
- [ ] Spawn rate limiting
  - Small percentage of naturally spawning villages
  - Prevent explosion spam

### Structures & Landmarks
- [ ] Alternative village schematics (custom jigsaw patterns)
- [ ] Landmark system
  - Rarer in smaller settlements (lower % chance)
  - Populated RNG (no two cities identical)
  - Slot-based placement
- [ ] Landmark examples
  - Graveyard → Grave keeper spawns
  - Textile mill → Spider villager (dye seller)
  - Church → Cleric refuge for wounded

### Infrastructure
- [ ] Walls for all settlements (prevent nightly mob obliteration)
- [ ] Town halls (gathering point during raids)
- [ ] Smarter structure placement (separate housing/workshops)
- [ ] Scale-based features
  - Bigger settlements spawn more golems
  - Size affects landmark frequency and variety

### Integration with Jobs/Dialogue
- [ ] Special dialogue for landmarks (environment context)
- [ ] Job availability tied to structure presence (profession-appropriate)
- [ ] Settlement-specific dialogue (location awareness)

---

## Version 4.0: Affinity Events & Relationship Progression
**Focus:** Deepen player-villager relationships through milestone events
**Effort:** Moderate, depends on v1-3 infrastructure
**Prerequisite:** v1 dialogue, v2 jobs, v3 settlements (context for events)

### Affinity System
- [ ] Affinity levels
  - Enemy → Disliked → Neutral → Acquaintance → Good Friend → Lover (6 levels, start neutral)
- [ ] Level-gated dialogue
  - Different dialogue variants per affinity level
  - Subtle dialogue changes vs major gates
- [ ] Affinity events (one acquired per level)
  - Scripted interactions or milestones
  - Ribbon feature (cosmetic, non-critical)

### Personality-Based Interactions
- [ ] Gossip option
  - Learn likes/dislikes of other villagers
  - Learn locations of other villages
  - Personality influences what they discuss
- [ ] Likes and Dislikes
  - 2 favorite + 2 least favorite item categories
  - 2 specific favorite + 2 specific least favorite items (good friend+ only)
  - Dialogue reflects preferences
- [ ] Dynamic personality acquisition
  - Villagers gain quirks at good friend stage
  - Secondary personality semi-randomly changes based on interaction count
  - Change triggers: mood hits 10 (or 0), affinity stage change

### Marriage System (Late, Non-Critical)
- [ ] Establish villager-to-villager marriages
- [ ] Establish villager-to-player marriages
- [ ] Baby generation
  - Inherit one parent's skin
  - Inherit main personality from one parent
  - Inherit immutable secondary personality from other parent
- [ ] Marriage benefits (minimal, formal rather than mechanical, mostly just dialogue, can't subordinate your baby or spouse and make them do chores like in MCA)

### Memory Expansion
- [ ] Likes and dislikes (only after acquaintance, consistent after)
- [ ] Extended tracking
  - Biome with most time (last 60 min)
  - Average depth (last 60 min, tracks sky/underground activity)
  - Most used item (rolling window)
  - Most placed/mined block (rolling window)
  - Most killed mob (rolling window)
  - Most hoarded item in chests (rolling window)

---

## Version 5.0+: The Script (Polish & Culture)
**Focus:** Final polish, AI depth, and emergent villager behavior
**Effort:** Ongoing, quality-of-life improvements
**Prerequisite:** All prior versions

### Villager AI & Independence
- [ ] Autonomous villager behavior (busy work, non-mechanical)
  - Daily routines tied to job
  - Job-specific idle behaviors
- [ ] Player solicitation (low probability at high affinity)
  - Personality-based conversation starters
  - Job-relevant topics
- [ ] Inter-villager interactions
  - Gossip and business transactions
  - Mundane discussion (non-romantic, see implementation below)
  - Reputation spreading
  - Produce relationship graph for village that player has declared residence in through claiming a bed in that area and reaching a certain threshold of influence, begin tracking villager relationships with one another. 
    - Personal interactions: Use a call and response method with the call being of a certain template modified by the personality of the one calling, and response being a template (determined by mood and relationship level) with the exact phrasing of the selected sentiment being personality dependent
    - Professional interactions: a call and response method where the call is targeted at a given profession, for example asking a guard about the patrol, and the response is also generated from the profession list 
  category, only phrased differently by personality
  - Possible emotes like in terraria 
  - Possible in-chat exchanges of 1-2 lines generated based on profession, relationship, personality, gossip, or weather 

### Culture & Community
- [ ] Festivals and games
  - Job-specific celebrations
  - Community gathering events
  - Reputation/relationship impacts
- [ ] Settlement-wide dynamics
  - Birth/death events
  - Village reputation system
  - Economic effects of trades

### Dialogue Refinement (Optional, High Detail)
- [ ] Biome and weather variants
- [ ] Villager death reactions
- [ ] Location/landmark awareness
- [ ] Other villager awareness
- [ ] Personality-tagged dialogue options
  - Expand player choice: go beyond chat/flirt/banter/joke and offer specific lines


### Final Stretch
- [ ] Comprehensive testing across all systems
- [ ] Balance affinity gain/loss rates
- [ ] Optimize memory usage (periodic checks if needed)
- [ ] Performance testing with dense settlements
- [ ] Cross-mod compatibility (MCA comparisons, etc.)

---

## Implementation Notes

### Parallel Work Possible
- v1 Dialogue code can be built while waiting for content population
- v1 Skins can be done independently
- v1 Bug fixes should happen immediately

### Content Scaling
- v1 dialogue content is 80% of v1 effort but can be done incrementally
- v2 job content is moderate (mostly numbers/balancing)
- v3 structures need schematic artists or procedural generation
- v4 is heavily dialogue-driven (reuse existing content)

### Critical Dependencies
- v2 depends on v1 (jobs inform dialogue weighting)
- v3 depends on v1 & v2 (settlements need dialogue and job context)
- v4 depends on v1-3 (affinity events use all systems)
- v5 depends on all prior (polish and refinement)

### Shipping Strategy
- Ship v1 → v2 together as complete experience (release v2 officially)
- v3 is independently shippable (aesthetic enhancement)
- v4 adds depth to existing systems (ship after v3)
- v5 is ongoing refinement