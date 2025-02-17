# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]
☮️ Peace in the world, or the world in pieces. 🕊️
### Changed
- Mighty Summoner will now summon tokens without actor link to prevent changes to the original actor. This means GMs don't have to unlink the actors manually anymore.

## [1.4.0] - 2023-03-28
☮️ Peace in the world, or the world in pieces. 🕊️
### Added
- Added a couple failsafes to the Fear Table macro hopefully improving its ability to find what it is looking for.
- Play the unshake SFX when successfully removing Stunned from a BRSW chat card.
- Added full support for injuries added by BRSW. The injury active effect will...
- - ... be given a new name so that it is in line with those placed by SWIM.
- - ... be given a new icon unique to the injury.
- - ... be given new effects that respect the rules a bit better, especially in the case of leg and scar injuries.
- - ... be given the proper SWIM flags needed to remove the injuries with the Personal Health Centre.
- Brought back the token merging effect on the Shape Changer.
- Added `affected` to power effect builder flags.
- Added a warning when a player tries to shape change while the GM is on a different scene. The Warning is displayed to the GM only.
- Shape Changer now sets the linked actor to the one created from the Shape Changer. This happens only if the actor who changes form is currently the linked actor of the user who shape changes (to prevent allied extras from becoming linked). This will never happen for GMs.
### Changed
- Invisible Power Effect doesn't turn tokens fully invisible anymore, instead they get a transparency to not hinder gameplay.
- - The previous alpha value is saved on the token and restored when the effect is removed.
- - As a consequence, SWIM doesn't use the invisible status effect anymore but creates its own AE.
- - Invisible in this fashion sets Alpha to 0.25 and for Intangibility the Alpha was changed to 0.5.
- Updated the Wiki with the new changes.
### Fixed
- Fixed a bug where SWIM didn't pass the proper actor when damage was applied from a BRSW chat card, resulting in sfx not playing.
### Breaking
- Shape Changer doesn't adopt sight and detection modes from the original actor. This was done to prevent the assumed form from becoming worse eyesight in case the creature has superior eyesight compared to the actor assuming the form. As a result, GMs have to set sight and detection modes properly for the Shape Change template.

