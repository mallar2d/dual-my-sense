# Dual My Sense — simple DualSense GUI

This is a small, simple GUI wrapper for the `dualsensectl` command-line tool.
It provides an easy way to change lights, triggers and basic settings from a window on Linux.

English
-------

- What: a tiny GUI for `dualsensectl` (built with Rust + egui).
- Requirements: Rust (stable) and `dualsensectl` in your PATH.

Build & run (from project folder):

```fish
# debug build
cargo run

# release build
cargo run --release
```

If `dualsensectl` needs extra permissions (udev rules), follow the instructions in the upstream `dualsensectl` README.

Quick notes:
- The device picker reads `dualsensectl -l`.
- The log panel shows the commands that the GUI runs and their output.
- Triggers tab has per-trigger settings and quick actions.

License: MIT

Українська
---------

- Що це: маленький GUI для `dualsensectl` (написано на Rust + egui).
- Потрібне: Rust (stable) та бінарний `dualsensectl` у PATH.

Збірка та запуск (з папки проекту):

```fish
# збірка для розробки та запуск
cargo run

# збірка в релізному режимі
cargo run --release
```

Якщо `dualsensectl` вимагає додаткових прав (udev), застосуйте правила з офіційного README `dualsensectl`.

Коротко:
- Список пристроїв читається через `dualsensectl -l`.
- Панель логів показує команди та їхній вивід.
- Вкладка тригерів має окремі налаштування для лівого і правого тригерів та швидкі дії.

Ліцензія: MIT

