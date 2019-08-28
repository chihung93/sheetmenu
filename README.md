# sheetmenu
Library for speedy implementation menu with BottomSheet

[![Release](https://jitpack.io/v/whalemare/sheetmenu.svg)](https://jitpack.io/#whalemare/sheetmenu)

![Screenshot](screens/1.3.2.gif)

Usage
-----

Use it in Kotlin

```kotlin
SheetMenu("Post", listOf("Send mail", "Send telegram", "Receive parcel")).show(this)
```

or in Java like `Kotlin`

```java
new SheetMenu().apply(it -> {
    it.setMenu(R.menu.menu_icons);
    it.setTitle("Title");
    it.setAutoCancel(true); 
}).show(this);
```

or with classic `Builder` pattern 

```java
SheetMenu.with(this)
        .setTitle(R.string.title)
        .setMenu(R.menu.menu)
        .setAutoCancel(false)
        .setClick(new MenuItem.OnMenuItemClickListener() {
            @Override
            public boolean onMenuItemClick(MenuItem item) {
                return false;
            }
        }).show();
```

Usecase
-------

Dynamic remove items from list before show it
```kotlin
SheetMenu(
    menu = R.menu.menu
    mapMenuItems = { items ->
        items.filter { menuItem ->
            menuItem.itemId == R.id.some_action
        }
    }
).show(this)
```

Install
-------

Be sure, that you have `Jitpack` in your root gradle file

```diff
allprojects {
    repositories {
      jcenter()
+     maven { url "https://jitpack.io" }
    }
}
```

Include dependency with `BottomSheet` in your app.gradle file with:

```diff
+ implementation 'com.github.whalemare:sheetmenu:1.4.0'
```


License
-------

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
