# KC Chats 0.1 (development)

KC Chats is an independent Telegram Desktop fork, based on upstream 7.3.3.
It uses Telegram's service and existing chat-filter implementation.

## First pass

- Labeled horizontal folder tabs are the default for a fresh KC Chats profile.
- Settings > Chat Folders offers People, Groups, Channels, and Bots with plain descriptions.
- People includes contacts and other direct conversations; automated accounts belong in Bots.
- Each starter excludes archived chats. Existing equivalent filter rules suppress duplicate suggestions.
- Adding a starter is an explicit action and follows Telegram's ordinary save path and folder limits.
- Saved folders sync to other Telegram clients. Existing folders remain available.

## Windows identity

The Windows binary is named KCChats.exe and has its own icon, app ID, application
name, and default data directory (%APPDATA%/KC Chats). Official auto-updates and
crash reporting are disabled. Startup does not register Telegram URL protocols.
The existing explicit URL-handler action remains available if the user chooses it.
Do not point KC Chats at an existing Telegram profile or copy its tdata directory.

## Build and acceptance

The source changes have passed git diff --check. The Windows compiler was detected,
but initial configuration stopped because Qt was not installed. Upstream's Windows
dependency preparation is in progress. Compilation and interactive acceptance are
pending; this is not yet a verified usable app.

Prepare dependencies with Telegram/build/prepare/prepare.py using the upstream
Windows instructions. For development, configure with:

    python Telegram/configure.py x64 -D TDESKTOP_API_TEST=ON
    cmake --build out --config Debug --target Telegram

Use Debug builds for local development. The public test API configuration is for
development only. Before distributing a build, obtain an application API ID and
hash through Telegram's developer portal and configure them locally; do not commit
private credentials. No API credentials or account data are included here.

Runtime acceptance must check the new profile's login screen, distinct icon/name,
the folder suggestions and labels, and classification after a user-authorized login.

## License

The upstream GPLv3 license with OpenSSL exception and third-party notices remain
in force. See LICENSE and LEGAL. Modifications copyright (C) 2026 KCCS.
