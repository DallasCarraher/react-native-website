---
id: version-0.20-timepickerandroid
title: TimePickerAndroid
original_id: timepickerandroid
---

Opens the standard Android time picker dialog.

### Example

```
try {
  const {action, hour, minute} = await TimePickerAndroid.open({
    hour: 14,
    minute: 0,
    is24Hour: false, // Will display '2 PM'
  });
  if (action !== DatePickerAndroid.dismissedAction) {
    // Selected hour (0-23), minute (0-59)
  }
} catch ({code, message}) {
  console.warn('Cannot open time picker', message);
}
```

### Methods

- [`open`](timepickerandroid.md#open)
- [`timeSetAction`](timepickerandroid.md#timesetaction)
- [`dismissedAction`](timepickerandroid.md#dismissedaction)

---

# Reference

## Methods

### `open()`

```jsx
static open(options)
```

Opens the standard Android time picker dialog.

The available keys for the `options` object are:

- `hour` (0-23) - the hour to show, defaults to the current time
- `minute` (0-59) - the minute to show, defaults to the current time
- `is24Hour` (boolean) - If `true`, the picker uses the 24-hour format. If `false`, the picker shows an AM/PM chooser. If undefined, the default for the current locale is used.

Returns a Promise which will be invoked an object containing `action`, `hour` (0-23), `minute` (0-59) if the user picked a time. If the user dismissed the dialog, the Promise will still be resolved with action being `TimePickerAndroid.dismissedAction` and all the other keys being undefined. **Always** check whether the `action` before reading the values.

---

### `timeSetAction()`

```jsx
static timeSetAction()
```

A time has been selected.

---

### `dismissedAction()`

```jsx
static dismissedAction()
```

The dialog has been dismissed.
