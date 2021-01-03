# chessMarkable

[![rm1](https://img.shields.io/badge/rM1-supported-green)](https://remarkable.com/store/remarkable)
[![rm2](https://img.shields.io/badge/rM2-needs_shim_or_launcher-yellow)](https://remarkable.com/store/remarkable-2)
[![opkg](https://img.shields.io/badge/OPKG-chessmarkable-blue)](https://github.com/toltec-dev/toltec)
[![launchers](https://img.shields.io/badge/Launchers-supported-green)](https://github.com/reHackable/awesome-reMarkable#launchers)
[![Mentioned in Awesome reMarkable](https://awesome.re/mentioned-badge.svg)](https://github.com/reHackable/awesome-reMarkable)

A chess game for the reMarkable tablet writting using the [pleco](https://crates.io/crates/pleco) chess library which is a port of [Stockfish](https://stockfishchess.org/).

<img src="https://transfer.cosmos-ink.net/VcnXJ/mainmenu.jpg" width="30%">&nbsp;<img src="https://transfer.cosmos-ink.net/pGFAe/2.jpg" width="30%">&nbsp;<img src="https://transfer.cosmos-ink.net/LZ9QT/3.jpg" width="30%">

## Controlling

A chess piece can be moved in two ways:

1. Clicking it once and clicking the spot it's supposed to
2. Clicking it and moving the finger onto the square to move it there on release

The second method has the advantage that it doesn't highlight the chess piece or shows the possible moves.

## FEN

When running the Game with the enviroment variable `RUST_LOG` set to `debug`, the [FEN](https://en.wikipedia.org/wiki/Forsyth%E2%80%93Edwards_Notation) of a board will be output on each move. This is useful for debugging but also for manually saving a game state or resuming it elsewhere since this notation should be compatible with other chess programs/engines.

The reverse can also be done. Running chessmarkable with `-i` set to a FEN, will start any game with the supplied board. That way a game can be resumed or debugging a edge case speed up.

## Installation

### Prebuilt binary/program

- Go the the [releases page](https://github.com/LinusCDE/chessmarkable/releases)
- Get the newest released binary file (the one without any extension) and copy it onto your remarkable, using e.g. FileZilla, WinSCP or scp.
- SSH into your remarkable and mark the file as executable with `chmod +x chess`
- Stop xochitl (the interface) with `systemctl stop xochitl`
- Start the game with `./chessmarkable` (or whatever the binary is called now)
- After you're done, restart xochitl with `systemctl start xochitl`

### Compiling

- Make sure to have rustup and a current toolchain (nightly might be needed)
- Install the [oecore toolchain](https://remarkable.engineering/).
  - If you're not using linux, you might want to adjust the path in `.cargo/config`
- Compile it with `cargo build --release`. It should automatically cross-compile.

## Todo

- Proper own icon(s)
- Clean the code

## reMarkable 2 support

Chessmarkable supports the input of the reMarkable 2 natively but not the framebuffer. For that [this shim](https://github.com/ddvk/remarkable2-framebuffer/) has to be used (or you won't get an image). Luckily current launchers support automaticially launching apps through the shim. So if you use a launcher (oxide or remux), it should just work.

Though, since the framebuffer uses a shim, specific refresh optimization may not apply to the reMarkable 2 and perform a bit worse there (but this is probably nitpicky anyway).

## Credit

- The [pleco](https://crates.io/crates/pleco) library is used as the engine, checking valid moves and providing the bots
- The chess pices are from [pixabay here](https://pixabay.com/vectors/chess-pieces-set-symbols-game-26774/)
