# Fury Claw Code - VS Code Codespaces Setup Guide

## Quick Start (3 Steps)

### Step 1: Create Your Codespace

1. Click the green **Code** button on this repository
2. Click the **Codespaces** tab
3. Click **Create codespace on main**
4. Wait for VS Code to load (2-3 minutes)

### Step 2: Add Your API Key

1. In VS Code, open the **Explorer** panel (left sidebar, top icon)
2. Right-click the **rust** folder → **New File**
3. Name it: `.env`
4. Copy this into the file:
```
ANTHROPIC_API_KEY=sk-ant-your-actual-key-here
```
5. Replace `sk-ant-your-actual-key-here` with your real key from https://console.anthropic.com
6. **Save** (Ctrl+S / Cmd+S)

**Don't commit this file** — it's automatically ignored.

### Step 3: Build Everything

1. Press **Ctrl+Shift+P** (or **Cmd+Shift+P** on Mac)
2. Type: `Tasks: Run Task`
3. Select: **Rust: Build Workspace**
4. Wait for the build to complete (2-5 minutes)

## Verify Installation

Once the build finishes:

1. Press **Ctrl+`** to open the integrated terminal
2. Type:
```bash
cd rust
source ../.env
./target/debug/claw doctor
```

You should see ✅ green checkmarks confirming:
- API key is valid
- Models are accessible
- Tools are configured

## Using the CLI

All commands run in VS Code's integrated terminal:

```bash
# One-shot prompt
./target/debug/claw prompt "explain this codebase"

# Interactive REPL
./target/debug/claw --model opus

# Run all tests
cargo test --workspace
```

## Available VS Code Tasks

Press **Ctrl+Shift+P** → **Tasks: Run Task** to access:

- ✅ **Rust: Build Workspace** — Full debug build
- ✅ **Rust: Run Doctor Check** — Verify setup
- ✅ **Rust: Run Tests** — Execute test suite
- ✅ **Rust: Release Build** — Optimized production build

## Extensions Included

Your Codespace automatically installs:

- **rust-analyzer** — Code intelligence
- **CodeLLDB** — Debugging
- **Crates** — Dependency management
- **Dependi** — Update tracking

## Troubleshooting

### "command not found: claw"
Make sure you're in the `rust` directory and sourced the `.env`:
```bash
cd rust
source ../.env
./target/debug/claw doctor
```

### "ANTHROPIC_API_KEY not set"
1. Check that `.env` file exists in the project root
2. Verify it has `ANTHROPIC_API_KEY=sk-ant-...` (with your real key)
3. Run `source ../.env` in terminal before running `claw`

### Build is slow
- Debug builds are normal (2-5 min first time)
- Codespaces machines are 4-core, so builds are slower than local
- Subsequent builds are much faster (cached dependencies)

## Resource Usage

Your GitHub Pro includes **120 core-hours/month**:
- Full build: ~10-15 core-minutes
- 10+ full rebuilds per month available
- Plenty for development and testing

## Next Steps

1. ✅ Codespace created
2. ✅ Build complete
3. ✅ Doctor check passed
4. Try: `./target/debug/claw prompt "what files are in this project?"`

## Documentation

- **USAGE.md** — Task-oriented usage guide
- **rust/README.md** — Workspace layout and features
- **PHILOSOPHY.md** — Project design principles

---

**All setup complete!** You're ready to use Fury Claw Code. No terminal knowledge needed — everything works in VS Code. 🎉
