# VOLUMIO-Custom-Keyboard
On screen keyboard for Volumio

sudo apt-get install matchbox-window-manager matchbox-keyboard
sudo chmod 777 /opt/volumiokiosk.sh
sudo nano /opt/volumiokiosk.sh

#!/bin/bash
xset +dpms
xset s blank
xset 0 0 120

matchbox-keyboard -d &
matchbox-window-manager -use_titlebar no &

while true; do
  /usr/bin/chromium-browser \
    --no-touch-pinch \
    --kiosk \
    --no-first-run \
    --disable-3d-apis \
    --disable-breakpad \
    --disable-crash-reporter \
    --disable-infobars \
    --disable-session-crashed-bubble \
    --disable-translate \
    --no-sandbox     http://localhost:3000
done

#If you want a different keyboard layout, you can copy a custom keyboard.xml to /root/.matchbox/.
