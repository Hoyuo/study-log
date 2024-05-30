# Auth-State, Event

## State
```Kotlin
data class AuthenticationState(
    val authenticationMode: AuthenticationMode = AuthenticationMode.SIGN_IN,
    val email: String? = null,
    val password: String? = null,
    val passwordRequirements: List<PasswordRequirements> = emptyList(),
    val isLoading: Boolean = false,
    val error: String? = null,
) {
    fun isFormValid(): Boolean {
        return password?.isNotEmpty() == true &&
            email?.isNotEmpty() == true &&
            (
                authenticationMode == AuthenticationMode.SIGN_IN ||
                    passwordRequirements.containsAll(PasswordRequirements.entries)
            )
    }
}
```

## Event
```Kotlin
sealed class AuthenticationEvent {
    data object ToggleAuthenticationMode : AuthenticationEvent()

    class EmailChanged(val email: String) : AuthenticationEvent()

    class PasswordChanged(val password: String) : AuthenticationEvent()

    data object Authenticate : AuthenticationEvent()

    data object ErrorDismissed : AuthenticationEvent()
}
```

## ETC

```Kotlin
enum class AuthenticationMode {
    SIGN_UP,
    SIGN_IN,
}

enum class PasswordRequirements(
    @StringRes val label: Int,
) {
    CAPITAL_LETTER(R.string.password_requirement_capital),
    NUMBER(R.string.password_requirement_digit),
    EIGHT_CHARACTERS(R.string.password_requirement_characters),
}
```