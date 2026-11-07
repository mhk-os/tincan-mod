# tincan-mod

TINcan Race as a mod for Moorhuhn Kart: Open Source Edition, with 8 tracks, 7 drivers, powerups and effects converted from the original game. Every push to main builds the mod for Windows, macOS, Linux and Android and publishes it as a GitHub release. To install it, put the zip of your platform into the Mods folder of the game.

## Audio

Music (including menu/title/highscore cues) is normalized per song to -16 LUFS. Effects use one attenuation-only gain per source game, matching group medians to the quietest source while preserving intentional differences between cues; borrowed clips follow their source game's gain. Decoded peaks stay below 0 dBFS. Local cue gains and track music volumes are unchanged.

## Items and stage hazards

The Self Guiding Missile always launches forwards, including while looking backwards. Stage crushers flatten the kart and driver with the run-over squash instead of starting a character death animation; their existing hit duration and respawn behavior are unchanged.

Every race track has two special item boxes (the SDK's `SpecialItemBox`, `@special`), placed like the special boxes on the Moorhuhn Kart tracks: alone, at least 35 m from the random box rows, on drivable floor at the special box's own height above the ground, and never across the whole road. One sits in the middle of an alternative route (the scene's racing-path route named in brackets), so only drivers who take that way can grab it; the other sits on the main road about half a lap away, on the exit of a bend and to one side of the line, so taking it is a choice:

- Courtyard: on the wide loop that leaves the main road late in the lap (Route 1), and after the bend at about a third of the lap.
- Entrance Hall: on the long alternative route soon after the start (Route 2), and after the bend at about 60 % of the lap.
- Forecourt: on the shortcut across the open floor late in the lap (Route 3), and after the bend at about a quarter of the lap.
- Laboratory: on the early shortcut (Route 2), and after the sharp bend at about 60 % of the lap.
- Office Level: on the shortcut late in the lap (Route 4), and at the foot of the ramp at about a quarter of the lap.
- Production: at the start of the floor shortcut that skips the conveyor belts (Route 1), and after the bend at about 60 % of the lap.
- Ventilation: on the raised alternative route (Route 1), and after the sharp bend at about 80 % of the lap.
- Warehouse: on the long shortcut late in the lap (Route 2), and after the bend at about a quarter of the lap.

A special box gives the driver's special powerup, or a random one to drivers without a special (the TINcan drivers have none). Battles keep special boxes.

## Racing paths

Racing paths are stored in the track scenes. They run in the middle of the drivable road, and their widths span it: on Warehouse and Production the painted road and the conveyor belts bound the main path, on the other tracks the walls, ledges and floor edges do. Where the floor opens into a hall, a junction or the gaps between pillars, the width keeps to the driving corridor. Production's main path follows the painted S-bend instead of cutting across the floor beside it. Alternate routes keep their shortcuts across the open floor and join the main path at its middle. Straight sections use fewer nodes; bends, doorways and checkpoints keep more.

## Lighting

Lighting is set per track in `tincan_lighting.asset` and baked with the SDK's track light baker. Tracks with sunlight keep the sun's shadows at 60 % strength, so shaded road stays readable. In Ventilation, a realtime light flashes the transformer room in step with the lightning arcs: `Props/traforaum_flash` plays `traforaum_flash.anim` on the arcs' race-clock cycle. It is placed by hand, so re-importing the track removes it.

## Track variants

Every track can be driven in reverse. Courtyard and Forecourt, the outdoor tracks, also have a time of day and a rain option. The overlay definitions are in each track's `Variants` folder, the overlay scenes (`<track>.night.unity`, `<track>.day.unity`, `<track>.rain.unity`, `<track>.snow.unity`, `<track>.sandstorm.unity`, `<track>.reverse.unity`) next to the track scene, the cover map for rain (`<track>.cover.asset`) beside them and the generated night, day, rain, snow and sandstorm skies in `Textures/Sky`. Night overlays darken the sun and ambient light and turn the karts' headlights on; rain adds rain with thunder, wet uncovered ground and less grip outdoors; snow adds snowfall and a little less grip outdoors; a sandstorm adds thick dusty fog and blowing sand. Reverse overlays turn the speed pad arrows round.

## License

MIT. Game assets belong to their respective owners. If there is a problem with any of them, message me and I will remove it.
