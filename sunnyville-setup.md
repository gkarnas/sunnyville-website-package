# Sunnyville Solar — Elementor setup

This is a draft implementation, not a published website. The new preview includes your real photos, logo and an optional silent installation clip. The production HTML uses external media paths that must be replaced with the actual WordPress Media Library URLs. Email delivery still needs to be configured and tested in WordPress.

## Visual plan

White background, navy #082B59 headings, amber #FFB300 primary buttons, blue #006FBA accents, pale #F3F7FA secondary sections. Colours are selected to complement the supplied logo, not claimed as exact sampled brand specifications.

1. Hero: full-width IMG_9885 rooftop photo behind a navy readability overlay, a large headline and immediate quote/contact actions.
2. Trust: 500+ installations completed by Gus, 10+ years’ experience, 10-year workmanship warranty and a typical 1–2 week installation timeframe.
3. Solutions: solar, batteries, combined systems.
4. Meet Gus: branded portrait extracted from IMG_4216, optional silent clip, installation experience, no subcontracting, selected panels with 25-year warranties and after-sales support.
5. Process: enquiry, assessment, installation, support.
6. Separate galleries: three rooftop solar photographs, followed by a dedicated section with two battery installations. Each photo opens a larger view in a new tab.
7. Reviews: prepared but hidden until genuine reviews are supplied.
8. Quote CTA and native WordPress form.

Hero: Solar & batteries. Built around your home.

## Confirmed experience and warranty wording

Gus confirmed over 500 distinct installations across his installation career, including work for other companies, 10+ years’ experience, no subcontracting for Sunnyville installations, a 10-year workmanship warranty and a 1–2 week installation timeframe. The copy attributes the installation count to Gus and describes the timeframe as typical, subject to site requirements, approvals and availability.

The 25-year panel warranty is described as a manufacturer warranty available on selected panels. Before publishing the final product offer, identify its panel models and whether the 25-year coverage is product, performance or both. The page does not claim 25 years of coverage for batteries, inverters or installation workmanship.

## 1. Page and header

Work on a draft page first. Choose Elementor Full Width and hide the default page title. In the page's Astra settings, disable the Astra header on THIS page only: the new HTML block includes the supplied logo and navigation. Retain Astra's footer. This supersedes the previous instructions to use Astra's header. Use a full-width parent container with zero padding and zero gap. Paste all of sunnyville-home.html into one HTML widget. Keep ancestor overflow visible to allow the mobile sticky contact bar to work.

The supplied logo is displayed using a CSS frame that trims its large white margins; the logo artwork was not redrawn. The header includes desktop section navigation and a call button, with a separate mobile Call / Message / Free quote bar. The phone is 0401 846 864. Message links open an SMS application where supported; desktop visitors can use email.

## 2. Preview and media connection

Open sunnyville-preview.html to see the whole design without uploading anything. It is a self-contained review file with embedded media, and its form submission button is deliberately disabled. Do not paste that full preview document into Elementor. Use sunnyville-home.html for the actual HTML widget.

Unzip sunnyville-website-package.zip and upload the eight files in assets/ to WordPress Media Library. Do not upload the ZIP itself as the website.

| Asset filename | Placement | Original source |
| --- | --- | --- |
| sunnyville-logo.webp | Header logo | Supplied logo PNG |
| sunnyville-solar-hero.webp | Full-width hero | IMG_9885.JPEG |
| sunnyville-installer.webp | Meet Gus portrait and video poster | Frame at approximately 0.7 seconds in IMG_4216.MOV |
| sunnyville-battery-clip.mp4 | Optional clip under Meet Gus | IMG_4216.MOV |
| sunnyville-rooftop-project.webp | Project gallery | IMG_2837.JPEG |
| sunnyville-battery-installation.webp | Project gallery | IMG_5073.JPEG |
| sunnyville-dual-battery.webp | Battery gallery | IMG_4659.JPEG |
| sunnyville-rooftop-detail.webp | Rooftop gallery | 8c31304b-fa7c-4c75-a0d6-9af1d168a944.JPEG |

For each asset, copy its actual WordPress File URL. Gallery photos now use that URL both in the image src and the enclosing link href. In sunnyville-home.html replace every occurrence of assets/FILENAME with that full URL. The portrait and clip appear more than once: replace all occurrences. If WordPress retains every filename in one upload directory, replacing assets/ with that directory's full URL is sufficient, but verify the actual URLs first. No public media URL has been invented or uploaded automatically.

The originals remain unchanged. Web copies are resized/re-encoded, with no generative content edits. The clip is converted from HDR HEVC to SDR H.264 MP4 for broader playback compatibility. Its audio is intentionally omitted, it does not autoplay, and it is labelled silent with an adjacent visual description. Keep the original if you later want to use speech; that version will need an audio review and accurate captions.

The hero uses the full original composition with responsive CSS cropping. Lower photos lazy-load. Video uses preload=none and native controls. Review templates remain hidden; no customer review or rating has been fabricated. Captions describe visible equipment without assuming system capacities, job dates or exact suburbs.

## 3. Form

This implementation uses Contact Form 7 and works without Elementor Pro. If a working form plugin already exists, reuse it with equivalent fields and recipient settings rather than installing another plugin unnecessarily.

