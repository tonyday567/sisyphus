# cache profiles

These are instructions for creating different cache files from sisyphus/. Each profile describes what to include, what to exclude, and when to use it. Hand any of these to an agent (yourself, Claude Code, a collaborator) and they'll know what to do.

## core

Create `cache-core.md` with your fundamental work - the base concepts and practical tools. This is the lightweight, shareable cache you'll use most often.

Include content/base/ and content/tools/. Exclude self/, ingest/, content/invoke/, .venv/, and .git/.

Before running, verify no self/ content will be included. This cache is safe to share with collaborators.

Use this for: default sessions, sharing context, quick warm-up.

---

## research

Create `cache-research.md` when you need reference material alongside your core work. This builds on the core cache by adding external papers, books, and pattern documentation from ingest/.

Start with everything from core, then add ingest/. Still exclude self/, content/invoke/, .venv/, and .git/.

This cache gets large. Use it when working with the agentic patterns documentation, diving into papers, or doing theoretical work that needs those references.

---

## local

Create `cache-local.md` for personal development sessions. This adds your private experiments and meta-work from self/ to the core content.

Start with everything from core, then add self/. Exclude ingest/ (unless you specifically need it), content/invoke/, .venv/, and .git/.

**Never share this cache.** It contains self/ directory which is private and git-ignored.

Use this for: working on sisyphus itself, personal experiments, debugging your own thinking.

---

## invoke

Create `cache-invoke.md` with just the invokable instructions from content/invoke/. This is meta-level - the instruction set without the knowledge base.

Include only content/invoke/. Exclude everything else.

Use this when building new tools or working on the instruction language itself. Rarely needed but useful when you need to see just the cards without the content.

---

## full

Create `cache-full.md` with everything except the noise (.venv/, .git/). This is your complete local context, including both self/ and ingest/.

Only use this for debugging cache issues or verifying flatten-md behavior. It's very large and includes private content.

**Never share this cache.** Contains self/ directory.

---

## how to use these

When someone says "get me core cache":

1. Read the core instructions above
2. Translate to flatten-md commands (or however you execute it)
3. Show what will be included and excluded
4. Check for warnings (any self/ content? output location safe?)
5. Run it
6. Verify the output

The instructions are stable. The execution method varies. You might use flatten-md directly, or generate file lists first, or do something else entirely. The card tells you what to create, not how to create it.

---

## composition

Profiles can reference each other. "Research = core + ingest" means take everything from core and add ingest/. You interpret what that means for your execution method.

If you need a one-off variation, just edit the list. The card is the program - changing it is programming.

---

## open questions

How should profile composition work precisely? If core excludes X but research tries to include X, which wins? We'll learn as we use this.

Should caches record their metadata (which profile, when created, from what git state)? Probably useful for "what am I looking at?" questions.

How do we prevent accidentally sharing self/ content? Maybe flatten-md should warn if self/ is included and output path looks shareable. Or require an explicit flag for private content.
