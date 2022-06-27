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
7. Note that variables that are not State-aware will not be used by Composable to trigger a recomposition. To be State-aware they must implement State or MutableState interface. These will trigger recomposition whenever their value changes. We can make a variable to be State-aware by using the mutableStateOf() function. For example, 
              val expanded = mutableStateOf(false)  
      - this defined a State-aware Boolean variable, expanded, with initial value set to false.
8. However, doing so is not enough to be used within a Composable. To preserve state across recomposition, we must apply the remember() function to the mutable state using 'remember { }'. In fact, the compiler will shows an error if the mutableStateOf variable is defined withing a composable without applying remember function.
9. The remember function is used to guard against recomposition, so the state is not reset. Note that if you call the same composable from different parts of the screen you will create different UI elements, each with its own version of the state. You can think of internal state as a private variable in a class.
10. The composable function will automatically be "subscribed" to the state. If the state changes, composables that read these fields will be recomposed to display the updates.