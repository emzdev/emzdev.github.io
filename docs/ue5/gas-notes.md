# GAS related notes

### Important GAS parts

#### Ability System Component (```UAbilitySystemComponent```)
The brain, or manager of abilities. Keeps track of granted abilities, and handles activating, canceling them etc.
This component is often attached to actors that you want to be responsible for instigating abilities, like Player Characters and AI Characters.

!!! note

    Abilities in GAS has the concept of a "source" and a "target".
	The ```UAbilitySystemComponent``` that owns and activates an ability will be treated as the "source" of that ability.



#### Gameplay Tags
Text tags used for many things related to the ability system. For instance, tagging certain abilities with "healing" for the AI to know which abilities are healing abilities etc.
You can also tag stuff as "cancellable" for the system to look for cancellable abilities and cancel them etc etc.

#### Gameplay Attributes
Numeric data values that has a concept of a "current value" and a "default value". Basically "stats" that can be used to calculate gameplay ability related effects.
E.g Health, Strength, WeaponDamge

!!! Warning

    Modifying Attributes directly through code should be avoided. This should instead be handled with [**Gameplay Effects**](#gameplay-effect-ugameplayeffect), as they're much easier to track and debug.

#### Attribute Sets (```UAttributeSet```)
A collection of Gameplay Attributes. Has a handful of overridable function that can handle logic when attributes changes.

#### GameplayAbility (```UGameplayAbility```)
A very flexible class that defines what an ability does, what is costs. The actual behaviour of an ability is scripted in this, and it has a lot of flexible ways to handle timings
of abilities based on animations, particles, sounds, different types of inputs etc. It also has handy tools to sync, predict and replicate ability behaviour in online environments.

#### Gameplay Effect (```UGameplayEffect``)
Data only Blueprints that define how attributes are changed within the GAS system. Direct changes like HP loss, over time changes like regeneration effects, temporary changes 
like buffs and debuffs are some of the things you can define with these.

!!! note

    It is recommended to use Gameplay Effects as much as possible to modify attributes, as opposed to modifying them directly through code.
	Gameplay Effects are much easier to track and debug, while modifying attributes directly through code can become messy.