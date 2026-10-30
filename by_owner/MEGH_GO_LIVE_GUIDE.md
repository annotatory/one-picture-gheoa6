# Megh go-live guide

Written 28 Oct 2026. Four jobs stand between today and post 1: put the waitlist page live on nari1.com, connect the Instagram account to Supermetrics, set up the spare account for the grid test, and open the second Meta ad account. Each is a numbered click path. Every button name below is from memory of how the apps look: if one has moved, pick the closest and send the series seat a screenshot. Nothing in this guide posts, spends or sends.

## Where things stand

| Item | State today (28 Oct) |
|---|---|
| Domain | nari1.com is owned (ledger C-694 closed). It is not on the Vercel account we can see, so it sits at the registrar where it was bought. The purchase receipt email names the registrar. |
| Waitlist page | Built and checked as a PREVIEW only. The live page needs the form relay URL, which does not exist yet. |
| Form relay | Not built. A draft is ready (section 1, step 2) and tested against a mock store. It has not been put on Cloudflare. |
| Instagram | The existing account is for live posts; the team posts by hand from a phone. No tool connection is needed to post. |
| Supermetrics | Neither Instagram Insights nor Facebook Ads is connected yet (checked today: both say NOT_AUTHENTICATED). |
| Meta ad accounts | One exists; a second is coming for the paid plan. |

**What I would do as the founder:** do section 1 first. Post 1 cannot go until the page is live (M1) and the grid test is done (M2). The grid test (section 3) can run the same day because it only needs a spare account and the team lead's phone.

## 1. Put the waitlist page live on nari1.com (answers M1)

> **Superseded for the page itself (28 Oct, Founding 1,000, R206):** the waitlist page is now the Founding 1,000 page (₹49 reserve through Razorpay, the real counter, cap 1,000), built in a separate session that gives its own go-live steps; you create the Razorpay payment page. The steps below describe the older free form and are kept for reference only. Do not set a cap of 100: the founding cap is 1,000.

**Who does what.** Megh clicks in the registrar and in Cloudflare (domain ownership and billing are his). Harsha, or anyone who can paste code into Cloudflare, can do step 2 for him. After each step, tell the series seat the result in one line: it runs the build commands and the checks.

> Three things the page cannot go live without. (a) The footer links open `nari1.com/privacy`, `/medical-disclaimer` and `/tools`: each must show a real page, or the footer links are dead. These are the website's pages, not this series'. (b) The page prints `care@nari1.com` as the contact: the mailbox must exist and receive mail. (c) The sign-off line from you: reply `Page signed: wishlist` (the plan file `DEEPIKA_PAGES_AND_SOCIAL_PLAN_2026-10-24.md` makes this line the approval, and the privacy-word record). The plan also notes an outside read of the page after the domain switch is still owed; the series seat can run it.

**Step 1. Review and sign the page.**

1. Open the preview file: `/Users/amr/Desktop/01_NILY/03_GTM_Marketing/NILY_CREATIVE_PLAN_2026-10-17/page_kit/out/wishlist.preview.html` (it opens in your browser; nothing is stored; the spots badge shows demo numbers).
2. Read it once on your phone width. If you want a change, tell the series seat. If it is right, reply in chat: `Page signed: wishlist`.

**Step 2. Set up the form relay (the thing that stores the emails).** Recommended for today: the Cloudflare Worker draft. It stores the email, the start choice and the wish, and counts spots.

1. Open the Cloudflare dashboard and sign in (create the free account with your own email if you have none). Go to **Workers & Pages**, then **Create**, then **Workers**, choose the **Hello World** template, name it `nari1-waitlist`, and click **Deploy**.
2. Click **Edit code**. Select everything in the editor, delete it, and paste the full contents of `/Users/amr/Desktop/01_NILY/03_GTM_Marketing/social_series_2026-10-28/kit_src/relay/relay_worker.mjs`. Click **Deploy**.
3. In the left menu go to **Storage & databases**, then **KV**, then **Create a namespace**, name it `nari1-waitlist`.
4. Go back to the Worker, then **Settings**, then **Bindings**, then **Add**, choose **KV namespace**. Variable name: `WAITLIST` (exactly). Pick the namespace you made. Save.
5. Still in **Settings**, open **Variables and secrets**, then **Add**. Name `CAP`, value = the number of founding spots (the brand deck says 100; it is your number). Save and deploy.
6. Copy the Worker's address (it looks like `https://nari1-waitlist.<something>.workers.dev`). Open it with `/count` added at the end in your browser. You should see `{"left":100,"cap":100}` (with your number). Send the series seat the address (without `/count`): that is the relay URL.

