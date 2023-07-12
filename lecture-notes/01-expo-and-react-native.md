# 01: Expo and React Native

## Expo

## React Native

## Getting Started


### App.jsx

```js
import { StatusBar } from 'expo-status-bar';
import { StyleSheet, Text, View } from 'react-native';

export default function App() {
  return (
    <View style={styles.container}>
      <Text>Open up App.js to start working on your app!</Text>
      <StatusBar style="auto" />
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#fff',
    alignItems: 'center',
    justifyContent: 'center',
  },
});
```

Run the following command:

```bash
npm run android
```

You should see the following:

![](../resources/img/01/phone-1.png)

**Tasks:** 
- Convert `App` into an arrow function.
- Change the `backgroundColor`.
- Change the `Text` component's `color`. **Note:** Use the `style` prop.

### ImageViewer.jsx

In the `assets` directory, create a new directory called `imgs`. You have been given five Pokémon images. Put these images into the `imgs` directory.

In the root directory, create a new directory called `components`. In the `components` directory, create a new file called `ImageViewer.jsx`. Add the following code:

```jsx
import { StyleSheet, Image } from "react-native";

const ImageViewer = (props) => (
  <Image source={props.placeholderImgSrc} style={styles.image} />
);

const styles = StyleSheet.create({
  image: {
    width: 300,
    height: 300,
    backgroundColor: "#ffffff",
    borderRadius: 5,
  },
});

export default ImageViewer;
```

Update the `App.jsx` to the following:

```jsx
import { StatusBar } from "expo-status-bar";
import { StyleSheet, View } from "react-native";

import ImageViewer from "./components/ImageViewer";

const placeholderImg = require("./assets/imgs/pikachu.png");

const App = () => {
  return (
    <View style={styles.container}>
      <View style={styles.imageContainer}>
        <ImageViewer placeholderImgSrc={placeholderImg} />
      </View>
      <StatusBar style="auto" />
    </View>
  );
};

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: "#25292e",
    alignItems: "center",
  },
  imageContainer: {
    flex: 1,
    paddingTop: 50,
  },
});

export default App;
```

You should see the following:

![](../resources/img/01/phone-1.png)


### Button.jsx

In the `components` directory, create a new file called `Button.jsx`. Add the following code:

```jsx
import { StyleSheet, View, Pressable, Text } from "react-native";
import FontAwesome from "@expo/vector-icons/FontAwesome";

const Button = (props) => {
  if (props.theme === "primary") {
    return (
      <View
        style={[
          styles.buttonContainer,
          { borderWidth: 4, borderColor: "#ffd33d", borderRadius: 18 },
        ]}
      >
        <Pressable
          style={[styles.button, { backgroundColor: "#fff" }]}
          onPress={() => alert("Pikachu")}
        >
          <FontAwesome
            name="picture-o"
            size={18}
            color="#25292e"
            style={styles.buttonIcon}
          />
          <Text style={[styles.buttonLabel, { color: "#25292e" }]}>
            {props.label}
          </Text>
        </Pressable>
      </View>
    );
  }

  return (
    <View style={styles.buttonContainer}>
      <Pressable
        style={styles.button}
        onPress={() => alert("Pikachu")}
      >
        <Text style={styles.buttonLabel}>{props.label}</Text>
      </Pressable>
    </View>
  );
};

const styles = StyleSheet.create({
  buttonContainer: {
    width: 320,
    height: 68,
    marginHorizontal: 20,
    alignItems: "center",
    justifyContent: "center",
    padding: 3,
  },
  button: {
    borderRadius: 10,
    width: "100%",
    height: "100%",
    alignItems: "center",
    justifyContent: "center",
    flexDirection: "row",
  },
  buttonIcon: {
    paddingRight: 8,
  },
  buttonLabel: {
    color: "#fff",
    fontSize: 16,
  },
});

export default Button;
```

Update the `App.jsx` to the following:

```jsx
import { StatusBar } from "expo-status-bar";
import { StyleSheet, View } from "react-native";

import Button from "./components/Button";
import ImageViewer from "./components/ImageViewer";

const placeholderImg = require("./assets/imgs/pikachu.png");

const App = () => {
  return (
    <View style={styles.container}>
      <View style={styles.imageContainer}>
        <ImageViewer placeholderImgSrc={placeholderImg} />
      </View>
      <View style={styles.footerContainer}>
        <Button theme="primary" label="Choose a Pokémon" />
        <Button label="Use this Pokémon" />
      </View>
      <StatusBar style="auto" />
    </View>
  );
};

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: "#25292e",
    alignItems: "center",
  },
  imageContainer: {
    flex: 1,
    paddingTop: 50,
  },
  footerContainer: {
    flex: 1 / 3,
    alignItems: 'center',
  },
});

export default App;
```

You should see the following:

![](../resources/img/01/phone-2.png)

What happens when you click on the Choose a Pokémon or Use this Pokémon buttons?

![](../resources/img/01/phone-2.png)







