# GLP Winner Affiliate Tracking - Google Tag Manager Template

Track affiliate referrals and conversions for GLP Winner with this easy-to-use Google Tag Manager template.

## Overview

The GLP Winner GTM template enables seamless integration of affiliate tracking on your website. It automatically captures affiliate click IDs, manages user sessions, and tracks conversions with advanced attribution capabilities.

## Features

- 🚀 **Automatic Initialization** - Detects affiliate traffic and initializes tracking automatically
- 🔒 **Secure Session Management** - Uses session tokens for secure, reliable tracking
- 📊 **Conversion Tracking** - Track conversions with optional metadata
- ⚡ **Async Loading** - Handles script loading without blocking your site
- 🧪 **Test Mode** - Built-in test mode for development and debugging
- 🎯 **Smart Attribution** - Supports both click ID, IP, and email-based attribution

## Installation

### From Community Template Gallery

1. Open Google Tag Manager
2. Navigate to Templates → Search Gallery
3. Search for "GLP Winner"
4. Click "Add to Workspace"
5. Follow the configuration steps below

### Manual Installation

1. Download `template.tpl` from this repository
2. In GTM, go to Templates → New
3. Click the menu (⋮) → Import
4. Select the downloaded `template.tpl` file
5. Save the template

## Configuration

### Step 1: Create Initialization Tag

1. Go to Tags → New
2. Choose "GLP Winner Affiliate Tracking" as tag type
3. Configure:
   - **Tag Type**: Initialize GLP SDK
   - **Provider ID**: Your numeric Provider ID from GLP Winner
   - **Test Mode**: Enable for testing (disable for production)
4. Set trigger to "All Pages"
5. Name it "GLP Winner - Initialize"
6. Save

### Step 2: Create Conversion Tag

1. Create another new tag
2. Choose "GLP Winner Affiliate Tracking" as tag type
3. Configure:
   - **Tag Type**: Track Conversion
   - **User Email**: {{Your Email Variable}} (optional)
   - **Conversion ID**: {{Transaction ID}} (optional)
   - **Load GLP Script**: Uncheck (script already loaded by init tag)
4. Set triggers for your conversion events:
   - Form submissions
   - Thank you pages
   - Purchase completions
5. Name it "GLP Winner - Conversion"
6. Save

## How It Works

1. **User clicks affiliate link** → Lands on your site with `?glp_click_id=XXX`
2. **Initialization tag fires** → Detects click ID and initializes SDK
3. **SDK creates session** → Exchanges click ID for secure session token
4. **User browses site** → Session persists via first-party cookie
5. **User converts** → Conversion tag fires and attributes to original click

## Advanced Configuration

### Advanced Settings

Click "Show Advanced Settings" in the initialization tag to access:

- **Use Session Tracking** - Recommended for security (default: true)
- **User Email** - Pre-populate if user is logged in
- **Clear Cookie After Conversion** - Remove tracking after conversion (default: true)
- **Cookie Expiration** - Days until attribution expires (default: 30)
- **Custom Cookie Names** - Override default cookie names

### Force Initialization (Testing)

Enable "Force Initialization" to initialize the SDK even without a `glp_click_id` in the URL. This is useful for testing but should never be enabled in production.

## Variables You Can Use

Create these GTM variables for dynamic values:

- **Email Variable**: Capture user email from your site
- **Transaction ID Variable**: Your internal order/conversion ID
- **Provider ID Variable**: Store your Provider ID centrally

## Testing

1. Enable Preview mode in GTM
2. Visit your site with a test click ID: `?glp_click_id=test123`
3. Check browser console for:
   - "GLP Winner: Initializing with config"
   - "GLP Winner: Script loaded successfully"
4. Complete a conversion action
5. Verify "GLP Winner: Tracking conversion" in console

## Troubleshooting

### SDK Not Initializing

- Verify `glp_click_id` is in the URL
- Check GTM Preview for tag firing status
- Ensure Provider ID is correct
- Look for console errors

### Conversions Not Tracking

- Confirm initialization tag fired first
- Check conversion triggers are correct
- Verify cookies are not blocked
- Review network tab for API calls

### Console Debugging

Enable GTM Preview mode to see detailed logs:
```
GLP Winner: Script loaded successfully
GLP Winner: Initializing with config: {providerId: 123, testMode: false}
GLP Tracking SDK initialized.
```

## Support

- **Documentation**: https://www.glpwinner.com/docs/gtm-template
- **Issues**: Please use the GitHub Issues tab
- **Email**: info@glpwinner.com

## License

Copyright 2025 GLP Winner Inc.

Licensed under the Apache License, Version 2.0 - see [LICENSE](LICENSE) file for details.
