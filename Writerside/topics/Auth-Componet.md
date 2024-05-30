# Auth-Component

## AuthForm
```Kotlin
@Composable
fun AuthenticationForm(
    modifier: Modifier = Modifier,
    authenticationMode: AuthenticationMode,
    email: String?,
    password: String?,
    completedPasswordRequirements: List<PasswordRequirements>,
    enableAuthentication: Boolean,
    onEmailChanged: (email: String) -> Unit,
    onPasswordChanged: (password: String) -> Unit,
    onAuthenticate: () -> Unit,
    onToggleAuthenticationMode: () -> Unit,
) {
    Column(
        modifier = modifier,
        horizontalAlignment = Alignment.CenterHorizontally,
    ) {
        Spacer(modifier = Modifier.height(32.dp))
        AuthenticationTitle(
            modifier = Modifier.fillMaxSize(),
            authenticationMode = authenticationMode,
        )

        Spacer(modifier = Modifier.height(40.dp))
        val passwordFocusRequester = FocusRequester()
        Card(
            modifier =
                Modifier
                    .fillMaxWidth()
                    .padding(horizontal = 32.dp),
            elevation = CardDefaults.elevatedCardElevation(defaultElevation = 4.dp),
        ) {
            Column(
                modifier = Modifier.padding(16.dp),
                horizontalAlignment = Alignment.CenterHorizontally,
            ) {
                EmailInput(
                    modifier = Modifier.fillMaxWidth(),
                    email = email,
                    onEmailChanged = onEmailChanged,
                    onNextClicked = { passwordFocusRequester.requestFocus() },
                )
                Spacer(modifier = Modifier.height(16.dp))
                PasswordInput(
                    modifier =
                        Modifier.fillMaxWidth()
                            .focusRequester(passwordFocusRequester),
                    password = password,
                    onPasswordChanged = onPasswordChanged,
                    onDoneClicked = { onAuthenticate() },
                )
                Spacer(modifier = Modifier.height(12.dp))
                AnimatedVisibility(
                    visible = authenticationMode == AuthenticationMode.SIGN_UP,
                ) {
                    PasswordRequirements(satisfiedRequirements = completedPasswordRequirements)
                }
                Spacer(modifier = Modifier.height(12.dp))
                AuthenticationButton(
                    authenticationMode = authenticationMode,
                    enableAuthentication = enableAuthentication,
                    onAuthenticate = onAuthenticate,
                )
            }
        }

        Spacer(modifier = Modifier.weight(1f))
        ToggleAuthenticationMode(
            modifier = Modifier.fillMaxWidth(),
            authenticationMode = authenticationMode,
            toggleAuthenticationMode = onToggleAuthenticationMode,
        )
    }
}
```

## AuthenticationTitle
```Kotlin
@Composable
fun AuthenticationTitle(
    authenticationMode: AuthenticationMode,
    modifier: Modifier = Modifier,
) {
    Text(
        text =
            stringResource(
                id =
                    when (authenticationMode) {
                        AuthenticationMode.SIGN_IN -> R.string.label_sign_in_to_account
                        AuthenticationMode.SIGN_UP -> R.string.label_sign_up_for_account
                    },
            ),
        fontSize = 24.sp,
        fontWeight = FontWeight.Black,
    )
}
```

## EmailInput
```Kotlin
@Composable
fun EmailInput(
    email: String?,
    onEmailChanged: (email: String) -> Unit,
    modifier: Modifier = Modifier,
    onNextClicked: () -> Unit,
) {
    TextField(
        modifier = modifier,
        value = email ?: "",
        onValueChange = { onEmailChanged(it) },
        label = {
            Text(text = stringResource(id = R.string.label_email))
        },
        singleLine = true,
        leadingIcon = {
            Icon(
                imageVector = Icons.Default.Email,
                contentDescription = null,
            )
        },
        keyboardOptions = KeyboardOptions(keyboardType = KeyboardType.Email),
        keyboardActions =
            KeyboardActions {
                onNextClicked()
            },
    )
}
```

## PasswordInput
```Kotlin
@Composable
fun PasswordInput(
    password: String?,
    onPasswordChanged: (email: String) -> Unit,
    modifier: Modifier = Modifier,
    onDoneClicked: () -> Unit,
) {
    var isPasswordHidden by remember { mutableStateOf(true) }

    TextField(
        modifier = modifier,
        value = password ?: "",
        onValueChange = { onPasswordChanged(it) },
        label = {
            Text(text = stringResource(id = R.string.label_password))
        },
        singleLine = true,
        leadingIcon = {
            Icon(
                imageVector = Icons.Default.Lock,
                contentDescription = null,
            )
        },
        trailingIcon = {
            Icon(
                imageVector =
                    if (isPasswordHidden) {
                        Icons.Default.Visibility
                    } else {
                        Icons.Default.VisibilityOff
                    },
                contentDescription = null,
                modifier =
                    Modifier.clickable(
                        onClickLabel =
                            if (isPasswordHidden) {
                                stringResource(id = R.string.cd_show_password)
                            } else {
                                stringResource(id = R.string.cd_hide_password)
                            },
                        onClick = { isPasswordHidden = !isPasswordHidden },
                    ),
            )
        },
        visualTransformation =
            if (isPasswordHidden) {
                PasswordVisualTransformation()
            } else {
                VisualTransformation.None
            },
        keyboardOptions =
            KeyboardOptions(
                keyboardType = KeyboardType.Password,
                imeAction = ImeAction.Done,
            ),
        keyboardActions = KeyboardActions(onDone = { onDoneClicked() }),
    )
}
```

## PasswordRequirements
```Kotlin
@Composable
fun PasswordRequirements(
    modifier: Modifier = Modifier,
    satisfiedRequirements: List<PasswordRequirements>,
) {
    Column(
        modifier = modifier,
    ) {
        PasswordRequirements.entries.forEach { requirement ->
            Requirement(
                message = stringResource(id = requirement.label),
                satisfied = satisfiedRequirements.contains(requirement),
            )
        }
    }
}
```

## AuthenticationButton
```Kotlin
@Composable
fun AuthenticationButton(
    modifier: Modifier = Modifier,
    authenticationMode: AuthenticationMode,
    enableAuthentication: Boolean,
    onAuthenticate: () -> Unit,
) {
    Button(
        modifier = modifier,
        onClick = onAuthenticate,
        enabled = enableAuthentication,
    ) {
        Text(
            text =
                stringResource(
                    if (authenticationMode == AuthenticationMode.SIGN_IN) {
                        R.string.action_sign_in
                    } else {
                        R.string.action_sign_up
                    },
                ),
        )
    }
}
```