# Kreo Studio site (Netlify)

public/index.html                  Kreo Studio homepage (with working contact form)
public/about.html                  Iyed's about page
public/style.css                   styles for about.html only (the homepage has its own CSS inside)
netlify/functions/contact.js       serverless function: validates the form, emails you, auto-replies, saves lead
netlify.toml                       Netlify settings (publish = public, functions folder)
.env.example                       environment variables to add in Netlify

## Deploy

1. Put this folder in a GitHub repo (git init, commit, push).
   Drag-and-drop deploys do NOT run functions, so the form needs the Git import.
2. On app.netlify.com: Add new site > Import an existing project > pick the repo.
   Settings are read from netlify.toml (publish directory: public). Leave the build command empty.
3. Site configuration > Environment variables: add RESEND_API_KEY, FROM_EMAIL, TO_EMAIL
   (optional: ALLOWED_ORIGIN, AIRTABLE_TOKEN, AIRTABLE_BASE_ID, AIRTABLE_TABLE).
4. Trigger a redeploy after adding variables.
5. Test: open the live site, wait 3+ seconds, send the form.

Static pages only? Drag the `public` folder onto app.netlify.com/drop. The form will not send.

## Email setup (Resend)
Create a free account at resend.com, make an API key, and verify your domain so FROM_EMAIL can be hello@yourdomain.com.

## Local testing
npm i -g netlify-cli, copy .env.example to .env, run: netlify dev

## Spam protection included
Hidden honeypot field, 3-second time check, server-side validation and length limits, optional ALLOWED_ORIGIN check.
