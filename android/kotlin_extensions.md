# Kotlin Extensions

- [Activity / Context](#activity)
- [View](#view)

## Activity

```kotlin
/**
* Kotlin extension to start an activity
**/

fun <T : Activity> KClass<T>.start(currentActivity: Activity, bundle: Bundle? = null, finish: Boolean = false) {
    Intent(currentActivity, this.java).apply {
        if (bundle != null) {
            putExtras(bundle)
        }
        currentActivity.startActivity(this)
    }
    if (finish) {
        currentActivity.finish()
    }
}

// Usage
1. HomeActivity::class.start(this)
2. HomeActivity::class.start(this, finish = true)
3. HomeActivity::class.start(this, bundle = bundle, finish = true)
```

```kotlin
/**
* Koltin extension: Bundle to parcelable object mapper
**/

fun <T : Parcelable> Activity.getParcelable(key: String): T? = intent?.extras?.getParcelable(key)

// Usage
val userDetails = getParcelable<UserDetails>(AppConstants.INTENT_USER_DETAILS)
```


```kotlin
/**
* Kotlin extension to check internet connectivity
**/

fun Context.isNetworkAvailable(): Boolean {
    val connectivityManager = getSystemService(Context.CONNECTIVITY_SERVICE) as ConnectivityManager
    return connectivityManager.activeNetworkInfo?.isConnected ?: false
}

// Usage
if(isNetworkAvailable()){
    // network related task goes here
} else {
    // offline task goes here
}
```

```kotlin
/**
* Kotlin extension to get mobile IMEI
* Requires READ_PHONE_STATE permission
* Android Q onwards this also requires READ_PRIVILEGED_PHONE_STATE permission.
**/

fun Activity.getImei(): String {
    val telephonyManager = this.getSystemService(Context.TELEPHONY_SERVICE) as TelephonyManager
    return if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.O) telephonyManager.imei.toString() else telephonyManager.deviceId.toString()
}

// Usage
val deviceImei = getImei()

```

```kotlin
/**
* Kotlin extension to show AlertDialog with all possible cases
**/

fun Context.showAlertDialog(
    title: String, content: String, isCancellable: Boolean = true,
    positiveBtnTitle: String = getString(android.R.string.yes),
    handlePositiveBtnClick: (which: Int) -> Unit = {},
    isNegativeButton: Boolean = false,
    negativeBtnTitle: String = getString(android.R.string.no),
    handleNegativeBtnClick: (which: Int) -> Unit = {}
) {
    val alert = AlertDialog.Builder(this)
    alert.setTitle(title)
        .setCancelable(isCancellable)
        .setMessage(content)
        .setPositiveButton(
            positiveBtnTitle
        ) { dialog, which -> dialog.dismiss();handlePositiveBtnClick(which) }
    if (isNegativeButton) {
        alert.setNegativeButton(
            negativeBtnTitle
        ) { dialog, which -> dialog.dismiss();handleNegativeBtnClick(which) }
    }
    alert.show()
}

// Usage
1. showAlertDialog("Success!", "You earned it!")
2. showAlertDialog("Title", "Content",
                isCancellable = false,
                positiveBtnTitle = "Yes",
                handlePositiveBtnClick = { /*positive button click logic goes here*/ },
                isNegativeButton = true,
                negativeBtnTitle = "No",
                handleNegativeBtnClick = { /*negative button click logic goes here*/ }
    )
```

## View

```kotlin
/**
* Kotlin extension to fetch value from EditText
**/
fun EditText.value(): String = this.text.toString()

// Usage
val name = editTextName.value()
```

```kotlin
/**
* Kotlin extension to check EditText is empty or not
**/

fun EditText.isEmpty(): Boolean = TextUtils.isEmpty(this.value())

// Usage
if(!editTextName.isEmpty()){
    val name = editTextName.value()
} else {
    // Show error
}
```

```kotlin
/**
* Kotlin extension to show error message in TextInputLayout and return false
* Comes in handy while validating fields
**/

fun TextInputLayout.setErrorMessage(msg: String): Boolean {
    error = msg
    return false
}

// Usage
fun validateFields() : Boolean {
    if(editTextName.isEmpty()){
        textInputLayoutName.setErrorMessage("Name should not be empty")
    }
    return true
}
```
