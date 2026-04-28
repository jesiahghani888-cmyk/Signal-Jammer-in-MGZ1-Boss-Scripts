# Signal Jammer in MGZ1 Boss Mod Documentation

## Technical Specification

### Mod Information
- **Target Game**: Sonic 3 Angel Island Revisited (S3AIR)
- **Version**: v26.03.28.0
- **Zone**: Marble Garden Zone Act 1 (MGZ1)
- **Replacement**: Tunnelbot -> Signal Jammer

### Scripting Architecture
The mod is implemented using the **Lemon** scripting language, the custom scripting engine for Sonic 3 A.I.R. It utilizes address hooks to override the vanilla game's object initialization and update logic.

#### Key Functions
- `Tenna.boss.signalJammer.InitReplacement()`: The entry point hooked at `0x088568`. It checks the current zone and act before initializing the custom boss.
- `SignalJammer.MGZ1.Initialize()`: Sets up the initial state, position, and health (8 hits) for the Signal Jammer.
- `SignalJammer.MGZ1.BaseUpdate()`: The main update loop handling movement, state transitions, and health tracking.
- `SignalJammer.MGZ1.StateMachine()`: Manages the boss's behavior phases (Moving, Dodging, and Attacking).
- `SignalJammer.MGZ1.SpawnDrones()`: Handles the logic for spawning support drones based on the boss's remaining health.

### Global Variables
The mod defines several global variables to maintain state across frames:
- `SignalJammer.MGZ1.state`: Current behavior phase.
- `SignalJammer.MGZ1.stateTimer`: Frame counter for the current state.
- `SignalJammer.MGZ1.maxDrones`: Maximum number of drones allowed on screen (increases as health decreases).
- `Tenna.fH.hurtTimer`: Invulnerability frames after taking damage.

### Implementation Details
The script ensures compatibility with the original game flow by calling `SetupAsSignpostSpawner()` upon the boss's defeat. This ensures the level transition to the signpost sequence remains seamless.

```lemon
if (global.zone_act == 0x0200)
{
    // Custom Boss Initialization
    SignalJammer.MGZ1.Initialize()
    SetupAsSignpostSpawner()
}
```

### Rendering
Custom sprites are rendered using the `Standalone.onWriteToSpriteTable` hook, allowing for dynamic sprite selection and effects like hit flashes.

---
*Documentation generated for jesiahghani888-cmyk*
