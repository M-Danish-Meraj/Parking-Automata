# Smart Parking DFA

Live demo: **https://smart-parking-dfa.vercel.app**

An interactive simulator of the deterministic finite automaton from our Theory of Automata presentation, *Automata in Smart Parking Systems*. Every sensor event is one input symbol, and the controller accepts a string only if it describes a complete, correctly ordered parking visit.

## The automaton

M = (Q, Σ, δ, q0, F)

- Q = {q0 Idle, q1 Detected, q2 Assigned, q3 Waiting, q4 Parked, q5 Ticket, q6 Payment, q7 Paid, q8 Exited, qR Reject}
- Σ = {v, a, f, t, i, p, e, s, x, g}
- q0 = start state, F = {q8}
- L(M) = v f* a p e t x* s g

| δ | | δ | |
|---|---|---|---|
| δ(q0, v) = q1 | | δ(q4, e) = q5 | |
| δ(q1, a) = q2 | | δ(q5, t) = q6 | |
| δ(q1, f) = q3 | | δ(q5, i) = qR | |
| δ(q3, a) = q2 | | δ(q6, x) = q6 | |
| δ(q3, f) = q3 | | δ(q6, s) = q7 | |
| δ(q2, p) = q4 | | δ(q7, g) = q8 | |

Every other (state, symbol) pair goes to the trap state qR, and δ(qR, any) = qR.

## What the demo shows

- Animated state diagram with the current state and the transition just taken
- Sensor-event buttons (or keyboard keys v a f t i p e s x g), string input with Run / Step / Undo / Reset
- Step-by-step trace with Mealy outputs (print ticket, open gate, beep)
- Moore slot LED (free / reserved / occupied), lot-full light and exit gate
- Full 10 × 10 transition table with the current cell highlighted

## Run locally

It is a single static page with no build step: open `index.html` in a browser, or serve the folder:

```
npx serve .
```

## Team

Hamna Ali Khan (CT-24157) · Amna Mohsin (CT-24169) · Muhammad Danish Meraj (CT-24269) · Muhammad Saraib (CT-24255)
