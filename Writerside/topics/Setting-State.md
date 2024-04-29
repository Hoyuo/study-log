# Setting-State, Event

```Kotlin
data class SettingsState(
    val notificationEnabled: Boolean = false,
    val hintsEnabled: Boolean = false,
    val marketingOption: MarketingOption = MarketingOption.ALLOWED,
    val themeOption: Theme = Theme.SYSTEM,
)
```

```Kotlin
sealed interface SettingsEvent {
    data object Back : SettingsEvent

    data object ToggleNotificationSetting : SettingsEvent

    data object ToggleHintsSetting : SettingsEvent

    data class SetMarketingOption(val option: MarketingOption) : SettingsEvent

    data class SetThemeOption(val option: Theme) : SettingsEvent
}
```