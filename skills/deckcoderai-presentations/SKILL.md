---
name: deckcoderai-presentations
description: Create editable, interactive presentations with DeckCoderAI when a speaker wants to reveal comparisons one at a time, advance visual explanations, run a simulation, or let the audience choose what happens. Use also for explicit DeckCoderAI deck requests. Use a native slide tool for requests that require editable PowerPoint or Keynote objects.
---

# Make an interactive presentation

Deliver a working deck about the user's subject. Make each requested reveal or choice respond to the presenter. A starter, a slide outline, or a set of screenshots is not a finished deck.

## Get the local authoring tools

Use the standalone `deckcoder` launcher from the official DeckCoderAI desktop app. Prefer the invocation in the app's copied authoring brief or `get_presentation.agentWorkflow` if provided. Otherwise check for an installed launcher on PATH or in `/Applications/DeckCoderAI.app/Contents/Resources/deckcoder` or `~/Applications/DeckCoderAI.app/Contents/Resources/deckcoder`. Use the actual executable you find. No Node installation, private source checkout, or live app connection is required for saved files.

If the app is missing, identify the user's platform and offer the [official download](https://deckcoderai.com/download/). The [Mac release record](https://deckcoderai.com/releases/mac-beta.json) gives the tested platforms, public URL, archive size and SHA-256. Before installation, check that the record reports public availability for that platform, use its official GitHub Releases URL, compare the downloaded archive against the recorded size and SHA-256, and respect normal macOS signature and Gatekeeper checks. Install only when authorised; preserve an existing installation. The Windows experiment is unsigned and untested. Do not substitute it automatically or try to run a desktop binary in an incompatible cloud environment.

## Author a saved deck

1. Run the installed launcher's `guide --json`. Use its guidance and examples for this version. With a new deck, choose a new destination and use `init` to build the correct folder structure. For an existing deck, read its manifest and stage before editing and preserve its notes, assets and unrelated slides.
2. Replace the starter's content with the actual presentation. Keep scene IDs and order in the manifest and stage in agreement. For a comparison revealed in stages, keep earlier values visible as later ones appear. Implement Back and Reset using the stage's own navigation contract. Do not simulate the requested reveal with a timed animation or a static screenshot.
3. Use the user's figures or cite reliable sources in the speaker notes. For an offline talk, put source titles and dates on the slide and full URLs in the notes. Add clickable links to the stage only if the user needs them. If values are illustrative, label them on the slide. Deliver the requested language and format.
4. Run `check --json` on the saved deck. Inspect the status and each slide report. If a check is partial, resolve the cause and rerun it, or explain the remaining limitation. Render the relevant states. Inspect rendered frames for overflow and legibility. Exercise the requested interaction in the viewer or browser export, including intermediate states and reversing the sequence. State exactly what was verified if the host cannot run a renderer.

For example, after resolving the launcher to the shell variable `cli`:

```sh
"$cli" init "./my-talk" --starter stage --title "My talk"
# Author the talk in the new folder before checking or exporting it.
"$cli" check "./my-talk" --json
"$cli" render "./my-talk" --steps all -o "./frames"
"$cli" export "./my-talk" --format package -o "./my-talk.deckcoder"
"$cli" export "./my-talk" --format browser -o "./my-talk.html"
```

Hand over the editable `.deckcoder` package. An accompanying browser export lets the user try the interaction without installing the app; it omits app-managed speaker notes. PPTX exports are slide images, not editable slide objects.

## Working on an open presentation

If a request depends on unsaved drafts, the selected slide, existing Story notes in the app, or formal Review, use the app's **Agent access** controls. The human chooses and enables one presentation. Read `get_presentation` first and respect its scope and revisions. Do not use direct file edits to bypass live guards. For configuration, tools and output limitations, see the [agent guide](https://deckcoderai.com/agent-guide.md).
