# Unity's 2D Platformer Demo

* [Video (Unity)](https://unity3d.com/learn/tutorials/modules/beginner/2d/2d-overview?playlist=17093)

* [Video (Youtube)](https://www.youtube.com/watch?v=4qE8cuHI93c)

##Current Edits:

Player now temporarily turns red & invincible when hit by an Enemy.
This prevents the Player from getting stuck between 2 Enemies.

* In `PlayerHealth.cs`:
  * Added a `"PlayerHurt"` layer.
  * Player is temporarily moved to this layer on collision with Enemy.
  * Player is tinted red while invincible.
  * Implemented using a coroutine:

```csharp
IEnumerator MakeInvincible()
{
    // Move player to a safe collision matrix layer (no collisions w/ Enemy layer).
    gameObject.layer = LayerMask.NameToLayer("PlayerHurt");
    body.color = Color.red;

    // Wait for 2 seconds.
    yield return new WaitForSeconds(RepeatDamagePeriod);

    // Move player back to its original layer (interacts with Enemy layer).
    gameObject.layer = LayerMask.NameToLayer("Player");
    body.color = Color.white;
}
```
