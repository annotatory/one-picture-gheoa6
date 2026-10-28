# Start sequence: from today to post 1 live

The team posts from the phone app. No tool is connected to the account. Nothing is posted until the start gates (M1, M2, M3) are YES.

## The steps, in order

1. **Send the packets.** Megh sends each owner their link (the SEND_TO text is ready for each). Ask Anji and Harsha first: their answers unlock posts 3 to 5 and 7 to 9. Then Counsel (6, 7, 10), the CCO (10), Naresh (10, 12), Raju (4, optional).
2. **The address and the waitlist page.** Megh: nari1.com bought (M2) and the waitlist page live at a real address (M1).
3. **The grid test.** The team posts the 12 tiles in order on a private test account (kit folder 03_GRID_TEST) and sends Megh one screenshot. Megh answers M3: joined or not. If not, the picture is re-made in about 30 seconds and the test repeats. Nothing goes live until M3 is YES.
4. **Record every answer.** As each owner replies, fill the Status and Answer date columns in MASTER_TRACKER. Tell the series seat "CCO cleared post 10" or "Counsel said NO on L2": the team kit is refreshed with one command (python3 -I refresh_kit.py --clear 10) and the zip is made again.
5. **Post 1 goes live.** When M1, M2 and M3 are YES. The team posts from the Instagram phone app, following the kit (no tool connects to the account).
6. **One post a day, in order.** Post 2, 3, 4 and so on, each only when its own questions (table below) are answered. Never skip a post, never reorder: if one is held, the series waits there.

## What each post needs

"New at this post" means questions that first stop this post, in addition to every question in the rows above it (a held post holds back every post after it). "Not blocking" questions never stop the post: it goes out with the fallback.

| Post | New at this post | Not blocking (post goes out with the fallback) |
|---|---|---|
| 1 · Tease | M1, M2, M3 | - |
| 2 · Problem | nothing new | L1 |
| 3 · Blueprint | A1 | K1, K2, H1 |
| 4 · Piece 1 · Energy | H4, A2 | R1 |
| 5 · Piece 2 · Focus | nothing new | - |
| 6 · Piece 3 · Stress | L2, A3, A4 | - |
| 7 · Piece 4 · Sleep | L3, H2, H3, A5 | - |
| 8 · Piece 5 · Mood | nothing new | - |
| 9 · Piece 6 · Body | A6 | K3, L4 |
| 10 · Prove | K4, L5, N1, A7 | - |
| 11 · Invite | M4 | - |
| 12 · Launch | M5, M6, H5, N2, A8 | - |

## How far the series gets, by who has answered

(Every start gate is YES in all rows. A post goes out only if all questions that stop it are YES.)

| Answered YES by | Last post that can go |
|---|---|
| Megh only (start gates, bio link, store links, date) | post 2 |
| + Anji | post 3 |
| + Anji and Harsha | post 5 |
| + Anji, Harsha and Counsel | post 9 |
| + Anji, Harsha, Counsel and CCO | post 9 |
| + Anji, Harsha, Counsel, CCO and Naresh | post 12 |
| Everyone (Raju too) | post 12 |

Posts 1 and 2 show no app screen, so they need only the start gates. Post 8 has no new question of its own but cannot go before post 7. Post 9 is not stopped by the cycle sentence: if the CCO has not said yes (K3), the paid-safe slides 2 and 3 go out instead.

## Which posts can go, and which stop the series

- **Go with no one else's answer (after the start gates):** posts 1 and 2. They show no app screen.
- **Go once Anji and Harsha confirm their screens are in the launch build:** posts 3, 4 and 5. Post 8 goes right after post 7 is out.
- **Go with the prepared fallback, never a stop:** post 3 without the "compares you with you" sentence (K1); post 4 with no time in the caption (R1); post 9 with the paid-safe slides 2 and 3 instead of the cycle sentence (K3). Paid ads for posts 2, 3 and 9 wait for Counsel or the CCO (L1, K2, L4); the organic posts do not.
- **Stop the series until cleared:** post 6 (Counsel, Anji), post 7 (Counsel, Harsha, Anji), post 10 (CCO, Counsel, Naresh, Anji), post 11 (Megh: the bio link), post 12 (Megh, Naresh, Harsha, Anji). Each one also holds back every post after it, because the profile picture only forms in order.
