# Two-Digit 7-Segment Display (Logisim 2.7.1)

A from-scratch digital logic build of a **two-digit 7-segment display** with:
- **BCD → 7-segment decoder** implemented using basic gates (AND/OR/NOT).
- **Digit multiplexing** using 2:1 multiplexers.
- A **manual digit-select** input to switch which digit is active (for demo clarity in Logisim 2.7.1).

This repo is designed to show **logic design fundamentals** without black-box chips: truth tables → boolean simplification → gate-level implementation → system integration.

## Why this is interesting
- **No magic parts:** The decoder is built gate-by-gate from the BCD truth table.
- **Clear system thinking:** Separate concerns for **decode** (combinational), **select** (control), and **display** (output).
- **Readable documentation:** Truth table, segment equations, and architecture notes included.

## How it works
- Inputs: `x3 x2 x1 x0` (BCD 0–9)
- Decoder outputs: `a b c d e f g` (active-high segment lines)
- Two physical displays → segment lines are shared; a **digit-select** line routes the decoded segments to either the left or right display via multiplexers.

> In hardware you’d drive both digits via time-division multiplexing at ~1 kHz with enable lines; for visual clarity here we use a manual toggle to show each digit cleanly in 2.7.1.

## Open the circuit
1. Install **Logisim 2.7.1** (the file’s `project source="2.7.1"`).
2. Open `Two-Digit-7seg-Display.circ`.
3. Set BCD inputs (`x3..x0`) to 0–9 and flip the **Digit Select** to view each display.

## Validation
- Verified that the gate-level decoder matches the standard BCD→7-segment truth table for digits 0–9.
- Inputs 10–15 default to “off” (or undefined) to avoid misleading outputs.

## Next steps / extensions
- Replace manual toggle with a **clocked multiplexing** (oscillator + digit enable) for a true two-digit refresh.
- Add **latches** so each digit can hold its own value while scanning.
- Port to hardware with a microcontroller and real LED modules.

## License
MIT
