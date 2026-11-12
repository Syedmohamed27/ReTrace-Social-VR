# ReTrace Social VR

A single-user, browser-based wooden museum for exploring two ideas about recommendations built on ambiguous behaviour: **visibility** (see why a gallery was suggested) and **reversibility** (reject the suggestion with Undo).

## Project status

**Works**
- Four-gallery 3D wooden museum with first-person movement and collision.
- Deliberately wrong starting recommendation (Abstract Art, 43%) with the best alternative (Pop / Street Art, 80%).
- HUD with score bars, "View provenance details" (why the inference may be wrong) and **Undo**, which moves you to the best alternative.
- Wrist-style panels: six editable art-style weights, a live top-three gallery ranking and arrows that jump straight to a gallery.
- Explanation pop-up on arriving at any gallery, showing its score and the weights behind it.
- Motion-controls panel (walk speed, sprint speed, mouse sensitivity).

**Simulated**
- The "dwell-time" inference is a fixed starting state, not real tracking.
- "My saved preference" is hard-coded (Impressionism 50, Classical 35). Nothing is stored, and a reload resets everything.

**Future Development**
- Headset VR, real behavioural tracking, persistent profiles, multi-user, and participant testing.
- Portal auras (postponed) and reversal of individual weight changes (Undo only reverses the recommendation).
- Known quirk: Impressionism and Classical share the same two weights, so their scores always tie.

## Technology stack

- **HTML, CSS, JavaScript** in one file, `ReTrace Social VR Final.html`: interface, scoring and scene.
- **Three.js 0.164.1** via the `esm.sh` CDN: 3D rendering, so an internet connection is needed.
- **Canvas textures drawn in code:** wood, signs and the artworks, which are original "studies after" the named artists rather than image reproductions.
- **Rule-based scoring:** a gallery's score is the average of its two linked style weights. No AI model, server, database or API key.
- **ChatGPT (development aid only):** helped debug code. It is not part of the running prototype.
- **Undecided:** the headset framework (for example WebXR) and how profiles would be stored.

## Running or inspecting the work

Use a desktop browser with WebGL (Chrome, Edge or Firefox). There is nothing to install, and no keys.

```bash
git clone https://github.com/Syedmohamed27/ReTrace-Social-VR.git
cd ReTrace-Social-VR
python3 -m http.server 8000
# open http://localhost:8000 and click "ReTrace Social VR Final.html"
```

Opening `ReTrace Social VR Final.html` directly also works in most browsers.

**Controls:** click the scene to capture the mouse (`Esc` releases it) · `W A S D` or arrows move · `Shift` sprint · `Space` jump · scroll zooms · `H` toggles the HUD and wrist panels · `M` toggles the motion panel.

**Suggested walkthrough**
1. Start in Abstract Art and read the pop-up, then press `H`.
2. Click **View provenance details**.
3. Click **Undo this inference** and note the new gallery and explanation.
4. Click **My saved preference**, close the pop-up, and see the weights change.
5. Drag the sliders and use the arrows beside the top-three list.
6. Click **Reset demonstration** to start again.

## Development record


| Stage | Change and reason | Checked |
|---|---|---|
| Museum | Built the four galleries, collision and movement so the interface could be tested in a believable space without a headset. | Walked every gallery and confirmed walls block movement. |
| Recommendation logic | Added rule-based scoring and the wrong starting inference to demonstrate challenging a system assumption. | Starting scores match the weights (43% and 80%). |
| Visibility | Added the HUD, provenance details and entry pop-ups listing scores and reasons the inference may be wrong. | Pop-up appears in each gallery and its scores match the sliders. |
| Reversibility | Added Undo, saved preference and weight sliders, keeping Undo separate from the weights. | Undo leaves the sliders unchanged. |
| Attention and control | Made the HUD hideable and added `H`/`M` keys, wrist panels and jump arrows. | Ranking updates on each slider move. |

## AI assistance

- **Tool:** ChatGPT.
- **Asked for:** help finding and fixing JavaScript errors, for example when the scene, controls or panels did not behave as expected.
- **How used:** I pasted the error or faulty function, read the suggested fix, and applied only the parts I understood, adapting names and logic to my own code.
- **Checked:** I reran the page in the browser, followed the suggested walkthrough, and confirmed scores, Undo and sliders still behaved as described above.

## Additional files

- `ReTrace Social VR Final.html`: the full prototype; open it in a browser.
- Design report: `ReTrace Social VR Design Report.pdf` (rationale, system diagram, storyboards).
