# Auth-ViewModel

```Kotlin
class AuthenticationViewModel : ViewModel() {
    val uiState = MutableStateFlow(AuthenticationState())

    fun handleEvent(event: AuthenticationEvent) {
        when (event) {
            is AuthenticationEvent.ToggleAuthenticationMode -> {
                toggleAuthenticationMode()
            }

            is AuthenticationEvent.EmailChanged -> {
                updateEmail(event.email)
            }

            is AuthenticationEvent.PasswordChanged -> {
                updatePassword(event.password)
            }

            is AuthenticationEvent.Authenticate -> {
                authenticate()
            }

            is AuthenticationEvent.ErrorDismissed -> {
                dismissError()
            }
        }
    }

    private fun toggleAuthenticationMode() {
        val authenticationMode = uiState.value.authenticationMode

        val newAuthenticationMode =
            if (authenticationMode == AuthenticationMode.SIGN_IN) {
                AuthenticationMode.SIGN_UP
            } else {
                AuthenticationMode.SIGN_IN
            }

        uiState.value =
            uiState.value.copy(
                authenticationMode = newAuthenticationMode,
            )
    }

    private fun updateEmail(email: String) {
        uiState.value = uiState.value.copy(email = email)
    }

    private fun updatePassword(password: String) {
        val requirements = mutableListOf<PasswordRequirements>()
        if (password.length > 7) {
            requirements.add(PasswordRequirements.EIGHT_CHARACTERS)
        }
        if (password.any { it.isDigit() }) {
            requirements.add(PasswordRequirements.NUMBER)
        }
        if (password.any { it.isUpperCase() }) {
            requirements.add(PasswordRequirements.CAPITAL_LETTER)
        }

        uiState.value =
            uiState.value.copy(
                password = password,
                passwordRequirements = requirements,
            )
    }

    private fun authenticate() {
        uiState.value = uiState.value.copy(isLoading = true)

        viewModelScope.launch(Dispatchers.IO) {
            delay(2000L)
            withContext(Dispatchers.Main) {
                uiState.value =
                    uiState.value.copy(
                        isLoading = false,
                        error = "Something went wrong. Please try again.",
                    )
            }
        }
    }

    private fun dismissError() {
        uiState.value = uiState.value.copy(error = null)
    }
}
```