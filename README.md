# DataLayer Implementation Specifications
## Park Avenue Auto Group Dealership Websites

This document outlines the dataLayer implementation requirements for the following Park Avenue Auto Group dealership websites:

- Park Avenue BMW
- MINI Brossard
- BMW Sainte-Julie
- Park Avenue Volvo
- Park Avenue Audi
- Mercedes-Benz Silver Star
- Park Avenue Lexus

## Introduction

This document provides specifications for implementing a standardized dataLayer across all dealership websites to ensure consistent event tracking and analytics. The implementation will support Google Tag Manager (GTM) and Google Analytics 4 (GA4).

## Important Notes for Development Team

1. **Existing Implementations**: We acknowledge that some websites may already have dataLayer implementations in place. If naming conventions differ from those specified in this document, please communicate these differences so we can adapt our GTM configuration accordingly.

2. **Consistent Structure**: While maintaining flexibility with existing implementations, we aim to standardize the tracking structure across all seven websites.

3. **Implementation Status**: All events listed in this document are currently marked as "A faire" (To do).

## DataLayer Implementation

### Initial DataLayer Setup

Include the following code at the top of every page (ideally in the `<head>` section before the GTM container):

```javascript
window.dataLayer = window.dataLayer || [];
```

### Event Tracking Specifications

Below are the detailed specifications for each event that needs to be tracked across all dealership websites:

---

#### 1. Vehicle Detail View

**Event Details:**
- **Trigger**: Page load of a Vehicle Detail Page (VDP)
- **GA4 Event Name**: `vehicle_detail_view`
- **GTM Tag Name**: `GA4 - vehicle_detail_view`
- **Conversion**: No

**DataLayer Implementation:**
```javascript
window.dataLayer = window.dataLayer || [];
window.dataLayer.push({
  event: 'vehicle_detail_view',
  pageType: 'VDP',
  vehicleId: '[VEHICLE_ID]',  // e.g., '12345'
  vehicleModel: '[MODEL]',    // e.g., 'XC60', 'X5', etc.
  vehicleMake: '[MAKE]',      // e.g., 'BMW', 'Volvo', etc.
  vehicleYear: '[YEAR]',      // e.g., '2023'
  vehiclePrice: '[PRICE]',    // e.g., '65000'
  vehicleType: '[TYPE]',      // e.g., 'New', 'Used'
  vehicleTrim: '[TRIM]'       // e.g., 'Momentum', 'M Sport'
});
```

---

#### 2. Special Offer View

**Event Details:**
- **Trigger**: Page load of an Offers Page
- **GA4 Event Name**: `special_offer_view`
- **GTM Tag Name**: `GA4 - special_offer_view`
- **Conversion**: No

**DataLayer Implementation:**
```javascript
window.dataLayer = window.dataLayer || [];
window.dataLayer.push({
  event: 'special_offer_view',
  pageType: 'offer',
  offerType: '[OFFER_TYPE]',    // e.g., 'Finance', 'Lease', 'Cash'
  offerModel: '[MODEL]',        // If applicable
  offerID: '[OFFER_ID]'         // If available
});
```

---

#### 3. Click to Call

**Event Details:**
- **Trigger**: User clicks on a phone number link
- **GA4 Event Name**: `click_to_call`
- **GTM Tag Name**: `GA4 - click_to_call`
- **Conversion**: No

**DataLayer Implementation:**
```javascript
window.dataLayer = window.dataLayer || [];
window.dataLayer.push({
  event: 'click_to_call',
  phoneNumber: '[PHONE_NUMBER]',  // e.g., '5141234567'
  departmentName: '[DEPARTMENT]',  // e.g., 'Sales', 'Service', 'Parts'
  pageLocation: '[PAGE_TYPE]'     // e.g., 'VDP', 'Homepage', 'Contact'
});
```

---

#### 4. SMS Opt-in Form Submit

**Event Details:**
- **Trigger**: User submits a form to receive SMS follow-up
- **GA4 Event Name**: `form_submit_sms_optin`
- **GTM Tag Name**: `GA4 - form_submit_sms_optin`
- **Conversion**: Yes

