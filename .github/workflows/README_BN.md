# খাইছেরে লুডু — Android Studio প্রজেক্ট

এটি একটি ছোট, অফলাইন-উপযোগী Ludo-style demo project। এটি Ludo King-এর অফিসিয়াল অ্যাপ নয় এবং তার সম্পূর্ণ নিয়ম/গ্রাফিক্সের অনুলিপি নয়।

## কী আছে
- চার রঙের গুটি
- পাশা ১–৬
- ৬ উঠলে “ছয়!”
- ১ উঠলে “কানা পড়ছে রে!”
- প্রতিপক্ষের গুটি কাটলে “খাইছেরে!”
- Android Text-to-Speech দিয়ে বাংলা কণ্ঠস্বর
- নতুন খেলা শুরু করার বোতাম

## APK বানানোর নিয়ম
1. কম্পিউটারে Android Studio ইনস্টল করুন।
2. Android Studio থেকে **Open** বেছে `KhaichereLudo` ফোল্ডারটি খুলুন।
3. Gradle sync শেষ হতে দিন। Android SDK Platform 35 ইনস্টল করতে বলতে পারে।
4. মেনু থেকে **Build → Build APK(s)** নির্বাচন করুন।
5. APK সাধারণত এখানে তৈরি হবে: `app/build/outputs/apk/debug/app-debug.apk`
6. APK ফোনে পাঠিয়ে ইনস্টল করুন। ফোনে “Install unknown apps” অনুমতি দিতে হতে পারে।

## বাংলা অডিও চালু করা
- ফোনের Settings-এ Text-to-speech output / Speech services-এ যান।
- বাংলা (Bangla/Bengali) voice/data থাকলে ইনস্টল করুন।
- সব Android ফোনে বাংলা TTS অফলাইনে পাওয়া যায় না। না থাকলে কথাগুলো স্ক্রিনে Toast হিসেবে দেখাবে।
- এই প্রজেক্টে আলাদা রেকর্ড করা MP3 ফাইল নেই; Android-এর TTS ব্যবহার করা হয়েছে।

## গুরুত্বপূর্ণ সীমাবদ্ধতা
এটি একটি starter/demo implementation। সম্পূর্ণ Ludo King-স্তরের অফিসিয়াল ৪-গুটি-পিছু, সঠিক ৫২-ঘরের ট্র্যাক, নিরাপদ ঘর, ব্লক, সব গুটির আলাদা চাল, অনলাইন মাল্টিপ্লেয়ার, অ্যানিমেশন এবং সাউন্ড প্যাক এতে এখনো নেই। বর্তমান কোডে প্রতি রঙে একটি নিয়ন্ত্রণযোগ্য গুটি দেখানো হয়েছে এবং সহজ ট্র্যাক-লজিক ব্যবহার করা হয়েছে। পূর্ণাঙ্গ গেম বানাতে পরবর্তী ধাপে গেম ইঞ্জিন/বোর্ড-লজিক উন্নত করা দরকার।


## GitHub Actions দিয়ে APK বানানো (কম্পিউটারে Android Studio ছাড়াও)

1. GitHub-এ সাইন ইন করে **New repository** তৈরি করুন; যেমন `KhaichereLudo`।
2. এই ZIP Extract করে ভেতরের সব ফাইল GitHub repository-তে upload/commit করুন। `.github/workflows/build-apk.yml` ফাইলটিও অবশ্যই থাকতে হবে।
3. Repository-তে **Actions** ট্যাব খুলুন।
4. `Build Android APK` workflow নির্বাচন করে **Run workflow** চাপুন (অথবা `main`/`master` branch-এ push করলেই build শুরু হবে)।
5. Workflow সবুজ টিক হলে run খুলে নিচের **Artifacts** অংশ থেকে `KhaichereLudo-debug-apk` ডাউনলোড করুন।
6. Artifact ZIP Extract করে `app-debug.apk` ফোনে ইনস্টল করুন।

**নোট:** GitHub account ও repository লাগবে। এই workflow APK স্বয়ংক্রিয়ভাবে build করার চেষ্টা করবে; build ব্যর্থ হলে Actions-এর log-এ error দেখা যাবে। এটি APK আগে থেকেই তৈরি করে দেয় না।
