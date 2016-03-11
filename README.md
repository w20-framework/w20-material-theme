# W20 Material Theme

## Installation

```
bower install w20-material-theme
```

## Configuration

In `#/modules/main/theme`, `primaryPalette` and `accentPalette` properties MUST be defined. Each defined `*Palette` property MUST have at least their `name` properties defined. The `hues` property follows [Material Angular color intentions syntax](https://material.angularjs.org/latest/Theming/03_configuring_a_theme#specifying-custom-hues-for-color-intentions). A list of color palettes is present on the [Material Design Specification](http://www.google.com/design/spec/style/color.html#color-color-palette).

```javascript
"bower_components/w20-material-theme/w20-material-theme.w20.json": {
  "modules": {
    "sidenav": {
      "logoUrl": "/home",
      "logoImg": "/images/logo.png",
      "backgroundImg": "/images/header-background.jpg"
    },
    "main": {
      "theme": {
        "primaryPalette": {
          "name": "indigo",
          "hues": {
            "default": "",
            "hue-1": "",
            "hue-3": ""
          }
        },
        "accentPalette": {
          "name": "amber"
        },
        "warnPalette": {
          "name": "red",
          "hues": {
            "default": "",
            "hue-2": ""
          }
        },
        "backgroundPalette": {
          "name": "blue-grey"
        },
        "dark": true // Defaults to false
      }
    }
  }
}
```

## Usage

A simple usage would be:

```html
<!DOCTYPE html>
<html data-w20-app>
<head>
  <meta http-equiv="X-UA-Compatible" content="IE=Edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta charset="utf-8">
  <title>W20 Material Theme Test</title>
  <script type="text/javascript" data-main="bower_components/w20/modules/w20" src="bower_components/requirejs/require.js"></script>
</head>
<body layout ng-cloak md-swipe-left="$emit('w20.material.sidenav.open', false)" md-swipe-right="$emit('w20.material.sidenav.open', true)">
  <div id="w20-loading-cloak">
    <div class="w20-loading-indicator"></div>
  </div>
  <w20-material-sidenav component-name="w20.material.sidenav"></w20-material-sidenav>
  <main class="app-main" layout="column" flex>
    <w20-material-topbar></w20-material-topbar>
    <md-content class="app-content" ng-view layout="column" layout-align="start center" flex></md-content>
  </main>
  <div data-w20-error-report></div>
</body>
</html>
```

### w20-material-sidenav

Create a [Material Angular sidenav](https://material.angularjs.org/latest/demo/sidenav) based upon a [temporary drawer from the Material Design Specification](https://www.google.com/design/spec/patterns/navigation-drawer.html#navigation-drawer-behavior).

Generated by the `routes` property present in the fragment configuration. For each route, the `icon` property define its icon. Icons are [Material Design Icons](https://design.google.com/icons/). By default the icon is `arrow_right`.

```javascript
"routes": {
  "/home": {
    "templateUrl": "/views/home.html",
    "hidden": false,
    "icon": "home"
  }
},
```

#### component-name attribute

Defaults to `w20.material.sidenav`.

Customize the event name for opening the sidenav.

#### Sidenav event

`$scope.$emit('w20.material.sidenav.open'[, state])`: 
- `state`: Boolean. Open the sidenav if `true`. Optional

If `state` is omitted, the event toggle the state of the sidenav.

**Tips**: If you consider opening and closing the sidenav by swiping, bind the event emitters on `<body>` like below.

```
<body md-swipe-left="$emit('w20.material.sidenav.open', false)" md-swipe-right="$emit('w20.material.sidenav.open', true)">
```