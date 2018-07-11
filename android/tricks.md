# Be Productive - Tips and Tricks

+ **Know the power of [`.gitignore`](https://stackoverflow.com/a/17803964/5629056) and push only what is needed. [`git rm --cached <file>`](https://stackoverflow.com/a/1274447/5629056) to your rescue if you want to remove already tracked files**

+ **Use `alias` and make terminal work for you. Few of [nisrulz adb aliases](https://gist.github.com/nisrulz/b0e79f2b3e27f99ca8b5dba9db6281ec)**

+ **Lint’s [STOPSHIP](https://medium.com/@naveentp/lints-stopship-can-save-you-from-pushing-your-buggy-code-to-production-4fa0db40d9b1) can save you from pushing your buggy code to production**

+ **Use [LeakCanary](https://github.com/square/leakcanary) to find memory leak in app**

+ **Learn [MVP, MVVM, MVI](https://github.com/Naveentp/Link-Me-Up/blob/master/android/architecture.md) architectural patterns**

+ **Create build time resource/variables in `build.gradle`**
```
android{
  defaultConfig {
    ...
    //Build variable
    buildConfigField "String", "NEWS_API", '"YOUR_NEWS_API"'

    //Resource variable
    resValue 'string', 'APP_NAME', APP_NAME

    //Manifest Placeholder 
    manifestPlaceholders = [crashlyticsApiKey: "514bec26d15bb8f67dc8129f0eda3cabf79fXXXX"]
    ...
  }
}

//Can be accessed as
BuildConfig.NEWS_API

getString(R.string.APP_NAME);

<meta-data
       android:name="io.fabric.Api∏Key"
       android:value="${crashlyticsApiKey}" />
``` 

+ **Make use of IntelliJ's Live templates [this](https://github.com/keyboardsurfer/idea-live-templates), [this](https://www.bignerdranch.com/blog/android-studio-live-templates/)**

+ **Stay updated and Learn from [youtube programming channels](https://www.lvguowei.me/post/ultimate-list-of-youtube-programming-channels/)** 

+ **[Android Gradle DSL ref](http://google.github.io/android-gradle-dsl/) - Be productive by using gradle scripts of building and delevering your app**