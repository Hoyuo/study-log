# Setting-ViewModel

```Kotlin
class SettingsViewModel : ViewModel() {
    val uiState = MutableStateFlow(SettingsState())

    fun toggleNotificationSetting() {
        uiState.value = uiState.value.copy(notificationEnabled = !uiState.value.notificationEnabled)
    }

    fun toggleHintsSetting() {
        uiState.value = uiState.value.copy(hintsEnabled = !uiState.value.hintsEnabled)
    }

    fun setMarketingOption(option: MarketingOption) {
        uiState.value = uiState.value.copy(marketingOption = option)
    }

    fun setThemeOption(option: Theme) {
        uiState.value = uiState.value.copy(themeOption = option)
    }

    fun sendEvent(event: SettingsEvent) {
        when (event) {
            is SettingsEvent.ToggleNotificationSetting -> toggleNotificationSetting()
            is SettingsEvent.ToggleHintsSetting -> toggleHintsSetting()
            is SettingsEvent.SetMarketingOption -> setMarketingOption(event.option)
            is SettingsEvent.SetThemeOption -> setThemeOption(event.option)
            SettingsEvent.Back -> Unit
        }
    }
}
```