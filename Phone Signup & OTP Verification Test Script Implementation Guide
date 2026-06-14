# Phone Signup & OTP Verification Test Script Implementation Guide

## Purpose

This document explains how testing can be implemented for the Phone Signup and OTP Verification flow in the MyClickBook application.

The goal is to ensure that users can successfully:

1. Enter their name and phone number.
2. Request an OTP.
3. Verify the OTP.
4. Continue to the next screen after successful verification.

---

# Existing Testing Setup

The project already uses:

| Tool                         | Purpose                                  |
| ---------------------------- | ---------------------------------------- |
| Jest                         | Test runner                              |
| React Native Testing Library | Render screens and simulate user actions |
| jest-expo                    | Expo testing support                     |
| Mock Functions               | Simulate navigation and APIs             |

Current test files are stored inside:

```text
ScreenTests/
```

Examples:

```text
ScreenTests/NewUserSignUp.test.tsx
ScreenTests/PhoneSignUp.test.tsx
```

---

# How Existing Tests Work

Most existing tests follow this flow:

```mermaid
flowchart LR
A[Render Screen] --> B[Find UI Elements]
B --> C[Simulate User Action]
C --> D[Verify Expected Result]
```

Example:

1. Render screen.
2. Find input field.
3. Type value.
4. Verify screen updates correctly.

---

# Phone Signup Testing

## What Should Be Tested?

### 1. Screen Rendering

Verify that the following are visible:

* Name input field
* Phone number input field
* Country code selector
* Get OTP button

---

### 2. User Input

Verify that:

* User can enter name.
* User can enter phone number.
* Values appear correctly.

---

### 3. Validation

Verify error messages appear when:

* Name is empty.
* Phone number is empty.
* Phone number is less than 10 digits.

Example:

```text
Please enter a valid phone number
```

---

### 4. Button State

Verify:

* Button remains disabled for invalid input.
* Button becomes enabled when valid data is entered.

---

### 5. OTP Request

Verify:

* Loading indicator appears.
* OTP process starts.
* Navigation occurs correctly.

---

## Phone Signup Test Flow

```mermaid
flowchart LR
A[Open Phone Signup Screen]
--> B[Enter Name]
--> C[Enter Phone Number]
--> D[Press Get OTP]
--> E[Loading State]
--> F[Navigate To OTP Screen]
```

---

# OTP Verification Testing

## What Should Be Tested?

### 1. Screen Rendering

Verify:

* OTP screen loads.
* OTP input boxes appear.
* Verify button appears.

---

### 2. OTP Input

Verify:

* User can enter OTP digits.
* Input accepts values correctly.

---

### 3. Validation

Verify:

* Empty OTP is rejected.
* Incorrect OTP shows error.

Example:

```text
Incorrect OTP. Please try again.
```

---

### 4. Successful Verification

Verify:

* Correct OTP is accepted.
* User is navigated to next screen.

---

### 5. Failed Verification

Verify:

* Wrong OTP shows error.
* Attempt counter works correctly.

---

### 6. Resend OTP

Verify:

* Countdown timer starts.
* Resend button becomes active.
* Timer resets after resend.

---

# OTP Verification Flow

```mermaid
flowchart LR
A[Enter OTP]
--> B[Press Verify]
--> C{OTP Correct?}

C -->|Yes| D[Navigate To Home Screen]

C -->|No| E[Show Error Message]
```

---

# Mocking Strategy

## Why Mocking Is Needed

Tests should run without:

* Real API calls
* Real SMS delivery
* Real Firebase requests

Instead, we simulate responses.

---

## Navigation Mock

Used to verify screen navigation.

```text
User clicks button
↓
Navigation function called
↓
Test verifies correct screen opened
```

---

## API Mock

Instead of sending a real OTP:

```text
Request OTP
↓
Return Mock Success Response
↓
Continue Test
```

---

## OTP Mock

Example:

```text
1234 → Success

0000 → Failure
```

This allows testing both success and error scenarios.

---

# Recommended Test Files

```text
ScreenTests/
│
├── PhoneSignUp.test.tsx
│
└── OtpForSignup.test.tsx
```

---

# Implementation Approach

## Step 1

Create Phone Signup test file.

Test:

* Screen rendering
* Input fields
* Validation
* Button states
* OTP request flow

---

## Step 2

Create OTP Verification test file.

Test:

* OTP entry
* Validation
* Success flow
* Failure flow
* Resend OTP

---

## Step 3

Mock:

* Navigation
* OTP service
* API responses

---

# Tools Used

| Tool                         | Purpose                            |
| ---------------------------- | ---------------------------------- |
| Jest                         | Run tests                          |
| React Native Testing Library | Simulate user interaction          |
| jest-expo                    | Expo testing support               |
| Mock Functions               | Simulate APIs and navigation       |
| Fake Timers                  | Simulate OTP delays and countdowns |

---

# Final Recommendation

The Phone Signup and OTP Verification flow should be tested separately.

Phone Signup tests should focus on:

* Input validation
* Button behavior
* OTP request flow

OTP Verification tests should focus on:

* OTP validation
* Success and failure scenarios
* Resend OTP functionality

Following the existing project testing pattern will keep the implementation consistent, maintainable, and easy to extend in future releases.
