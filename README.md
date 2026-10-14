# Legendary Guide Desktop

## Run your own desktop

After forking, create or open a Codespace (or another private environment) from
your fork. Each environment should use its own VNC password and browser
profile; do not share the original Codespace.

1. Create a local environment file and browser profile directory:

   ```sh
   cp .env.example .env
   chmod 600 .env
   mkdir -p chrome-profile
   chmod 700 chrome-profile
   ```

2. Edit `.env` and replace the example value with your own VNC password.
3. Start the desktop:

   ```sh
   docker compose up --build -d
   ```

`.env` and `chrome-profile/` are local-only and ignored by Git. A fresh
Codespace from the updated branch gets its own VNC password and an empty browser
profile. Never commit or share `.env` or `chrome-profile/`.

**History warning:** browser profile files were tracked in earlier commits.
Removing them from the current branch does not remove them from Git history or
from existing forks. Until that history is cleaned up, old profile data may
still be accessible to people with repository history. If that history was
public, treat saved passwords and active sessions as exposed: change passwords
and sign out other sessions.
