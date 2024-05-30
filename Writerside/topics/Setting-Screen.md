# Setting-Screen

```Kotlin
@Composable
fun SettingsScreen(
    viewModel: SettingsViewModel = viewModel()
) {
    val state by viewModel.uiState.collectAsState()

    SettingsList(
        settings = state,
        handleEvent = viewModel::handleEvent,
    )
}

@Composable
fun SettingsList(
    settings: SettingsState,
    modifier: Modifier = Modifier,
    handleEvent: (event: SettingsEvent) -> Unit,
) {
    Scaffold(
        topBar = {
            SettingTopAppBar(
                title = stringResource(id = R.string.title_settings),
                onBack = { handleEvent(SettingsEvent.Back) },
            )
        },
    ) { _ ->
        Column(
            modifier = modifier.verticalScroll(rememberScrollState())
        ) {
            NotificationSettingItem(
                modifier = Modifier.fillMaxWidth(),
                title = stringResource(id = R.string.setting_enable_notifications),
                checked = settings.notificationEnabled,
                onCheckedChange = { handleEvent(SettingsEvent.ToggleNotificationSetting) },
            )
            Divider()
            HintSettingsItem(
                modifier = Modifier.fillMaxWidth(),
                title = stringResource(id = R.string.setting_show_hints),
                checked = settings.hintsEnabled,
                onShowHintsToggle = { handleEvent(SettingsEvent.ToggleHintsSetting) },
            )
            Divider()
            ManageSubscriptionSettingItem(
                modifier = Modifier.fillMaxWidth(),
                title = stringResource(id = R.string.setting_manage_subscription),
                onSettingClicked = { },
            )
            Divider()
            SectionSpacer(modifier = Modifier.fillMaxWidth())
            MarketingSettingItem(
                modifier = Modifier.fillMaxWidth(),
                title = stringResource(id = R.string.setting_option_marketing),
                selectedOption = settings.marketingOption,
                onOptionSelected = { option -> handleEvent(SettingsEvent.SetMarketingOption(option)) },
            )
            Divider()
            ThemeSettingItem(
                modifier = Modifier.fillMaxWidth(),
                title = stringResource(id = R.string.setting_option_theme),
                selectedTheme = settings.themeOption,
                onOptionSelected = { option -> handleEvent(SettingsEvent.SetThemeOption(option)) },
            )
            SectionSpacer(modifier = Modifier.fillMaxWidth())
            AppVersionSettingItem(
                title = stringResource(id = R.string.setting_app_version_title),
                appVersion = stringResource(id = R.string.app_version),
                modifier = Modifier.fillMaxWidth(),
            )
            Divider()
        }
    }
}
```