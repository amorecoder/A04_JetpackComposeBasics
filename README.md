# A04_JetpackComposeBasics

This project is one of the CodeLab for learning Jetpack Compose at the Android Developer site.

In this codelab, we will learn:

    What Compose is
    How to build UIs with Compose
    How to manage state in composable functions
    How to create a performant list
    How to add animations
    How to style and theme an app

1. With Compose, Activities is still the entry point to an Android app.
2. We use setContent to define our layout, but instead of using an XML file as per traditional view definition, we call Composable functions.
3. The Surface composable understands that when background is set to primary color, any text on top of it should use the onPrimary color which is defined in the theme.
4. Modifiers tell a UI element how to lay out, display, or behave within its parent layout. Complete list of modifiers are documented in https://developer.android.com/jetpack/compose/modifiers-list .
5. The three basic standard layout elements in Compose are Column, Row, and Box.
6. The weight modifier makes the element fill all available space, making it flexible, effectively pushing away the other elements that don't have a weight, which are called inflexible. It also makes the fillMaxWidth modifier redundant.
7. 