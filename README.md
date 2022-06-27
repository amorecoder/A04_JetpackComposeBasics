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
11. In Composable functions, state that is read or modified by multiple functions should live in a common ancestor—this process is called state hoisting. To hoist means to lift or elevate. Making state hoistable avoids duplicating state and introducing bugs, helps reuse composables, and makes composables substantially easier to test. Contrarily, state that doesn't need to be controlled by a composable's parent should not be hoisted. The source of truth belongs to whoever creates and controls that state.
12. In Compose you don't hide UI elements. Instead, you simply don't add them to the composition, so they're not added to the UI tree that Compose generates.
13. LazyColumn doesn't recycle its children like RecyclerView. It emits new Composables as you scroll through it and is still performant, as emitting Composables is relatively cheap compared to instantiating Android Views.
14. The remember function works only as long as the composable is kept in the Composition. When we rotate, the whole activity is restarted so all state is lost. This also happens with any configuration change and on process death. Instead of using remember we can use rememberSaveable. This will save each state surviving configuration changes (such as rotations) and process death.
15. The animateDpAsState composable returns a State object whose value will continuously be updated by the animation until it finishes. It takes a "target value" whose type is Dp.
16. Use rememberSaveable to restore your UI state after an activity or process is recreated. rememberSaveable retains state across recompositions. In addition, rememberSaveable also retains state across activity and process recreation. e.g.
        var selectedCity = rememberSaveable { mutableStateOf( City("Madrid", "Spain") ) }
17. Note that rememberSaveable can only support types that can be stored inside the Bundle. If it is not supported, then we need to create a custom Saver. For example, we can make the type parcelable using @Parcelize annotation. e.g.
        @Parcelize
        data class City(val name:String, val country:String) : Parcelable
18. MaterialTheme is a composable function that reflects the styling principles from the Material design specification. That styling information cascades down to the components that are inside its content, which may read the information to style themselves.
19. Because A04_JetpackComposeBasicsTheme wraps MaterialTheme internally, MyApp is styled with the properties defined in the theme. From any descendant composable you can retrieve three properties of MaterialTheme: colors, typography and shapes.
20. In general it's much better to keep our colors, shapes and font styles inside a MaterialTheme. For example, dark mode would be hard to implement if you hard-code colors and it would require a lot of error-prone work to fix. 
21. However sometimes you need to deviate slightly from the selection of colors and font styles. In those situations it's better to base our color or style on an existing one. For this, we can modify a predefined style by using the copy function.
22. 