The draft and its test are in `/Users/amr/Desktop/01_NILY/03_GTM_Marketing/social_series_2026-10-28/kit_src/relay/`: eleven tests pass against a mock store (join, duplicate, bad email, oversize, wrong website refused, preflight, at-cap, store failure). It is **not tested on Cloudflare itself**: step 2.6 is that test.

**One caution for Counsel (add one line to the message you send them):** until Harsha's own relay exists, the waitlist emails sit in Cloudflare's store, outside Nily's servers. That is normal for a waitlist with a consent line, but it is personal data: ask Counsel to confirm it is fine for the waitlist, and to say how long we keep it. The alternative is Harsha building the relay on Nily's own database (lane L7b): cleaner for data, but the page then waits for him.

**Step 3. Build the live page.** The series seat runs this once it has the relay URL (you do not run it). It refuses to build if any claim rule fails:

```
cd /Users/amr/Desktop/01_NILY/03_GTM_Marketing/NILY_CREATIVE_PLAN_2026-10-17/page_kit
python3 -I build_pages.py --page wishlist --relay https://<relay-address> --out out
```

It writes `out/wishlist.html` (and a report). Only that file is published. The preview file is never published.

**Step 4. Host the page (Cloudflare Pages, free, allowed for a company) and point nari1.com at it.**

1. **Before anything:** open the registrar, find nari1.com, and copy or screenshot its current DNS records. If `care@nari1.com` already receives mail, the MX records in that list are what makes it work: keep them.
2. Cloudflare dashboard, then **Add a domain** (or **Websites**, then **Add a site**), type `nari1.com`, choose the **Free** plan. Cloudflare scans the existing records and copies them. Compare its list with the one you saved in step 1: every record must be there, MX included. Cloudflare then shows **two nameservers**.
3. Log in at the registrar where nari1.com was bought: **Domains**, then `nari1.com`, then **Nameservers** (sometimes **DNS settings**), choose **Custom nameservers**, paste the two Cloudflare names (replace the old ones), save. Cloudflare shows **Active** when it has taken over: this can take a while, and nothing is wrong while it waits.
4. In Cloudflare: **Workers & Pages**, then **Create**, then **Pages**, then **Upload assets**. Name the project `nari1`. Make a folder on your Mac containing only the live page renamed `index.html`, plus a folder for each website page the footer needs, if those pages are not on another host yet (`privacy/index.html`, `medical-disclaimer/index.html`, `tools/index.html`: the website owner supplies them). Drag the folder in and click **Deploy**.
5. In the project, **Custom domains**, then **Set up a custom domain**, type `nari1.com`, then **Activate**. Do the same for `www.nari1.com` if you want it to work too.
6. Open `https://nari1.com` on your phone, on mobile data (not the office wifi). Fill the form with your own email. Then open the Cloudflare Worker, **Storage & databases**, **KV**, your namespace, **KV Pairs**: your email must be there. Delete your test row. Tell the series seat: `M1 done`.

**If you want to keep DNS at the registrar:** Vercel can host the page without moving the nameservers (two DNS records at the registrar; Vercel shows the exact values). The Vercel account here is connected, so a session can deploy the page when you say `deploy the page`. The catch: the free Hobby plan of Vercel is for non-commercial use, so this needs the paid plan. I do not recommend it unless the Vercel team is already on a paid plan (not checked today).

**Message to Harsha, if you want him to do step 2 (paste as it is):**

```
Hi Harsha, I need the form relay for the Nari 1 waitlist page live today so post 1 can go. Contract: GET /count returns {"left": int, "cap": int}; POST /join takes {"email","start","wish","tags","copy"} and returns 2xx, or 409 if the email already joined. The page is on https://nari1.com, so the relay must answer CORS for that origin (and https://www.nari1.com), including the OPTIONS preflight. A draft that does this (Cloudflare Worker plus KV) is at /Users/amr/Desktop/01_NILY/03_GTM_Marketing/social_series_2026-10-28/kit_src/relay/relay_worker.mjs. Use it as it is, or build it on our database if you can do that today. Please send me the relay address when it answers /count.
```

**Then, after the page is live:** set the Instagram bio link to the page's address (the plan files do not name a path: if the page is the whole home page, that is `nari1.com`; if you put it on a path, use that path). Open the bio link on your phone to check it. Tell the series seat `M3 done`. M3 only matters from post 11 on.

## 2. Instagram: the live account and the spare account

**The live account** is the existing one. The team posts by hand from the Instagram app on a phone. Nothing connects to it to post. For insights and later ad work it must be a **Professional** account.

