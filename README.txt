FamWay / FamGateway — Dashboard redesign (reference match)
=========================================================

Kya karna hai
-------------
Ye 4 files apne repo me EXACT in paths par replace kar do:

  templates/dashboard.html
  templates/_sidebar.html
  templates/_icons.html
  static/dash.css

Baaki kuch nahi chhedna. Koi naya route, env variable ya DB field nahi chahiye.

Preview (browser me kholo)
--------------------------
  preview_default.html   -> naya user (MID badge + "IMAP Not Configured")
  preview_orders.html    -> orders hone par + "IMAP Connected"

Dono preview standalone hain (CSS inline hai), bas double-click karke kholo.

Kya hataya (repo me extra tha, reference me nahi hai)
-----------------------------------------------------
  1. "1 - Payment settings" card            -> ab Integrations page par
  2. "2 - Mailbox that receives alerts"     -> ab Integrations page par
  3. "3 - API credentials" card             -> ab API Keys page par
  4. "Try it: create a test order" card
  5. "Recent payments detected" table
  6. "Recent emails processed" table
  7. Failed-webhooks notice + "new API key" card
  8. Purana Quick Setup Guide checklist     -> ab video + "Next Steps"

Kya move hua
------------
  - MID badge + mailbox status ab page title ke right side me (pill badge).
  - Mailbox status: green "IMAP Connected" ya amber "IMAP Not Configured"
    (+ Configure button -> /integrations, amber dot par pulse animation).
  - Stat cards: Total Requests / Successful / Failed-Pending / Total Revenue,
    icon tile RIGHT side me, label uppercase (reference jaisa).
  - Sidebar: lucide icons (layout-dashboard, link-2, plug-zap, user-circle,
    book-open, log-out) + WhatsApp link me wa.me text.
  - Transactions table ab .tx-table class + empty state me inbox icon.

Video iframe
------------
"Quick Setup Guide" card ke andar iframe ka src JAAN-BUJH KAR KHALI hai
(tumhare saved dashboard me bhi khali tha). Apna tutorial link daal do:

  <iframe src="https://www.youtube.com/embed/XXXXXXX" ...>

Backend
-------
Saare Jinja variables, forms, routes, CSRF aur url_for waise hi hain:
stats, orders, m, greeting, display_name, chart, fmt, status_of,
pay, transactions, integrations, docs, profile, api_keys,
webhooks_page, status_page, logout.

Chart wahi JS SVG chart hai (7D/15D/30D pills + Revenue/Requests toggle).
MID par click = copy. "Hide for 24 hours" button = localStorage (24h).

Note
----
Verification text-flow + section-order diff se kiya gaya hai (52/52 tokens
match, section order same). Screenshot comparison is environment me
available nahi tha — layout/colour kuch bhi off lage to batao.
