# wireshark-beaconing-analysis
Detecting Command-and-Control Beaconing via Network Traffic Analysis

🎯 Objective

you analyzed a PCAP

goal was to identify beaconing behavior

focused on outbound C2-style communication

2–3 sentences. No fluff.

🧠 Skills Demonstrated

This is where recruiters skim.

Examples:

Network traffic analysis (Wireshark)

Beaconing & C2 detection

Host-centric analysis

IOC extraction

Incident reporting (blue team)

🛠 Tools Used

Wireshark

Public PCAP dataset (link to source site, not the file)

🧪 Methodology (THIS IS THE MOST IMPORTANT PART)

Walk through your process, not the answers.

Example flow (high level):

Scoped internal vs external traffic

Eliminated broadcast/multicast noise

Pivoted to host-centric analysis

Identified automated outbound HTTP behavior

Validated timing patterns

Extracted indicators of compromise

This section proves you understand why, not just what.

🔍 Key Findings (no spoilers, no overreach)

Here you state facts, not drama.

Examples:

One internal host exhibited repeated outbound HTTP requests

Requests occurred at consistent ~4-second intervals

Communication targeted a single external endpoint

Behavior consistent with automated beaconing

Notice:
No malware name needed. No solution leak.

🚨 Indicators of Compromise (sanitized)

List only what you can justify:

Internal host IP

External IP

Protocol

Behavioral description

You can even say:

“Full indicators intentionally limited to avoid misuse.”

That’s actually a good look.

📝 Lessons Learned

This makes it feel like a real project.

Examples:

Why IP rotation complicates detection

Why host-centric analysis matters

Why timing is more important than volume

Recruiters love this section.
