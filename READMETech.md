# Technical Guide: Updating Foundry Libraries

## Post-clone setup (Bash)

Run these from the project root: `c:\_sonia\dev\baseChallenge\base`.

### 1) Initialize and update Git submodules
```bash
git submodule update --init --recursive
```

### 2) Update Foundry libraries
```bash
forge update
```

### 3) Build the project
```bash
forge build
```

### 4) Run tests
```bash
forge test
```

### 5) Optional: create a local `.env` from the example
```bash
cp .env.example .env
```

### 6) Optional: pin a specific library version (e.g., forge-std)
```bash
forge install foundry-rs/forge-std@v1.9.6 --no-commit
```

### Troubleshooting
- Verify Foundry availability:
```bash
forge --version
```

- If Foundry is not installed (Bash):
```bash
curl -L https://foundry.paradigm.xyz | bash
```

- Then initialize the toolchain:
```bash
foundryup
```
- If submodules don’t sync, try:
```bash
git submodule sync --recursive
```
```bash
git submodule update --init --recursive
```