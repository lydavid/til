
# Multipreview
There are now default multipreviews in Jetpack Compose: https://developer.android.com/jetpack/compose/tooling/previews

I used to use:
```kt
@Preview(name = "Light")  
@Preview(name = "Dark", uiMode = Configuration.UI_MODE_NIGHT_YES)  
actual annotation class DefaultPreviews
```

Now I can replace it with `@PreviewLightDark`, whose implementation is similar:
```kt
@Retention(AnnotationRetention.BINARY)  
@Target(  
        AnnotationTarget.ANNOTATION_CLASS,  
        AnnotationTarget.FUNCTION  
)  
@Preview(name = "Light")  
@Preview(name = "Dark", uiMode = UI_MODE_NIGHT_YES or UI_MODE_TYPE_NORMAL)  
annotation class PreviewLightDark
```

I tried stacking multiple of these multipreviews:
```kt
@PreviewLightDark  
@PreviewScreenSizes  
@Composable  
internal fun PreviewCollectionList()
```

But it just gives me previews for 1 light screen, 1 dark screen, and then each of the screen sizes with the light theme. It does not multiply light/dark with screen sizes. Which is expected but not what I want.

So, I copied `PreviewScreenSizes`'s implementation, duplicated its previews for dark theme, and grouped them together:

```kt
@Retention(AnnotationRetention.BINARY)  
@Target(  
    AnnotationTarget.ANNOTATION_CLASS,  
    AnnotationTarget.FUNCTION,  
)  
@Preview(  
    name = "Phone",  
    device = Devices.PHONE,  
    showSystemUi = true,  
    uiMode = UI_MODE_NIGHT_YES,  
    group = "Dark",  
)  
@Preview(  
    name = "Phone - Landscape",  
    device = "spec:width = 411dp, height = 891dp, orientation = landscape, dpi = 420",  
    showSystemUi = true,  
    uiMode = UI_MODE_NIGHT_YES,  
    group = "Dark",  
)  
@Preview(  
    name = "Unfolded Foldable",  
    device = Devices.FOLDABLE,  
    showSystemUi = true,  
    uiMode = UI_MODE_NIGHT_YES,  
    group = "Dark",  
)  
@Preview(  
    name = "Tablet",  
    device = Devices.TABLET,  
    showSystemUi = true,  
    uiMode = UI_MODE_NIGHT_YES,  
    group = "Dark",  
)  
@Preview(  
    name = "Desktop",  
    device = Devices.DESKTOP,  
    showSystemUi = true,  
    uiMode = UI_MODE_NIGHT_YES,  
    group = "Dark",  
)  
@Preview(  
    name = "Phone",  
    device = Devices.PHONE,  
    showSystemUi = true,  
    group = "Light",  
)  
@Preview(  
    name = "Phone - Landscape",  
    device = "spec:width = 411dp, height = 891dp, orientation = landscape, dpi = 420",  
    showSystemUi = true,  
    group = "Light",  
)  
@Preview(  
    name = "Unfolded Foldable",  
    device = Devices.FOLDABLE,  
    showSystemUi = true,  
    group = "Light",  
)  
@Preview(  
    name = "Tablet",  
    device = Devices.TABLET,  
    showSystemUi = true,  
    group = "Light",  
)  
@Preview(  
    name = "Desktop",  
    device = Devices.DESKTOP,  
    showSystemUi = true,  
    group = "Light",  
)  
actual annotation class DefaultPreviews
```

It no longer makes sense to apply this every single composable preview. The UI for a [Screen](https://slackhq.github.io/circuit/screen/) should use this, while components should use `@PreviewLightDark`.

## Multiplatform previews?

Nope. It's under `Multipreviews.android.kt`.
