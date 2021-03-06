# react-google-maps-loader ![npm](https://img.shields.io/npm/v/react-google-maps-loader.svg) ![license](https://img.shields.io/npm/l/react-google-maps-loader.svg) ![github-issues](https://img.shields.io/github/issues/xuopled/react-google-maps-loader.svg)

React HOC to use google maps services into your react applications

## Install

```sh
npm install --save react-google-maps-loader

// OR

yarn add react-google-maps-loader
```

## Changelog

See [changelog](./CHANGELOG.md)

## Usage

The `googleMapsLoader` HOC take an options object in parameter.
You can specify any parameters Google let you use to load Google Maps API.
Checkout [Google Maps Javascript API documentation](https://developers.google.com/maps/documentation/javascript/libraries) to specify librairies or others parameters.

```js
import React, {Component} from "react"
import googleMapsLoader from "react-google-maps-loader"

CONST = GOOGLE_MAPS_API_KEY = "myapikey" // Change your api key

class MyComponent extends Component {
    constructor() {
        super()
        this.state = {
            map: null,
        }
    }

    componentDidMount() {
        if (this.props.googleMaps)
            this.initMap()
        }
    }

    componentDidUpdate(prevProps) {
        if (!prevProps.googleMaps && this.props.googleMaps)
            this.initMap()
        }
    }

    initMap() {
        const map = new googleMaps.Map(this.ref_map)
        this.setState({map})
    }

    render() {
        const {googleMaps} = this.props

        // You should handle the case when Google Maps is not loaded yet
        return googleMaps
            ? <div ref={ref => this.ref_map = ref} />
            : <Spinner /> // You should use a custom loader here
    }
}

export default googleMapsLoader(MyComponent, {
  libraries: ["places", "geometry"],
  key: GOOGLE_MAPS_API_KEY,
})
```

## Development

### Clean `lib` folder

```js
npm run clean
```

### Build `lib` folder

```js
npm run build
```

### Watch `src` folder

```js
npm run watch
```

### Lint `src` folder

```js
npm run lint
```

## License

See [MIT](./LICENCE)
