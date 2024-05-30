# Auth-Screen

```Kotlin
@Composable
fun AuthenticationScreen(
    viewModel: AuthenticationViewModel = viewModel()
) {
    val authenticationState by viewModel.uiState.collectAsState()

    AuthenticationContent(
        authenticationState = authenticationState,
        modifier = Modifier.fillMaxWidth(),
        handleEvent = viewModel::handleEvent,
    )
}

@Composable
fun AuthenticationContent(
    authenticationState: AuthenticationState,
    modifier: Modifier = Modifier,
    handleEvent: (event: AuthenticationEvent) -> Unit,
) {
    Box(
        modifier = modifier,
        contentAlignment = Alignment.Center,
    ) {
        if (authenticationState.isLoading) {
            CircularProgressIndicator()
        } else {
            AuthenticationForm(
                modifier = Modifier.fillMaxSize(),
                authenticationMode = authenticationState.authenticationMode,
                email = authenticationState.email,
                password = authenticationState.password,
                completedPasswordRequirements = authenticationState.passwordRequirements,
                enableAuthentication = authenticationState.isFormValid(),
                onEmailChanged = { email ->
                    handleEvent(AuthenticationEvent.EmailChanged(email))
                },
                onPasswordChanged = { password ->
                    handleEvent(AuthenticationEvent.PasswordChanged(password))
                },
                onAuthenticate = {
                    handleEvent(AuthenticationEvent.Authenticate)
                },
                onToggleAuthenticationMode = {
                    handleEvent(AuthenticationEvent.ToggleAuthenticationMode)
                },
            )
        }
        authenticationState.error?.let { error ->
            AuthenticationErrorDialog(
                error = error,
                dismissError = { handleEvent(AuthenticationEvent.ErrorDismissed) },
            )
        }
    }
}

```