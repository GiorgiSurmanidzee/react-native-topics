## Animations

### There are two main ways to animate things:

### 🎨 1. Animations in React Native (built-in Animated API)
React Native comes with the Animated API, which lets you animate style values (opacity, position, scale, etc.).


### ⚡ 2. React Native Reanimated (Reanimated 2+)

react-native-reanimated is a powerful animation library built on the new JSI architecture, which makes animations run directly on the UI thread instead of the JS thread.
This means buttery-smooth 60fps animations even if your JS thread is busy. 🚀

### 🔹 Example: Move a Box with Gesture + Reanimated

```jsx
import React from "react";
import { View, StyleSheet } from "react-native";
import Animated, {
  useSharedValue,
  useAnimatedStyle,
  withSpring,
} from "react-native-reanimated";

export default function ReanimatedExample() {
  const offset = useSharedValue(0); // like useState but for animations

  const animatedStyles = useAnimatedStyle(() => {
    return {
      transform: [{ translateX: offset.value }],
    };
  });

  return (
    <View style={styles.container}>
      <Animated.View style={[styles.box, animatedStyles]} />
      <View style={{ marginTop: 50 }}>
        <View
          style={{ backgroundColor: "tomato", padding: 10 }}
          onTouchStart={() => {
            offset.value = withSpring(offset.value + 50); // smooth spring move
          }}
        >
          <View><Text style={{color:"white"}}>Move Right</Text></View>
        </View>
      </View>
    </View>
  );
}

const styles = StyleSheet.create({
  container: { flex: 1, justifyContent: "center", alignItems: "center" },
  box: { width: 100, height: 100, backgroundColor: "purple", borderRadius: 20 },
});
```

👉 Here’s what’s happening:

- ```useSharedValue``` → like useState but optimized for animations.

- ```useAnimatedStyle``` → styles that update when shared values change.

- ```withSpring``` → makes it move with physics-like spring animation.


### ✅ Summary:

- Use Animated API for quick, simple animations (fade, slide, scale).

- Use Reanimated for smooth, complex animations (gestures, bottom sheets, carousels, swipe cards).