# LION BATTLE (free-entry MVP)

1. Create a Firebase project (Spark plan). Add a Web App and copy its configuration into `config.js`.
2. Firebase Console > Authentication > Sign-in method > enable Email/Password.
3. Firestore Database > Create database. In Rules tab, paste `firestore.rules` and Publish. Do NOT leave test-mode rules open.
4. Deploy files as a static website over HTTPS (e.g. Cloudflare Pages, GitHub repository with Pages). In Firebase Authentication > Settings > Authorized domains, add the deployed hostname.
5. Sign up with your own account on the deployed app. Firebase Console > Authentication > Users: copy your UID. Firestore > Start collection `admins` > Document ID = your exact UID > field `enabled` boolean `true`. Do this ONLY in Firebase Console, never in browser code. Log out and back in to show Admin tab.
6. Admin creates tournaments and releases room credentials. Players join using verified email accounts. This is a starter MVP: no payments, prizes, OTP phone verification, push notifications, anti-cheat, image uploads, or referral rewards. Phone is stored as unverified profile text.

IMPORTANT: Firebase web config is public by design; Firestore rules protect the data. The admin collection cannot be edited by clients. Room details are stored on the tournament document, which all signed-in users can read via Firestore; the UI hides them for non-joiners, but this is NOT secure confidentiality. Before running real tournaments with private room passwords, move credentials into a separate document with server-enforced access restricted to joined users. Do not use this starter to run paid-entry or cash-prize matches. Test with two player accounts before launch. Firestore and hosting free tiers have limits.
