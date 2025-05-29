za_auto_core: نسخة ذكية قابلة للتطوير الذاتي

import os import json import time from datetime import datetime

==== إعداد الذاكرة الذاتية ====

MEMORY_FILE = "self_memory.json" def load_memory(): if os.path.exists(MEMORY_FILE): with open(MEMORY_FILE, 'r', encoding='utf-8') as f: return json.load(f) return {"log": [], "version": "1.0", "actions_done": 0}

def save_memory(mem): with open(MEMORY_FILE, 'w', encoding='utf-8') as f: json.dump(mem, f, indent=2, ensure_ascii=False)

memory = load_memory()

==== وظائف ذكية بسيطة ====

def auto_scan(): print("[🔍] فحص المجلد الحالي...") files = os.listdir('.') for f in files: if f.endswith('.txt'): analyze_file(f)

def analyze_file(filename): print(f"[📄] تحليل الملف: {filename}") with open(filename, 'r', encoding='utf-8') as f: content = f.read() words = len(content.split()) memory['log'].append({ "file": filename, "words": words, "time": datetime.now().isoformat() }) memory['actions_done'] += 1 save_memory(memory) print(f"[✅] تم تحليل: {words} كلمة")

==== التحديث الذاتي (قيد التطوير) ====

def self_update(): print("[🧠] التحقق من وجود تحديثات... (قيد التطوير)") # هنا يمكنك ربطه بمستودع GitHub لاحقًا return False

==== التشغيل الأساسي ====

def main(): print("\n🤖 Za-AutoCore v" + memory['version']) print("[🚀] تشغيل الذكاء الذاتي...") time.sleep(1) auto_scan() print("[📝] عدد العمليات: ", memory['actions_done'])

if name == "main": main()

