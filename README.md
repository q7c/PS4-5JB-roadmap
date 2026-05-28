# 🎮 PS4 / PS5 Jailbreak Roadmap

> Полная интерактивная карта взлома PlayStation 4 и PlayStation 5. Таблицы, ссылки на официальные GitHub-репозитории и пошаговые блок-схемы для всех прошивок.

---

## 📋 Содержание

- [PS4 — Полная блок-схема взлома](#ps4--полная-блок-схема-взлома)
- [PS4 — Таблица эксплойтов по прошивкам](#ps4--таблица-эксплойтов-по-прошивкам)
- [PS4 — Ссылки на официальные GitHub](#ps4--ссылки-на-официальные-github)
- [PS5 — Блок-схема установки и запуска джейлбрейка](#ps5--блок-схема-установки-и-запуска-джейлбрейка)
- [PS5 — Таблица эксплойтов по прошивкам](#ps5--таблица-эксплойтов-по-прошивкам)
- [PS5 — Ссылки на официальные GitHub](#ps5--ссылки-на-официальные-github)
- [Полезные ссылки и сообщества](#полезные-ссылки-и-сообщества)

---

# PS4 — Полная блок-схема взлома

```
┌───────────────────────────────────────────────────────────┐
│  ШАГ 1: АНАЛИЗ ПРОШИВКИ И РЕВИЗИИ СИСТЕМЫ                │
│  • Проверка системного ПО (Все версии от 1.76 до 13.00)  │
│  • Аппаратный чек: Blu-Ray дисковод или LAN-порт          │
└──────────────────────┬────────────────────────────────────┘
                       ▼
┌───────────────────────────────────────────────────────────┐
│  ШАГ 2: БЛОКИРОВКА ОБНОВЛЕНИЙ SONY (ТЕНЕВОЙ DNS)          │
│  • DNS EchoStretch / Al-Azif → изоляция от серверов Sony  │
└──────────────────────┬────────────────────────────────────┘
                       ▼
┌───────────────────────────────────────────────────────────┐
│  ШАГ 3: ТОЧКА ВХОДА (USERLAND EXPLOITS)                   │
│  ┌─────────────────────────────────────────────────────┐  │
│  │ A: Браузер (WebKit/psFree)      — FW 5.05 — 9.60   │  │
│  │ B: Сеть (PPPwn)                 — FW 7.00 — 11.00  │  │
│  │ C: Blu-Ray Java (BD-JB)         — FW 9.00 — 13.00  │  │
│  │ D: Lua-скрипты (luac0re)        — FW 9.00 — 12.02  │  │
│  │ E: Эмулятор PS2 (Mast1c0re)     — FW 5.05 — 12.50+ │  │
│  │ F: Медиа-приложения (Netflix/Vue)— FW 7.00 — 13.00 │  │
│  └─────────────────────────────────────────────────────┘  │
└──────────────────────┬────────────────────────────────────┘
                       ▼
┌───────────────────────────────────────────────────────────┐
│  ШАГ 4: СТАБИЛИЗАЦИЯ И УПРАВЛЕНИЕ ПАМЯТЬЮ                │
│  • < FW 9.60: Heap Feng Shui                              │
│  • ≥ FW 9.60: NetCat GUI / Remote XML / Java-консоль      │
└──────────────────────┬────────────────────────────────────┘
                       ▼
┌───────────────────────────────────────────────────────────┐
│  ШАГ 5: ТРИГГЕР ЯДРА (KERNEL EXPLOITS)                   │
│  ┌─────────────────────────────────────────────────────┐  │
│  │ Исторические: BadIRET / NamedOBJ / BPF Race         │  │
│  │ Флешка: exfathax (pOOBs4)         — FW 9.00        │  │
│  │ Сеть: PPPoE эмуляция              — FW 11.00       │  │
│  │ LAPSE (abc/Gezine)                — FW 9.00 — 12.02│  │
│  │ POOPSPLOIT (TheFlow/15432)        — FW 12.50—13.00 │  │
│  └─────────────────────────────────────────────────────┘  │
└──────────────────────┬────────────────────────────────────┘
                       ▼
┌───────────────────────────────────────────────────────────┐
│  ШАГ 6: ЗАГРУЗКА И ВЫБОР СРЕДЫ (XPLOIT ENABLER)          │
│  • GoldHEN (v2.4+)                    — FW ≤ 11.00       │
│  • HEN-vtx (EchoStretch)              — FW 11.02—13.00   │
└──────────────────────┬────────────────────────────────────┘
                       ▼
┌───────────────────────────────────────────────────────────┐
│  ШАГ 7: ИТОГОВЫЙ ИНТЕРФЕЙС И ЗАПУСК КОНТЕНТА             │
│  • Debug Settings → Package Installer                     │
│  • PS4 Homebrew Store                                     │
│  • Itemzflow Manager                                      │
│  • PS4 Linux Loader                                       │
└───────────────────────────────────────────────────────────┘
```

---

# PS4 — Таблица эксплойтов по прошивкам

| FW версия | Userland Entry | Kernel Exploit | Среда (HEN) | Метод запуска |
|:----------|:---------------|:---------------|:------------|:--------------|
| 1.76 | WebKit | BadIRET | — | Браузер |
| 4.07 | WebKit | NamedOBJ | — | Браузер |
| 4.55 — 5.05 | WebKit / psFree | BPF Race | GoldHEN | Браузер |
| 5.05 — 6.72 | WebKit / psFree | BPF Race | GoldHEN | Браузер |
| 7.00 — 7.55 | PPPwn / WebKit | BPF Race | GoldHEN | Сеть / Браузер |
| 9.00 | BD-JB / WebKit | exfathax (pOOBs4) | GoldHEN | Флешка exFAT |
| 9.60 | BD-JB / WebKit | LAPSE | GoldHEN | Браузер / BD-JB |
| 10.00 — 10.50 | BD-JB / PPPwn | LAPSE | GoldHEN | Сеть / BD-JB |
| 10.70 — 11.00 | BD-JB / PPPwn / Lua | LAPSE | GoldHEN | Сеть / BD-JB / Lua |
| 11.02 | BD-JB / Lua | LAPSE | HEN-vtx | BD-JB / Lua |
| 12.00 — 12.02 | BD-JB / Lua | LAPSE | HEN-vtx | BD-JB / Lua |
| 12.50 — 13.00 | BD-JB / Vue | POOPSPLOIT | HEN-vtx | BD-JB / Vue |

---

# PS4 — Ссылки на официальные GitHub

| Репозиторий | Описание |
|:------------|:---------|
| [🎯 **GoldHEN**](https://github.com/GoldHEN/GoldHEN) | Главный HEN-анблокер для PS4 (FW ≤ 11.00). Меню, читы, темы, fPKG |
| [🎯 **Henloader_LP**](https://github.com/GoldHEN/henloader_lp) | Blu-Ray загрузчик LAPSE эксплойта для высоких прошивок |
| [🎯 **PPPwn**](https://github.com/TheOfficialFloW/PPPwn) | Сетевой эксплойт через PPPoE (FW 7.00 — 11.00) от TheFlow |
| [🎯 **PPPwn GUI**](https://github.com/TheOfficialFloW/PPPwn_GUI) | Графическая оболочка для PPPwn |
| [🎯 **PPPwn Lite**](https://github.com/TheOfficialFloW/PPPwn_lite) | Облегченная версия PPPwn для слабых устройств |
| [🎯 **pOOBs4**](https://github.com/CyFi360/pOOBs4) | exFAT флеш-эксплойт для FW 9.00 |
| [🎯 **PS4 Exploit Host**](https://github.com/chronoss09/PS4ExploitHost) | Хостинг эксплойтов через ПК / Raspberry Pi |
| [🎯 **BD-JB**](https://github.com/chronoss09/BD-JB) | Blu-Ray Java джейлбрейк для высоких прошивок |
| [🎯 **ps4-hen-vtx**](https://github.com/EchoStretch/ps4-hen-vtx) | HEN-vtx для FW 11.02 — 13.00 от EchoStretch |
| [🎯 **Itemzflow**](https://github.com/LightningMods/Itemzflow) | Менеджер файлов, дампер дисков и лаунчер fPKG |
| [🎯 **PS4 Linux Loader**](https://github.com/ps4linux/ps4-linux-loader) | Загрузчик Linux на PS4 с 3D-ускорением |
| [🎯 **PS4 Homebrew Store**](https://github.com/ps4homebrew/ps4_hb_store) | Магазин Homebrew софта для PS4 |
| [🎯 **NetCat GUI**](https://github.com/stooged/PS4-NetCat-GUI) | Отправка payload через графический NetCat |
| [🎯 **Handy**](https://github.com/stooged/PS4-Handy) | Утилита отправки ELF-файлов с ПК / смартфона |
| [🎯 **Vue After Free**](https://github.com/stooged/Vue-After-Free) | Эксплойт через приложение PlayStation Vue |

---

# PS5 — Блок-схема установки и запуска джейлбрейка

```
┌───────────────────────────────────────────────────────────┐
│  ШАГ 1: ПОДГОТОВКА И ПРОВЕРКА                             │
│  • Проверка версии System Firmware в настройках           │
│  • Установка кастомных DNS (Al-Azif) для блокировки OTA   │
└──────────────────────┬────────────────────────────────────┘
                       ▼
┌───────────────────────────────────────────────────────────┐
│  ШАГ 2: ВЫБОР ТОЧКИ ВХОДА (USERLAND)                     │
│  ┌─────────────────────────────────────────────────────┐  │
│  │ До FW 5.50:      Браузер (WebKit / PSFree)         │  │
│  │ До FW 12.00—12.40: YouTube (Y2JB)                  │  │
│  │ До FW 12.70:      PS2-игра (P2JB через Lua)        │  │
│  │ До FW 13.20:      Blu-Ray диск (BD-UN-JB)          │  │
│  └─────────────────────────────────────────────────────┘  │
└──────────────────────┬────────────────────────────────────┘
                       ▼
┌───────────────────────────────────────────────────────────┐
│  ШАГ 3: ЗАПУСК ОПТИМИЗАТОРА                               │
│  • Popsploit — ускорение триггера ядра (стабилизация RAM) │
└──────────────────────┬────────────────────────────────────┘
                       ▼
┌───────────────────────────────────────────────────────────┐
│  ШАГ 4: СРАБАТЫВАНИЕ ЭКСПЛОЙТА ЯДРА (KERNEL)             │
│  • Уязвимость UMTX → права Read/Write на ядро             │
│  • Уведомление: "Kernel Exploit Affected!"                │
└──────────────────────┬────────────────────────────────────┘
                       ▼
┌───────────────────────────────────────────────────────────┐
│  ШАГ 5: АКТИВАЦИЯ ELF-ЗАГРУЗЧИКА (elfldr)                │
│  • Открытие портов 9019/9020 — ожидание ELF с ПК/телефона │
│  • Экран становится белым или показывает логи              │
└──────────────────────┬────────────────────────────────────┘
                       ▼
┌───────────────────────────────────────────────────────────┐
│  ШАГ 6: ОТПРАВКА СРЕДЫ / ПОЛЕЗНОЙ НАГРУЗКИ               │
│  • Утилита Handy с ПК или смартфона                        │
│  • Ввод IP-адреса консоли и отправка .elf файла           │
└──────────────────────┬────────────────────────────────────┘
                       ▼
┌───────────────────────────────────────────────────────────┐
│  ШАГ 7: ВЫБОР ГРАФИЧЕСКОЙ ОБОЛОЧКИ И РЕЖИМА             │
│  ┌─────────────────────────────────────────────────────┐  │
│  │ A: VoidShell — Всё в одном (fPKG + Kstuff патчи)   │  │
│  │ B: Elf Arsenal — Wi-Fi управление (бывш. SonicLD)  │  │
│  │ C: etaHEN — Классический HEN в фоне                │  │
│  └─────────────────────────────────────────────────────┘  │
└──────────────────────┬────────────────────────────────────┘
                       ▼
┌───────────────────────────────────────────────────────────┐
│  ШАГ 8: ФИНАЛЬНЫЙ РЕЗУЛЬТАТ                               │
│  • Запуск бэкапов игр через Itemzflow                      │
│  • Запуск Linux через ps5-linux-loader                     │
└───────────────────────────────────────────────────────────┘
```

---

# PS5 — Таблица эксплойтов по прошивкам

| FW версия | Userland Entry | Kernel Exploit | Среда (HEN) | Метод запуска |
|:----------|:---------------|:---------------|:------------|:--------------|
| 1.xx — 4.xx | WebKit / PSFree | UMTX | etaHEN | Браузер |
| 5.00 — 5.50 | WebKit / PSFree | UMTX | etaHEN / VoidShell | Браузер |
| 6.00 — 7.00 | WebKit | UMTX | etaHEN / VoidShell | Браузер |
| 8.00 — 12.00 | YouTube (Y2JB) | UMTX | VoidShell / Elf Arsenal | Приложение YouTube |
| 12.01 — 12.40 | YouTube (Y2JB) | UMTX | VoidShell / Elf Arsenal | Приложение YouTube |
| 12.50 — 12.70 | PS2-игра (P2JB) | UMTX | VoidShell / Elf Arsenal | PS2-диск + флешка |
| 12.71 — 13.20 | Blu-Ray (BD-UN-JB) | UMTX | VoidShell / Elf Arsenal | Blu-Ray диск |

---

# PS5 — Ссылки на официальные GitHub

| Репозиторий | Описание |
|:------------|:---------|
| [🎯 **VoidShell**](https://github.com/stooged/VoidShell) | Главная графическая оболочка для PS5 (fPKG + Kstuff) |
| [🎯 **etaHEN**](https://github.com/LightningMods/etaHEN) | HEN-анблокер для PS5, работающий в фоне |
| [🎯 **Elf Arsenal**](https://github.com/LightningMods/Elf-Arsenal) | Веб-панель управления PS5 (бывший Sonic Loader) |
| [🎯 **BD-UN-JB**](https://github.com/LightningMods/BD-UN-JB) | Blu-Ray джейлбрейк для высоких прошивок PS5 |
| [🎯 **P2JB**](https://github.com/chronoss09/P2JB) | Эксплойт через PS2-игру для PS5 |
| [🎯 **Y2JB**](https://github.com/chronoss09/Y2JB) | Эксплойт через приложение YouTube для PS5 |
| [🎯 **ps5-linux-loader**](https://github.com/ps5linux/ps5-linux-loader) | Загрузчик Linux на PS5 |
| [🎯 **Itemzflow PS5**](https://github.com/LightningMods/Itemzflow) | Лаунчер игр и файловый менеджер для PS5 |
| [🎯 **Handy**](https://github.com/stooged/PS5-Handy) | Отправка payload на PS5 с ПК / смартфона |

---

# Полезные ссылки и сообщества

| Ресурс | Ссылка | Описание |
|:-------|:-------|:---------|
| 📺 Modded Warfare | [YouTube](https://www.youtube.com/watch?v=EdserHNynL4) | Главный гайд-канал по взлому PlayStation |
| 📖 ConsoleMods Wiki | [PS4 Exploit Chart](https://consolemods.org/wiki/PS4:Exploit_Chart) | Сводная таблица всех эксплойтов PS4 |
| 📖 ConsoleMods Wiki | [PS4 Getting Started](https://consolemods.org/wiki/PS4:Getting_Started) | Полное руководство по началу взлома PS4 |
| 📺 Modded Warfare Guide | [YouTube](https://www.youtube.com/watch?v=ZFsvV70GkzQ) | Подробный гайд по BD-JB и LAPSE |
| 📺 Modded Warfare PS5 | [YouTube](https://www.youtube.com/watch?v=iuEPhhJYrVU) | Гайд по джейлбрейку PS5 |
| 💬 Reddit PS4Homebrew | [r/ps4homebrew](https://www.reddit.com/r/ps4homebrew/) | Главное сообщество по взлому PS4 |
| 💬 Reddit PS5Homebrew | [r/ps5homebrew](https://www.reddit.com/r/ps5homebrew/) | Сообщество по взлому PS5 |

---

## ⚠️ Важные замечания

1. **FW 13.02+ для PS4**: Sony закрыла уязвимость `__sys_netcontrol` и изменила правила Java в дисководе. Консоли на 13.02+ намертво закрыты.
2. **FW 13.20+ для PS5**: На данный момент эксплойты для прошивок выше 13.20 отсутствуют.
3. **HEN-vtx на PS4 FW 12.50—13.00**: Работает «вслепую» в фоне, но функционала достаточно для Debug Settings и запуска fPKG.
4. **Vue After Free**: Приложение PlayStation Vue имеет системный доступ к вызову `dup`. Если установить его до FW 13.00 (через бэкап), джейлбрейк запускается без диска и сети.

---

<div align="center">

**⭐ Если этот roadmap был полезен — поставьте звезду!**

[![GitHub stars](https://img.shields.io/github/stars/q7c/PS4-5JB-roadmap?style=social)](https://github.com/q7c/PS4-5JB-roadmap)

</div>
