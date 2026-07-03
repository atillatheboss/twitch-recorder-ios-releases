# Twitch Recorder iOS App

Flutter companion app for the existing Node.js Twitch Recorder server.

The iPhone app does not run Streamlink or FFmpeg itself. Keep the Node server
running on your Mac, NAS, or Docker host and connect the app to that server over
your local network or VPN.

## Run In The iOS Simulator

From this directory:

```bash
flutter run
```

Default server URL inside the app:

```text
http://127.0.0.1:3001
```

This works for the iOS Simulator when the Node server runs locally with:

```bash
npm start
```

## Run On An iPhone

1. Start the recorder server on the host machine.
2. Find the host's LAN IP address, for example `192.168.178.20`.
3. Open the app's server sheet and set:

```text
http://192.168.178.20:3001
```

When using Docker Compose, use the mapped host port:

```text
http://192.168.178.20:3002
```

You can also bake a default URL into a local build:

```bash
flutter run --dart-define=RECORDER_BASE_URL=http://192.168.178.20:3001
```

## License Server

Commercial app builds can require a license server:

```bash
flutter run \
  --dart-define=LICENSE_SERVER_URL=https://licenses.example.com \
  --dart-define=LICENSE_APP_ID=twitch-recorder-ios
```

The app posts license checks to `/api/licenses/verify` by default. Override the
path with `LICENSE_VERIFICATION_PATH` if your server uses a different route.

Request body:

```json
{
  "licenseKey": "USER-LICENSE-KEY",
  "installationId": "stable-local-installation-id",
  "appId": "twitch-recorder-ios",
  "platform": "ios"
}
```

Expected success response:

```json
{
  "valid": true,
  "message": "License active",
  "plan": "pro",
  "holder": "Customer Name",
  "expiresAt": "2027-01-01T00:00:00Z"
}
```

Without a valid license, the app locks recorder, recordings, VOD/download,
local media actions, and metrics. Settings remain available so users can enter
or refresh the license key. A previously valid license can be used offline for
up to three days while the license server is temporarily unreachable.

## Build For iOS

```bash
flutter build ios --no-codesign \
  --dart-define=LICENSE_SERVER_URL=https://licenses.example.com
```

For installation on a physical iPhone, open `ios/Runner.xcworkspace` in Xcode,
select your Apple development team, set a bundle identifier, and run the app on
the device.

## Implemented App Areas

- Recorder start form with quality, schedule, duration/end time, chat toggle,
  channel suggestions, and per-channel extra chat selection
- Twitch channel suggestions with live/offline status while typing in recorder,
  extra chat, and VOD search fields
- Active and scheduled jobs with pause, resume, stop, cancel, and extend actions
- Recordings library with MP4/HLS link copy, MP4 finalization, processing control,
  native iOS playback, and delete action
- VOD and clip search with separate VOD/Clip tabs plus server-side download controls
- Download jobs and downloaded media list with native iOS playback
- Dedicated metrics tab and recorder settings

Playback is implemented through a small iOS `AVPlayerViewController` bridge in
`ios/Runner/AppDelegate.swift`, not through an additional Flutter plugin.
