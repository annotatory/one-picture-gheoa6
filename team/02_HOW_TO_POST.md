# How to post

Read this once before your first post. Replace "P05" with the post number you are posting. If a button has a different name in your version of an app, pick the closest one **only if you are sure it does the same thing**. If you are not sure, stop and ask Megh.

## Which folder goes to which platform

| Platform | Folder to use | Which file |
|---|---|---|
| Instagram feed (a carousel) | INSTAGRAM_feed_4x5 (tall, portrait) | all the slides, in order |
| Instagram Story | INSTAGRAM_story_9x16 (very tall) | the one story file |
| Facebook | LINKEDIN_FACEBOOK_1x1 (square) | all the slides, in order |
| LinkedIn | LINKEDIN_FACEBOOK_1x1 (square) | all the slides, in order |
| X | X_LINKEDIN_wide_16x9 (wide, landscape) | the one wide file |

LinkedIn uses the **square** folder, not the wide one. The wide folder is for X. Copy only the folder for the platform you are posting to. When you pick pictures, pick them from the folder in your Files or Drive app if the platform lets you; if you must use the camera roll, check the shape (tall, square or wide) matches the table before you post.

## The time

Post everything for the day between **7:30 and 9:30 pm India time**, in this order: Instagram feed, Instagram Story, Facebook, LinkedIn, X. This window is a default to review after the first week. It is not based on our own data. Use it unless Megh tells you otherwise. The Story goes after the feed post, never before.

## Before every post (2 minutes)

1. Open 01_POSTING_CALENDAR. Find today's post. Check the status is **GO** or **GO-WITH-FALLBACK**. If it says **STOP-UNTIL**, do not post. Tell Megh.
2. Check yesterday's post is in 07_POSTED_LOG.csv.
3. Open today's post folder in 04_POSTS. The folder name ends in the status (for example P05_Focus__GO).
4. Open STATUS.txt. It has a **card for each platform** with the account, the exact files in the order to pick them, the caption file and a ready log row. If it says GO-WITH-FALLBACK, use the fallback files it names.
5. Copy the files to your phone: the folder for each platform, plus caption.txt, caption_for_X.txt and alt_text.txt.
6. Look at yesterday's reach and write it in the log (see 06_COMMENTS_AND_SAFETY, "The stop rule").

## Instagram feed (a carousel of slides)

1. Open Instagram. Tap the **+** button, then **Post**.
2. Tap the **Select multiple** button (two overlapping squares), then tap the slides **in order: slide 1 first, then slide 2, then slide 3.** Check the little numbers 1, 2, 3 on the pictures. A post with one slide: just pick it.
3. The pictures are already 4:5 portrait. If Instagram offers a crop or format button, choose the **full portrait** version. Do not zoom or move the picture.
4. Tap **Next**. Leave everything alone: no filters, music, stickers, text, hashtags, people tags, product tags or location. Tap **Next**.
5. **Caption:** open caption.txt, select all, copy. In Instagram tap the caption box and paste. Do not change a word.
6. **Alt text:** scroll down, tap **Advanced settings**, then **Write alt text**. For each picture paste the line from the matching block of alt_text.txt (PICTURE 1 for the first picture, and so on). Tap **Done**. If a box cuts a line off, paste what fits and tell Megh.
7. Leave **Audience**, **Also share to Facebook** and **Threads** as they are (off). Do not change any other option.
8. Tap **Share**.

## Instagram Story

1. In Instagram swipe right (or tap **+**, then **Story**).
2. Pick the story file from INSTAGRAM_story_9x16 (P05_story.png). Do not add text, stickers, music or links.
3. Tap **Your story**. A Story has no caption and needs no alt text. (The same file is what Megh uses for WhatsApp Status. You do not post to WhatsApp unless Megh asks.)

## Facebook (square pictures)

1. Open Facebook. Tap **Photo** in the post box.
2. Pick the slides from LINKEDIN_FACEBOOK_1x1 in order, slide 1 first.
3. Paste caption.txt. If you can edit a photo and see **Alt text**, paste the matching block. If not, skip.
4. Tap **Post**.

## LinkedIn (square pictures)

1. Open LinkedIn. Tap **Post**.
2. Tap the picture button. Pick the slides from LINKEDIN_FACEBOOK_1x1 **in order, slide 1 first.**
3. Paste caption.txt. If an **Alt text** button shows when you tap a picture, paste the matching block. If not, skip.
4. Tap **Post**.

## X (one wide picture)

1. Open X. Tap the new post button.
2. Tap the picture button and pick the wide file from X_LINKEDIN_wide_16x9 (P05_wide.png).
3. Paste **caption_for_X.txt**. It is the caption cut to fit X. When the caption already fits, the two files are the same, and that is fine. If the picture has an alt-text option (Add description), paste the "Story and wide picture" line from alt_text.txt.
4. Tap **Post**.

## Alt text: how to read alt_text.txt

The file has one block per picture: "PICTURE 1 of 3", then the line to paste on the next line. Paste only that line (the words under the label, not the label). Do not change a word.

## After you post (check each platform)

| Platform | Check | Then |
|---|---|---|
| Instagram feed | Open the live post. Swipe every slide: order 1, 2, 3, nothing cut off (except the on-purpose crops on slide 1 of posts 4 to 9). Read the caption. Open the three dots, Edit, and check the alt text is there. Open your profile and take a **screenshot of the grid**; send it to Megh. | Add the log row. |
| Instagram Story | Open your story. Check the picture shows and is the right one. | Add the log row. |
| Facebook and LinkedIn | Open the post. Check slide order and the caption. | Add the log row. |
| X | Open the post. Check the picture and the caption. | Add the log row. |

**The log.** Add one row to **07_POSTED_LOG.csv** per platform, after the checks. Use the ready row from STATUS.txt and fill in the date and time, the link and your name. Format: date and time as 2026-11-12 20:05 (India time); platform exactly as written in the card; link is the web link to the live post (for a Story, write "story, no link"); no commas in the issue column (use semicolons), or write none. Example row:

```
5,Instagram feed,2026-11-12 20:05,https://www.instagram.com/p/EXAMPLE/,Priya,none
```

## Mistakes and how to fix them

| What went wrong | What to do |
|---|---|
| Slides in the wrong order | **Do not delete.** Take a screenshot and tell Megh. Deleting changes the profile picture. |
| A typo in the caption | Edit the caption only (the three dots, then Edit). Paste the right caption from caption.txt. Do not touch the pictures. Tell Megh. |
| The wrong picture went up | **Do not delete.** Screenshot, tell Megh. |
| You posted something marked STOP | Tell Megh at once. Do not delete until Megh says so. |
| You forgot alt text | Add it: three dots, Edit, Alt text. |
| A post failed or got stuck | Do not try again many times. Screenshot, tell Megh. |
