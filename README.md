# Contents
* [The package](#react-native-countdown-timer)
* [Installation](#installation)
* [Usage](#usage)
* [Examples](#examples)
* [License](#license)
* [Pull Requests](#pull)

# react-native-countdown-timer

[![npm version](https://badge.fury.io/js/react-native-countdown-timer.svg)](https://www.npmjs.com/package/react-native-countdown-timer)
[![npm](https://img.shields.io/npm/dm/react-native-countdown-timer.svg)]()

<i>react-native-countdown-timer</i> is a small library that provides a custom countdown timer 
component which is created using a custom hook. All you have to do is pass a timestamp(as total number of seconds) to it and it will calculate the total number of days, hours, minutes and seconds automatically.

It also supports a callback function which you can utilize to let the use know when the timer is over. You can also give a option to user to reset the timer using this function <i>refTimer.current.resetTimer()</i>.

<b>NOTE :</b> The pin code input is not part of this library. You can install it from this package:-
(https://www.npmjs.com/package/react-native-pin-code)

<p float="left">
  <img src="https://raw.githubusercontent.com/shubhambathe1/react-native-countdown-timer/development/screenshots/screenshot1.png" width="280" height="600" alt="screenshot1.png" />
  <img src="https://raw.githubusercontent.com/shubhambathe1/react-native-countdown-timer/development/screenshots/screenshot2.png" width="280" height="600" alt="screenshot2.png" /> 
</p>

```javascript
// packages
import React, { useEffect } from 'react';
import { StyleSheet, Text, View, Dimensions } from 'react-native';
import CountDownTimer from 'react-native-countdown-timer';

function App() {
  // Timer References
  const refTimer = useRef();

  // For keeping a track on the Timer
  const [timerEnd, setTimerEnd] = useState(false);

  const timerCallbackFunc = (timerFlag) => {
    // Setting timer flag to finished
    setTimerEnd(timerFlag);
    console.warn('You can alert the user by letting him know that Timer is out.');
  };

  return (
    <View style={styles.container}>
      <View style={{ display: timerEnd ? 'none' : 'flex' }}>
        <CountDownTimer
          ref={refTimer}
          timestamp={120}
          timerCallback={timerCallbackFunc}
          containerStyle={{
            height: 56,
            width: 120,
            backgroundColor: '#FFFFFF',
          }}
          textStyle={{
            fontSize: 15,
            color: 'gray,
            fontWeight: '500',
            letterSpacing: 0.25,
          }}
        />
      </View>
      <TouchableOpacity
        style={{ display: timerEnd ? 'flex' : 'none' }}
        onPress={() => {
          setTimerEnd(false);
          refTimer.current.resetTimer();
        }}
      >
        <Text style={styles.resendLabel}>{appStrings.LABEL_RESEND}</Text>
      </TouchableOpacity>
    </View>
  );
}

export default App;
```

# Installation

`npm i react-native-countdown-timer`

OR

`yarn add react-native-countdown-timer`

Note: Linking and Pod install not needed.

# Usage

# Updates 🚀

### Props

| Name             | Type       | Default                                      | Description                                                                                                                                                                                       |
| ---------------- | ---------- | -------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| timestamp        | `number`   | required                                     | Total number of seconds to be passed to the timer component. Example:- passing {60} seconds will give timestamp of 01:00 minutes to the timer                                                             |
| timerCallback    | `function` | `void`                                       | Called when the Timer countdown ends. This is a function where you can alert the user that the timer has ended.                            |                                                                                                                                             
| containerStyle   | `style`    | { backgroundColor: 'rgba(0, 0, 0, .2)' }     | Style of Timer Component Container dots                                                                                                                                                                 |
| textStyle        | `style`    | { fontSize: 15, fontWeight: '600', color: 'rgba(0, 0, 0, .2)' }  | Style of Timer Component Text dots                                                                                                                                                                 |

# Examples

You can find a working example of this over the [related example repository] soon ;-)

# License

MIT

# Pull

Pull requests are welcome! Please make the PR to `development` branch though and not `master`. Thanks.
