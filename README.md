# tincan-mod

TINcan Race as a mod for Moorhuhn Kart: Open Source Edition, with 8 tracks, 7 drivers, powerups and effects converted from the original game. Every push to main builds the mod for Windows, macOS, Linux and Android and publishes it as a GitHub release. To install it, put the zip of your platform into the Mods folder of the game.

## Audio

Music (including menu/title/highscore cues) is normalized per song to -16 LUFS. Effects use one attenuation-only gain per source game, matching group medians to the quietest source while preserving intentional differences between cues; borrowed clips follow their source game's gain. Decoded peaks stay below 0 dBFS. Local cue gains and track music volumes are unchanged.

## Items and stage hazards

The Self Guiding Missile always launches forwards, including while looking backwards. Stage crushers flatten the kart and driver with the run-over squash instead of starting a character death animation; their existing hit duration and respawn behavior are unchanged.

## Racing paths

Racing paths are stored in the track scenes. They run in the middle of the drivable road, and their widths span it: on Warehouse and Production the painted road and the conveyor belts bound the main path, on the other tracks the walls, ledges and floor edges do. Where the floor opens into a hall, a junction or the gaps between pillars, the width keeps to the driving corridor. Production's main path follows the painted S-bend instead of cutting across the floor beside it. Alternate routes keep their shortcuts across the open floor and join the main path at its middle. Straight sections use fewer nodes; bends, doorways and checkpoints keep more.

## Lighting

Lighting is set per track in `tincan_lighting.asset` and baked with the SDK's track light baker. Tracks with sunlight keep the sun's shadows at 60 % strength, so shaded road stays readable. In Ventilation, a realtime light flashes the transformer room in step with the lightning arcs: `Props/traforaum_flash` plays `traforaum_flash.anim` on the arcs' race-clock cycle. It is placed by hand, so re-importing the track removes it.

## License

MIT. Game assets belong to their respective owners. If there is a problem with any of them, message me and I will remove it.
