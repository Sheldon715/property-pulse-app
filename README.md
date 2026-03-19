# PropertyPulse

A full-stack property listing platform built with **Next.js 14**. It supports **Google authentication**, **property bookmarks (saved listings)**, **image uploads via Cloudinary**, **interactive maps/geocoding**, and a **contact form** that sends messages to property owners/managers (stored in MongoDB).

## Live Demo

- **Vercel**: https://property-pulse-app-snowy.vercel.app/


## Features

- **Authentication**: Google OAuth login via NextAuth
- **Property listings**: browse listings + listing details
- **Bookmarks / Saved properties**: save & remove saved listings (per-user)
- **Contact form (Messages)**: authenticated users can message the property owner/manager
- **Images**: upload and serve property images using Cloudinary
- **Maps & geocoding**: MapTiler + OpenCage for map display and address → coordinates
- **Deployment**: designed to deploy on Vercel

## Tech Stack

- **Frontend / Fullstack**: Next.js 14 (App Router), React 18
- **Auth**: NextAuth (Google provider)
- **Database**: MongoDB + Mongoose
- **Images**: Cloudinary
- **Maps/Geocoding**: MapTiler, OpenCage
- **UI/UX**: Tailwind CSS, React Toastify, PhotoSwipe

## Architecture Notes

- **Bookmarks (Saved Properties)** are stored on the `User` document (a `bookmarks` array of property IDs).
- **Contact Form** submits a message and stores it in MongoDB (`Message` model) so the owner can view messages in-app (instead of sending emails).
- This project uses **Next.js Server Actions** for some mutations (e.g. bookmark toggling, sending messages).

## Getting Started

First, run the development server:

```bash
npm run dev
# or
yarn dev
# or
pnpm dev
# or
bun dev
```

Open `http://localhost:3000`.

## Deployment (Vercel)

1. Push the project to GitHub (or import the folder into a repository).
2. Create a new project on Vercel and import the repository.
3. In **Vercel → Project Settings → Environment Variables**, add all variables listed in the `.env.local` section.
4. Deploy.

### Notes for production

- Set `NEXTAUTH_URL` to your Vercel production URL (e.g. `https://<your-app>.vercel.app`).
- Update `NEXT_PUBLIC_DOMAIN` to match the deployed domain (used for share links).

## Scripts

```bash
npm run dev     # start dev server
npm run build   # build for production
npm run start   # start production server
npm run lint    # run linter
```
