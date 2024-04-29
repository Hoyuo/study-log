# Setting-Componet

* SettingItem

```Kotlin
@Composable
fun SettingItem(
    modifier: Modifier = Modifier,
    content: @Composable () -> Unit,
) {
    Surface(
        modifier =
            modifier
                .heightIn(min = 56.dp),
    ) {
        content()
    }
}
```

* SettingTopAppBar
    * Appbar
```Kotlin
@Composable
fun SettingTopAppBar(
    title: String,
    onBack: () -> Unit,
) {
    TopAppBar(
        title = {
            Text(
                text = title,
                fontSize = 18.sp,
            )
        },
        navigationIcon = {
            Icon(
                imageVector = Icons.Default.ArrowBack,
                contentDescription = stringResource(id = R.string.cd_go_back),
            )
        },
        actions = { onBack() },
    )
}
```

* NotificationSettingItem
    * Switch
```Kotlin
@Composable
fun NotificationSettingItem(
    title: String,
    checked: Boolean,
    modifier: Modifier = Modifier,
    onCheckedChange: (Boolean) -> Unit,
) {
    val notificationEnabledDescription =
        if (checked) {
            stringResource(id = R.string.cd_notification_enabled)
        } else {
            stringResource(id = R.string.cd_notification_disabled)
        }

    SettingItem(modifier = modifier) {
        Row(
            modifier =
            Modifier
                .toggleable(
                    value = checked,
                    onValueChange = onCheckedChange,
                    role = Role.Switch,
                )
                .semantics {
                    stateDescription = notificationEnabledDescription
                }
                .padding(horizontal = 16.dp),
            verticalAlignment = Alignment.CenterVertically,
        ) {
            Text(text = title, modifier = Modifier.weight(1f))
            Switch(
                checked = checked,
                onCheckedChange = null,
            )
        }
    }
}
```

* HintSettingsItem
    * Checked
```Kotlin
@Composable
fun HintSettingsItem(
    title: String,
    checked: Boolean,
    modifier: Modifier = Modifier,
    onShowHintsToggle: (checked: Boolean) -> Unit,
) {
    val hintEnabledDescription =
        if (checked) {
            stringResource(id = R.string.cd_hints_enabled)
        } else {
            stringResource(id = R.string.cd_hints_disabled)
        }
    SettingItem(modifier = modifier) {
        Row(
            modifier =
                Modifier
                    .toggleable(
                        value = checked,
                        onValueChange = onShowHintsToggle,
                        role = Role.Checkbox,
                    )
                    .semantics {
                        stateDescription = hintEnabledDescription
                    }
                    .padding(horizontal = 16.dp),
            verticalAlignment = Alignment.CenterVertically,
        ) {
            Text(text = title, modifier = Modifier.weight(1f))
            Checkbox(
                checked = checked,
                onCheckedChange = null,
            )
        }
    }
}
```

* ManageSubscriptionSettingItem
    * Layout 
```Kotlin
@Composable
fun ManageSubscriptionSettingItem(
    title: String,
    modifier: Modifier = Modifier,
    onSettingClicked: () -> Unit,
) {
    SettingItem(modifier = modifier) {
        Row(
            modifier =
                Modifier
                    .clickable(
                        onClickLabel = stringResource(id = R.string.cd_open_subscription),
                    ) { onSettingClicked() }
                    .padding(16.dp),
            verticalAlignment = Alignment.CenterVertically,
        ) {
            Text(
                text = title,
                modifier = Modifier.weight(1f),
            )
            Icon(
                imageVector = Icons.Default.KeyboardArrowRight,
                contentDescription = null,
            )
        }
    }
}
```

* MarketingSettingItem
  * RadioButton
```Kotlin
@Composable
fun MarketingSettingItem(
    title: String,
    selectedOption: MarketingOption,
    modifier: Modifier = Modifier,
    onOptionSelected: (MarketingOption) -> Unit,
) {
    val options = stringArrayResource(id = R.array.setting_options_marketing_choice)

    SettingItem(modifier = modifier) {
        Column(
            modifier = Modifier.padding(16.dp),
        ) {
            Text(text = title)
            Spacer(modifier = Modifier.height(8.dp))
            options.forEachIndexed { index, option ->
                Row(
                    modifier =
                    Modifier
                        .fillMaxWidth()
                        .clickable(
                            onClickLabel = option,
                        ) {
                            if (index == MarketingOption.ALLOWED.id) {
                                onOptionSelected(MarketingOption.ALLOWED)
                            } else {
                                onOptionSelected(MarketingOption.NOT_ALLOWED)
                            }
                        }
                        .padding(10.dp),
                    verticalAlignment = Alignment.CenterVertically,
                ) {
                    RadioButton(
                        selected = selectedOption.id == index,
                        onClick = null,
                    )
                    Spacer(modifier = Modifier.width(10.dp))
                    Text(
                        text = option,
                        modifier = Modifier.padding(start = 18.dp),
                    )
                }
            }
        }
    }
}
```

* ThemeSettingItem
    * DropdownMenu
```Kotlin
@Composable
fun ThemeSettingItem(
    title: String,
    selectedTheme: Theme,
    modifier: Modifier = Modifier,
    onOptionSelected: (Theme) -> Unit,
) {
    var expanded by remember { mutableStateOf(false) }

    SettingItem(modifier = modifier) {
        Row(
            modifier =
                Modifier
                    .clickable(
                        onClick = { expanded = !expanded },
                        onClickLabel = stringResource(id = R.string.cd_select_theme),
                    )
                    .padding(16.dp),
            verticalAlignment = Alignment.CenterVertically,
        ) {
            Text(
                modifier = Modifier.weight(1f),
                text = title,
            )
            Text(text = stringResource(id = selectedTheme.label))
        }
        DropdownMenu(
            expanded = expanded,
            onDismissRequest = { expanded = false },
            offset = DpOffset(16.dp, 0.dp),
            properties = PopupProperties(usePlatformDefaultWidth = true),
        ) {
            Theme.entries.forEach { theme ->
                DropdownMenuItem(
                    onClick = {
                        onOptionSelected(theme)
                        expanded = false
                    },
                ) {
                    Text(text = stringResource(id = theme.label))
                }
            }
        }
    }
}
```

* AppVersionSettingItem
    * Layout
```Kotlin
@Composable
fun AppVersionSettingItem(
    title: String,
    appVersion: String,
    modifier: Modifier = Modifier,
) {
    SettingItem(modifier = modifier) {
        Row(
            modifier =
                Modifier
                    .padding(horizontal = 16.dp)
                    .semantics(mergeDescendants = true) { },
            verticalAlignment = Alignment.CenterVertically,
        ) {
            Text(
                text = title,
                modifier = Modifier.weight(1f),
            )
            Text(
                text = appVersion,
            )
        }
    }
}
```