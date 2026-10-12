# ArduPilot Python PID

Навчальний проєкт із керування висотою ArduPilot Copter SITL власним PID-контролером через Python і MAVLink.

<details>
<summary><strong>0. Етапи розробки</strong></summary>

0. Основа проєкту
1. ArduPilot SITL і QGroundControl і Структура репозиторію
2. Робота з MAVLink
3. Вивчення, реалізація та тест PID-контролера
4. Керування Copter
5. Тестовий політ у SITL
6. Повна висотна місія
7. Перевірка стабільності
8. Фінальна документація

</details>

<details>
<summary><strong>1. ArduPilot SITL і QGroundControl і Структура репозиторію</strong></summary>

Перевірене середовище - macOS | 15.7.3 (24G419), Apple Silicon

### Встановлення ArduPilot

```bash
git clone --recurse-submodules https://github.com/ArduPilot/ardupilot.git
cd ardupilot

python3.11 -m venv .venv
source .venv/bin/activate
/bin/bash ./Tools/environment_install/install-prereqs-mac.sh
```

### Збірка Copter SITL

```bash
source .venv/bin/activate
./waf configure --board sitl
./waf copter
```

### Запуск Copter SITL

```bash
source .venv/bin/activate
./Tools/autotest/sim_vehicle.py \
  -v ArduCopter \
  -f quad \
  --console \
  --out=127.0.0.1:14551
```

MAVProxy автоматично використовує UDP-порт `14550` для<br>
QGroundControl. Додатково налаштовано UDP-порт `14551`.

### Установлення і перевірка QGroundControl

```bash
brew install --cask qgroundcontrol
open -a QGroundControl
```

</details>
