RENDER DEPLOYMENT - FIXED

Files to put in GitHub repo root:
- hosting_render_fixed.py
- requirements.txt
- render.yaml

Build Command:
pip install -r requirements.txt

Start Command:
python hosting_render_fixed.py

Environment variables:
BOT_TOKEN = your Telegram bot token
ADMIN_ID = your numeric Telegram user/chat ID
STORAGE_DIR = /var/data

IMPORTANT:
The program now checks whether STORAGE_DIR is writable. If /var/data is not mounted or is not writable, it automatically falls back to a writable directory instead of crashing with PermissionError.

For persistence, attach a Render Persistent Disk and mount it at /var/data. If no disk is attached, the fallback storage is ephemeral and files can be lost on redeploy/restart.

Bot flow:
Admin uploads .py -> imports detected -> missing packages installed -> script starts -> host bot username shown.

Only the configured ADMIN_ID can upload/host files.