1. On your phone: Instagram, your profile, the menu (three lines), **Settings and activity**, then **Account type and tools**. If it shows **Switch to professional account**, tap it, choose **Creator** or **Business**, pick a category, finish. (It is free and you can switch back.) If it already shows **Switch to personal account**, it is professional: nothing to do.
2. For ads and for the Facebook route to insights, the account must be linked to a Facebook **Page** you manage. On Facebook: your Page, **Settings**, then **Linked accounts** (the name moves; it is where the Page lists Instagram), then **Connect Instagram**, and sign in. If you have no Page, create one named Nari 1 first. If the link is already there, nothing to do.

**The spare account (grid test only).** The team lead creates it on a phone with a new email address, sets it to **Private** (Settings and activity, then Account privacy, then Private account), and tells you the username. It holds the 12 test tiles and is **deleted** at the end (kit folder `03_GRID_TEST` has the exact delete steps). Credentials stay with the team lead: never in a chat. It is never the live account.

## 3. Connect Instagram and Facebook Ads to Supermetrics (reading numbers only)

This lets the series seat read the post numbers into the engagement log and, later, the ad results. **It never posts**: posts stay by hand. Two separate sign-ins (one for Instagram Insights, one for Facebook Ads). Do both in Chrome on your Mac, signed in to the Facebook and Instagram you own.

1. Open `/Users/amr/Desktop/01_NILY/03_GTM_Marketing/social_series_2026-10-28/MEGH_ONLY/supermetrics_login_links.txt` (a local file on this Mac; it holds two sign-in links. Do not forward it: the links are personal to your Supermetrics login).
2. Click the **Instagram Insights** link. Choose **Log in with Instagram** (preferred: it does not expire every two months). If it offers only **Log in with Facebook**, use that; it needs the Page link from section 2 and has to be renewed about every 60 days (from the connector notes, not checked today). Sign in as the live account, then **Allow**. The page says it is connected.
3. Click the **Facebook Ads** link. **Continue with Facebook**, sign in, choose the business and the ad accounts to share, **Allow**. When the second ad account exists (section 4), repeat this step so both are shared.
4. Tell the series seat: `Supermetrics connected`. It then checks that the Instagram profile and the ad account(s) show up. If a link says it has expired, say so: a new one is made. A manual route also exists: `hub.supermetrics.com`, your login list (**Token management**), **Add login**, pick the source.

If the account is not Professional, the Instagram sign-in fails: do section 2, step 1 first.

## 4. Meta Business: the second ad account (for the paid plan)

You have one ad account; a second keeps the launch ads (health-adjacent, so most likely to be questioned) apart from the first one's history. This is your call and costs nothing until an ad runs.

1. Open Meta Business Settings (`business.facebook.com`, then **Business settings**, signed in as the business admin). **Accounts**, then **Ad accounts**, then **Add**, then **Create a new ad account**.
2. Name it `Nari 1 launch`. Choose **Indian rupee (INR)** and the **India (IST)** time zone: Meta does not let you change either later. Under **Who will use this ad account**, choose **My business**.
3. Give yourself **full control** (manage ad account), and add the Page and the Instagram account to it (**Add assets**) so ads can run as Nari 1.
4. **Payment:** you add the payment method yourself in Ads Manager (**Billing & payments**). Nobody else enters card details. Set an **account spending limit** equal to the first campaign you approve, so a mistake cannot overspend.
5. Tell the series seat the ad account name. It connects it (section 3) and drafts campaigns **paused**; nothing runs until you say the word for that campaign (see PAID_PLAN).

## 5. What you forward

The full list with the exact message and attachment for each person is `/Users/amr/Desktop/01_NILY/03_GTM_Marketing/social_series_2026-10-28/by_owner/SEND_LIST.md`. In short: the team kit to the team lead and the packets to Counsel and Naresh now; Harsha and Anji for information (posts do not wait); Raju only if you want his one number; the CCO page only if you cannot confirm what the CCO signed. Each message is a text file next to the packet.

## 6. Your list (nothing else is waiting on you)

1. Send the owner messages and the team kit (SEND_LIST). Give the team lead's name and contact so it goes in the kit.
2. Put the waitlist page live (section 1) and reply `Page signed: wishlist`. Tell the series seat `M1 done`.
3. When the team lead sends the grid-test screenshot, answer `JOINED` or `NOT JOINED` (M2).
4. Approve (or change) the three safe comment replies: `MEGH_ONLY/COMMENT_REPLIES_FOR_APPROVAL.md` (the same words are in the kit, 06_COMMENTS_AND_SAFETY). Until you do, the team passes every comment to you.
5. Give your contact and the accounts to post from, so the Right now box in the kit is filled.
6. Connect Supermetrics (section 3) and open the second ad account (section 4).
7. Say which campaigns you approve and with what budget (PAID_PLAN). Until then nothing is spent.
