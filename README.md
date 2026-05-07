Cultured
An interactive canvas where touch becomes organism.

Cultured is a generative art tool that transforms human gesture into living biological form. Every stroke, tap, and hold leaves a trace — not ink, but colonies. Slow deliberate movement grows dense branching hyphae. Fast gestures scatter spore clusters. Hold the surface and watch growth accelerate, filaments pushing outward, satellites budding from the body. Release and the organism breathes.
The simulation runs on two systems working together: a Physarum polycephalum slime mould algorithm — the same mechanism real slime moulds use to solve mazes and optimise networks — layered with particle-based colony growth that builds powdery, stippled surfaces with concentric ring texture. Neither system knows the other exists. The results emerge from their interaction.

Inspiration
Physarum polycephalum — single-celled organisms that spread across surfaces in search of nutrients, leaving trails of chemo-attractant that other cells follow, collectively forming efficient transport networks without any central control. The IAAC Slime Mould Simulation research was a key reference for the agent steering algorithm.
Petri dish microbiology — the reference image that started everything: a glass dish photographed from above, crowded with Penicillium, Aspergillus, Fuligo, Lycogala and others, each species a different colour and texture, their colonies overlapping and competing for space. That image lives in the palette: ten named species, each with its own base colour and accent variants derived from real mycology.
Process art and action painting — the idea that the gesture itself is the artwork, and the tool mediates between intention and outcome in unpredictable ways. Cultured is designed so that identical strokes never produce identical results.
Generative typography — the text tool lets you place letterforms anywhere on the canvas and grow mould directly from the glyph outlines, so language becomes substrate. The chaos slider controls how far the organism strays from the letterform: at zero, the text is still legible; at maximum, the letters dissolve into colonies.

How it works

Draw anywhere on the canvas. Speed controls morphology — slow strokes produce thick branching networks, fast strokes scatter spore patches. Hold longer and the colony expands.
Text tool — place multiline text at any position, choose typeface (Roboto Flex variable sans or Instrument Serif), adjust weight, width and slant, then bloom. The mould grows along the letterforms.
Species palette — ten named mould species plus a custom colour picker. Each species has a base colour and accent variants; the simulation mixes them with per-agent jitter.
Chaos slider — controls randomness in text blooms: stagger timing, energy variance, stroke width, accent colour probability, and how far growth extends beyond the letterform.
Export — PNG at screen resolution, 2K or 4K (longest side scaled), with or without background.


Technical
Built as a single self-contained HTML file — no build step, no dependencies, no server. Open in browser and draw.
The core simulation:

Physarum agents — each agent senses three positions ahead, steers toward the highest chemo-attractant concentration, deposits trail, branches at intervals. Parameters follow the IAAC algorithm: 45° sensor angle, 9px sensor distance, 45° rotation step.
Trail grid — a downsampled Float32Array that diffuses and decays each frame. Decay rate is tuned so gradients stay sharp and steering doesn't break down over time.
Blob colonies — particle-stipple approach: each colony emits dozens of small arcs per frame at noise-displaced positions within a FBM-deformed radius, with concentric ring marks at growth thresholds. No filled gradients — texture emerges from particle density.
Displacement field — a second Float32Array tracks mouse influence. Hovering over grown mould drags filaments gently. Pressing deforms the colony outward.


Made with claude by
@helloiammaxim
