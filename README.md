**PART 1**

🤖 **TRU AI TOKENS, EXPLAINED SIMPLY**

**What is it?**
On TRU you can make a token that grows and changes over time, with an AI helping write each new chapter.

Think of a Tamagotchi or a Pokémon that levels up. Each time your token evolves, the AI writes a new description or style for it. TRU then stamps a permanent receipt of that change on the blockchain.

**The two kinds of AI tokens**

🧠 **SFT (Sentient Fungible Token)**: a batch of tokens with a personality that grows. The AI can update:
• description_ai: the token's story or description
• learning_mode, growth_algorithm, adaptation_rate: how it "grows"
• ai_version: which brain version it's on

🎨 **NCFT (Neural Canvas Fungible Token)**: an art-style token whose look evolves. The AI can update:
• description_ai
• style_descriptor: its art style
• dynamic_morph: how it transforms
• update_interval: how often it changes

**What the AI can NOT do (this is the important part)** 🔒
The AI is only allowed to write descriptions and style. It can never touch who owns the token, how many exist, balances, or anything about the chain itself. The AI is a storyteller, not a bank teller.

**What the chain proves**
Every evolution becomes a numbered "epoch" (1 → 2 → 3…), and each one is linked to the one before it, like a chain of diary pages. The blockchain proves what was written and when. It does not prove the AI's words are true. It's a verified history, not a fact-checker.

---

**PART 2**

🛠 **HOW TO USE IT, STEP BY STEP**

**Step 1: Run a node**
Run TRU Core, let it fully sync, and keep a little TRU in your wallet.

**Step 2: Give it an AI brain**
You can run one on your own computer (free and private):
• Ollama (default address 127.0.0.1:11434)
• Oobabooga (OpenAI-style local server)

Or you can use a cloud AI by setting its key on your machine: OPENAI_API_KEY, ANTHROPIC_API_KEY, GEMINI_API_KEY, or XAI_API_KEY.

Note: the "Create AI Token" screen currently talks to an Oobabooga-style server. The Evolution screen lets you pick from the AI providers your node has set up.

**Correct template:**

```bash
# ================================================
# 🧠 TRU AI PROVIDER KEYS
# Fill in ONLY the ones you use. Leave the rest blank.
# Ollama (local) needs no key.
# ================================================

# Local Oobabooga (used by "Create AI Token"); optional
OOBABOOGA_API_KEY=

# OpenAI
OPENAI_API_KEY=

# xAI / Grok
XAI_API_KEY=

# Anthropic / Claude
ANTHROPIC_API_KEY=

# Google Gemini
GEMINI_API_KEY=

# Nemotron (local or remote OpenAI-compatible server)
NEMOTRON_API_KEY=
NEMOTRON_ENDPOINT=

# Custom OpenAI-compatible provider (key only; endpoint is set via configureAIProvider)
CUSTOM_AI_API_KEY=
```

---

🔑 **Step 2b: Your AI keys file**

Make a file called `.env` next to your node, and fill in only the AI keys you use. Leave the rest blank. Ollama needs no key.

TRU reads these as environment variables, so load the file before starting the node:
`set -a; source .env; set +a`
Then start TRU in that same terminal.

Running TRU as a service? Add `EnvironmentFile=/path/to/.env` to your systemd unit.
Using Docker? Add `--env-file .env` to your run command.

🔒 Lock it down: `chmod 600 .env`. Never commit it to GitHub, and never paste it in chat.

---

🧾 **Step 3: Pick your "stamp payer" address**

Every evolution gets stamped on-chain for a tiny fee. Tell your node which of your own wallet addresses pays for it by adding this to **tru.conf**:

`oracle.address=<one of your wallet addresses>`

✅ The address must be in your node's wallet (tru.dat).
✅ Keep your wallet encrypted and unlocked while the node runs.
✅ Keep a small amount of TRU on that address for fees.

No private keys go in tru.conf. Your node signs with your wallet.

If this isn't set, your evolution still saves locally, but it waits in line and won't show as confirmed on-chain.

---

Tip: use a separate address with just a little TRU, so the fee payer never touches your main balance.

**Step 4: Create your AI token**
Main menu → **17 AI Tools** → **1 Create AI Token**
Pick SFT or NCFT, then fill in the name, description, image link, and (for SFT) supply, symbol, and decimals. Confirm, then wait for it to be mined and confirmed.

**Step 5: Preview an evolution (try it on for size)**
**17 AI Tools** → **2 AI Evolution** → **1 Preview**
Pick your token, pick an AI provider, and type a reason, like "won a battle" or "season 2". The AI proposes the new version and you get to look it over. Nothing is saved yet, so preview as many times as you like.

**Step 6: Commit it**
**2 Commit Exact Preview**, then type **COMMIT** exactly. What you saw is exactly what gets saved, with no second AI call and no surprises.

**Step 7: Watch it land on-chain**
Your node stamps the evolution onto the chain automatically. Use **3 View Token History** to see every epoch. Advanced users can verify it from the command line:
`./tru-cli -json raw verifytokenevolution '{"tokenID":"<your-id>","require_confirmed":true}'`
✅ `runtime_ok: true` and `fully_anchored: true` mean it's fully confirmed.

💡 **IDEAS YOU CAN BUILD TODAY**
• 🐉 **Game characters and pets** that evolve after wins, quests, or seasons
• 🎨 **Living art** (NCFT) whose style shifts over time, with every look saved forever
• 📖 **Story collectibles** where each epoch is the next chapter
• 🏷 **Brand or community mascots** that grow with your project's milestones
• 🎟 **Event tokens** that evolve after the event ("I was there → Season 2 veteran")

🔮 **COMING LATER**
The foundation is already built for **human, sensor, and device writers**. For example, a plant sensor could update a token's "health," or a certified expert could sign an update. Every change would be signed and permissioned by the token owner, and the history would stay verifiable. It isn't switched on for users yet.

🛡 **SAFETY TIPS**
• Keep your RPC private (localhost only). Never expose it to the internet.
• Use a separate, low-balance address for the oracle stamp payer.
• API keys live on your machine and never go on-chain.

Go build something weird. 🚀

---
