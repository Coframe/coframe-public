# Coframe

> Bring your UX to life with AI-powered optimization and personalization

![Coframe Banner](https://files.readme.io/dc9a9f5-coframe-banner.png)

Coframe brings the content of your app or website to life through AI-powered optimization, personalization, and overall self-improvement. It takes minutes to integrate, and the ROI is clear to measure.

## Table of Contents

1. [Getting Started](#getting-started)
2. [Coframe Configuration](#coframe-configuration)
5. [Deploying with a Script Tag](#deploying-with-a-script-tag)
7. [Upcoming Features](#upcoming-features)

## Getting Started

### Step 1: Sign Up for a Coframe Account

Visit [coframe.ai](https://coframe.ai) to sign up for a Coframe account.

### Step 2: Access the Dashboard

Once you've signed up and logged in, you'll be directed to the dashboard, where you can manage your coframes.

### Step 3: Create a New Coframe

Click the "New Coframe" button to start optimizing a section of text or images on your website.

*Full documentation can be found at https://docs.coframe.ai/.*

## Coframe Configuration

After clicking "New Coframe", you'll need to provide the necessary information and configure the settings:

1. **Enter the URL** for the page you want to optimize and click "Next". Please note that you'll need to enter the full URL, including the protocol (e.g. `https://`). The easiest way to do this is to visit the page in your browser and copy the URL from the address bar.
2. Configure the coframe settings:
   - **Original Text**: Provide the original text you want to optimize. Again, you'll want to copy and paste this directly from your website.
   - **Context (optional)**: Add any context or background information that may be helpful for generating improved variants. You can add information about your target audience, the purpose/objectives of the text, or any other relevant information about what it's describing.
   - **Active**: Toggle this button (default is ON) to control whether the coframe is actively testing new variants and measuring conversion rates.
   - **Optimize Automatically**: Toggle this switch (default is OFF) to allow the coframe to generate variants to automatically optimize the copy.
   - **Personalized**: Toggle this switch (default is OFF) to allow the coframe to ingest user data and personalize the element for each visitor. _This is currently not released but is coming soon._
   - **Preview**: This is a clickable screenshot taken of your website target for easy checking.
   - **Save/Delete**: Click "Save" to save your coframe settings or "Delete" to remove the coframe.
3. Click "Save" to save your coframe settings or "Delete" to remove the coframe.
4. A table will appear with a "Generate Variants" button on top of it. Click this button to generate variants of the original text. A modal will appear with a slider which will allow you to select the number of variants to generate. Click "Generate" to generate the variants.

The top variant will always be your original, which will be kept as a control. The following variants are generated through our platform and will be ranked based upon engagement rate. The more variants you generate, the more likely you are to find a variant that outperforms your original.

You can also remove variants. Through this process of removing and adding variants, you can gradually optimize the copy presented on the website. Note that selecting "Optimize Automatically" will automatically do this for you.

**Copy the provided script tag** into your website head:

## Deploying with a Script Tag

To implement the optimization, paste the copied script tags into the head section of your website's page. You'll be able to copy it from the Coframe dashboard, or you can copy it from here and replace the page ID accordingly:

```
<script>window.COFRAME_PAGE_ID="{{page ID}}";</script>
<script src='https://cdn.jsdelivr.net/npm/coframe-ai/dist/cf.min.js'></script>
```

If using a Next project, you can use a Script from next/script at the root of your project:

```
<Script strategy="afterInteractive">
   {`
      window.COFRAME_PAGE_ID="{{page ID}}";
      var s = document.createElement('script');
      s.src = 'https://cdn.jsdelivr.net/npm/coframe-ai/dist/cf.min.js';
      s.async = 1;
      document.head.appendChild(s);
   `}
</Script>
```

Alternatively, add it in a useEffect on a single page:

```
useEffect(() => {
    const coframeId = document.createElement('script')
    coframeId.innerHTML =
      'window.COFRAME_PAGE_ID="{{page ID}}";'
    document.head.appendChild(coframeId)

    const coframeScript = document.createElement('script')
    coframeScript.src = 'https://cdn.jsdelivr.net/npm/coframe-ai/dist/cf.min.js'
    coframeScript.async = true
    document.head.appendChild(coframeScript)
},[])
```

The script will perform the following tasks:

1. Search for matches of the "original" copy for each coframe associated with the page.
2. Replace the original content with a variant to test.
3. Gather information on user engagement, such as session duration and conversions.
4. Send the data back to Coframe, where it will be processed to create relevant metrics.
5. Use the processed data to optimize the variants further and improve your website's overall performance.

You can track specific events with the following code snippet:

```
// Replace the name with something that makes sense for your product
Coframe.logCoframeConversion('Pressed Pricing Button')
```
These events will be sent to the dashboard, and can be set as conversion events to help further optimize your experiments. 

You can specify any label name as a parameter, such as "Sign Up", or "Try Demo Button", if you want to track multiple different events. Tracking these can help you answer questions about your product like 'What % of users that land on the demo page acutally sign up for a demo?'

## Upcoming Features

Coframe will soon support image optimization and other website elements, providing even more versatility in optimizing your website's content. Stay tuned for updates and enhancements to the platform.
