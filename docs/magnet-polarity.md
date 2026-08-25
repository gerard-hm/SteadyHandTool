# Magnet Polarity Standard

Magnet orientation is the one part of this design that **cannot be recovered from a model
file**. An STL describes a ⌀4 mm hole; it says nothing about which way the magnet in that hole
faces. Two people can print the same adapter from the same file, populate it correctly by every
visible measure, and end up with parts that push each other away.

This document fixes that, so an adapter designed by one person clicks into a base owned by
another.

## The rule

> **Fixed parts present NORTH. Removable parts present SOUTH.**

| Part | Role | Exposed pole |
| :--- | :--- | :--- |
| Base tool pockets | fixed | **North** |
| Carriage tool interface | fixed | **North** |
| Tool adapters | removable | **South** |

**Every magnet in a single array shares the same pole.** There is no alternating pattern and no
keyed position. Any rotation seats correctly.

## Geometry

Each of the four base pockets holds six ⌀4 × 2 mm neodymium magnets on a **⌀18 mm bolt circle,
60° apart**. Seats are 2 mm deep, so a correctly seated magnet sits flush with the pocket floor.

```
        pocket, viewed from above          side view, one seat

              N     N                      ___________________
           N           N                   |    magnet   |     <- N face up, flush
              N     N                      |_____________|
                                           |   ⌀1.5 air relief
        all six the same pole              |
        ⌀18 bolt circle, 60 deg apart      v  ballast chamber
```

The ⌀1.5 mm hole under each seat is air relief — it lets a magnet press home instead of riding
on trapped air. It is not a through-hole to the outside.

## Installing without a compass

Neodymium magnets ship as a stack, uniformly polarised. **Do not separate the stack and sort the
magnets.** Slide one magnet off the end of the stack at a time and drop it straight into its
seat without turning it over. Every magnet then lands the same way round, and you only have to
verify the array once rather than six times.

If a magnet flips itself as it approaches the seat, it was already attracted to a neighbour in
the wrong orientation — take it out and start that seat again.

## Verifying the array

**Against known-good hardware, which is the easy case.** Offer a factory-built adapter to the
array. If it snaps flat and stays put at every rotation, the array is correct. If it pushes away
or sits proud on one side, the array is inverted.

**With a compass, for a first build.** A compass needle's marked, north-seeking end is a magnetic
*north* pole, so it is attracted to a magnet's *south* pole. Hold the compass over a seated
magnet in a base pocket:

- The marked end is **pushed away** — correct, the seat presents north.
- The marked end is **pulled in** — inverted, that array presents south.

Check one magnet per array. Because the stack method makes all six identical, one check settles
the pocket.

## If you get it wrong

A fully inverted array is harmless and reversible — the adapter simply will not stick, and the
magnets press out from the relief hole with a pin. A *single* reversed magnet among five correct
ones is the case worth avoiding: the part still holds, but it rocks on the odd magnet and the
holding force drops noticeably. That is why the whole array shares one pole. There is no phase to
get right, and a mistake is obvious rather than subtle.

## For adapter designers

Build to **south exposed** and your adapter will seat in any base built to this standard, at any
rotation. Copy the seat pattern from `InterfaceTemplate.stl` rather than re-deriving it — the
⌀18 bolt circle and 2 mm seat depth are what make the parts interchangeable, and the polarity
rule above is what makes them interchangeable *between owners*.

## Why not alternating poles

Alternating north and south around the ring would hold harder, because flux closes between
neighbours, and it would key the adapter to three rotational positions. It was rejected: a
mis-phased adapter would actively *repel* its base, which is a poor failure mode for someone
seating a tool one-handed with a tremor. Uniform polarity trades some holding force for an
interface that cannot be assembled out of phase.
