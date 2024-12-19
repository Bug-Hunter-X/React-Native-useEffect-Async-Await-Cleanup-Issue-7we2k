# React Native useEffect Async/Await Cleanup Issue

This repository demonstrates a common error in React Native applications involving the `useEffect` hook with asynchronous operations. The example showcases incorrect cleanup handling within `useEffect` when using `async/await`, potentially leading to memory leaks and unexpected behavior.

## Bug Description

The bug arises from the improper management of the asynchronous `fetch` call within the `useEffect` hook. When the component unmounts, the `fetch` operation might still be in progress, causing issues such as memory leaks and race conditions. The cleanup function provided to `useEffect` is not effectively cancelling or aborting the ongoing `fetch` request. 

## Solution

The solution addresses this problem by implementing a proper cleanup mechanism.  The `fetch` call is assigned to a variable that is accessible within the cleanup function so that we can terminate the `fetch` operation using `AbortController`. This ensures that the asynchronous operation is stopped cleanly when the component unmounts, preventing potential issues.