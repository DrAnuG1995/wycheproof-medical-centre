# Wycheproof Medical Centre, website prototype

One self-contained HTML file. No build step, no package manager, no dependencies
to install. Open `index.html` in a browser and it runs.

Built as a working prototype for the practice to review, not as a production
site. Treat it as a content and design specification that happens to be
clickable. Everything below is what a developer taking this over needs to know.

## What it is

- `index.html` is the whole site. Styles and script are inline.
- Twelve pages: home, appointments, after hours, services, medicals, our team,
  aged care, new patients, MyMedicare, practice policies, work with us, contact.
- Two webfonts from Google Fonts: Lexend for body text, Literata for headings.
  Nothing else is fetched from anywhere.
- Responsive. Verified with no horizontal overflow at 360, 390, 768 and 1024px.

## Important: this is a single-page app, and a real site should not be

Navigation is client side, using the URL hash (`#/appointments`, `#/contact`).
That was the right call for a prototype in one file. It is the wrong call for a
live clinic website, because:

- Search engines index one page, not twelve. A patient searching for
  "Wycheproof doctor after hours" should land on the after hours page.
- Hash URLs cannot be shared or linked to reliably from directories.
- Google Business Profile, healthdirect and the practice's own printed material
  will want real page URLs.

**Each `<section data-route="...">` should become its own page with its own
real URL.** The markup inside each section can be lifted across as is.

## Not wired up

These are deliberately inert in the prototype:

1. **Appointment request form.** Collects name, date of birth, phone, preferred
   days and times. Submits nowhere. Requests are meant to reach
   `reception@wycheproofmedicalcentre.com.au`, and the site promises a callback
   within 30 minutes during opening hours, so whatever it posts to has to land
   somewhere reception genuinely watches.
2. **General enquiry form** on the contact page. Same, submits nowhere.
3. **QR code** on the practice policies page is a placeholder box. It needs to
   point at the complaints and feedback form, which routes to the practice
   manager, principal GP and Practice Hub team.
4. **Map** on the contact page is a placeholder box.

## Things that are live logic, not static text

- The open or closed banner under the navigation computes from the browser
  clock against Monday to Friday, 9:00 to 17:30. Public holidays are not
  handled. See the `openpill` block in the script.
- The appointment request flow is real client side state: three steps, a
  summary panel that updates as you choose, and a confirmation screen.

## Content rules that must not be broken

- **No patient testimonials or reviews, anywhere.** Section 133 of the Health
  Practitioner Regulation National Law prohibits using testimonials to
  advertise a regulated health service. Do not add a reviews widget, a star
  rating, or quoted patient feedback. Linking out to Google reviews from the
  site counts as using them. Maximum penalty is $60,000 per offence for an
  individual.
- Practice information on the site is written to satisfy RACGP Standards
  Criterion C1.1, which requires patients can access current information about
  hours, after hours arrangements, billing, the communication policy, the
  complaints process and the range of services. Removing those pages creates an
  accreditation problem, not just a content one.
- Body typeface was chosen for legibility for an older, rural patient group.
  Do not drop the base font size below 18px.

## Still to be filled in

Anything in square brackets in the source is a real fact nobody has supplied
yet. Search the file for `class="ph"` to find them all. As at handover:

- Grace's surname on the team page
- Medical fees other than paperwork, which is $100 out of pocket
- Registrar accreditation status, supervision detail, housing and internet on
  the work with us page, and Dr Folorunsho's direct email
- Whether the busy licence renewal window really is November to January
- Confirmation of Wycheproof's Distribution Priority Area status

## Facts to verify before this goes live

- The urgent care number, 03 5478 0700, has not been independently confirmed.
- The practice changes ownership on 12 October 2026. Confirm the phone number,
  fax and practice name all transfer, because the entire site assumes they do.

## Licence and ownership

Written for Wycheproof Medical Centre. No third party code is included beyond
the two Google Fonts stylesheets.
