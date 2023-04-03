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

![image](https://user-images.githubusercontent.com/47273077/229427882-24090f01-dcdb-4d47-95e6-fd0ae0b0b399.png)

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
