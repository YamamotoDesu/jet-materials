# Jetpack Compose by Tutorials: Materials

This repo contains all the downloadable materials and projects associated with the **[Jetpack Compose by Tutorials](https://www.kodeco.com/books/jetpack-compose-by-tutorials)** from [Kodeco](https://www.kodeco.com).

Each edition has its own branch, named `editions/[EDITION]`. The default branch for this repo is for the most recent edition.

## Forum

We’ve set up an official forum for the book at [https://forums.kodeco.com/c/books/jetpack-compose-by-tutorials](https://forums.kodeco.com/c/books/jetpack-compose-by-tutorials). This is a great place to ask questions about the book or to submit any errors you may find.

## Release History

| Branch                                                                           | Edition | Release Date |
| ---------------------------------------------------------------------------------|:-------:|:------------:|
| [editions/1.0](https://github.com/kodecocodes/jet-materials/tree/editions/1.0) | 1.0     | 2021-02-13   |
| [editions/1.1](https://github.com/kodecodes/jet-materials/tree/editions/1.1) | 1.1     | 2021-05-07   |
| [editions/2.0](https://github.com/kodecocodes/jet-materials/tree/editions/2.0) | 2.0     | 2023-03-29   |

## [1. Developing UI in Android](https://www.kodeco.com/books/jetpack-compose-by-tutorials/v2.0/chapters/1-developing-ui-in-android)

### ViewGroup
* LinearLayout: Use this when you want to organize children in a row or column.
* RelativeLayout: Enables you to specify the location of child objects relative to each other or to the parent.
* FrameLayout: One of the simplest containers, it lets you stack widgets, vertically on top of one another. It is usually used to host a single widget or a Fragment.

![image](https://user-images.githubusercontent.com/47273077/229027896-14a55986-f025-46f7-a7ea-79e0900bfbbd.png)
However, UIs are not always so simple that you can use just one ViewGroup in your layouts. When building more complicated UIs, you often define different areas of the screen and use the specific ViewGroup best matching your use case.

That leads to a lot of nested ViewGroups, making your code hard to read and maintain. Most importantly, it decreases the performance of your app.

Recently, the Android UI toolkit received a new ViewGroup, to address this issue — ConstraintLayout. It allows the creation of large and complex layouts with a flat view hierarchy. In short, you use it to create complex constraints between views so you don’t have to nest layouts. Each constraint describes if a View is constrained to the start, end, top or bottom of another View.

This doesn’t quite solve the problem of nested layouts. There are times when you can get better performance by combining simpler ViewGroups rather than using ConstraintLayout.

## [2. Learning Jetpack Compose Fundamentals](https://www.kodeco.com/books/jetpack-compose-by-tutorials/v2.0/chapters/2-learning-jetpack-compose-fundamentals)

### TextField
<img width="300" alt="スクリーンショット 2023-04-03 15 26 24" src="https://user-images.githubusercontent.com/47273077/229427882-24090f01-dcdb-4d47-95e6-fd0ae0b0b399.png">

TextScreen.kt
```kt
@Composable
fun TextScreen() {
  Column(
      modifier = Modifier.fillMaxSize(),
      horizontalAlignment = Alignment.CenterHorizontally,
      verticalArrangement = Arrangement.Center
  ) {
    MyText()
  }

  BackButtonHandler {
    JetFundamentalsRouter.navigateTo(Screen.Navigation)
  }
}

@Composable
fun MyText() {
    //TODO add your code here
    Text(
        text = stringResource(id = R.string.jetpack_compose),
        fontStyle = FontStyle.Italic,
        color = colorResource(id = R.color.colorPrimary),
        fontSize = 30.sp,
        fontWeight = FontWeight.Bold
    )
}
```

* color: Lets you set the text color.
* fontSize: Changes the font size. You measure it in scalable pixels (sp).
* fontStyle: Lets you choose between normal and italic font.
* fontWeight: Sets the weight of the text to Bold, Black, Thin and similar types.
* textAlign: Sets the horizontal alignment of the text.
* overflow: Determines how the app handles overflow, using either Clip or Ellipsis.
* maxLines: Sets the maximum number of lines.
* style: Lets you build a specific style and reuse it, rather than explicitly setting all the other parameters. The current app theme defines the default style, making it easier to support different themes.

### TextField

<img width="300" alt="スクリーンショット 2023-04-03 15 26 24" src="https://user-images.githubusercontent.com/47273077/229430415-3826365c-fe96-47db-b23c-47a5afd6000d.png">

```kt
@Composable
fun TextFieldScreen() {
  Column(
      modifier = Modifier.fillMaxSize(),
      horizontalAlignment = Alignment.CenterHorizontally,
      verticalArrangement = Arrangement.Center
  ) {
    MyTextField()
  }

  BackButtonHandler {
    JetFundamentalsRouter.navigateTo(Screen.Navigation)
  }
}

@Composable
fun MyTextField() {
    val textValue = remember { mutableStateOf("") }

    TextField(
        value = textValue.value,
        onValueChange = {

        },
        label = {})
}
```

### Adding an Email Field With OutlinedTextField

```kt
@Composable
fun MyTextField() {
    val textValue = remember { mutableStateOf("") }

    val primaryColor = colorResource(id = R.color.colorPrimary)

    OutlinedTextField(
        label = { Text(text = stringResource(id = R.string.email)) },
        colors = TextFieldDefaults.outlinedTextFieldColors(
            focusedBorderColor = primaryColor,
            focusedLabelColor = primaryColor,
            cursorColor = primaryColor
        ),
        keyboardOptions = KeyboardOptions.Default.copy(keyboardType = KeyboardType.Email),
        value = textValue.value,
        onValueChange = {
            textValue.value = it
        }
    )
}

```

<img width="300" alt="スクリーンショット 2023-04-03 15 26 24" src="https://user-images.githubusercontent.com/47273077/229438646-4375bed6-f959-4cff-b376-38d456bbbcf7.png">

<img width="300" alt="スクリーンショット 2023-04-03 15 26 24" src="https://user-images.githubusercontent.com/47273077/229438689-fe2acda9-0867-4dd5-8e5d-033036baf495.png">

### Building a Login Button

<img width="300" alt="スクリーンショット 2023-04-03 15 26 24" src="https://user-images.githubusercontent.com/47273077/229442145-f983083b-dae3-4310-909f-51ea4100e2cb.png">


```kt
@Composable
fun MyButton() {
  //TODO add your code here
    Button(
        onClick ={},
        colors = ButtonDefaults.buttonColors(backgroundColor = colorResource(id = R.color.colorPrimary)),
        border = BorderStroke(
            1.dp,
            color = colorResource(id = R.color.colorPrimary),
        )
    ) {
        Text(
            text = stringResource(id = R.string.button_text),
            color = Color.White
        )
    }
}
```

* onClick: The most common property you’ll use with buttons, this calls a function when the user clicks the button. If you don’t provide onClick, the button will be disabled.
* enabled: Allows you to control when a button is clickable.
* elevation: Sets the elevation of a button. The default elevation is 2 dp.
* shape: Defines the button’s shape and shadow. With MaterialTheme.shapes, you can choose a shape’s size: small, medium or large. Or you can specify a * custom shape as well.
* border: Draws a border around your button.
* content: A composable function that displays the content inside the button, usually text.

### RadioButton

<img width="300" alt="スクリーンショット 2023-04-03 15 26 24" src="https://user-images.githubusercontent.com/47273077/229445659-6312659e-ef17-45fe-9751-e65ba1fc03a1.png">

```kt
@Composable
fun MyRadioGroup() {
  val radioButtons = listOf(0, 1, 2) // 1

  val selectedButton = remember { mutableStateOf(radioButtons.first()) } // 2

  Column {
    radioButtons.forEach { index -> // 3
      val isSelected = index == selectedButton.value
      val colors = RadioButtonDefaults.colors( // 4
        selectedColor = colorResource(id = R.color.colorPrimary),
        unselectedColor = colorResource(id = R.color.colorPrimaryDark),
        disabledColor = Color.LightGray
      )

      RadioButton( // 5
        colors = colors,
        selected = isSelected,
        onClick = { selectedButton.value = index } // 6
      )
    }
  }
}
```

### FloatingActionButton

<img width="300" alt="スクリーンショット 2023-04-03 15 26 24" src="https://user-images.githubusercontent.com/47273077/229447024-11def30a-a442-4e29-ae47-922f9efe56fa.png">

```kt
@Composable
fun MyFloatingActionButton() {
  FloatingActionButton(
      onClick = {},
      backgroundColor = colorResource(id = R.color.colorPrimary),
      contentColor = Color.White,
      content = {
        Icon(Icons.Filled.Favorite, contentDescription = "Test FAB")
      }
  )
}
```

## Exploring the Progress Indicators
```kt
Column(
   modifier = Modifier.fillMaxSize(),
   horizontalAlignment = Alignment.CenterHorizontally,
   verticalArrangement = Arrangement.Center
) {
 CircularProgressIndicator(
     color = colorResource(id = R.color.colorPrimary),
     strokeWidth = 5.dp
 )
 LinearProgressIndicator(progress = 0.5f)
}
```

### AlertDialog
```kt
@Composable
fun MyAlertDialog() {
  val shouldShowDialog = remember { mutableStateOf(true) } // 1

  if (shouldShowDialog.value) { // 2
    AlertDialog( // 3
      onDismissRequest = { // 4
        shouldShowDialog.value = false
        JetFundamentalsRouter.navigateTo(Screen.Navigation)
      },
      // 5
      title = { Text(text = stringResource(id = R.string.alert_dialog_title)) },
      text = { Text(text = stringResource(id = R.string.alert_dialog_text)) },
      confirmButton = { // 6
        Button(
          colors = ButtonDefaults.buttonColors(backgroundColor = colorResource(id = R.color.colorPrimary)),
          onClick = {
            shouldShowDialog.value = false
            JetFundamentalsRouter.navigateTo(Screen.Navigation)
          }
        ) {
          Text(
            text = stringResource(id = R.string.confirm),
            color = Color.White
          )
        }
      }
    )
  }
}
```
