# Contentsquare Dynamic Variables Tag for GTM

A Google Tag Manager community template that enables seamless integration with Contentsquare by sending custom dynamic variables to track user behavior and enhance analytics insights.

## Overview

The **Contentsquare Dynamic Variables** template is a custom GTM tag that allows you to send dynamic variables to Contentsquare's User Experience Analytics (UXA) platform. This template simplifies the process of capturing and transmitting custom data points, enabling richer behavioral tracking and more granular analytics reporting.

### Key Features

- **Easy Configuration**: Simple table-based UI for defining dynamic variables
- **Multiple Data Types**: Support for both string and numeric values
- **Scalable**: Track up to 40 unique variables per pageview
- **Type Safety**: Built-in type conversion for numeric values
- **Flexible**: Define multiple variables or send one per action using separate rules
- **Community Template**: Published in the GTM Community Template Gallery

## Installation

### Method 1: From GTM Community Template Gallery

1. Open your **Google Tag Manager** container
2. Navigate to **Templates** → **Tag Templates**
3. Search for **"Contentsquare - Dynamic Variables"**
4. Click on the template and select **Add to Workspace**
5. Review and accept the terms of service
6. Click **Save**

### Method 2: Manual Installation

1. Copy the contents of `template.tpl`
2. In GTM, go to **Templates** → **Tag Templates**
3. Click **Create Tag Template**
4. Paste the template code
5. Click **Save**

## Configuration

### Basic Setup

1. **Create a New Tag**:
   - Go to **Tags** in your GTM container
   - Click **New** to create a new tag
   - Select **Contentsquare - Dynamic Variables** as the tag type

2. **Define Dynamic Variables**:
   - Click **Add New Dynamic Variable** to add a row
   - Fill in the following fields for each variable:
     - **Key**: The variable identifier (max 512 characters)
     - **Value**: The variable value (max 255 characters)
     - **Type**: Select either `String` or `Number`

3. **Configure Trigger**:
   - Select an appropriate trigger (e.g., Page View, Event)
   - Configure trigger conditions as needed

4. **Save and Publish**:
   - Click **Save** to save the tag
   - Publish your container changes

### Example Configuration

```
Key: "user_segment"
Value: "premium"
Type: String

Key: "checkout_step"
Value: "3"
Type: Number

Key: "product_category"
Value: "electronics"
Type: String
```

## Variable Parameters

| Parameter | Type | Max Length | Required | Description |
|-----------|------|-----------|----------|-------------|
| **Key** | Text | 512 chars | Yes | Unique identifier for the variable (must be unique within the variable set) |
| **Value** | Text | 255 chars | Yes | The data value to send |
| **Type** | Select | - | Yes | Data type: `Number` (0-4294967296) or `String` |

## Usage Guidelines

### Best Practices

- **One Variable Per Action**: It's recommended to define only one variable per tag and create separate tags/rules for each action to send the relevant variable
- **Unique Keys**: Use descriptive, unique key names to avoid overwriting data
  - ❌ `var1`, `var2`, `var3`
  - ✅ `user_segment`, `checkout_step`, `product_category`
- **Type Matching**: Ensure numeric values are sent as `Number` type for proper tracking
- **Variable Limits**: Be aware that only the first 40 unique keys per pageview will be recorded

### Important Notes

- **Key Deduplication**: If you send the same key multiple times, only the last value associated with that key will be recorded
- **Numeric Conversion**: When using the `Number` type, values are automatically converted to numeric format. Invalid numeric values will default to 0
- **Value Encoding**: Special characters in values are handled by Contentsquare's platform

## How It Works

The template uses GTM's `createQueue` function to push data to Contentsquare's `_uxa` global variable:

```javascript
_uxaPush(["trackDynamicVariable", { key: key, value: value }]);
```

Each dynamic variable is processed and sent individually to Contentsquare's tracking system, where it's associated with the current user session and pageview.

## Troubleshooting

### Variables Not Appearing in Contentsquare

1. **Verify GTM Installation**: Ensure the Contentsquare GTM container is properly installed on your website
2. **Check the Container Version**: Publish your GTM container and wait a few minutes for changes to propagate
3. **Inspect Browser Console**: Use GTM's preview mode to verify the tag is firing
4. **Validate Data Layer**: Confirm that any variables referenced in the tag values are available in your data layer

### Numeric Type Issues

- Ensure numeric values don't exceed the maximum (4294967296)
- Remove any non-numeric characters from Number type values
- Test numeric values in GTM's Preview Mode to see actual values being sent

### More Than 40 Variables

- The platform limits to 40 unique keys per pageview
- Prioritize which variables are most important to your analysis
- Consider splitting variables across multiple tags on different triggers

## Documentation

- **Contentsquare Documentation**: [https://docs.contentsquare.com/uxa-en/](https://docs.contentsquare.com/uxa-en/)
- **GTM Documentation**: [https://support.google.com/tagmanager/](https://support.google.com/tagmanager/)
- **Google Tag Manager Community Templates**: [https://tagmanager.google.com/gallery/](https://tagmanager.google.com/gallery/)

## Technical Details

- **Template Type**: Tag
- **Container Context**: Web
- **Brand**: Contentsquare
- **License**: Apache 2.0
- **Developer**: Uri Gobey @ Contentsquare
- **Status**: Production Ready

## Requirements

- **Google Tag Manager**: Active GTM container
- **Contentsquare**: Active Contentsquare account and UXA implementation on your website
- **Permissions**: GTM tag administrator access

## License

This template is licensed under the Apache License 2.0. See the [LICENSE](LICENSE) file for details.

## Support & Feedback

For support or to report issues:

1. Check the [Contentsquare Documentation](https://docs.contentsquare.com/uxa-en/)
2. Review [GTM Community Template Guidelines](https://developers.google.com/tag-manager/gallery-tos)
3. Contact your Contentsquare account manager

## Version History

### v1.0.0 (Initial Release)
- First version of Contentsquare Dynamic Variables template
- Support for string and numeric variable types
- Up to 40 unique variables per pageview

## Related Templates

- Contentsquare Events Tag
- Contentsquare E-commerce Analytics
- Google Analytics 4 with Contentsquare Integration

---

**Last Updated**: 2026  
**Maintained By**: Contentsquare Professional Services