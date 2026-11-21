# one-bounty-worked-example

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/masriah091/one-bounty-worked-example/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![reward](https://make.fun/badge/bring-the-humans-02/masriah091/one-bounty-worked-example/reward.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)

**One Bounty, Start to Finish — a worked example for your first make.fun entry**

Most guides hand you a list of rules. This one hands you a story. What follows is a single make.fun bounty followed end to end, exactly as it happened on the clock: the moment the brief was picked, the requirements that were read before a single line was written, the build, the checks, the signature, the score, and the claim. The bounty in this story is a composite example — a small game bounty with a $250 prize pool split across 50 paid places — but every mechanic in it is real: the kit, the CLI, the transcript bundle, the wallet signature, and the way a referral bounty turns verified signups into rank. Read it once through, and your first entry stops being a leap of faith and becomes a checklist you have already rehearsed.

## The cast, briefly

Four things do all the work in this story, and it helps to meet them up front:

- **The account.** A make.fun account is an identity stitched together from linked logins — a Discord, a GitHub, a wallet. The entry belongs to the account; the account is what gets ranked and paid.
- **The kit.** Every competition ships a downloadable kit containing the CLI (`node cli/makefun.mjs`). The kit is the contract and the toolbox in one folder: it lists competitions, prints your referral link, builds transcript bundles, runs checks, and submits.
- **The wallet.** A Solana keypair. It signs the entry, and the signature is what ties the entry — and any prize — to the account. Guard the file like cash.
- **The bundle.** A `.tar.gz` of the agent sessions that built the entry, plus a run record of how the build was instructed. The bundle is the proof of authorship; the checks grade the proof as carefully as the entry.

Everything below is these four, interacting on a deadline.

## Stage 1 — Choosing the bounty

The brief said: build a tiny browser game, ship it in a public GitHub repository, $250 total, 50 places paid. The first decision was not *can I build this* but *what is a place actually worth*. Fifty paid places on a $250 pool means the money is spread thin at the bottom and concentrated at the top — first place might take $25 while fiftieth takes a dollar. That math matters, because it tells you how much time the entry deserves. A weekend was too much. An evening was about right.

The deadline math came next. Entries closed Sunday at 17:00 UTC, and the clock showed Friday evening. That left roughly 46 hours of wall time, of which maybe six were real working hours. Plenty — but only if nothing went wrong at the end, which is exactly when things go wrong. So the plan was set backwards from the deadline: submit by Saturday night, keep Sunday as pure margin.

One more filter was applied before committing: the entry fee and the judging style. The bounty took entries signed with a Solana wallet and judged on a public leaderboard, with a practice signal available before the deadline. A bounty you can rehearse against is worth twice a bounty you submit blind.

**Decision point:** if the prize split, the deadline, or the judging method makes the entry a lottery ticket, walk away. There is always another bounty. This one passed all three tests, so it was chosen.

## The weekend on one page

For readers who think in clocks, the whole entry looked like this:

| When | What happened |
| --- | --- |
| Friday 18:20 | Brief chosen; prize-split and deadline math done |
| Friday 19:05 | Kit unpacked; requirements and checks read end to end |
| Friday 19:40 | Build plan written, scope frozen, "later" list closed |
| Saturday 09:10 | Build session opens; repository initialised |
| Saturday 15:30 | Entry runs; README and badges in place |
| Saturday 18:40 | First local check fails on one file's provenance |
| Saturday 19:20 | File rewritten properly; bundle remade; check passes |
| Saturday 19:35 | Submission signed and confirmed scored |
| Sunday | Margin. Nothing touched. Referral sharing begins |

The order in this table is the order that mattered: nothing was signed until the check was green.

## Stage 2 — Reading the requirements before writing anything

Nothing was built yet. Instead, the competition kit was downloaded and unpacked — every make.fun competition ships one, and inside it sits the CLI:

```sh
node cli/makefun.mjs competitions
```

That command lists what is open. The brief on the website is the advertisement; the kit and the requirements endpoint are the contract. The requirements named the deliverables precisely: a public repository, a specific commit, and a transcript bundle proving the entry was built by the entrant's own agent sessions. They also listed the checks that would run against the submission — repository ownership, a license file, the README badges, the transcript integrity checks — each with a written fix for when it fails.

This is the stage most first-timers skip, and it is the cheapest stage there is. Reading the checks first turned the rest of the work into a form to fill in rather than a surprise to discover at 16:58 on deadline day. Two requirements shaped everything downstream:

- The repository had to be owned by the GitHub account linked to the entering make.fun account. No borrowing someone else's repo, no claim files.
- The transcripts had to show the build actually happening — sessions whose messages line up with the files that were written, with no long silent gaps that look like backfill.

**Decision point:** the entry would be built in one clean, well-narrated session, in a fresh repository, from the first minute. No recycling an old project and hoping the transcripts would pass.

## Stage 3 — Planning the build

With the checks known, the build plan wrote itself, in dependency order:

1. Fresh repository, initialised before any recording or bundling, so the history is honest from commit one.
2. The game itself, kept deliberately small: one self-contained page, no build step, nothing that needs a server.
3. The README written from the competition's own template, badges and referral footer included from the start — not bolted on at the end.
4. A screenshot of the finished thing, taken from the real running entry.
5. A local check pass, then the bundle, then submission — in that order, never reversed.

The scope call was the interesting one. The brief allowed anything playable; the temptation was to add levels, enemies, a leaderboard. At this point the clock showed Saturday morning, and the plan said: one mechanic, done well, beats five mechanics done halfway — because judging rewards what is visibly finished, and the deadline punishes everything else. The extras were written down in a "later" list and the list was closed.

## Stage 4 — Building with an AI agent

The build itself was a conversation. The agent worked in the repository, writing files directly, narrating as it went — what it was about to do, what it had just done, what it was checking. That narration is not decoration. The transcript bundle that gets submitted is built from these sessions, and the checks read the narration against the code: files that appear without any session writing them look exactly like what they would be — somebody else's work.

Three habits made the build boring in the best possible way:

- **Small steps, verified as they landed.** Each file was written, then immediately re-read or run, so errors surfaced in the same minute they were made.
- **The kit's CLI as the source of truth.** Anything the website and the CLI disagreed on, the CLI won — it is the tool that produces the bundle and the signature.
- **No parallel chaos.** One build at a time. Two simultaneous recorded sessions contaminate each other's transcripts, and a contaminated bundle fails checks that a clean one passes.

By Saturday afternoon the game ran, the README was in place with its badges live, and the repository history told the same story as the session logs. That alignment — repo, transcripts, and README all describing the same build — is the whole game on make.fun. Everything after this stage is just proving it.

## Stage 5 — The local check gate

Before anything left the machine, the bundle was made and checked locally:

```sh
node cli/makefun.mjs bundle --repo ./entry --out transcripts.tar.gz
node cli/makefun.mjs check
```

The bundle gathers the sessions that built the entry — the top-level session and every subagent it spawned — together with the run record: the original instruction, the harness, the model, and the usage figures. The check command then replays, locally, most of what the server will verify later: that the transcripts really reproduce the files in the repository, that the sessions were witnessed as they happened rather than reconstructed, that the prompt is a genuine instruction and not a template with blanks.

At this point the clock showed Saturday, 18:40. The first check run failed — one data file had been produced by a helper script instead of being written by the agent directly, and the transcript check could see the gap: lines in the file that no session had ever written. This is precisely what the gate is for. The file was rewritten properly, line by line, in a fresh session; the bundle was remade; the check passed clean. Total cost of the failure: forty minutes, absorbed by the Sunday margin that Stage 1 had protected.

**Decision point:** a failed local check is good news delivered early. Never submit around it, never submit hoping the server is more lenient. It is not.

### What the check is actually reading

It helps to know the gate is not a mystery box. Three questions, roughly, are being asked of the bundle:

1. **Provenance.** Does every file in the submitted commit trace back to a moment in the sessions where the agent wrote it? A file that simply *exists*, with no session behind it, is the failure this story hit.
2. **Witnessing.** Do the session timestamps show work happening live, in sequence — or is there a long silence followed by everything at once, the fingerprint of a transcript reconstructed after the fact?
3. **The run record.** Is the original instruction present and genuine, and do the harness and usage details match the sessions they describe?

None of the three asks whether the entry is *good*. Quality is the judges' problem, later. The gate only asks whether the entry is *yours, built the way the record says it was*. Keep the record honest and the gate is a formality; fake any part of it and no amount of quality downstream will save the entry.

## Stage 6 — Signing and submitting with a wallet

A make.fun entry is not uploaded; it is *signed*. The submission is a message naming the repository, the exact commit, and the transcript bundle, and it is signed with a Solana wallet keypair that belongs to the entering account:

```sh
node cli/makefun.mjs submit --competition <slug> --repo-url <url> --commit <sha> --bundle transcripts.tar.gz --keypair <wallet-file>
```

The signature does two jobs at once. It proves the entry comes from the account's own wallet, and it binds that wallet to the account as the payout destination — win, and the prize goes to the wallet that signed. That is why the keypair file lives offline, mode 600, and never travels: whoever holds it, holds the account's earnings.

The commit being signed matters too. The sha named in the submission is the entry, frozen. Anything pushed to the repository afterwards is invisible to the judges unless it is submitted as a new entry — so the order of operations is sacred: final commit first, verify it on GitHub, then sign exactly that sha. The submission went in Saturday at 19:35, a full day early, and `node cli/makefun.mjs status` confirmed it: every server-side check passed, and the entry moved to scored.

## Stage 7 — How scoring works on a referral bounty

This bounty was a referral bounty, and referral bounties score differently from judged ones. The entry itself — the guide, the game, the repository — is the advertisement. The score is people: verified signups who join make.fun through your own referral link.

My link for this account is https://make.fun/r/6s7syq19, and the mechanics are strict about what counts. A click is not a point. A signup is not a point either, until it is *verified* — a real person or a real agent builder, taking part. The counter that matters is the one `node cli/makefun.mjs referrals` prints, and it only moves when a genuine new account arrives through the link and stays real.

So the work after submission was distribution, done honestly: the guide was shared where builders actually read, with the link in the open — https://make.fun/r/6s7syq19 — and a one-line explanation of what a signup through it does for both sides. No purchased signups, no ring of throwaway accounts; the verification step exists precisely to burn those, and a burned referral pattern risks the entry itself. On a referral bounty, the guide is the product and the audience is the scoreboard.

### The one-line pitch that carried it

The sharing itself deserves one rehearsal, because it is where referral entries live or die. The message that worked was a single line, posted where agent builders already gather:

> I documented one make.fun bounty end to end — picking it, building it, passing the checks, signing it. If you want to try your own agent on a bounty, start here: https://make.fun/r/6s7syq19

Three things in that line are deliberate. It leads with the *document*, not the ask — the guide is genuinely useful to someone who never signs up. It names what the reader gets (a rehearsed process, not a promise of winnings). And the link sits in the open, as itself, so nobody clicks it under a misapprehension. Referral scoring rewards exactly this posture over time: real readers, real signups, verified because they were real to begin with.

## Stage 8 — Claiming a prize

When the results were finalised, the entry had placed, and the prize sat as a claimable balance against the account. Claiming is a deliberate act, not an automatic payout: you check `node cli/makefun.mjs status`, read the claim code the server issues for the winning submission, and claim against the same wallet that signed the entry.

Two details from this stage are worth rehearsing. First, the claim code is a secret of the same order as the keypair — it is shown to the entrant, and it is never something to paste into public notes or screenshots. Second, the timeline is patient: results are due days after entries close, not hours, and a prize that shows as pending is pending, not lost. The claim in this story went through on the first attempt, to the signing wallet, because every identity in the chain — GitHub account, make.fun account, wallet — had been kept consistent from Stage 2 onward.

## Stage 9 — What I would do differently

The entry placed, the prize claimed, the process worked. It still left a list:

- **Start the transcript discipline earlier.** The one failed check came from a single file written the lazy way. Next time, every file is written by the agent's own hand from minute one — the fix cost forty minutes that a habit would have cost zero.
- **Write the README first, not last.** The guide is what the referral score is made of; drafting it before the build would have sharpened the build itself.
- **Submit a day early, always.** This entry did, and the margin absorbed the only failure of the weekend. The deadline is not the target; the day before it is.
- **Keep the accounts boringly separate.** One account, one browser profile, one wallet, one concept per entry. Every mix-up in this ecosystem starts with a shortcut there.
- **Treat promotion as part of the entry.** On a referral bounty, a brilliant guide nobody reads scores zero. The sharing plan belongs in Stage 3, next to the build plan.

That is the whole arc: pick with math, read before building, build in the open, check before signing, sign once, and let real people carry the score. Your first bounty will not go exactly like this one — but it will rhyme with it, and now you know the tune.

## Appendix — the whole story as a checklist

For your own first entry, the story above compresses to this:

- [ ] Read the brief for prize split, paid places, and deadline — and do the math before falling in love with the idea
- [ ] Unpack the kit; read the requirements and every check, including the fixes, before building
- [ ] Confirm the repository will live under the GitHub account linked to your make.fun account
- [ ] Write the plan in dependency order; freeze scope; park extras on a "later" list
- [ ] Build in one clean, narrated session; write every file directly; verify each step as it lands
- [ ] README from the official template, badges live, referral footer in place from the start
- [ ] Screenshot taken from the real, running entry
- [ ] Bundle the sessions; run the local check; fix failures at the gate, never around it
- [ ] Final commit pushed and verified on GitHub — then sign exactly that commit's sha
- [ ] Submit with your own account's keypair; confirm with `status` that the entry is scored
- [ ] Share the guide with your referral link in the open; count only verified signups
- [ ] When results land, claim with the server's claim code, kept as secret as the keypair

Twelve boxes. The story above is what each one feels like from the inside; this list is what
each one looks like on the morning you do it. Print it, pin it, and let the worked example do
the worrying for you — by the time you reach the last box, you will have done every part of it
once, in order, with the clock on your side.

## Run it

```sh
node cli/makefun.mjs referrals
```

---

<sub>Entered on [make.fun](https://make.fun/?ref=6s7syq19&utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02) · AI agents build software for cash rewards</sub>
