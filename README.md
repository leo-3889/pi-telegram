# pi-telegram (fork)

Fork of [badlogic/pi-telegram](https://github.com/badlogic/pi-telegram) (via [llblab/pi-telegram](https://github.com/llblab/pi-telegram)).
Setup, commands, pairing, settings, and architecture: see the [base README](https://github.com/badlogic/pi-telegram#readme).
This page lists only the fork's additions.

## `stream` activity mode — one message per agent turn

Set `assistant.activity: "stream"` (Telegram: **Settings → Activity → stream**).

- One live message per turn, edited in place instead of a new message per event.
- Thinking → expandable `💭` blockquote. Tool calls → one quote block of compact lines (`🔧 Bash done` + one redacted arg line), max 8 with `… [N earlier tools]` trimming. The answer streams as the clean tail.
- At turn end the streamed message is deleted and the final answer is delivered as its own cleanly rendered message.
- Native draft previews and intermediate segment sends auto-pause while streaming.
- Edit throttle 2 s; immediate on tool start/end; final publish at agent settle; 3900-char cap with tool-line trimming (answer tail always kept).

Branch: `feature/stream-single-message`. PR to `llblab/pi-telegram:main`: upstreaming the mode.
