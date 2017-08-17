# Proposal: three-particle-designer

Author(s): [rohan-deshpande](http://github.com/rohan-deshpande)

Last updated: 2017-08-17

## Abstract

This application will aim to deliver a fully featured 3D particle designer for Mac, Linux and Windows. This will be accomplished using web technologies such as 

* [JavaScript](https://www.javascript.com/)
* [React](https://facebook.github.io/react/)
* [Three](https://threejs.org)
* [NWJS](https://nwjs.io)

The app will have a GUI for creating, editing and saving projects as well as the ability to export particle designs in different formats.

## Background

Currently, there is no way to easily design particles for `three` based apps. There are a number of particle engines that have been developed for the library such as

* [ShaderParticleEngine](https://github.com/squarefeet/ShaderParticleEngine)
* [three.proton](https://a-jie.github.io/three.proton/)

However, these engines have limitations when wanting to design advanced particle effects as all the work would need to be done in code, which is impractical. 

This app will leverage, `three` and one of the libraries listed above for visualization, couple it to a GUI and enable designers to create particle designs without having to write code and with instant feedback.

## Proposal

Much like 71Squared's **[Particle Designer](https://71squared.com/particledesigner)** a desktop application will need to be created with a number of views and controls to support the ability design, save, edit and export particles. 

The difference to Particle Designer is that particles will need to support emission in 3D space.

I propose that we leverage what this application is doing as much as we can, but add features to make the particles work in 3D space. 

Conceptually, and at a basic level, this should be as simple as adding a third axis to the potential direction in which a particle can go. For example in the _Emitter Settings_ of the app, there are configurations for `Source Position Variance X` and `Source Position Variance Y`; we would simply add `Source Position Variance Z`.  

If we want to get really advanced, we would add some kind of path finding where we could force the particles to follow a line or a curve the user has drawn. This is pretty advanced though.

## Rationale

There aren't really any alternative approaches here. The drawback is that it will most likely be quite a lot of work, it's best if we start with simple features first then expand it later if need be.

## Implementation

As mentioned above there are a few open source libraries which we will have to use to make this in a reasonable amount of time while still delivering something stable. In terms of UX, I would take more of a Photoshop like approach in terms of layout as opposed to Particle Designer. Palettes will allow the UI to scale better than panes.

We should definitely use a UI kit to make things easier, I recommend [ant design](https://ant.design/) as it has a lot of pre built components we can leverage.

## Open issues (if applicable)

There's definitely some unknowns here. One major one for me is that Particle Designer doesn't seem to really have a "timeline" like feature which would be very useful for creating particle effect sequences. This of course would be a tonne of work, but I'm not sure how an effect would "start" and "end" without one.

There's also the question of collisions. This is something that is not relevant to 2D environments but is very real for 3D ones. Particles colliding with 3D meshes can create ugly clipping like effects and artifacts. I'm not sure if the designer should have some kind of control for this or if that should be the job of the tool importing the particle design data which the app exports.
