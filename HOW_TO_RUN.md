# How to Run Markpad (after building)

Markpad is a **Tauri desktop app**. Running `npm run build` only compiles the
**frontend** (`build/`) — it does **not** refresh the double-clickable desktop
app. To actually run the app with your latest changes, use one of the options
below.

> ⚠️ The prebuilt `src-tauri/target/release/bundle/macos/Markpad.app` may be
> older than your source edits. If its timestamp predates your changes,
> double-clicking it will **not** show them — rebuild first (Option 2).

## Option 1 — Run it directly (fastest to see changes)

```bash
cd ~/repo/Markpad
npm run tauri dev
```

Compiles the Rust shell + loads the frontend and opens the app window
automatically. The **first** run compiles Rust and can take a few minutes;
subsequent runs are fast. Best for iterating while you watch the result.

## Option 2 — Rebuild the double-clickable app

```bash
cd ~/repo/Markpad
npm run tauri build
```

Then open the freshly built bundle:

```bash
open "src-tauri/target/release/bundle/macos/Markpad.app"
```

Use this when you want a proper app you can move into `/Applications`.

## Verify the change

Open any `.md` file (e.g. a resume), click the **⋮** menu at the top-right, and
at the bottom you should see:

```
🔠 Font Size   [ − ]  100%  [ ＋ ]
```

- **［−］** shrinks, **［＋］** enlarges — scales the editor **and** preview together.
- Click **100%** to reset. Equivalent to the ⌘+ / ⌘− / ⌘0 shortcuts.

## Useful commands

| Command | What it does |
| --- | --- |
| `npm run dev` | Frontend-only dev server (browser preview, no native shell) |
| `npm run tauri dev` | Run the full desktop app (compiles Rust) |
| `npm run build` | Build the frontend bundle only |
| `npm run tauri build` | Build the distributable desktop app |
| `npm run check` | Type-check (svelte-check) |
| `npm test` | Run the test suite |
