# MSPI

<p align="center">
  <img src="assets/mspi-cover.png" alt="MSPI - Ministère de la Sécurité Publique et de l'Immigration" width="620">
</p>

MSPI is the official digital platform of Chad's Ministry of Public Security and Immigration. It connects citizens to the ministry through a bilingual (French / Arabic) mobile app, a public website, and a back office that lets ministry staff manage everything themselves. The whole thing replaced a paper process where getting an official publication out used to take days - now it's under 10 minutes.

The app is live on the Play Store as the ministry's official app.

[![React Native](https://img.shields.io/badge/React_Native-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)](https://reactnative.dev/)
[![Next.js](https://img.shields.io/badge/Next.js-000000?style=for-the-badge&logo=nextdotjs&logoColor=white)](https://nextjs.org/)
[![Supabase](https://img.shields.io/badge/Supabase-3ECF8E?style=for-the-badge&logo=supabase&logoColor=white)](https://supabase.com/)
[![Google Play](https://img.shields.io/badge/Google_Play-live-414141?style=for-the-badge&logo=googleplay&logoColor=white)](https://play.google.com/store/apps/details?id=td.gov.mspi.app)

## Links

- 📱 Mobile app: [Google Play](https://play.google.com/store/apps/details?id=td.gov.mspi.app)
- 🌐 Website: [securitepublique-tchad.org](https://www.securitepublique-tchad.org)

> The source code is private (government property). Happy to walk through the architecture and the tricky parts in an interview.

## What it does

- Citizens submit and track requests from their phone, with history and push notifications
- OTP authentication (no passwords to leak)
- Full French / Arabic support, including right-to-left layout
- A back office where ministry teams publish content and handle requests on their own, without a developer in the loop
- A public website for official communications

## Architecture

```mermaid
flowchart LR
    A[Mobile app<br/>React Native<br/>FR / AR] -- OTP + requests --> D[(Supabase<br/>Postgres · Auth · Storage)]
    B[Website<br/>Next.js] -- publications --> D
    C[Back office<br/>Next.js] -- content + requests --> D
```

Supabase handles auth, data and storage so the whole system stays lean - one source of truth for the mobile app, the website and the back office. The interesting design constraint was making the back office simple enough that non-technical ministry staff could run the platform themselves, which is what actually killed the multi-day publication delay.

## Screenshots

<p align="center">
  <img src="assets/mspi-web.png" alt="Institutional website" width="45%">
  &nbsp;
  <img src="assets/mspi-app.png" alt="Mobile app" width="24%">
</p>
