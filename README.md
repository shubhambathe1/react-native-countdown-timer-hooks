# Contents

- [The package](#react-native-countdown-timer-hooks)
- [Installation](#installation)
- [Usage](#usage)
- [Examples](#examples)
- [License](#license)
- [Pull Requests](#pull)

# react-native-countdown-timer-hooks

[![npm version](https://badge.fury.io/js/react-native-countdown-timer-hooks.svg)](https://www.npmjs.com/package/react-native-countdown-timer-hooks)
[![npm](https://img.shields.io/npm/dm/react-native-countdown-timer-hooks.svg)]()

<i>react-native-countdown-timer-hooks</i> is a small library that provides a custom countdown timer
component which is created using a custom hook. All you have to do is pass a timestamp(as total number of seconds) to it and it will calculate the total number of days, hours, minutes and seconds automatically.

It also supports a callback function which you can utilize to let the use know when the timer is over. You can also give a option to user to reset the timer using this function <i>refTimer.current.resetTimer()</i>.

<b>NOTE :</b> The pin code input is not part of this library. You can install it from this package:-
[react-native-pin-code](https://www.npmjs.com/package/react-native-pin-code)

<p float="left">
  <img src="https://raw.githubusercontent.com/shubhambathe1/react-native-countdown-timer-hooks/master/screenshots/screenshot1.png" width="280" height="600" alt="screenshot1.png" hspace="50" />
  <img src="https://raw.githubusercontent.com/shubhambathe1/react-native-countdown-timer-hooks/master/screenshots/screenshot2.png" width="280" height="600" alt="screenshot2.png" hspace="50" /> 
</p>

```javascript
/**
 * CountdownTimerApp Functional Component
 */

import React, { useRef, useState } from "react";
import { StyleSheet, Text, TouchableOpacity, View } from "react-native";
import CountDownTimer from "react-native-countdown-timer-hooks";

function CountdownTimerApp() {
  // Timer References
  const refTimer = useRef();

  // For keeping a track of the timer
  const [timerEnd, setTimerEnd] = useState(false);

  const timerOnProgressFunc = (remainingTimeInSecs) => {
    console.log("On Progress tracker :", remainingTimeInSecs);
  };

  const timerCallbackFunc = (timerFlag) => {
    // Setting timer flag to false once complete
    setTimerEnd(timerFlag);
    console.warn("Alert the user when timer runs out...");
  };

  return (
    <View style={styles.container}>
      <View style={{ display: timerEnd ? "none" : "flex" }}>
        <CountDownTimer
          ref={refTimer}
          timestamp={120}
          timerOnProgress={timerOnProgressFunc}
          timerCallback={timerCallbackFunc}
          containerStyle={styles.timerContainerStyle}
          textStyle={styles.timerTextStyle}
        />
      </View>
      <TouchableOpacity
        style={[
          {
            display: timerEnd ? "flex" : "none",
          },
          styles.touchableOpacityStyle,
        ]}
        onPress={() => {
          setTimerEnd(false);
          refTimer.current.resetTimer();
        }}
      >
        <Text style={styles.touchableOpacityTextStyle}>Resend</Text>
      </TouchableOpacity>
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: "center",
    alignItems: "center",
  },
  timerContainerStyle: {
    height: 56,
    width: 120,
    justifyContent: "center",
    alignItems: "center",
    borderRadius: 35,
    backgroundColor: "#2196f3",
  },
  timerTextStyle: {
    fontSize: 25,
    color: "#FFFFFF",
    fontWeight: "500",
    letterSpacing: 0.25,
  },
  touchableOpacityStyle: {
    height: 56,
    width: 120,
    justifyContent: "center",
    alignItems: "center",
    borderRadius: 35,
    backgroundColor: "#512da8",
  },
  touchableOpacityTextStyle: {
    fontSize: 18,
    color: "#FFFFFF",
    fontWeight: "bold",
  },
});

export default CountdownTimerApp;
```

# Installation

`npm i react-native-countdown-timer-hooks`

OR

`yarn add react-native-countdown-timer-hooks`

Note: Linking and Pod install not needed.

# Usage

# Updates 🚀

Added demo project for more details on usage. Checkout the [Examples](#examples) sections.

### Props

| Name            | Type       | Default                                                         | Description                                                                                                                                   |
| --------------- | ---------- | --------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| timestamp       | `number`   | required                                                        | Total number of seconds to be passed to the timer component. Example:- passing {60} seconds will give timestamp of 01:00 minutes to the timer |
| timerCallback   | `function` | `void`                                                          | Callback when the timer countdown ends. This is a function where you can alert the user that the timer has ended.                             |
| timerOnProgress | `function` | `void`                                                          | Callback for the timer countdown progress. You can keep track on the progress of timer countdown by remaining seconds.                        |
| containerStyle  | `style`    | { backgroundColor: 'rgba(0, 0, 0, .2)' }                        | Style of Timer Component Container dots                                                                                                       |
| textStyle       | `style`    | { fontSize: 15, fontWeight: '600', color: 'rgba(0, 0, 0, .2)' } | Style of Timer Component Text dots                                                                                                            |

# Examples

You can find a working example of this over the [related example repository](https://github.com/shubhambathe1/CountDownTimerDemo)

# License

MIT

# Pull

Pull requests are welcome! Please make the PR to `dev` branch though and not `master`. Thanks.