**DataLayer Implementation:**
```javascript
window.dataLayer = window.dataLayer || [];
window.dataLayer.push({
  event: 'form_submit_sms_optin',
  formType: 'sms_optin',
  formLocation: '[LOCATION]',    // e.g., 'popup', 'sidebar', 'footer'
  vehicleId: '[VEHICLE_ID]',     // If form is on a VDP
  vehicleModel: '[MODEL]'        // If form is on a VDP
});
```

---

#### 5. Quote Request Form Submit

**Event Details:**
- **Trigger**: User submits a quote request form
- **GA4 Event Name**: `form_submit_quote`
- **GTM Tag Name**: `GA4 - form_submit_quote`
- **Conversion**: Yes

**DataLayer Implementation:**
```javascript
window.dataLayer = window.dataLayer || [];
window.dataLayer.push({
  event: 'form_submit',
  formType: 'quote',
  vehicleId: '[VEHICLE_ID]',       // If applicable
  vehicleModel: '[MODEL]',         // If applicable
  vehicleMake: '[MAKE]',           // If applicable
  vehicleYear: '[YEAR]',           // If applicable
  vehiclePrice: '[PRICE]',         // If applicable
  quoteType: '[QUOTE_TYPE]'        // e.g., 'Finance', 'Lease', 'Cash'
});
```

---

#### 6. Test Drive Request Form Submit

**Event Details:**
- **Trigger**: User submits a test drive request form
- **GA4 Event Name**: `form_submit_test_drive`
- **GTM Tag Name**: `GA4 - form_submit_test_drive`
- **Conversion**: Yes

**DataLayer Implementation:**
```javascript
window.dataLayer = window.dataLayer || [];
window.dataLayer.push({
  event: 'form_submit',
  formType: 'test_drive',
  vehicleId: '[VEHICLE_ID]',       // If applicable
  vehicleModel: '[MODEL]',         // If applicable
  vehicleMake: '[MAKE]',           // If applicable
  vehicleYear: '[YEAR]',           // If applicable
  preferredDate: '[DATE]',         // Optional
  preferredTime: '[TIME]'          // Optional
});
```

---

#### 7. Special Offer Form Submit

**Event Details:**
- **Trigger**: User submits a form related to a special offer
- **GA4 Event Name**: `form_submit_special_offer`
- **GTM Tag Name**: `GA4 - form_submit_special_offer`
- **Conversion**: Yes

**DataLayer Implementation:**
```javascript
window.dataLayer = window.dataLayer || [];
window.dataLayer.push({
  event: 'form_submit',
  formType: 'special_offer',
  offerId: '[OFFER_ID]',           // If available
  offerType: '[OFFER_TYPE]',       // e.g., 'Finance', 'Lease', 'Cash'
  offerModel: '[MODEL]',           // If applicable
  offerMake: '[MAKE]'              // If applicable
});
```

---

#### 8. Contact Form Submit

**Event Details:**
- **Trigger**: User submits a general contact form
- **GA4 Event Name**: `form_submit_contact`
- **GTM Tag Name**: `GA4 - form_submit_contact`
- **Conversion**: Yes

**DataLayer Implementation:**
```javascript
window.dataLayer = window.dataLayer || [];
window.dataLayer.push({
  event: 'form_submit',
  formType: 'contact',
  message: '[INQUIRY_TYPE]',       // e.g., 'general_inquiry', 'feedback', etc.
  department: '[DEPARTMENT]'       // e.g., 'Sales', 'Service', 'Parts', etc.
});
```

---

#### 9. Trade-In Appraisal Form Submit

**Event Details:**
- **Trigger**: User submits a trade-in appraisal form
- **GA4 Event Name**: `form_submit_trade_in`
- **GTM Tag Name**: `GA4 - form_submit_trade_in`
- **Conversion**: Yes

