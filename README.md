# 📘 Краткая методичка: Установка и настройка Python  
**Windows + Linux** | 10 минут до работающего кода

---

## 🎯 Что будет в итоге
- Python 3.12+ установлен  
- Виртуальное окружение создано  
- Jupyter запущен  
- Git настроен  

---

## 🪟 Windows (3 минуты)

### 1. Скачать установщик
- Переходим на [python.org/downloads]([https://www.python.org/downloads/](https://www.python.org/downloads/release/python-31210/))
- Жмём **"Download Python 3.12.x"**
- Запускаем `.exe` ➝ **ВАЖНО**: ставим галку **"Add Python to PATH"**

### 2. Проверить в PowerShell
```powershell
python --version        # Должно вывести 3.12.x
pip --version           # Должен быть доступен
```

### 3. Создать виртуальное окружение
```powershell
cd C:\Users\%USERNAME%\Projects
python -m venv venv
.\venv\Scripts\activate   # (venv) появится слева
```

### 4. Установить пакеты интенсива
```powershell
# Установите библиотеку torch с поддержкой библиотеки cuda (если присутствует видеокарточка Nvidia)
pip install torch==2.9.1 torchvision==0.24.1 torchaudio==2.9.1 --index-url https://download.pytorch.org/whl/cu126
# Установите остальные полезные библиотеки
pip install matplotlib jupyter ipykernel gradio python-telegram-bot opencv-python
```

### 5. Запустить Jupyter
```powershell
jupyter lab               # Откроется браузер
```

---

## 🐧 Linux (Ubuntu/Debian, 3 минуты)

### 1. Обновить и установить Python
```bash
sudo apt update && sudo apt upgrade -y
sudo apt install python3.12 python3.12-venv python3-pip -y
```

### 2. Сделать `python3` дефолтным
```bash
sudo update-alternatives --install /usr/bin/python python /usr/bin/python3.12 1
python --version          # 3.12.x
```

### 3. Создать проект и окружение
```bash
mkdir -p ~/projects/neural-intensive
cd ~/projects/neural-intensive
python -m venv venv
source venv/bin/activate  # (venv) появится
```

### 4. Установить зависимости
```bash
pip install --upgrade pip
# Установите библиотеку torch с поддержкой библиотеки cuda (если присутствует видеокарточка Nvidia)
pip install torch==2.9.1 torchvision==0.24.1 torchaudio==2.9.1 --index-url https://download.pytorch.org/whl/cu126
# Установите остальные полезные библиотеки
pip install matplotlib jupyter ipykernel gradio python-telegram-bot opencv-python
```

### 5. Запустить Jupyter
```bash
jupyter lab --no-browser --ip=0.0.0.0 --port=8888
# Открыть ссылку в браузере
```

---

## ⚙️ Общие настройки (2 минуты)

### 1. Git (одинаково на Windows/Linux)
```bash
git config --global user.name "Ваше Имя"
git config --global user.email "email@example.com"
git config --global init.default-branch main
```

### 2. Jupyter kernel внутри venv
```bash
python -m ipykernel install --user --name neural --display-name "Neural Intensive"
```

### 3. Проверка перед интенсивом
```bash
python -c \"import torch; print(torch.__version__)\"   # 2.x.x
jupyter lab --version                                 # 3.x.x или 4.x.x
git --version                                         # 2.x.x
```

---

## 🧪 Быстрый тест (1 минута)

Создайте файл `test.py`:
```python
import torch, cv2, matplotlib, gradio
print("✅ Все пакеты установлены!")
print(f"PyTorch: {torch.__version__}")
print(f"CUDA доступен: {torch.cuda.is_available()}")
```

Запустите:
```bash
python test.py
```

---

## 📦 Готовый `requirements.txt` для интенсива

Сохраните как `requirements.txt`:
```
torch==2.9.1
torchvision==0.24.1
matplotlib==3.10.1
jupyterlab==4.3.5
opencv-python==4.11.0.86
gradio==6.4.0
python-telegram-bot==22.6
facenet-pytorch==2.6.0
scikit-learn==1.7.2
tqdm==4.67.1
```

Установка одной командой:
```bash
pip install -r requirements.txt
```

---

## ❓ Частые проблемы

| Проблема | Решение |
|---------|---------|
| **"python не найден"** | Используйте `python3` или добавьте в PATH |
| **"pip не найден"** | `python -m ensurepip --upgrade` |
| **"CUDA не видит GPU"** | Установите `pip install torch==2.9.1 torchvision==0.24.1 torchaudio==2.9.1 --index-url https://download.pytorch.org/whl/cu128` |
| **"Jupyter не открывается"** | `jupyter lab --ip=0.0.0.0 --port=8888 --no-browser` |

---

## 🎯 Итог: 10 минут и вы готовы!

1. **Windows**: Установщик + PowerShell  
2. **Linux**: `apt install` + терминал  
3. **Общее**: venv + pip + jupyter + git  

Готово к интенсиву!

