# Countdown Scripting Example

The countdown sprites can be modified via the exposed variables on `Countdown`.
Scripts may read or change `Countdown.spriteGroup`, `Countdown.stepSprites` and
`Countdown.currentSprite` to customize the countdown.

Below is a minimal song script written in HScript that offsets the `THREE`
countdown sprite and fades the whole group.

```haxe
import funkin.play.Countdown;
import funkin.play.Countdown.CountdownStep;

class CountdownCustomizer extends ScriptedSong {
  override public function onCountdownStart(event:CountdownScriptEvent) {
    // make the group slightly transparent at start
    Countdown.spriteGroup.alpha = 0.5;
  }

  override public function onCountdownStep(event:CountdownScriptEvent) {
    if (event.step == CountdownStep.THREE) {
      var s = Countdown.stepSprites.get(event.step);
      if (s != null) s.x += 20; // move the "3" sprite a bit to the right
    }
  }
}
```
