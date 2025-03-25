**Structures**
- = - Base
- s - Any Structure
- d - Disc
- b - Ball
- p - Pillar
- c - Cube
- w - Wall
- o - Boulder

**Modifiers**
- S - Straight
- K - Kick
- U - Uppercut
- P - Parry
- G - Stomp
- H - Hold
- F - Flick
- E - Explode
  
- O - Unground
- X - Any Modifier

**Movement**
- m - Move
- t - Turn
- u - 180
- ^ - Lock on
- J - Jump
- D - Dash
- B - Bump
- M - Mount

**Stones**
 - F/ - Flow Stone
 - C/ - Charge Stone
 - V/ - Volatile Stone
 - G/ - Guard Stone
   g - Guard

**States**
- [] - Grounded
- ( ) - Free
- |  | - Any
- { } - Incoming
- < > - Explosive

**Extra**
- > - Transition to Next Notation string
- ** - Offhand
- ! - Notes
- . - Pause
- ... - Repeat
- _ - Wait



# Insanity Extension

**Extra**
- O - Unground,   O;e !Unground using Explosive
- h - Hit something
  If used in an Indicator, this notates to perform while in Hitstop
  ;R - Notates Ricochet
- C - Crush a Structure
  C1;2 - Break Structure 1 using 2, C\<s> - Break an Explosive
  C;T - Break Structure on Terrain, C;M - Break both structures
- **Bold** - Charged Force Modifier
- L - Land
  Land on the ground, or a structure if specified. Ends Aerial
- : - Optional
- \\ - Logical OR
- X - Any Modifier
- & - Bloodbend, Used like Bump, but on the Opponent
- ...*n* - Used after an existing repeat, *n* specifies which repeat to end
- e - Move a Structure due to an Explosive (e1;u !explosive to move 1 up)
- ~~Strikethrough~~ - Restrictive; Do not perform, or Stop doing this
  ~~M~~ to unmount, ~~C~~ to not crush
- @ - Opening (with space) or P2P state (with h or c)
  h@/ - Host match,  c@/ - Client match,  @ / - Start of match
- <u>Underlined</u> - Conditional String, use to specify continuing after the string is true
- "Vocal" - Say the quoted phrase

**Specification**
- A - Aerial
  Used with movement indicators in flight
  If used in an Indicator, this notates to perform while Airborne
- t*n* - Rotate *n* Degrees, can be approximated with " ~ "
  l \\ r - Used after t*n* to specify a direction, assumed to be 90°
- s-*n* - Negative structure number specifies the *last nth* of it
- a - Notates arms
  Used with movement indicators to aim arms
  Double Indicator to notate a Pose
  Use a;+(  ) for Nova's advanced hand positioning
- {X} - Opponent does this
- `X` - Persisting
  Keep doing this string, ex. `M`{s}F to stay mounted while flicking
- **^** - Line of Sight

**Indication**
- ;Indicators, - Indicator String
  Combines Indicators to notation
  Use Structure states or Numbers to not confuse with Positioning
  Broken by Space, or Arrows. Otherwise must end with a Comma
  **Charged** indicators makes it emphasized (m;**f** = move far forward)
  
- ;f \\ ;b \\ ;l \\ ;r \\ ;u \\ ;d \\ ;s \\ ;o \\ ;i - Relative Positioning, propagates to structures
  In order - Front, Behind, Left, Right, Up, Down, Side, Opponent, Self
  Combine for Diagonals, add a Pause to sequence positioning
  Relative to You, unless after a Structure / Opponent, then it is relative to it / them
  Add a number to indicate distance in Cubes (;u2+ !Up 2+ Cubes, ;s0 !Touching side)
  
- ;|s| - Notates Indication as Relative to a Structure
  t;|s| \\ m;|s| - Turn \\ Move towards a Structure, ;|s|s is from the side of it
  Numbers can be used in place of States to indicate the Nth Structure
  ex. B(b;H);{c}s !Waterbend an Incoming Cube to the side with an Ungrounded Held Ball
  
- M; - Indicators for the way you mount
  | = Joystick, -- = Handlebars, : = Yeehaw

**Specific States**
  These add to the pre-existing structure states : (), [], {}, ||, <>
- s1+s2 \\ s1-s2 - Structure 1 has More \\ Less weight than Structure 2
- s+ \\ s-   - Any Structure with More \\ Less weight than the noted structure
- s;f \\ s;S \\ s;H \\ s;F - Indicators for Structure are:
  Flat, Sideways, Held, or Flicked. (Respectively)


# DISTINCTIONS
{w} dES !Opponent summons wall, you dES
{w}dES !dES an incoming wall

;fl !Diagonal of front and left
;f.l !Front, then left

;o !Relative to Opponent
;|o| !Relative to Boulder

w... > C-1 !Crush the last wall

JF\HM !Jump, (flick or hold) mount
JF\ HM !Jump, then flick or (hold and mount)
JF \HM !(Jump and flick) or hold, then mount
JF \ HM !Jump and flick, or hold and mount

:DJ !(Optionally Dash) then Jump
: DJ !(Optionally Dash and Jump)

[c:] !Cube that is *optionally* grounded

\> Finishes all strings
" " Finishes most strings
... > !Stop repeating after >
:"meow" !Everything after " " is not optional anymore
:>"meow" "meow" !Using > bypasses " "
JF\ HM   !Everything after " " is not (OR) anymore
\>\\"meow" "meow" !Using > bypasses " "
;f.s d !d is not apart of the indication string due to " "