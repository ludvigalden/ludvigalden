# Profile assets

These are the images on the GitHub profile of [ludvigalden](https://github.com/ludvigalden), and the profile README fetches all of them from this directory. The files under `avatar/` are the whole profile picture. The files under `github/` are cut for inlining in GitHub Markdown, which keeps neither inline styles nor the page theme.

## The wanderer

The profile picture is a painted figure in a red robe, a short cape, and a tall pointed hat, walking with a staff along a pale path under a warm evening sky.

The SVG files are not line drawings, because paint on canvas does not survive being reduced to flat vector shapes. Each file carries the painting itself, cut into layers for the landscape, the robe below the waist, the cape and shoulders, the head with its hat, the staff, and the hand. Every layer is a JPEG embedded in the file and cut out by a vector clip path. The landscape and the cloth are painted in behind whatever stands in front of them, so nothing shows through when a layer moves. Where the staff stood in front of the cape's shoulder, the outline from the hood to the shoulder is redrawn, so the cape stays whole when the staff moves away. The staff itself is cut to its wood alone, row by row from its first dark edge to its last, so it carries nothing of what it stood against.

The face is repainted from a photograph. The photograph is frontal while the body faces along the path, to the viewer's right, so the face is given depth, with a rounded head, a brow, nose, lips, and chin that stand out, and eye sockets set in. That surface is turned about 25 degrees the way the body faces and tilted with the hat. The nose swings toward the far cheek and the near cheek opens out, while the far side keeps its cheek and the full width of its jaw, so the face stays as broad as it is. The photograph's side light is evened out, and its colors are replaced tone for tone by those of the painted face, so the features come from the photograph and the paint from the painting. The face has one even outline of its own, from the hat's brim around the jaw and chin. It lies in front of the hood and collar with a soft shadow under the jaw, and at that outline it fades into the painting instead of being cut. The canvas grain is laid back over the face, and the eyes are left a little crisper than the rest.

The eyes and the mouth are separate parts. The irises are lifted out of the face, with the whites painted in behind them, so they can move inside the eye openings. Since the head is turned away, they rest toward their near corners and look sideways at the viewer. An upper lid for each eye, in the skin's own tones, comes down over the iris in a blink. A second version of the mouth and cheeks, the same face smiling a little more, lies over the first and fades in and out.

The layers hang on a small rig in which each turns about its own joint at the feet, the waist, the neck, the elbow, or the hand. A sleeved forearm, made of the robe's own cloth, comes out from under the edge of the cape on the figure's right side and carries the hand and the staff. The elbow stays under the cape, and the forearm's angle is worked out from where the hand needs to be.

| File | Use |
| --- | --- |
| `avatar/wanderer.svg` | The whole picture, still. |
| `avatar/wanderer-animated.svg` | The whole picture, animated. |
| `avatar/wanderer-1024.jpg` | 1024×1024 raster for uploading as the profile picture, since GitHub accepts no SVG there and nothing over 1 MB. |
| `avatar/wanderer-512.jpg` | 512×512 raster. |

In the animated files the figure stands in place and breathes, shifts its weight from foot to foot, and lets the hem settle. Nothing else in the picture moves. Everything the figure does with its face and its staff runs on one 40-second loop:

- The staff hand makes four small gestures. It lifts the staff and sets it down, raises it and waves it, tips its head forward to point the way along the path, and taps the ground twice.
- The eyes rest sideways on the viewer and, with each gesture, jump to the staff or to the path ahead. The head follows a little.
- The blinks come at uneven intervals and with most shifts of the gaze. The lid drops in about 70 milliseconds, rests, and rises more slowly.
- The smile deepens with each gesture and eases off again.

The animation is CSS inside the SVG, so it plays wherever the file is shown as an image, and it stops for readers who have asked their system for reduced motion.

## The GitHub inlining set

| File | Use |
| --- | --- |
| `github/wanderer-portrait.svg` | A closer framing of head, cape, and staff, still, cut to a squircle. The eye line sits at the center, so the top of the hat is cropped. |
| `github/wanderer-portrait-animated.svg` | The same framing, animated, placed inside the profile README's heading and floated to the top right corner. |
| `github/trail-animated.svg` | The footer strip, theme-aware. |
| `github/trail-animated-on-light.svg` | The footer strip with fixed dark ink for a light background. |
| `github/trail-animated-on-dark.svg` | The footer strip with fixed light ink for a dark background. |

GitHub strips `style` attributes from Markdown, so the portrait cannot be shaped there. The squircle is therefore part of its geometry, a superellipse whose corners run into its sides without a break in curvature. The portrait carries its own background and looks the same on either theme. Its `<img>` in the README sets a width and no height, because GitHub gives an image with both a muted placeholder background, which shows around the squircle's corners. The image sits inside the `#` heading, and the sections below it use `###` headings. GitHub positions each heading's wrapper, so the underline of an `h1` or `h2` that follows the float is drawn over it, while an `h3` has no underline.

The trail's line work sits on a transparent background, so its ink has to follow the theme. GitHub serves README images through a proxy that does not pass on the theme a reader chose on GitHub. The README therefore pins each theme to a fixed-ink file with a `<picture>` element and falls back to the theme-aware file, which follows the system setting.

```html
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="…/github/trail-animated-on-dark.svg">
  <source media="(prefers-color-scheme: light)" srcset="…/github/trail-animated-on-light.svg">
  <img src="…/github/trail-animated.svg" alt="…" width="840">
</picture>
```

The trail has nine waymarks, one for each repository in the profile index and in the same order, and the last one is hollow for the archived repository. Each waymark lights up as the wanderer passes it. When the index gains or loses a repository, the trail is redrawn to match.

## The walk

On the trail the wanderer walks with a computed gait. A small model of the walk is sampled 32 times over one stride and written into the file as keyframes, and it moves each part as follows.

- A planted foot stays where it is on the ground while the body travels over it, then lifts, swings ahead, and comes down heel first. The shoes are drawn, because the painting shows only the tip of one. Their tops are hidden under the hem, and their soles stand on the trail's own line.
- The staff is planted ahead and stays planted while the hand passes it. Since the staff does not change length, the hand rises as the staff comes upright, then lifts the staff and swings it forward for the next plant. The forearm turns about the elbow to carry the hand through the whole movement.
- The body rides up over each standing leg and sinks at each footfall, leans a little into the walk, and sways from foot to foot.
- Each swinging leg carries the hem forward a moment late, and the head stays level and nods slightly after each footfall.

The figure covers 30 px a second in steps of 24 px, which is 75 steps a minute, and crosses the strip in 32 seconds. At no sample does a planted foot or the planted tip of the staff slide against the ground.

## Colors

The wanderer's colors are those of the painting. The trail's ink uses GitHub's own foreground colors, so it matches the text around it.

| Element | Color |
| --- | --- |
| Trail ink | `#1f2328` on light, `#f0f6fc` on dark |
| Waymark highlight | `#c4442f` |
