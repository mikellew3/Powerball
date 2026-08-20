# The Bulldog League — Draft Drum

A Powerball-style drawing machine for setting fantasy football draft order. Twelve
balls tumble in a glass drum, each one carrying a manager's name. They pop out one
at a time, and the order they come out **is** the draft order — first ball out takes
the first overall pick.

Themed to the league mark: forest green, black and bone. The drum wears a studded
bulldog collar, the C rides on the back of the glass, and the ball that comes out
first is a forest-green one so the top pick is unmistakable on video.

Built to be screen-recorded: 16:9 broadcast layout, big legible type, a countdown
before every ball, and a final frame that shows the whole order at once.

## Running it

It is a single self-contained file. Open `index.html` in any modern browser — no
server, no build, no install. To share it with the league, drop the file in any
static host (GitHub Pages works: enable Pages on this repo and point it at the
branch root).

## Setting up your league

The setup screen loads first. Enter your league name and one manager per line, then
hit **Load the drum**. You can also drop in the league logo — it gets scaled down,
ghosted onto the back of the drum in place of the C, and kept in your browser. PNG,
JPG and SVG all work. Names are saved in the browser, so the next time you open it
your roster and logo are already there. Anywhere from 2 to 24 names works; 12 is the sweet
spot for how the drum and tray are sized.

## Recording the draw

1. Open the page and set your roster.
2. Press **F** (or click Fullscreen) — the whole thing scales to fill the screen.
3. Start your screen recorder. Grab system audio if you want the blower and the
   chimes.
4. Click **Start the drawing**.

With **Auto** on, the machine runs itself: about three seconds to the first ball,
then roughly five between picks, with an on-screen countdown. A full 12-man draw
takes a bit over a minute and a half — one continuous take, no clicking during the
recording.

Turn **Auto** off if you would rather build suspense yourself: the drum keeps
churning until you press **Draw next ball** (or Space) for each pick.

### Controls

| Key | Does |
| --- | --- |
| `Space` | Start the drawing, or pull the next ball |
| `F` | Fullscreen |
| `M` | Mute |

Once all the balls are out, Space is deliberately dead — so a stray keypress can't
wipe the final board mid-recording. Use **Run it again** to redraw.

**Copy order** puts the finished order on your clipboard as plain text, along with
the draw ID and timestamp, ready to paste into the league chat.

## Is it actually random?

Yes. The order is drawn once, up front, with a Fisher–Yates shuffle over
`crypto.getRandomValues()` — the browser's cryptographic entropy source, not
`Math.random()`. Values are rejection-sampled so every ordering is equally likely,
with no modulo bias toward the low seats.

Every drawing gets an ID and timestamp in the top right corner. It carries through
to the copied results, so the screen recording and the text you post to the league
chat can be matched to each other.

The balls tumbling in the drum are pure showmanship — the physics has no say in the
outcome. The result is already decided when you press start; the drum just makes it
fun to watch.
