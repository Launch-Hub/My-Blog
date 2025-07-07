# React Custom Utility Hooks

## 🔁 1. `useDebounce`

Delays a value update until after a specified delay (useful for input, search, etc.)

```ts
import { useEffect, useState } from 'react';

export function useDebounceT(value T, delay number) T {
  const [debouncedValue, setDebouncedValue] = useStateT(value);

  useEffect(() = {
    const handler = setTimeout(() = setDebouncedValue(value), delay);
    return () = clearTimeout(handler);
  }, [value, delay]);

  return debouncedValue;
}
```

---

## 🕓 2. `useThrottle`

Ensures a value only updates at most once per interval.

```ts
import { useEffect, useState } from 'react';

export function useThrottleT(value T, limit number) T {
  const [throttledValue, setThrottledValue] = useStateT(value);
  const [lastExecuted, setLastExecuted] = useStatenumber(Date.now());

  useEffect(() = {
    const now = Date.now();
    const remaining = limit - (now - lastExecuted);

    if (remaining = 0) {
      setThrottledValue(value);
      setLastExecuted(now);
    } else {
      const timer = setTimeout(() = {
        setThrottledValue(value);
        setLastExecuted(Date.now());
      }, remaining);
      return () = clearTimeout(timer);
    }
  }, [value, limit, lastExecuted]);

  return throttledValue;
}
```

---

## 🔙 3. `usePrevious`

Captures the previous value of a variable.

```ts
import { useEffect, useRef } from 'react';

export function usePreviousT(value T) T  undefined {
  const ref = useRefT();

  useEffect(() = {
    ref.current = value;
  }, [value]);

  return ref.current;
}
```

---

## 💾 4. `useLocalStorage`

Synced local storage state (with JSON support).

```ts
import { useState, useEffect } from 'react';

export function useLocalStorageT(key string, initialValue T) {
  const [storedValue, setStoredValue] = useStateT(() = {
    if (typeof window === 'undefined') return initialValue;
    try {
      const item = window.localStorage.getItem(key);
      return item  (JSON.parse(item) as T)  initialValue;
    } catch {
      return initialValue;
    }
  });

  useEffect(() = {
    try {
      window.localStorage.setItem(key, JSON.stringify(storedValue));
    } catch {}
  }, [key, storedValue]);

  return [storedValue, setStoredValue] as const;
}
```

---

## 🧠 Would you like to proceed with the next group

The next hooks I can provide are

 `useSessionStorage`
 `useEventListener`
 `useOnClickOutside`
 `useToggle`
 `useInterval`
 `useTimeout`
 `useCopyToClipboard`
 `useMediaQuery`

Please confirm if you'd like all of them, or specify a few.