## [1.3.0] - 2023-03-13
☮️ Peace in the world, or the world in pieces. 🕊️
### Added
- Campfire ambient sound effect.
- New craft campfire macro and script that allows players to create a campfire.
- - It allows the user to select a location where then a campfire is created as a tile including a light source and ambient sound.
- - Currently this works without a roll and no resource consumption but this may be added at a later time.
- - Note that this works best (but does not require) [Monk's Active Tile Triggers](https://foundryvtt.com/packages/monks-active-tiles). Without this module the placed campfire tile, sound and light need to be deleted manually. With Monk's Active Tile Triggers you can simply double click the campfire to delete all of them at once.
- New setting to choose a campfire animation or image.
- Stealth as a skill for consumable weapons, because of mines, I guess?
- Added Compatibility with the generic Unstun Bonus introduced by SWADE in v.2.2: The Unstun Script now checks for that bonus and is backwards compatible, so AEs with `SWIM.unStunMod` as change will still work. **I strongly advise to not mix and match both effect keys on the same actor as this could lead to unexpected behaviour.**
- Effect Builder now supports the Relief: Numb power. Duration is always an hour and it is not maintained according to the rules. It sets the `system.woundsOrFatigue.ignored` property (introduced by SWADE v.2.2) to 1 or 2 with a raise.
- Started work on a new Power Point Management. Far from being completed yet and currently unusable and inaccessible; I just lack the time to complete it right now.
### Changed
- Changed some image styling in some chat messages in the translation strings.
- Consumable weapons are now deleted when the last one is used as BRSW now allows rolling damage for deleted items.
### Fixed
- Fixed another bug that caused the reloading sfx to not play in certain circumstances.
- Arcane Protection from the BRSW support will now reduce damage as it should.
- Fixed a bug that caused the Power Effect Builder to add Arcane Potection when Damage Field was chosen.
- Fixed a bug in the Mighty Summoner that caused the dismiss dialogue to not appear due to changes Warpgate made. This now uses SWIM flags to make it more resilient against changes.
- Fixed a bug in the Effect Builder that caused Pace to not get boosted on applying the Speed effect.

## [1.2.3] - 2022-12-03
### Changed
- Shape Change presets in the dialogue to change shape are now sorted by size and name. The options also show the size.
- Token Vision now respects and uses values taken from SWPF which is fortunately not as lackluster on ranges than SWADE.
### Fixed
- Fixed a bug that caused the ToC block list of SWADE to be reset.
- Fixed a bug in the Ammo Management that caused AEs from ammo to not be applied when the loaded ammo was empty.
- Fixed a bug in the Ammo Management that caused the reload SFX to not be played under certain circumstances.

## [1.2.2] - 2022-11-21
### Added
- New translation strings.
### Changed
- Token vision macro always enables vision unless the "No Change" option was chosen for vision (in which case it just uses the current value).
- Token vision macro now also fully supports the systems infravision sight mode.
- Updated the deflection global actions for BRSW (thanks @grendel111111).
### Fixed
- Fixed a critical Bug in the migration of items. Note that this only affects items migrated manually, the migration that ran automatically was not affected and should be fine.
- Fixed several bugs in the ammo management which made it impossible to use.
- Fixed a bug in Power Effect Builder where a property path was declared faulty.
- Fixed a bug in the Shape Changer Macro that caused the user to not get permission of the actor they change into.
- Fixed a bug in the Shape Changer Macro that caused the function to stop due to sequencer not getting a proper scale for the animation.
- Fixed a few instances where functions didn't get the sound effects properly.

## [1.2.1] - 2022-11-11
### Added
- Two new SFX (night vision device toggled on and off).
- Completely overhauled Token Vision Macro to integrate Foundry v10 features.
- Button in lighting controls of a scene that defines the illumination level of the current scene.
- - This will set the default selected illumination level in the Token Vision macros dialogue.
- - If not set, the macro will make an estimation based on the darkness level of the scene.
- - **WARNING:** The token vision macro will **irreversibly overwrite your configured detection modes on the token!** This is because it's really hard to deal with them atm. It will set up "Basic sight" and "See heat" as the others are not that useful for SWADE right now. I will adjust that when this changes.
- New translation strings.
### Fixed
- Skills on the power effect builder macro now get sorted properly.
- Fixed a bug that caused the initiative tracker showing the wrong turn when toggling on the holding status effect. (SWIM will continue to provide it's own functionality as it is more expanding on the feature.)
- Token Vision macro works again.

## [1.2.0] - 2022-11-05
### Added
- Conviction Maintenance:
- - When a new round in combat starts, a dialogue is shown to players maintaining conviction.
- - In the dialogue, you can choose to spend a Benny to maintain your conviction or...
- - decline and your conviction will be deactivated.
- - The dialogue is not shown if you are out of Bennies and conviction will end.
- - This will only happen if the conviction condition (provided by SUCC) is active, so you can still activate conviction using another effect and maintain it indefinitely if you want.
- New Translation strings.
### Changed
- The `check_bennies` function now takes an optional modifier (boolean) to stop the no more bennies left notification. It defaults to true.

## [1.1.0] - 2022-11-03
### Added
- Highly automated Fear Table macro. Various effects are applied to te selected targets depending on the result of the table.
- - You need to select the cause of the fear, the macro will try to find the Fear modifier for it.
- - Target all of those tokens who were unable to make their spirit roll and the macro will roll on the fear table for each and applies the appropriate effects.
- Added Heart Attack removal to the Personal healing Centre macro.
- New API functions: `swim.shake(token)` and `swim.stun(token)` which adds Shaken and Stunned respectively and plays the appropriate SFX.
### Changed
- **Breaking**: The Fear Table macro now requires exactly one token to be selected and one or more to be targeted.
- Made the callback functions (rolls to unshake, unstun and Bleeding out) optional.
- Added more SWIM compendiums to the toc block list.

## [1.0.0] - 2022-10-31
### Added
- New Setting that lets users choose to use the SWD unshake rules. If this setting is active...
- - ... SWIM will disable the adjust Pace with Wounds Setting and
- - puts an effect to Shaken that halves the actors Pace.
- SWIM now overwrites the callback functions of effects in SWIM, meaning it will initiate its own functions when the character is Shaken, Stunned or Bleeding Out. You are notified about that on your turn.
- A way to add a bonus to unstun rolls using Active Efects. To use it create an active effect with the attribute key `SWIM.unStunMod` (case sensitive), the change mode `Add` and a value of your choosing. A bonus must not have a `+` in front of the number, a penalty needs a `-` in front of the number.
- If the Summoner has the Command edge, the Fervor and/or the Hold the Line! edge, the summoner will add an AE to the summoned creature which respects that.
- New translation strings and extended localization of the module.
- New API function which returns all contents of a folder and its sub-folders up to three layers deep.
- On startup SWIM will check if the actor folder compendium is in the systems block toc list and if not prompt a dialogue to add it as otherwise the folders are invisible.
- Add button in the header of items and actors that opens a SWIM configuration window (@loofou).
- - The button is accessible by the GM and optionally by players (see settings).
- - The data will be saved no matter if you hit save or the close button to prevent accidental data loss.
- - Along with this comes a new way of storing data, menaing that existing actor and item configurations using additional stats would break, so...
- - a migration script is provided that goes through all actors and items of a world (but not compendiums) and updates them to this new way of storing data.
- - all items and actors not covered by the script (i.e. because they're in a compendium or imported later) are migrated as soon as the SWIM config button is pressed. (In this case the actor and all its items are migrated at once or only the item if the button is pressed on the item.) The migration will also start as soon as the new data is needed (i.e. when using a macro that tries to accesses the new stuff on an actor or item.)
- - The migration function is also exposed in case it is needed. See [the wiki](https://github.com/SalieriC/SWADE-Immersive-Macros/wiki/API#run-migration) for more information.
- Added the `get_weapon_sfx` api function to get the sfx from the flags of a weapon.
- Added file pickers for more SFX to actors (becoming stunned, gaining and loosing fatigue).
- Soak Damage macro should now play the death SFX on a perish result.
- A configuration for actors that lets users select a pronoun for each character and NPC. 
- Better BRSW integration: The global actions SWIM needs to function with BRWS together are now set up automatically. Please delete those from SWIM you've set up earlier.
### Changed
- **Breaking:** Changed the API so that the Unshake macro gets the version from the settings rather than being passed to the function. This means that the Unshake macro needs to be replaced by the one in the SWIM compendium.
- - Added a detailed error message explaining the problem in case the old version of the macro is used.
- Adjusted property paths to support FoundryVTT v10.
- SWIM now completely ignores the death flag featured in Health Estimate. Instead the proper incapacitation icon will be set in the Health Estimate settings when the game starts and HE is installed. As a result, HE is not a dependency any longer, though still strongly suggested.
- Adjusted manifest to reflect the FVTT v10 requirements.
- Changed some translation strings.
- Removed settings-extender.js and moved to the regular dependency structure suggested by the lib now.
- A creature summoned with a raise will now receive a max wound in addition to its current max wounds instead of setting it fixed to one. This should cover the Fantasy Companion where some summonable creatures already are resilient.
- General cleanup of code.
- Changed the `get_actor_sfx` api function to get the sfx from the flags instead of the additional stats.
- Ammo Management completely overhauled (@loofou):
- - Refactored the macro completely and added a new design to the dialogue. It now should display the proper options depending on selection (shooting or reloading)
- - Implement Ammo ActiveEffect system: Ammo that has an Active Effect assigned to it using the SWIM configuration on the ammo item, is applying the effect on the actor if the ammo is loaded. The effect is removed when the ammo is unloaded.
- - Ammo management now uses the audio from the SWIM config instead of additional stats as well as other configurations.
- Renamed the module to "SWADE Immersion Module". It describes better what it is now and keeps the cool abbreviation.
### Fixed
- Fixed a bug in the effect builder that didn't set maintainedPowers additional stat up when the caster was also the target.
- Fixed a bug in the Shape Changer that rendered the ignore size rule setting useless (thanks @jdavasligil).
- Fixed a bug when holding which resulted on having the combat tracker focus on top of the tracker instead of the token which should have its turn.
- Fixed a bug that created a second result chat message when an actor rolled a critical failure to unstun.
- Fixed a bug that caused a duplicate dialogue when using the token vision macro.
- Fixed a massive bug that caused a freeze scenario in the fall damage macro in FVTT v10.
- Fixed a bug in the Power Effect Builder that applied Distracted twice on Confusion instead of Distracted and Vulnerable.
- Power Effect Builder is now able apply multiple instances of Protection, Smite, Boost and Lower.
- Typo in the Loot-o-Mat.
### Known Issues
- Holding still breaks on first round of combat but I have no clue why.
- The Shape Changer macro throws a lot of errors when merging. Line 235, 350 and 365 where disabled to prevent that until further investigation. That means that the token merging / blending feature is disabled for now. It otherwise works as it should. The feature will be reindtroduced once the issue was found.
### Removed
- Unshake macros from the compendium were removed and unified into a single macro since the version is now drawn from the settings.
- Removed v10 update warning.
### Deprecated
- Old macros deprecated from the repo. They are still available in a zip file in case s/o wants to check them out.
- Ways to get data from additional stats were completely removed. A migration is provided.

## [0.18.5] - 2022-08-14
### Added
- Soak damage now also handles Bleeding Out rolls.
### Changed
- The `play_sfx` function now accepts a boolean to determine whether the SFX should be played for everyone (true) or just the current user (false). It defaults to true.
### Fixed
- Falling damage now caps at 10d6+10.

## [0.18.4] - 2022-07-22
### Added
- Added FVTT card deck support for the chase setup (thanks a lot @mafamac).
### Fixed
- Two bugs in the PEB that caused either not applying additional changes to protection or not adding it at all.
- Falling damage didn't explode.

## [0.18.3] - 2022-06-13
### Added
- Mighty Summoner: Maintenance Active Effects. Upon summoning a creature, the summoned creature and the summoner will gain an active effect containing the duration and some additional data from SWIM. If either of those effects ands and is deleted, the summoned creature will be dismissed. This works both ways. If the no power point setting is chosen, the duration of the power is near infinite and the maintenance AE on the caster incurs a penalty to the skill as per the no power point setting rule.

## [0.18.2] - 2022-06-11
### Added
- Translation update for german language via weblate.
### Changed
- Changed the global actions for invisibility to also cover detect arcana (@grendel111111).
- Changed the PEB to cover the new Deflection rules and new global actions to automate it in BR2.
### Fixed
- Another faulty translation string in the PHC.
- PHC now passes the correct healed wounds amount to the injury removal function when using generic healing. (It passed the wound value instead of the amount of healed wounds causing it to remove combat injuries if no wounds were healed.)
- PEB now properly applies changes to `maintainedPowers` additional stats if found. This was buggy as of yet.

## [0.18.1] - 2022-05-21
### Added
- Added a setting that disables the rank requirement for players when using the Shape Changer.
- Other option for the Power Effect Builder that allows setting up powers and maintaining them even if they're not (yet) added in the PEB. This (currently) doesn't offer the ability to set up any changes (will be added in a future version).
- New Translation Strings.
### Changed
- The Power Effect Builder now works even if GM and player are not on the same scene.
### Fixed
- Missing translation string in Effect Builder.
- Faulty translation String in the Personal Health Centre.
- Fixed a bug in the ammo management that prevented reloading.
- Fixed a critical bug in the Power Effect Builder.

<a href="https://ko-fi.com/salieric"><img style="border: 0px; display: block; margin-left: auto; margin-right: auto;" src="https://www.ko-fi.com/img/githubbutton_sm.svg" width="223" height="30" /></a>

## [0.18.0] - 2022-05-09
### Added
- Mighty Summoner: Summoned Creatures now get an Active Effect with the appropriate duration. Duration is doubled if the summoner has the Concentration Edge.
- Various new assets (see ReadMe for credits, all altered by SalieriC#8263):  
- New translation strings.
- New Setting rule: No Power Points. This enables near-infinite duration and a -1 to the spellcasting roll on the caster. SWIM does not use the systems setting rule in case that gets changed to do other things as well.
- New Macro: Power Effect Builder. Opens a dialogue to add active effects for almost all maintained core powers. This makes heavy use of the new effect updater by SUCC. **Make sure to update SUCC, unless you want total carnage.**

<details>
<summary>Currently supported Powers</summary>

- - Added boost/lower trait to Power Effect Builder.  
- - Added protection to Power Effect Builder.  
- - Added smite trait to Power Effect Builder.  
- - Added growth/shrink to Power Effect Builder.  
- - Added sloth/speed to Power Effect Builder. 
- - Added Beast Friend to Power Effect Builder.   
- - Added Invisibility to Power Effect Builder.  
- - Added Confusion to Power Effect Builder.
- - Added Deflection to Power Effect Builder.
- - Added Arcane Protection to Power Effect Builder.
- - Added Burrow to Power Effect Builder.
- - Added Damage Field to Power Effect Builder.
- - Added Darksight to Power Effect Builder.
- - Added Detect/Conceal Arcana to Power Effect Builder.
- - Added Disguise to Power Effect Builder.
- - Added Environmental Protection to Power Effect Builder.
- - Added Farsight to Power Effect Builder.
- - Added Fly to Power Effect Builder.
- - Added Intangibility to Power Effect Builder.
- - Added Mind Link to Power Effect Builder.
- - Added Puppet to Power Effect Builder.
- - Added Slumber to Power Effect Builder.
- - Added Silence to Power Effect Builder.
- - Added Speak Language to Power Effect Builder.
- - Added Wall Walker to Power Effect Builder.
- - Added Warrior's Gift to Power Effect Builder.
- - Added Empathy to Power Effect Builder.
- - Added Elemental Manipulation to Power Effect Builder.
- - Added Blind to Power Effect Builder.
</details>  

- - Enabled near-infinite duration on powers if no power points setting rule active.
- - Add an AE to the caster if he is not the target, that gives the casters spellcasting trait a -1 for maintaining the power if the power is found and no power points is active. In case no power points is not used, an AE is added to the caster (if the power is found) thats sole purpose is to track and cancel maintained powers.
- - If there is no active combat, start round of the effects will be set to 0 which ensures that the duration will work if combat starts while the AE is applied.
- If a power effect is set up using the power effect builder, the caster gains the ability to delete the AE on all actors he previously added it to. That means if the caster drops the power (or the duration runs out) it will be dropped on each actor, giving full control over maintenance to the player.
- Localisation for:
- - Fear Table function.
- - Mark Dead function.
- Various new localisation strings.
- New setting to check single reload by default.
- Make tokens invisible (no player owner) or half transparent (player owner) when the invisibility condition is applied.
- Make tokens slightly less visible if an effect called "Intangibility" (or their localised counterpart) is applied.
- Token Vision macro opens up if the torch condition is applied or removed.
- The Holding condition makes the token indeed holding in the combat tracker. Removing the condition prompts the player with a dialogue to choose between acting now or after current turn. The initiative is then set appropriately. This gives the player more control over their own initiative and alleviates GM workload.
- On world load SWIM will set the round time to 6 seconds as appropriate to the setting. This is a temporary implementation and will be removed as soon as the system covers this by itself.
- Added plea for support on SWIM config menu.
### Changed
- Incapacitation and Bleeding Out are added as overlays instead of small icons now. Inc. will be set as small icon if Bleeding Out is applied.
- Changed and fixed Deviation link to be future proof.
### Fixed
- Various errors in the personal health center that prevented chat messages from being created.
- Incorrectly named translation string.
- Fixed a bug in the ammo management where single reloading a weapon which is full would overflow the weapons capacity.
- Fixed a bug that caused weapons which do not require reloading actions to reload anyway.
- Fixed a bug that prevented the removal of Shaken if all Wounds were soaked.  

## [0.17.1] - 2022-04-27
### Fixed
- Faulty Translation string in Ammo Management (@Razortide)  

## [0.17.0] - 2022-04-21
### Added
- Combat Setup Button in the Token Actions:
- - Automatically adds all tokens on the current scene to the combat tracker (excluding NPCs which are incapacitated)
- - Automatically starts combat, drawing initiative for all tokens and sets the turn to the first token
- Settings to define a combat playlist which starts when combat starts
- When combat starts, all playlists are stopped
- - There is a way to define a folder in the settings which holds playlists that are never stopped on combat start.
- Added Macro Option tab in SWIM configuration window.
- Added ability for Shape Change function to have the token be a larger size on a raise. The scale multiplier is a configurable option in the Macro Option tab (@pmoore603).
- Added constants.js file as a central repository for constant values (@pmoore603).
- Dismiss function for the Mighty Summoner: If the selected token is a summoned creature, the owner (and GMs) can choose to dismiss it instead of summoning a new creature.
- Token Vision now supports custom (and preset) light colours.
- Started localization of some macros (@Razortide). This is far from being finished and a long-term project but there will be some amount of process in future releases until it's all done.  
- New sound effect for use in the token vision.
### Changed
- Enhanced Shape Change function to morph changing token into each other by growing/shrinking size and opacity (alpha) of both tokens as needed (@pmoore603).
- - This can be configured (and disabled) in the settings.
- Enhanced numeric input handling for SWIM configuration. Allows number input fields to have min, max, and step fields, which allows fields to be range and precision (decimal places) checked (@pmoore603).
- Token Vision now enables non-GMs to edit their vision type.
### Fixed
- Corrected an issue in the Shape Change function where temporary preset actors were incorrectly cleaned up. The issue happened when the player transforms into the same creature twice (or more) in a row (@pmoore603).

## [0.16.0] - 2022-04-03
### Added
- Common Bond function to give a Benny from one token to another.
- Free Reroll to the Radiation Centre macro if the Soldier Edge is found.
- Added warnings to some functions to install Helath Estimate if it is not installed.
- Localisation for Edges and Abilities. The module should now be *functional* in other languages. Please note that a lot of texts are still not localised. This is a lengthy process that will be done bit by bit over the course of the following months. New functionality will be fully localised however.
- Added Coup (50 Fathoms) to the benny checker.
- Added SFX to execute when BR2 sends the unshake hook.
- Added SFX player to the API.
- Added default volume option to the settings.
- Mighty Summoner macro that summons a creature selected by the user.  
- Soak Damage now allows for Incapacitation rolls and applies appropriate injuries.
- PHC can heal Wounds and remove fatigue for non-owned tokens/actors in the Personal Health Centre (PHC).
- PHC offers a way to use the Healing *skill* in combat to remove Bleeding Out and/or Inc but not Wounds (important because healing Wounds takes ten minutes, stabilising however is an Action).
- PHC now removes combat injuries and those from Incapacitation (unless they are permanent).
- PHC now removes Bleeding Out before and Incapacitation with Wounds.
- PHC now removes the Health Estimate flag if Incapacitated.
- Shape Changer now copies the permission settings from the original actor to give the player owner permissions.
- Shape Changer adds focus to new token.
### Changed
- Refactored the shape changer script to a few less lines (@pmoore603).
- Shape changer now makes the newly created actor the same `type` as the original. This means that PCs will change into PCs and NPCs will change into NPCs, no matter what the preset type is. This is important for the Joker's Wild setting rule to work properly.
- GMs are now able to access all shape change sizes instead of only those the characters rank permits.
- The injury table results are no longer checked with case sensitive translation strings.
### Fixed
- Radiation Centre will now inform about Benny use.
- Small fix in shape changer that will hopefully update the combat.
- Combat injuries were not properly applied in soak damage.
- A bug that caused the PHC to break because of a faulty setting string.
- A leftover variable declaration in the shape changer caused it to fail when trying to play the VFX if executed by a non-GM.
- Fixed missing variable exception error when shape changing (@pmoore603).
- Shape changer now adds elevation of the original token to the newly created token (thanks @pmoore603 for spotting this).
- Shape changer now creates the new actor in the proper folder even if executed by non-GM.
- Shape changer dialogue now gets the proper div class.
- Unstun doesn't remove prone but now properly removes stunned on a raise (thanks @Razortide for spotting).
- Macros now have the proper icons from SUCC.
### Languages:
- English
- German (@Razortide)

## [0.15.0] - 2022-03-18
### Added  
- A full-fledged, all-new API the module makes much use of now. Thanks to honeybadger#2614 for the suport on setting it up.  
- Finally an auto-updateable BR2 Ammo Management macro. You'll need to import it from the BR2 folder inside the SWIM compendium into your world (or just copy and paste the one line of code to the macro you already have) and you're set, no need to manually update it ever again (hopefully).  
- A documentation for the new API.
- A new configuration menu with tabs (made by @javierriveracastro).  
- Default options for the chase setup.
### Changed
- **BREAKING:** Due to changes in Foundry VTT core all script macros had to be pulled out of the compendium and are now maintained as .js files in the module itself. As a Result, *all auto-update macros became unusable*. You need to import the new auto-update macros in your world (and delete the old ones), then you'll be set up for the future. This time for good (hopefully).  
- More options on laying out cards for other chase scenes (made by @pmoore603).  
- Shape Changer now adds the new token (the target of the shape shift) up in the combat tracker.  
### Fixed
- Players were unable to execute the macros due to permission enforcement changes in FVTT core. This is fixed via the aboce change.  
- Players are now able to use the Shape Changer macro. Before it was GM only because of permission issues. Now it relays the script to the GM.  
### Removed
- Deprecated all the standard macros. They are still available for reference on the repo but won't be maintained anymore. The core features are integrated into the module now and others may follow.  

## [0.14.1] - 2022-03-06  
### Added
- Stealth added as a Skill for Consumable Weapons in the BR2 Ammo Management macro.  
### Fixed  
- Fixed a bug in the (Un-)Shake and Soak Damage macros where they were still using the old way of toggling the status which caused the status to not be toggled properly.
- Fixed a bug in the BR2 ammo usage macro that caused it to not get the ammo without te loaded ammo additional stat.
- Fixed a bug that made the Unshake macro non-functional.
- Fixed a bug that prevented installing the module.  

## [0.14.0] - 2022-02-15  
### Added  
- [SUCC](https://github.com/SalieriC/SUCC) dependency. SWADE v.1+ handles conditions inherently different from the way they were handled before, thus making CUB not viable any longer. Since CUB will likely take a long time until it is compatible with SWADE once again, I have teamed up with Javier again to create SUCC which works similar to CUBs Enhanced Conditions but it built for SWADE and thus requires less setup.
- A new setting to register the Irradiated Condition.
- Hijacked (or rather: replaced) the SWADE systems "Clear Chase" button and added the Chase Layout Manager instead. Make sure to only use it on one of the chase layout scenes. Nothing bad will happen otherwise but the macro may not place the cards as expected.
- Added a compendium with a chase deck roll table and a compendium with the cards for that table since SWADE is going to remove the compendium with the images.
### Removed
- CUB dependency. Please disable CUB in your world and use [SUCC](https://github.com/SalieriC/SUCC) instead to continue using SWIM.
- All the condition icons as they are now in SUCC.
- CUB imports as they are of no use now.
- CUB setup documentation as it is not needed anymore.
- Removed SWADE Systems chase button from the left scene controls.
### Fixed  
- A bug in the shape changer macro that could cause issues when updating skills.  
- A bug in the shape changer macro that caused players not showing all their options to shift into in creature form.
- Fixed a bug in the Deviation Macro, that made it non-functional.
### Changed  
- Changed the way token size settings are applied in the shape changer macro to reduce load and thus improve performance.  
- Changed the macros to use [SUCC](https://github.com/SalieriC/SUCC) rather than CUB for handling conditions.
- Changed the check for the Irradiated condition in the radiation centre macro from CUB to SUCC and added a dialogue for GMs to activate it from the macro itself.
- Changed the license of the chase layouts. They may *not* be redistributed under any circumstances.

## [0.13.0] - 2022-01-21  
### Added
- Function to test for crit fails in the swim class, to make it centrally available for all macros.  
- Shape Changer Macro which does everything for you, you just need to set up some presets the players can shape shift into.  
### Fixed  
- Fixes a bug with duplicate chat messages in the (Un-)Shake Macros.  
- Fixed showing an npc as crit failing when it rolled a single 1. 
### Changed  
- Set all compendiums from SWIM to be hidden from players by default.  
### Known Issues  
- Shape Changer Macro does not update permissions on the duplicate actor. This currently cannot be changed due to limitations in Foundry core.  
- Shape Changer Macro does not delete powers on the presets yet.  

## [0.12.3] - 2022-01-16  
### Fixed  
- Fixes a bug with faulty libWrapper dependency.
  
## [0.12.2] - 2022-01-15  
### Added
- Added "Amorphous" (The After) to the (Un-)Shake macros.
### Fixed
- Added the dependencies to the manifest and added a warning to the init hook if they are not present.
- Also added libWrapper, not required by SWIM itself but by compendium-folders so I stuck it in there because FVTT doesn't check dependencies of dependencies.

## [0.12.1] - 2021-12-27  
### You need to update these macros:  
- None, unless you're still using the script macros ([see releases notes to 0.10.1](https://github.com/SalieriC/SWADE-Immersive-Macros/releases/tag/v.0.10.1)).  
- - Seriously, if you've not done so yet, do so now. This is the last major release this message will be shown.  
### Added  
- Gritty Damage (Soak Damage macro) now applies the appropriate Active Effects. Since I am not including a table for this and had issues with the sub-tables, it searches the table results text for words it can allocate to an AE. Thus it is important to use either the original table or include those words in your own table (case insensitive): "unmentionables", "arm", "leg", "guts", "broken", "battered", "busted", "head", "hideous scar", "blinded" and "brain". Do *not* use any of these words in other table results.  
### Changed  
- Soak Damage macro now doesn't exclude the GM from applying Gritty Damage any longer. Instead it only applies them to PCs by default. You can activate Gritty Damage for NPCs in the modules settings though.  

## [0.12.0] - 2021-12-17  
### You need to update these macros:  
- BR2 Ammo Usage  
- None other, unless you're still using the script macros ([see releases notes to 0.10.1](https://github.com/SalieriC/SWADE-Immersive-Macros/releases/tag/v.0.10.1)).  
- - Seriously, if you've not done so yet, do so now. This is the last major release this message will be shown.  
### Added  
- New game setting, allowing GMs to rule that NPCs do not use Ammo items from inventory. NPCs will still use Ammo in the weapon (magazines, clips, etc.) but won't require an item to draw ammo from. Instead they will just reload the weapon to the maximum shots (or by 1 shot if "Single Reload" is checked) without using an item from the inventory. This is especially useful for official modules which do not populate actors with ammunition, making prep for SWIM compatibility a little easier.  
- CUBs latest methods to apply status effects to the (Un-)Stun macro, making it a lot more stable and fixing a bug at the same time.  
- Radiation Centre macro. This macro rolls Vigor and applies Fatigue based on the result from radiation and is also able to apply Fatigue from radiation directly. It makes use of a new status called "Irradiated". An optional additional stat "Radiation Resistance" with the key "radRes" can be added to actors to provide a direct modifier to the roll, useful for settings which make heavy use of Radiation. The additional stat does not need to be set up in order for the macro to function.  
- "Irradiated" status added to the CUB mapping file in the module.  
### Fixed  
- Deprecation warnings, should be compatible with Foundry VTT v9 now. Let me know if I missed something.  
- (Un-)Stun macro adding a new prone status.  
### Removed  
- Prone image game setting, as it is no longer needed with the changes in CUB. The (Un-)Stun macro will now apply the prone status directly, instead of the icon. The macro will also check if the status is set up and throw a warning if not.  
- Removed Sprawlrunners CSS usage on the Falling Damage macro as it doesn't work well in the chat message.  
### Known issues  
- There are a couple of deprecation warnings caused when executing some macros which actually come from CUB. This is due to the fact that CUB has not been updated to v9 yet and will likely cause issues on v9 because of that. This is nothing I can change right now. Wait until CUB has been updated before updating to FVTT v9.  

## [0.11.0] - 2021-12-05  
### You need to update these macros:  
- None, unless you're still using the script macros ([see releases notes to 0.10.1](https://github.com/SalieriC/SWADE-Immersive-Macros/releases/tag/v.0.10.1)).  
### Added  
- **Falling Damage Macro.** It supports all options from the core rules and rolls for each selected and targeted token individually. Dialogue CSS credit: Kyane von Schnitzel#8654. The macros chat message uses the CSS of the activated core module (if any), supported are SWADE, Deadlands, Sprawlrunners and Pathfinder. It works without these modules as well though.  
**Bounty Notice:** I have very limited time atm. Everyone who creates merge requests with (working) updates to the macros which respect changes from Foundry version 9 (and thus gets rid of the warnings in the console) will receive a reward in the form of a free, high quality Battle Map. You may choose from one of these settings: Medieval Fantasy, Western or Pirates. A merge request covering three or more macros (that have not yet been covered) will be rewarded with an export of the selected map, set up with walls, lights and everything. The first merge request that covers *all* macros and works will be rewarded with a custom made battle map made after *your* specifications (within a reasonable degree of detail).  

## [0.10.3] - 2021-11-16  
### You need to update these macros:  
- None, unless you're still using the script macros ([see releases notes to 0.10.1](https://github.com/SalieriC/SWADE-Immersive-Macros/releases/tag/v.0.10.1)).  
### Fixed  
- The chat message of Soak Wounds now shows the systems benny image.  
### Added  
- The two Unshake macros now utilise the actors `data.attributes.spirit.unShakeBonus` data. As of yet, the system does not support this but the bonus is added in case a script changed it on an actor. It also checks all Active Effects on the actor for this and applies the modifier individually if the AE is active, making it finally possible to affect the Unschake macro with AEs (and thus items that use AEs to affect unshake).  
**Warning:** Do *not* use an AE to set the `data.attributes.spirit.unShakeBonus` for Edges that are already covered by the Unshake macors, otherwise the bonus will be added twice.  

## [0.10.2] - 2021-11-15  
### You need to update these macros:  
- None, unless you're still using the script macros (see previous releases notes).  
### Fixed  
- Fixed a bug in data structure resulting in not getting owned potions in the Personal Health Centre macro.  
- Fixed a minor bug that resulted in not waiting for the drinking sound before the next sfx.  
### Changed (**Breaking**)  
- Changed the setup for Potion names from comma-space seperated (', ') to pipe seperated ('|'). You need to adjust the settings manually if you're already using SWIM, otherwise the macro will not find the potions. This was done to make comma useable in potion names for better sorting (i.e. `Healing Potion, lesser`). So a string like "Healing Potion, Greater Healing Potion" now needs to be changed to "Healing Potion|Greater Healing Potion".  

## [0.10.1] - 2021-11-11  
### You need to update these macros:  
- **All of them.** (Now featuring: Automatic updates, see below.)  
### Fixed  
- Mark dead now gets the correct SFX from the actor.  
- Mark dead and Soak Damage updated to obey the current flag use for marking a token as dead of Health Estimate.  
### Added  
- Automatic updates for macros by using dummy macros that just call the original. From now on, use all the macors in the compendiums "User Macros (use these)" folder. The other folder contains the script macros which you don't need anymore.  
- - If you're using the BR2 Macros for handling ammo and power sfx you need to copy those into your world as usual. I'm, working on a solution for this as well but haven't found one yet.  

## [0.10.0] - 2021-10-31  
**Note:** From my testing this is compatible with Foundry 0.8.x but - as usual with software development - problems may occur. Please report them on this repo as usual.  
**Bounty Notice:** I have very limited time atm. Everyone who creates merge requests with (working) updates to the macros which respect changes from Foundry version 9 (and thus gets rid of the warnings in the console) will receive a reward in the form of a free, high quality Battle Map. You may choose from one of these settings: Medieval Fantasy, Western or Pirates. A merge request covering three or more macros (that have not yet been covered) will be rewarded with an export of the selected map, set up with walls, lights and everything. The first merge request that covers *all* macros and works will be rewarded with a custom made battle map made after *your* specifications (within a reasonable degree of detail).  
### You need to update these macros:  
- SWIM: Ammo Management  
- (Un-)Shake (both)  
- (Un-)Stun  
- Ammo Management (enhanced)  
- Mark Dead  
- Soak Damage  
- Spend Benny
- Chase Setup  
### New Macros:  
- Loot-o-Mat (see ReadMe)  
### Added
- Support for the *weaken undead* power (Hellfrost) in the Unshake (SWD) macro that disables the +2 bonus if the token is undead but has an active effect called "Undead" that is disabled.  
- Support for actor specific shaken and unshake sfx.  
- The macros now use the Benny image configured in the system.  
- Ammo Management now supports attack sounds for regular, frenzy and improved frenzy attacks, this requires the Ammo field to contain "MELEE".  
### Fixed  
- Fixed a bug that sometimes prevented a second shot sfx to be played in the BR2 integration.  

## [0.9.0] - 2021-07-05  
**Possibly** compatible with Foundry 0.8.x but I can't say for sure.  
### You need to update these macros:  
- Ammo Management (enhanced)  
- SWIM: Ammo Management  
### Added  
- Now also features the ability to play SFX only without the need for ammunition. For this just set the Ammo on the weapon to be `NONE` (exactly like this). This may be useful if you want SFX for melee weapons. It uses the same sfx path structure (see below), so you'll have the same sfx for melee and ranged attacks unfortunately.   
- Chase Setup macro for a quick setup that takes only a click. Also supports cleaning the table.  
- Six chase layouts, one for foot/riding chases, one for (ground) vehicle chases and one for ship (watercraft, aircraft and spacecraft) chases/battles with regular and modern theme each. See the [Chase Scenes documentation](https://github.com/SalieriC/SWADE-Immersive-Macros/blob/main/documentation/Chase%20Scenes.md) for details.  
- Immersion macro to play SFX when using powers in BR2. It does not manage Power Points, just plays a sound effect when using a power.  
### Fixed  
- Fixed the BR2 integration .json files. Now it isn't neccessary any longer to set up a World Global Action for each skill, the integration will trigger whenever a weapon or power is rolled on, no matter the skill, even untrained.  

## [0.8.0] - 2021-07-01
**Possibly** compatible with Foundry 0.8.x but I can't say for sure.  
### You need to update these macros:  
- (Un-)Stun  
- Ammo Management (enhanced)  
- SWIM: Ammo Management  
### Added  
- Ammo Management: Now supports Weapons that do not require a reload action (i.e. bows).  
- Ammo Management: Now offers a way to only reload a single bullet instead of reloading the entire weapon. This is especially useful for revolvers and such.  
- Ammo Management: Charge Packs can now change the ammo type but old Charge Packs are only refilled if the weapons current shots are equal the maximum shots as there is no way to track remaining charges on a Charge Pack.  
- Ammo Management (BR2 integration only): Now supports weapons which *may* be thrown but don't need to. It filters for a set of Skills and only applies ammo usage if such skills are found. See the [documentation on Ammo Management](https://github.com/SalieriC/SWADE-Immersive-Macros/blob/main/documentation/Ammo%20Management%20Setup.md) for further details.  
- BR2 integration for ammo management now gets the correct amount of shots from BR2 (requires [Better Rolls 2 (BR2)](https://foundryvtt.com/packages/betterrolls-swade2) **greater** than version 2.36.).  

## [0.7.0] - 2021-05-29  
### You need to update these macros:  
- All of them.  
### Fixed  
- All Macros that became broken due to the Foundry Version 0.7.10
- Fixed a bug in the Unshake (SWADE) macro that removed Shaken on a Failure.  
### Added  
- Reload and Reload (enhanced) macro.  
- BR2 integration for Shooting action.  
- Scale calculator macro, thanks @brunocalado.  
- Deviation macro, thanks @brunocalado.  
- (Un-)Stun now also applies Elan bonus on rerolls if the selected token has that edge.  
## VERY IMPORTANT:  
Most of these macros cannot be used as they are, reading the [ReadMe](https://github.com/SalieriC/SWADE-Immersive-Macros/blob/main/README.md) is **mandatory**!  
If you want to use the new Ammo Managemenet, make sure to read the [Documentation on Ammo Management](https://github.com/SalieriC/SWADE-Immersive-Macros/blob/main/documentation/Ammo%20Management%20Setup.md) as well!  
I can't stress enough how important it is to do so. *Do not blame me, if something goes sideways if you haven't read and followed the steps outlined there!*  

## [0.6.1] - 2021-03-10
### You need to update these macros:
- Spend Benny
- (Un-)Shake (both versions)
- (Un-)Stun
- Personal Health Centre
- Power Point Management
- Soak Damage
### Fixed
- Removed the border of images in chat messages.
- Fixed a breaking bug that caused the module to not work if SWADE Spices & Flavours was not installed (thx @Khitan#9089 for bringing it to my attention).

## [0.6.0] - 2021-03-10
### You need to update these macros:
- (Un-)Stunned
- Personal Health Centre
### Added
- RollTable importer macro.
- Cure Fatigue and Healing Potion options added to the Personal Health Centre macro.
- - Drinking a potion reduces its quantity. If it was the last it gets removed.
- - Drinking a potion has its own sfx (configurable in the settings).
- - Potion names can be configures in the modules settings. Must be **exact** names (also case sensitive) and seperated by `, `.
- Added a drinking sfx to the assets.
### Fixed
- Unstun chat message on spending a Benny was giving false information.

## [0.5.0] - 2021-03-08
### You need to update these macros:
- (Un-)Shake (both versions)
- (Un-)Stun
- Fear Table
- Personal Health Centre
- Power Point Management
- Soak Damage
- Token Vision
- Raise Calculator (both versions)
### Added
- Raise Calculator (Dynamic) now accessible from the basic controls on the left side.
- Default Buttons to most dialogues (where it makes sense).
- Added autofocus to input fields in dialogues (where it makes sense).
- Added autoselection of input content when rendering a dialogue as well es on selecting the input to reduce the amount of mouse usage needed to operate the macros.
- Documentation on how to set up CUB.
### Changed
- The Dynamic version of the Raise Calculator now changes the output on typing (even more dynamically), thus the Result input doesn't need to loose focus anymore.
### Fixed
- Token Vision Makro was not working for non GM users.

## [0.4.0] - 2021-03-07
### You need to update these macros:
None.  
### Added
- **Macro:** Raise Calculator
- **Macro:** Raise Calculator (Dynamic)

## [0.3.0] - 2021-03-03
### You need to update these macros:
- (Un-)Shake (both versions)
- (Un-)Stun
- Personal Health Centre
- Soak Damage
### Added
- Support for Special Abilities
- Ability Converter macro (**read the ReadME!**)
- Thick Fur (Saga of the Goblin Horde) for +2 Soak Rolls in the Soak Damage macro.
### Fixed
- Minor bug that caused some macros to not display all included Edges in the results chat message (thanks javierrivera#4813 for spotting that).

## [0.2.0] - 2021-02-26
### You need to update these macros:
- Personal Health Centre.
- Soak Damage.
### Added
- Added a male *huh* sfx for removing Fatigue (and healing for now).
- Added a heartbeat sfx for Inc.!
- Added a checkbox to activate Gritty Damage.
### Changed
- Injury Table is now independent of Gritty Damage.
### Fixed
- Fixed a typo that caused the injury table localisation to not show.
- Fixed Personal Health Centre playing sound even if no wounds were healed.
- Fixed Personal Health Centre showing a message reading that wounds will be removed even if no wounds were healed.

## [0.1.0] - 2021-02-24
### Added
- Initial Release
