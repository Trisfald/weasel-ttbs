# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [0.11.0] - 2020-11-03
### Added
- Added the possibility to invoke team powers, similarly to actors' abilities.
- New associated type `Invocation` in `TeamRules`.
- New methods `invocable` and `invoke` in `TeamRules`.
- New event `InvokePower`.
- Added team powers.
- New associated types `Power`, `PowersSeed` and `PowersAlteration` in `TeamRules`.
- New methods `generate_powers` and `alter_powers` in `TeamRules`.
- New events `AlterPowers` and `RegeneratePowers`.

## [0.10.0] - 2020-08-22
### Fixed
- Improved the ergonomics of handling errors from `EventProcessor`. `ProcessOutput` has a new method `result()` to get a `WeaselResult`.

## [0.9.0] - 2020-08-15
### Changed
- Rounds and turns now reflect the most used definition (a round is made of multiple turns).
- Renamed `StartRound` into `StartTurn`, swapped `EndRound` and `EndTurn` and renamed `EnvironmentRound` into `EnvironmentTurn`.
- Renamed `check_objectives_on_round` into `check_objectives_on_turn`.
- Renamed `on_round_start` into `on_turn_start` and `on_round_end` into `on_turn_end`.
- Renamed `RoundState` into `TurnState`.

## [0.8.1] - 2020-08-12
### Added
- Event trigger `RemoveEntityTrigger` that can fire either a `RemoveCreature` or a `RemoveObject`.
- Re-exported the most used names.

### Fixed
- Fixed the incorrect name `ConcludeMissionTrigger`. It is now `ConcludeObjectivesTrigger`.

## [0.8.0] - 2020-07-06
### Added
- New methods `on_character_added` and `on_character_transmuted` in `CharacterRules`.
- `Client` and `Server` are now `Send`. For this to happen some types requires `Send` as well.
- Client and Server implements a new trait, `BattleController`.
- Multiplayer example 'King of the hill'.
- Added accessors to flat event structures.
- Removed metric `ROUNDS_STARTED`. Added counters for rounds and turns in `Rounds`. Added also an `EndTurn` event.
- Introduced `BattleController` trait.

### Fixed
- Ambiguous metric ids for `CREATURES_CREATED` and `OBJECTS_CREATED`.

## [0.7.0] - 2020-03-30
### Added
- Implemented `Hash` and `Eq` for `EntityId`.
- Methods to obtain a mutable access to all rules and models.

### Changed
- Rounds can now be initiated by multiple actors.

## [0.6.0] - 2020-03-11
### Added
- Support for status effects.
- New methods `generate_status` and `alter_statuses` in `CharacterRules`.
- New methods `apply_status`, `update_status` and `delete_status` in `FightRules`.
- `InflictStatus` and `ClearStatus` events.
- Added `StatusNotPresent` to `WeaselError`.
- Mutable iterators over statistics and abilities.
- New event `EnvironmentRound`.
- New associated type `Potency` in `FightRules`.
- New associated types `Status` and `StatusesAlteration` in `CharacterRules`.
- Example to showcase status effects.

### Changed
- Renamed `ActorRules`'s `alter` into `alter_abilities` and `CharacterRules`'s `alter` into `alter_statistics`.

### Fixed
- Event's origin is not overridden anymore by the server if it is already set.

## [0.5.0] - 2020-02-26
### Added
- Example for undo/redo of events.
- Added a `GenericError` variant to `WeaselError`.
- Example to showcase passive abilities.

### Changed
- The methods `activable`, `on_round_start` and `on_round_end` now take `BattleState` as argument.
- The methods `allow_new_entity`, `activable`, `check_move` now return a `WeaselResult` instead of a bool.

## [0.4.1] - 2020-02-22
### Changed
- Replaced most usages of `HashMap` with `IndexMap`.

## [0.4.0] - 2020-02-21
### Added
- Doc tests for all events and few other structs.
- `Originated` decorator.
- Introduced inanimate objects.
- New events `CreateObject` and `RemoveObject`.
- Improved public API for `Battle` and its submodules.
- New associated type `ObjectId` in `CharacterRules`.

### Changed
- It's now possible to manually set an event's origin.

## [0.3.1] - 2020-02-17
### Added
- Order of rounds and initiative example.
- Methods to retrieve an iterator over actors or characters.
- `on_actor_removed` method in `RoundsRules`.

## [0.3.0] - 2020-02-16
### Added
- `AlterSpace` event.
- Example showing different ways to manipulate the space model.

### Changed
- `SpaceRules`'s `check_move` and `move_entity` now take as argument a `PositionClaim` instead of an `Option<&dyn Entity<R>>`.
- `SpaceRules`'s `move_entity` is used also to move entities out of the space model.
- `RemoveCreature` frees the entity's position.
- `RoundsRules`'s and `on_start` and `on_end` take as arguments the entities and the space manager objects.

## [0.2.0] - 2020-02-15
### Added
- `RemoveTeam` event.
- An example showing how to use event sinks.
- Example to demonstrate how to create user defined events and metrics.
- `RegenerateStatistics` event.
- `RegenerateAbilities` event.
- `EntityId` now implements `Copy`.

## [0.1.0] - 2020-02-08
### Added
- First available version.