**DataLayer Implementation:**
```javascript
window.dataLayer = window.dataLayer || [];
window.dataLayer.push({
  event: 'form_submit',
  formType: 'trade_in',
  vehicleOwned: '[VEHICLE_OWNED]',  // e.g., '2019 XC40'
  vehicleOwnedMake: '[MAKE]',       // e.g., 'BMW', 'Volvo'
  vehicleOwnedModel: '[MODEL]',     // e.g., 'X5', 'XC60'
  vehicleOwnedYear: '[YEAR]',       // e.g., '2019'
  vehicleOwnedMileage: '[MILEAGE]'  // If available
});
```

---

#### 10. Finance Application Form Submit

**Event Details:**
- **Trigger**: User submits a finance application
- **GA4 Event Name**: `form_submit_finance`
- **GTM Tag Name**: `GA4 - form_submit_finance`
- **Conversion**: Yes

**DataLayer Implementation:**
```javascript
window.dataLayer = window.dataLayer || [];
window.dataLayer.push({
  event: 'form_submit',
  formType: 'finance',
  financeType: '[FINANCE_TYPE]',    // e.g., 'Lease', 'Loan'
  vehicleId: '[VEHICLE_ID]',        // If applicable
  vehicleModel: '[MODEL]',          // If applicable
  vehicleMake: '[MAKE]',            // If applicable
  vehiclePrice: '[PRICE]'           // If applicable
});
```

---

#### 11. Service Appointment Form Submit

**Event Details:**
- **Trigger**: User submits a service appointment booking form
- **GA4 Event Name**: `form_submit_service`
- **GTM Tag Name**: `GA4 - form_submit_service`
- **Conversion**: Yes

**DataLayer Implementation:**
```javascript
window.dataLayer = window.dataLayer || [];
window.dataLayer.push({
  event: 'form_submit',
  formType: 'service',
  serviceType: '[SERVICE_TYPE]',     // e.g., 'Oil Change', 'Maintenance', 'Repair'
  vehicleOwned: '[VEHICLE_OWNED]',   // If provided
  preferredDate: '[DATE]',           // If provided
  preferredTime: '[TIME]'            // If provided
});
```

## Additional Technical Requirements

### Form Submission Tracking

For all form submissions, ensure the dataLayer push is triggered:
- After successful validation
- Before the form redirects to a thank you page
- OR on successful AJAX submission

### iFrame Form Handling

Some forms on the dealership websites are embedded within iFrames. For these forms:

1. **Cross-domain messaging**: Implement a cross-domain messaging solution using `postMessage()` to communicate form submission events from the iFrame to the parent window.

```javascript
// Inside the iFrame (form provider's domain)
// When form is successfully submitted
parent.postMessage({
  event: 'form_submit',
  formType: '[FORM_TYPE]',  // Same parameters as defined in the main specs
  // Additional form data...
}, 'https://parentdomain.com');  // Replace with actual parent domain
```

2. **Parent window listener**: Add an event listener in the parent window to capture these messages:

```javascript
// In the parent window (dealership website)
window.addEventListener('message', function(event) {
  // Verify message origin for security
  if (event.origin !== 'https://formproviderdomain.com') return;
  
  // Check if this is a form submission event
  if (event.data && event.data.event) {
    // Push to dataLayer
    window.dataLayer = window.dataLayer || [];
    window.dataLayer.push(event.data);
  }
}, false);
```

3. **Alternative approach**: If direct code modification of the iFrame is not possible, coordinate with the form provider to implement a callback function that can be triggered upon form submission, which then pushes the appropriate event to the dataLayer.

### Error Handling

Consider implementing error tracking for forms:
```javascript
window.dataLayer = window.dataLayer || [];
window.dataLayer.push({
  event: 'form_error',
  formType: '[FORM_TYPE]',
  errorMessage: '[ERROR_MESSAGE]'
});
```

### Cross-Domain Tracking

If the websites have separate domains or subdomains that users navigate between, ensure proper cross-domain tracking is maintained.

## Implementation Timeline

Please implement these dataLayer events on all seven dealership websites by [INSERT_DEADLINE]. 

## Questions and Support

For any questions regarding these specifications or technical assistance during implementation, please contact:

[INSERT_CONTACT_INFORMATION]

## Change Log

| Date | Version | Description |
|------|---------|-------------|
| [INSERT_DATE] | 1.0 | Initial specification document |
