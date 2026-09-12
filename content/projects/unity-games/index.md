# Unity Games

[< Back Home](/)

Making games represents a lot of why I like making software: rules need to interact with each other, state needs to be tracked, and seemingly small changes can have a surprisingly big impact.   

Game development has been a useful way to learn software development because it makes state, behaviour, and system interactions impossible to ignore.

I've worked with classes, inheritance, interfaces, polymorphism, events, LINQ, coroutines, and Unity's component-based architecture while building these projects.

More importantly, I've learned how quickly a collection of individually simple systems can become complicated once they start interacting.

That's a problem I enjoy taking on.

You can find and play my finished projects on [itch.io](https://tmcausla.itch.io/).

## Tech Stack

- C#
- Unity
- Git / GitHub

## Jungle Defense

A month-long game-jam project built around defending a jungle settlement from waves of enemies.

This was the project where I had the opportunity to contribute not just code, but game design. I pushed for a card-based mechanic early in development, which eventually became a central part of the gameplay.

### Systems & Concepts

This project gave me experience working with a larger collection of interconnected gameplay systems:

- Card systems and deck management
- Player state and scoring
- Turn and wave management
- Resource and action point systems
- Game state transitions
- Unity events
- Object-oriented design

The card system made particularly good use of inheritance and polymorphism. A common **Card** base class defines shared behaviour, while individual cards override that behaviour to implement their own effects.

This allowed us to add different card types without turning the central card-management system into one giant collection of special cases.

And now I have a modular **card.cs** file that I look forward to using again in future game projects.

### Screenshots

![Jungle Defense Title screen](/images/unity/jungle-defense-title.png)

![Jungle Defense card display](/images/unity/jungle-defense-display.png)

![Jungle Defense gameplay](/images/unity/jungle-defense-gameplay2.png)

## Season of the Witch

Another game jam project, with a greater emphasis on working as part of a team and contributing to an existing codebase.

We built a single level for a magic-slinging adventure platformer that concluded with a boss fight.  

### Systems & Concepts

This project gave me experience implementing new functionality while working within systems that other people had already built.

That meant spending a fair amount of time understanding unfamiliar code before changing it, then debugging the interactions between my additions and the existing game systems.

I also took on a strong organizational role within the team, helping to coordinate work and keep the project moving toward a finished game within the game jam's deadline.

That experience reinforced something I've encountered in software development as well: sometimes the difficult part isn't writing the new code, it's understanding the code that's already there.

### Screenshots

![Season of the Witch title screen](/images/unity/season-of-witch-title.png)

![Season of the Witch gameplay 1](/images/unity/season-of-witch-gameplay1.png)

![Season of the Witch gameplay 2](/images/unity/season-of-witch-gameplay2.png)

![Season of the Witch boss fight](/images/unity/season-of-witch-bossfight.png)

## Can't Stop

A solo project based on one of my favourite board games: Can't Stop.

I built this one because I wanted to see what it would take to turn a physical board game into a digital system.

## Systems & Concepts

The challenge here was translating rules that are easy to understand when looking at a physical board into explicitly programmed state and behaviour.

This project includes systems for:

- Player state and scoring
- Dice rolling
- Point tracks / completion
- Turn progression
- Local multiplayer

The project is intentionally much more focused on functionality than presentation.

There aren't elaborate menus or particularly impressive visual effects. The important part to me was getting the underlying rules working correctly and making the game playable from start to finish.

That makes it a useful reminder of why I enjoy programming: **I like making the thing work**.

### Screenshots

{{ img of Can't Stop gameplay }}

[< Back Home](/)
