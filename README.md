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

# Examples

You can find a working example of this over the [related example repository](https://github.com/shubhambathe1/react-native-responsive-screen-hooks/tree/master/examples/responsive-screen/README.md)

# License

MIT

# Pull

Pull requests are welcome! Please make the PR to `development` branch though and not `master`. Thanks.
