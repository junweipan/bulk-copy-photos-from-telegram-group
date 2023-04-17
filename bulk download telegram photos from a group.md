## App configuration
**App api_id: xxxx**
**App api_hash: **xxxxxxxxxxxxxxxxxxxxxxx
**App title: **Skybot
**Short name: **demo project for download images
alphanumeric, 5-32 characters
### Available MTProto servers
**Test configuration:**
**149.154.167.40:443**
DC 2
**Public keys:**
```
-----BEGIN RSA PUBLIC KEY-----
MIIBCgKCAQEAyMEdY1aR+sCR3ZSJrtztKTKqigvO/vBfqACJLZtS7QMgCGXJ6XIR
yy7mx66W0/sOFa7/1mAZtEoIokDP3ShoqF4fVNb6XeqgQfaUHd8wJpDWHcR2OFwv
plUUI1PLTktZ9uW2WE23b+ixNwJjJGwBDJPQEQFBE+vfmH0JP503wr5INS1poWg/
j25sIWeYPHYeOrFp/eXaqhISP6G+q2IeTaWTXpwZj4LzXq5YOpk4bYEQ6mvRq7D1
aHWfYmlEGepfaYR8Q0YqvvhYtMte3ITnuSJs171+GDqpdKcSwHnd6FudwGO4pcCO
j4WcDuXc2CTHgH8gFTNhp/Y8/SpDOhvn9QIDAQAB
-----END RSA PUBLIC KEY-----
```

**Production configuration:**
**149.154.167.50:443**
DC 2
**Public keys:**
```
-----BEGIN RSA PUBLIC KEY-----
MIIBCgKCAQEA6LszBcC1LGzyr992NzE0ieY+BSaOW622Aa9Bd4ZHLl+TuFQ4lo4g
5nKaMBwK/BIb9xUfg0Q29/2mgIR6Zr9krM7HjuIcCzFvDtr+L0GQjae9H0pRB2OO
62cECs5HKhT5DZ98K33vmWiLowc621dQuwKWSQKjWf50XYFw42h21P2KXUGyp2y/
+aEyZ+uVgLLQbRA1dEjSDZ2iGRy12Mk5gpYc397aYp438fsJoHIgJ2lgMv5h7WY9
t6N/byY9Nw9p21Og3AoXSL2q/2IJ1WRUhebgAdGVMlV1fkuOQoEzR7EdpqtQD9Cs
5+bfo3Nhmcyvk5ftB0WkJ9z6bNZ7yxrP8wIDAQAB
-----END RSA PUBLIC KEY-----
```

```python
from telethon import TelegramClient
import telethon.sync

import asyncio
import socks

api_id = PLACE_YOUR_APP_ID_HERE
api_hash = PLACE_YOUR_API_HASH_HERE

# to use with TOR proxy
#client = TelegramClient('my_session', api_id, api_hash, proxy=(socks.SOCKS5, 'localhost', 9150))
# to use without proxy
client = TelegramClient('my_session', api_id, api_hash)

client.start()

def load_messages():
    dialogs = client.get_dialogs()
    chat = None

    for dialog in dialogs:
        if dialog.name == YOUR_GROUP_NAME_HERE: # 'xxxxxxx'
            chat = dialog
            break

    for message in client.iter_messages(chat):
        if message.media:
            print('Downloading...')
            client.download_media(message)

load_messages()
```
