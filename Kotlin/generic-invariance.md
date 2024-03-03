
# Generic Invariance

https://kotlinlang.org/docs/generics.html#variance

Kotlin generics are invariant by default.

This means given this:

```kt
var collectableItems: Flow<PagingData<ListItemModel>> by remember { mutableStateOf(emptyFlow()) }
```

I cannot assign it something that returns `Flow<PagingData<AreaListItemModel>>` despite `AreaListItemModel` being
```
data class AreaListItemModel(...) : Area, ListItemModel()
```

A way to cheat this is to add the following to something that returns `Flow<PagingData<AreaListItemModel>>`. Now I can assign it to `collectableItems`.

```
.map { pagingData ->  
    pagingData.insertSeparators { _, _ ->  
        null  
    }  
}
```

