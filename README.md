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
import {
  widthPercentageToDP,
  heightPercentageToDP,
  listenOrientationChange as lor,
  removeOrientationListener as rol,
} from 'react-native-responsive-screen-hooks';

function App() {

  // TODO: Add a useState for monitoring the orientation of screen
  const [orientation, setOrientation] = React.useState('portrait');

  return (
    <View style={{styles.container}}>
      <View style={{ display: timerEnd ? 'none' : 'flex' }}>
        
        <CountDownTimer
          ref={refTimer}
          timestamp={120}
          timerCallback={timerCallbackFunc}
          containerStyle={styles.countdownTimerContainer}
          textStyle={styles.countdownTimerText}
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

### Smartphones
<img src="https://cdn-images-1.medium.com/max/800/1*aoIGDVNrcvIw_4NRqRtHTA.png" />
<img src="https://cdn-images-1.medium.com/max/800/1*Yl9k-Lxg9jxJ9g00qmRlIA.png" />
<img src="https://cdn-images-1.medium.com/max/800/1*rE43O18nt4_ECUvXr_fSZA.png" />

# License

MIT

# Pull

Pull requests are welcome! Please make the PR to `development` branch though and not `master`. Thanks.
