# Firebase Transaction Race Condition
This repository demonstrates a common race condition issue when using Firebase Realtime Database transactions to increment a counter. The incorrect implementation shows how concurrent updates can lead to inaccurate results, while the corrected version provides a robust solution. 

## Problem
Multiple clients concurrently attempting to increment a counter using `on('value', ...)` and `transaction()` will likely lead to incorrect counter updates. The asynchronous nature of the Firebase Realtime Database allows multiple transactions to occur simultaneously, causing the final value to deviate from the expected sum of increments.

## Solution
The solution uses a more robust approach that ensures atomicity. By always basing updates on the current value, the code prevents race conditions.