# 2–3 Minute Game Showcase Video Plan

## Goal

Create a **class/project demo** that quickly explains the game’s premise, shows the playable loop, and highlights the strongest implemented features without lingering on debug tooling.

**Target runtime:** ~2:30, hard cap 3:00  
**Voiceover style:** darkly funny, but still clear  
**Demo method:** debug shortcuts may be used to stage footage, but should be hidden from the final cut  
**Priority:** balanced mix of premise, AI companions, overworld, dungeon, combat, loot, upgrades, and progression UI

## Core Message

The player is a lonely witch cat trying to make friends in a world where companionship is useful, risky, and a little manipulative. NPC companions generate quest flavor through AI, send the player into dangerous dungeons, and feed the main loop:

> **Talk to a companion → accept a quest → enter a dungeon → fight enemies → loot chests → return → upgrade → repeat.**

## Setup Checklist

1. Start LM Studio if AI dialogue will be shown live.
2. Start the AI bridge:
   ```bash
   cd ai
   pnpm dev:server
   ```
3. Start the game:
   ```bash
   cd game
   npm run dev
   ```
4. Use a prepared save or staged state with:
   - at least one visible AI companion,
   - at least one quest available or ready to accept,
   - some inventory materials/currency for shop or upgrade footage,
   - a dungeon layout that is quick to clear on camera.
5. If needed, use hidden setup shortcuts before recording final takes:
   - conversation phrase: `I will do it` to force quest activation,
   - dungeon debug keys only off-camera to stage clears/chests/floor transitions,
   - creative item gallery only off-camera to seed upgrade/shop materials.

## Storyboard / Shot Plan

| Time | Shot | What to Show | Potential Voiceover |
| --- | --- | --- | --- |
| 0:00–0:12 | Title + premise | Start on overworld with witch cat visible. Slow pan/walk through the field toward town. | “You play as a lonely witch cat with one very dangerous flaw: she wants people to like her.” |
| 0:12–0:30 | Overworld exploration | Show handcrafted village/outskirts, minimap, landmarks, town NPCs, dungeon gate route. | “The safe-looking village is the hub: shops, upgrades, companions, and the road to absolutely questionable life choices.” |
| 0:30–0:55 | AI companion interaction | Approach Ember Voss / another active companion, press **E**, show parchment conversation UI, portrait, archetype label, typed player input, AI response. | “Companions are AI-driven archetypes. They remember context, offer quests, and frame dangerous errands as proof that you’re special.” |
| 0:55–1:10 | Quest activation + follow | Show quest toast, portal label, companion following the player after quest start. | “When you accept, the quest becomes a playable dungeon run, and your new ‘friend’ follows just close enough to feel supportive — not close enough to help.” |
| 1:10–1:35 | Dungeon entry + floor loop | Enter dungeon, show curated layout, enemy/chest counters, distinct dungeon visual theme, roaming enemies chasing through rooms. | “Dungeons are repeatable, curated layouts with roaming enemies, chest objectives, and a clear rule: clear the floor before moving on.” |
| 1:35–2:00 | Turn-based combat | Trigger combat. Show polished battle screen and command flow: Attack, Heavy, Item, Defend. Use one item if available. | “Combat is turn-based. Basic attacks are reliable, heavy strikes hit harder with risk and cooldown, items spend a turn, and defending can save a run.” |
| 2:00–2:18 | Loot + progression portal | Return to dungeon, open chest, show reward text/inventory update, then show progression/exit portal. | “Victory is only half the job. The game makes you collect the reward too, because apparently friendship has paperwork.” |
| 2:18–2:38 | Return + upgrades/shop | Return to overworld. Show latest reward, inventory, shop purchase or Claws/Ward/Guard upgrade prompt. | “Dungeon loot feeds the village economy: buy consumables, upgrade attack, health, or guard strength, then survive worse favors from better manipulators.” |
| 2:38–2:55 | Codex/friend roster + closing montage | Briefly open Lore Codex and/or Friend Roster. End on the companion/town/dungeon gate. | “The codex tracks quests, the roster tracks relationships, and the big question stays the same: are you getting stronger, or just easier to use?” |

## Must-Capture Feature Beats

- **Premise:** lonely witch cat seeking connection in an exploitative companion system.
- **AI companions:** in-game conversation overlay, archetype personality, quest generation/acceptance.
- **Quest feedback:** toast notification, quest title/portal labeling, companion follow behavior.
- **Overworld:** handcrafted route, town roles, minimap, dungeon gate.
- **Dungeon:** curated multi-room layouts, enemies, chests, floor completion portal.
- **Combat:** turn-based command UI with Attack / Heavy / Item / Defend and animated feedback.
- **Rewards/progression:** chest loot, inventory, shop buying, stat upgrades.
- **Persistence/UI:** lore codex and friend roster as quick proof of longer-term quest and relationship tracking.

## Editing Notes

- Use quick cuts; do not show full traversal or full battles.
- Hide loading, debug overlays, failed AI requests, and staging shortcuts.
- If AI response time is slow, record the conversation after the response appears and cut out the waiting.
- Keep UI text readable for at least 1–2 seconds when showing toasts, inventory, upgrades, or codex entries.
- Use captions for controls only when helpful: **E Talk**, **E Enter Dungeon**, **1 Attack**, **2 Heavy**, **3 Item**, **4 Defend**, **I Inventory**, **C Codex**, **F Friends**.

## Suggested Closing Line

> “It’s a dungeon RPG about getting stronger by doing favors for people who may or may not deserve you — mostly not.”
