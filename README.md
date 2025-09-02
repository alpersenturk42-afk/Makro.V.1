# Makro.V.1
Makro.V.1
import keyboard
import threading
import time
from colorama import init, Fore, Style

init(autoreset=True)

running = False

def themed_log(message, color=Fore.CYAN):
    print(color + Style.BRIGHT + f"[MakroBot] {message}")

def macro_loop():
    global running
    themed_log("Makro başlatıldı ✅", Fore.GREEN)
    while running:
        # Örnek işlem: Her 2 saniyede bir mesaj yaz
        themed_log("Makro çalışıyor... ⏳", Fore.YELLOW)
        # Buraya mouse hareketi, tıklama veya yazı eklenebilir
        time.sleep(2)
    themed_log("Makro durduruldu ❌", Fore.RED)

def start_macro():
    global running
    if not running:
        running = True
        threading.Thread(target=macro_loop).start()

def stop_macro():
    global running
    running = False

themed_log("Makro sistemi hazır. F6 ile başlat, F5 ile durdur.", Fore.MAGENTA)

keyboard.add_hotkey('F6', start_macro)
keyboard.add_hotkey('F5', stop_macro)

# Programı açık tut
keyboard.wait('esc')  # ESC tuşuna basıldığında çıkılır