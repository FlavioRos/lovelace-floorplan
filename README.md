# lovelace-floorplan

Floorplan for Lovelace is here!

## Installation

### HACS
**Just add the URI to [HACS](https://hacs.xyz/)'s as custom repository.**

In the procress, kindly note down the location of the files. Normally you'll find them in the community/lovelace-floorplan-directory.

### Manual

#### 1) Download files from repo

To get started, copy the [dist/floorplan-card.js](https://raw.githubusercontent.com/pkozul/lovelace-floorplan/master/www/floorplan/floorplan-card.js) to `www/lovelace-floorplan` folder of your Home Assistant installation (You can right-click the file, to save it to your disk):

#### 2) Floorplan image

You'll then need an SVG file of your floorplan, and a CSS file for styling. You can use the samples provided to get started. Copy them to the `www/lovelace-floorplan/examples/simple` folder of your Home Assistant installation:

- [examples/simple/simple.svg](https://raw.githubusercontent.com/pkozul/lovelace-floorplan/master/www/floorplan/examples/simple/simple.svg)
- [examples/simple/simple.css](https://raw.githubusercontent.com/pkozul/lovelace-floorplan/master/www/floorplan/examples/simple/simple.css)

In the SVG file, rename the element IDs to match the entitiy IDs you have in your Home Assistant installation.

#### 3) Adding to Lovelace

Add the following to the `resources:` section of your Lovelace config.

```
resources:
  - type: module
    url: /local/lovelace-floorplan/floorplan-card.js?v=1.1.14
```

You can then start adding floorplan cards to your Lovelace config. Under `entities:`, make sure to add the entity IDs which you want to use in the floorplan:

```
  - cards:
      - config:
          image: /local/lovelace-floorplan/examples/simple/simple.svg?v=1.1.14
          rules:
            - entities:
                - binary_sensor.main_bedroom
                - binary_sensor.living_area
                - binary_sensor.double_garage
              states:
                - class: 'binary-sensor-off'
                  state: 'off'
                - class: 'binary-sensor-on'
                  state: 'on'
          stylesheet: /local/lovelace-floorplan/examples/simple/simple.css?v=1.1.14
        title: Simple Floorplan
        type: 'custom:floorplan-card'
    icon: 'mdi:floor-plan'
    id: system
    title: Floorplan
```

Note: If you're using the Lovelace editor that is built into the user interface, click on the three dots in the upper-right corner of the screen and select `Configure UI`. Then click on the three dots again and select `Raw config editor`. Then you'll be able to add the resources and card described above.

## Floorplan examples

To get started with some fully working examples, try some of the floorplans below:

- [Simple Floorplan](https://github.com/pkozul/lovelace-floorplan/tree/master/www/floorplan/examples/simple)
- [Ring doorbell](https://github.com/pkozul/lovelace-floorplan/tree/master/www/floorplan/examples/ring)

## Inspiration and Support
Check the [Floorplan-section](https://community.home-assistant.io/c/third-party/floorplan/28) on the Home Assistant Community.


## Bulding floorplan-card.js
The script is bundled with browserify. 

To build floorplan-card.js, just run:
 1. `npm install`
 2. `npm run build`