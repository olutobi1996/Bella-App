# Built By Bella: content guide

## 1. Install this package (once)
1. Extract the zip into `C:\Projects\BellaApp`, choosing to replace `www\index.html`.
2. In the VS Code terminal:
   ```
   npm install -D @capacitor/assets
   npx capacitor-assets generate --android
   npx cap sync
   ```
   This makes the app icon and splash screen from `assets/icon-only.png` and `assets/splash.png` (placeholders built from the brand fonts and colours; swap in Bella's real logo files with the same names whenever she sends them).
3. Press play in Android Studio to check it still runs.

## 2. Where things live
- `www/content.js`: ALL text content: brand name, prices, plans, workouts, exercises, meals.
- `www/media/plans`, `media/exercises`, `media/meals`: photos and videos.
- `www/fonts`: Bodoni Moda and Montserrat, bundled so the app works offline. Don't touch.
- `www/index.html`: the app itself. You shouldn't need to edit it to add content.

## 3. Adding content (edit `content.js`)
- **Meal:** copy an existing meal block, give it a new unique `id`, and fill in `category` (Breakfast, Lunch, Dinner, Snacks or any new name: the filter buttons appear automatically), `name`, `minutes`, `tag`, `image`, `kcal`, `protein`, `carbs`, `fat`, `ingredients` (include amounts, e.g. "Oats – 30g") and `method` (one step per line).
- **Plan:** copy a plan block with a new `id`. A plan has `workouts`, each with `exercises` (`name`, `sets`, `reps`, `rest` in seconds, `video`, `poster`). The first plan in the list is the default.
- **Photos:** save to `www/media/meals/` or `www/media/plans/`, then set e.g. `"image": "media/meals/choc-smoothie.jpg"`. Use lowercase names with dashes and no spaces. JPG, about 1200px wide, under 300KB each.
- **Videos:** MP4 (H.264), 720p, under 15MB each. If Bella has lots of videos, don't bundle them: store them online (Supabase Storage, Bunny, Cloudflare Stream) and paste the https link into `video`. Bundled media makes the app bigger and the stores have size limits.
- **Prices:** change them in `prices` at the top. They must match the store products exactly.
- Leave `""` for anything missing and a placeholder shows.

## 4. After every change
```
npx cap sync
```
Press play to test, then save to GitHub: `git add .`, `git commit -m "add content"`, `git push`.

## 5. Still to build before launch
- Real accounts and saved data (Supabase or Firebase). The login screen is a demo for now.
- Real subscriptions (RevenueCat, plus products set up in App Store Connect and Play Console).
- Privacy policy and terms pages, support email, store descriptions and screenshots.
- Apple Developer and Google Play accounts in Bella's name, then the release builds.
