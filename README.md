প্রশ্ন ব্যাংক: নোট
Firebase-ভিত্তিক অনলাইন প্রশ্ন ব্যাংক তৈরির সংক্ষিপ্ত নির্দেশিকা
১. কী বানিয়েছি
•	Firebase-ভিত্তিক প্রশ্ন ব্যাংক (শ্রেণি ৬-১০)।
•	তিন ধরনের প্রশ্ন: MCQ, সৃজনশীল, সংক্ষিপ্ত।
•	ফিল্টার ও সার্চ, প্রশ্ন যোগ/সম্পাদনা/মুছে ফেলা, প্রশ্নপত্র ও উত্তরপত্র তৈরি, প্রিন্ট বা PDF।
•	এখনো বাকি: AI (Gemini) দিয়ে প্রশ্ন তৈরি, PDF থেকে প্রশ্ন তৈরি, ড্রাফট-রিভিউ ব্যবস্থা।
২. আমার প্রজেক্টের তথ্য
বিষয়	তথ্য
Firebase প্রজেক্ট	que-bank (Spark ফ্রি প্ল্যান)
সাইটের নাম	que-bank-sir
লিংক	https://que-bank-sir.web.app
ডাটাবেস	Firestore, Location asia-south1
লগইন	Email/Password (ইউজার নিজে বানানো)
Rules	শুধু লগইন করা ব্যক্তি পড়তে/লিখতে পারে
৩. নতুন অ্যাপের জন্য ধাপগুলো
Firebase Console-এ (একবার)
1.	Create a new Firebase project (Analytics বন্ধ)।
2.	Security → Authentication → Get started → Email/Password Enable → Users → Add user।
3.	Databases & Storage → Firestore → Create database → Location asia-south1 → Production mode → Backup বাদ দিয়ে Create।
4.	Rules ট্যাবে নিচের কোড বসিয়ে Publish করুন:
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /{document=**} {
      allow read, write: if request.auth != null;
    }
  }
}

5.	Project Overview → Add app → Web (</>) → nickname দিন, Hosting টিক দিন (সাইটের নাম দিন) → Register app।
6.	যে firebaseConfig আসবে সেটি কপি করে রাখুন।
ফাইল তৈরি
firebaseConfig সহ Claude-কে বলুন, সে index.html বানিয়ে দেবে।
পাবলিশ
1.	একটি ফোল্ডারে index.html ও publish.bat রাখুন।
2.	publish.bat ডাবল ক্লিক করুন, শেষে লিংক খুলুন।
৪. publish.bat নতুন অ্যাপে ব্যবহার করতে
ফাইলটি Notepad-এ খুলে এই দুটি জায়গা বদলান:
•	que-bank → নতুন প্রজেক্ট আইডি (দুই জায়গায় আছে)
•	que-bank-sir → নতুন সাইটের নাম (দুই জায়গায় আছে)
৫. মনে রাখার বিষয়
•	Firebase যে Google অ্যাকাউন্টে বানিয়েছি, সেই অ্যাকাউন্টেই firebase login করতে হবে। অন্য অ্যাকাউন্ট থাকলে আগে firebase logout, তারপর firebase login।
•	প্রথমবার "Allow usage collection?" প্রশ্নে n লিখে Enter চাপলেই চলে।
•	Backup অপশনে "Upgrade/Blaze" চাপবেন না, কার্ড লাগে। ফ্রি প্ল্যানই যথেষ্ট।
•	ফাইল বদলালে নতুন index.html পুরোনোটির জায়গায় রেখে আবার publish.bat চালান।
•	প্রশ্নপত্রে শুধু "অনুমোদিত" অবস্থার প্রশ্ন আসে।
•	বিষয় ও অধ্যায়ের নাম সবসময় একই বানানে লিখবেন।
•	PDF চাইলে প্রিন্টে Destination হিসেবে Save as PDF দিন।
•	Windows "protected your PC" বললে More info → Run anyway।
৬. পরবর্তী ধাপ
1.	প্রথমে ৫-১০টি প্রশ্ন দিয়ে পুরো প্রক্রিয়া পরীক্ষা।
2.	Gemini দিয়ে AI প্রশ্ন তৈরি (AI Studio থেকে ফ্রি API key)।
3.	PDF থেকে প্রশ্ন তৈরি।
4.	ধীরে ধীরে ১০০০ প্রশ্নে পৌঁছানো।
