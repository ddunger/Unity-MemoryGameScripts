# Unity Memory Game Scripts

Simple collection of C# MonoBehaviour scripts used to build a Memory / Concentration card-matching game in Unity. These scripts implement core game behavior (cards, shuffling, matching), simple UI handling (timers, click counter, pause menu) and audio persistence.

Download
--------
A build of the game is available here:
https://drive.google.com/file/d/1hJgarh2jS_ELYUNZwFbcmIEu4hDHNsBQ/view?usp=sharing


Included scripts
----------------
- `CanvasControl.cs` — Manages menus, pause UI, starting/ending game, reset and quit actions.
- `CardController.cs` — Per-card behavior: flip up/down, matched state, and checking matching pair.
- `ClickCounter.cs` — Updates and shows total player clicks using TextMeshPro.
- `CursorController.cs` — Custom cursor, input handling, raycast detection for card clicks.
- `GameController.cs` — Main game logic: shuffling, tracking pairs found, game-over detection, third-flip reset behavior.
- `Sound.cs` — Simple singleton to persist an AudioSource across scenes.
- `TimeCount.cs` — Tracks elapsed time while the game is in progress and updates a UI text element.


How it works (notes)
--------------------
- Flipping: Cards are flipped by changing localEulerAngles between (0, 0, 0) (face-up) and (0, 180, 0) (face-down).
- Matching: Each card has a `matchingCard` reference. When both matching cards are face-up, they are marked `matched` and `pairsFound` increments.
- Click/Flip control: `numberOfUpCards` in `GameController` limits flips; on a third flip `ThirdFlip()` flips non-matched cards back down.
- Timer: `TimeCount` increments while `pairsFound` is below the target (example code stops incrementing at 9 pairs).
- Click counter uses TextMeshPro — ensure TMP is installed and referenced.