In WordPress, open Contact > Add New. Name the form Sunnyville Solar Quote. Replace the Form tab with the following (do not add a form wrapper; Contact Form 7 creates it):

```html
<div class="sv-fields">
  <p><label>Your name (required)
    [text* your-name autocomplete:name maxlength:100]
  </label></p>
  <p><label>Phone (required)
    [tel* your-phone autocomplete:tel maxlength:30]
  </label></p>
  <p><label>Email (required)
    [email* your-email autocomplete:email maxlength:150]
  </label></p>
  <p><label>Suburb (required)
    [text* your-suburb maxlength:100]
  </label></p>
  <p class="sv-wide"><label>What are you interested in?
    [select your-interest "Not sure yet" "Solar panels" "Battery storage" "Solar + battery" "Upgrade an existing system"]
  </label></p>
  <p class="sv-wide"><label>Anything else? (optional)
    [textarea your-message maxlength:2000]
  </label></p>
</div>
<p>We'll use these details to respond to your enquiry. <a href="REPLACE_WITH_YOUR_PUBLISHED_PRIVACY_POLICY_URL">Privacy policy</a>.</p>
<p>[submit "Request my free quote"]</p>
```

Replace the privacy-policy URL with your actual published page before launching. Enable the form plugin's supported spam protection and complete its keys/settings.

Save the form. Copy the actual generated shortcode. Immediately below the homepage HTML widget, add an Elementor Shortcode widget and paste it there. In that widget's Advanced > CSS ID, enter sv-quote-form (without #). The homepage CSS includes styles for that exact ID. This ID is required for the matching form styles. Keep the widget immediately after the HTML block with zero gap so the pale quote-section background continues seamlessly.

## 4. Email configuration

Contact Form 7 > Mail:

To: gustavo.karnas@gmail.com

From: Sunnyville Solar <YOUR_AUTHENTICATED_SENDER@sunnyvillesolar.com.au>

Replace the entire sender placeholder with an actual sender authorised by your mail provider. The visitor's email belongs in Reply-To, not From. Configure an authenticated SMTP or transactional email connection in WordPress using that sender and the provider's domain authentication requirements.

Subject: New website enquiry — [your-name]

Additional headers:

```text
Reply-To: [your-email]
```

Message body:

```text
New Sunnyville Solar website enquiry

Name: [your-name]
Phone: [your-phone]
Email: [your-email]
Suburb: [your-suburb]
Interested in: [your-interest]

Message:
[your-message]
```

Use plain-text email; leave Mail (2) disabled unless you deliberately want a visitor confirmation email. Keep the plugin's visible validation, success and failure messages enabled. Confirm the recipient manually before publishing.

Submit a real test enquiry from the public page and check its arrival at gustavo.karnas@gmail.com, including Spam. Reply to that message and confirm the reply goes to the test visitor email. Check missing-required-field and invalid-email errors, plus all mobile call/SMS/quote links. An SMTP test alone does not verify the full form.

## 5. SEO and publishing

Configure the page title and meta description in your WordPress SEO plugin, not as head tags inside the Elementor widget.

Suggested title: Solar & Battery Installation Townsville | Sunnyville Solar

Suggested description: Local solar and battery installation in Townsville and North Queensland. Direct service, monitoring and a 10-year workmanship warranty. Request a free quote.

Use only verified business details in any LocalBusiness structured data. Do not add invented star ratings, licences, brands or address details. Assign the new page under WordPress Settings > Reading only after checking the draft and form delivery. Retain existing useful URLs or configure redirects where changing them.

## Verification and remaining setup

The local browser preview was tested at 1440px, 768px, 390px and 320px widths: no horizontal page overflow, no broken images, one H1 and working internal anchor targets. Desktop and mobile renders were visually reviewed. The MP4 loads with a duration of approximately 5.77 seconds, 540×960 resolution, no autoplay and muted playback. The HTML/CSS is isolated to sv-home and sv-quote-form.

These are local preview checks, not tests of the live WordPress page. Theme/plugin interactions, form validation, spam protection and delivery to Gmail still need end-to-end testing in your own installation. The 25-year panel warranty type remains model-specific and must be identified before the final offer is published. Reviews remain hidden until real review content is supplied for this page.

Reference documentation:
- https://elementor.com/help/shortcode-widget/
- https://elementor.com/help/using-elementors-full-width-page-template/
- https://contactform7.com/setting-up-mail/
- https://contactform7.com/best-practice-to-set-up-mail/
- https://contactform7.com/text-fields/

## Editing later

This is one HTML/CSS block inside Elementor, not individually draggable Elementor headings/images. Simple copy edits are easy with care; layout edits require CSS knowledge. To change text, find the exact phrase and replace only the text between HTML tags. To change a photo, replace its URL in both src and href, update the alt description and caption, and set the source dimensions. Make a copy before editing and check the mobile view afterwards.

The solar gallery is labelled 06A and the battery gallery 06B in comments. To add another job, copy a complete figure element inside the relevant sv-gallery container and update its details. The grid automatically adds rows; no manual column changes are needed. Upload the photo to WordPress first. Start with around six roof photos and two to four battery installations so the homepage stays focused. For a much larger collection, use a separate projects page.

For revisions through this conversation, specify the section, exact wording, source filename and preferred placement. For example: “Use IMG_1234 as the hero; move the existing hero into the solar gallery; keep everything else.”
