# Dual My Sense — simple DualSense GUI

This is a small, simple GUI wrapper for the `dualsensectl` command-line tool.
It provides an easy way to change lights, triggers and basic settings from a window on Linux.

English
-------

Requirements
- Rust (stable) toolchain installed (rustup, cargo)
- `dualsensectl` binary available in your PATH

How to compile
1. Open a terminal in the project folder (the folder that contains `Cargo.toml`).
2. For a debug build (fast compile, useful while developing):

```fish
cargo run
```

3. For an optimized release build (smaller/faster binary):

```fish
cargo run --release
```

4. If you want a standalone binary without running via `cargo`:

```fish
cargo build --release
# binary will be in target/release/<binary-name>
```

Permissions note
- If `dualsensectl` requires extra permissions to access devices (udev rules), follow the upstream `dualsensectl` README and add the recommended udev rules.

Features (what the GUI does)
- Device picker: reads devices using `dualsensectl -l`. Pick a device to target commands.
- Log panel: shows every command the GUI runs and its output (stdout/stderr). Useful for debugging.
- Triggers tab: independent settings for left and right triggers (L2, R2). You can pick mode (Off, Feedback, Weapon, Bow, Vibration, etc.), tweak mode-specific parameters, and apply to left, right, or both.
- Quick actions: reset both triggers, copy left → right, apply both at once.
- Lightbar: toggle, set RGB and brightness.
- Player LEDs: brightness, player index, fade toggle.
- Microphone LED and mute: control mic LED and mute state.
- Speaker / Headphone volumes: set device volumes.
- Monitor: can run a monitor command or a shell command on device connect/disconnect. The GUI can pass information via `$DS_DEV`.

Which `dualsensectl` commands the GUI runs
- The GUI calls `dualsensectl` with arguments depending on your actions. Example mappings:
	- Triggers: `dualsensectl trigger <left|right|both> <mode> [params...]`
	- Lightbar: `dualsensectl lightbar <on|off|rgb|brightness>` (GUI constructs appropriate args)
	- Player LED: `dualsensectl player-led <...>`
	- Monitor: `dualsensectl monitor` or monitor subcommands

If you need to see the exact commands and outputs, open the Log panel in the GUI.

Development notes
- Code is in `src/main.rs` (single-file GUI). The UI uses `eframe/egui`.
- To iterate quickly: change code, run `cargo run`, test, repeat.

Troubleshooting
- If the GUI shows "no device" but your controller is connected, try running `dualsensectl -l` in a terminal to check permissions.
- For udev permission errors, add the udev rules from `dualsensectl` and replug the controller.

Українська
---------

Потрібне
- Rust (stable) та cargo
- `dualsensectl` у PATH

Як компілювати
1. Відкрийте термінал в папці проекту (там, де `Cargo.toml`).
2. Для збірки в режимі розробки (швидко, для тестування):

```fish
cargo run
```

3. Для збірки в релізному режимі (оптимізована):

```fish
cargo run --release
```

4. Щоб отримати самостійний бінарник:

```fish
cargo build --release
# бінарник буде в target/release/<назва_бінарника>
```

Права доступу
- Якщо `dualsensectl` потребує прав доступу до пристроїв (udev), застосуйте правила з офіційного README `dualsensectl`.

Функції (що робить GUI)
- Вибір пристрою: читається через `dualsensectl -l`.
- Панель логів: показує всі виклики `dualsensectl` та їхній вивід.
- Вкладка тригерів: окремі налаштування для лівого і правого тригерів (режим, параметри) та застосування окремо.
- Швидкі дії: скинути обидва, скопіювати налаштування лівого на правий, застосувати обидва.
- Lightbar: вмик/вимк, RGB, яскравість.
- Player LEDs: яскравість, індекс гравця, ефект згасання.
- Мікрофон: LED та mute.
- Гучності: колонки та навушники.
- Монітор: запуск скрипта або команд при підключенні/відключенні; змінна `$DS_DEV` доступна для скрипту.

Які команди виконує GUI
- GUI формує та виконує виклики `dualsensectl` на основі ваших дій. Приклади:
	- Тригери: `dualsensectl trigger <left|right|both> <mode> [params...]`
	- Lightbar: `dualsensectl lightbar <on|off|rgb|brightness>`
	- Player LED: `dualsensectl player-led <...>`
	- Monitor: `dualsensectl monitor` або підкоманди monitor

Для дебагу відкривайте панель логів — там видно точні аргументи та вивід.

Розробка
- Головний файл: `src/main.rs` (інтерфейс на `egui/eframe`).
- Швидкий цикл: редагувати → `cargo run` → тестувати.

Проблеми
- Якщо пристрій не видно в GUI — перевірте `dualsensectl -l` у терміналі.
- Якщо це права — додайте udev правила з upstream проекту.

Ліцензія: MIT
