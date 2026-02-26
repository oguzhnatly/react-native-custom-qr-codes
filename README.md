# 🔲 react-native-custom-qr-codes

Fully customizable QR code component for React Native with TypeScript support and RTL layout compatibility. Style the code pieces, eye shapes, colors, gradients, logos, and background images however you need.

[![npm version](https://img.shields.io/npm/v/@oguzhnatly/react-native-custom-qr-codes.svg)](https://www.npmjs.com/package/@oguzhnatly/react-native-custom-qr-codes)
[![npm downloads](https://img.shields.io/npm/dw/@oguzhnatly/react-native-custom-qr-codes.svg)](https://www.npmjs.com/package/@oguzhnatly/react-native-custom-qr-codes)
[![license](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![platforms](https://img.shields.io/badge/platform-iOS%20%7C%20Android-lightgrey.svg)](https://github.com/oguzhnatly/react-native-custom-qr-codes)

<p align="center">
  <img alt="QR Code Example 1" src="https://raw.githubusercontent.com/oguzhnatly/react-native-custom-qr-codes/master/assets/qr-code-1.png" width="200">
  <img alt="QR Code Example 2" src="https://raw.githubusercontent.com/oguzhnatly/react-native-custom-qr-codes/master/assets/qr-code-2.png" width="200">
  <img alt="QR Code Example 3" src="https://raw.githubusercontent.com/oguzhnatly/react-native-custom-qr-codes/master/assets/qr-code-3.png" width="200">
</p>

---

## Features

- ✅ Full TypeScript support with typed props
- ✅ RTL layout support
- ✅ Multiple code piece styles: square, circle, dot, diamond, sharp, ninja
- ✅ Independent eye shape control (outer and inner separately)
- ✅ Linear gradient foreground colors
- ✅ Logo overlay in the center of the QR code
- ✅ Background image fill for code pieces
- ✅ Configurable error correction level
- ✅ iOS and Android

---

## Installation

```sh
npm install @oguzhnatly/react-native-custom-qr-codes
```

```sh
yarn add @oguzhnatly/react-native-custom-qr-codes
```

This package depends on `react-native-svg`. If you are not using Expo, install and link it manually:

```sh
npm install react-native-svg
cd ios && pod install
```

For manual linking instructions see the [react-native-svg documentation](https://github.com/software-mansion/react-native-svg#installation).

---

## Usage

```tsx
import { QRCode } from '@oguzhnatly/react-native-custom-qr-codes';

<QRCode content="https://github.com/oguzhnatly" />
```

---

## Props

| Prop | Type | Default | Description |
|---|---|---|---|
| `content` | `string` | `'No Content'` | The string to encode in the QR code |
| `size` | `number` | `250` | Width and height of the component in pixels |
| `padding` | `number` | `1` | Padding between the edge and the QR code in piece units |
| `color` | `string` | `'black'` | Foreground color of the QR code |
| `backgroundColor` | `string` | `'white'` | Background color of the component |
| `codeStyle` | `string` | `'square'` | Style of the centre QR code pieces. See values below |
| `outerEyeStyle` | `string` | `'square'` | Style of the outer frame of the QR code eyes |
| `innerEyeStyle` | `string` | `'square'` | Style of the inner dot of the QR code eyes |
| `ecl` | `string` | `'L'` | Error correction level. Higher levels allow logo overlays. `L` `M` `Q` `H` |
| `logo` | `ImageSource` | none | Image source to display in the center of the QR code. Requires a higher `ecl` |
| `logoSize` | `number` | none | Size of the logo overlay in pixels |
| `linearGradient` | `ColorValue[]` | none | Two colors used for a linear gradient on the foreground |
| `gradientDirection` | `number[]` | `[0,0,170,0]` | Numbers defining the [gradient orientation](https://developer.mozilla.org/en-US/docs/Web/SVG/Tutorial/Gradients) |
| `backgroundImage` | `ImageSource` | none | Image used as the fill pattern for QR code pieces. Eye styling is disabled when this is used |
| `isRTL` | `boolean` | `false` | Enables right-to-left layout rendering |

### `codeStyle` values

`square` `circle` `dot` `diamond` `sharp` `ninja`

### `outerEyeStyle` values

`square` `circle` `circles` `diamond` `rounded`

### `innerEyeStyle` values

`square` `circle` `circles` `diamond` `rounded`

---

## Examples

### Code styles

```tsx
<QRCode content="https://example.com" codeStyle="square" />
<QRCode content="https://example.com" codeStyle="circle" />
<QRCode content="https://example.com" codeStyle="dot" />
<QRCode content="https://example.com" codeStyle="diamond" />
<QRCode content="https://example.com" codeStyle="sharp" />
```

<img src="./assets/example-code-styles.png" height="220" />

### Eye styles

```tsx
<QRCode content="https://example.com" outerEyeStyle="square" innerEyeStyle="square" />
<QRCode content="https://example.com" outerEyeStyle="circle" innerEyeStyle="circle" />
<QRCode content="https://example.com" outerEyeStyle="diamond" innerEyeStyle="diamond" />
```

<img src="./assets/example-outer-eye-styles.png" height="220" />
<img src="./assets/example-inner-eye-styles.png" height="220" />

### Logo overlay

Use `ecl="H"` to ensure the QR code remains scannable with a logo covering the center:

```tsx
<QRCode
  content="https://example.com"
  logo={require('./logo.png')}
  logoSize={60}
  ecl="H"
/>
```

<img src="./assets/example-logo.png" height="220" />

### Linear gradient

```tsx
<QRCode
  content="https://example.com"
  linearGradient={['rgb(255,0,0)', 'rgb(0,100,255)']}
/>

<QRCode
  content="https://example.com"
  linearGradient={['rgb(255,0,0)', 'rgb(0,100,255)']}
  gradientDirection={[0, 170, 0, 0]}
/>
```

<img src="./assets/example-linear-gradient.png" height="220" />

### Background image

Eye styling is not available when using `backgroundImage`:

```tsx
<QRCode
  content="https://example.com"
  backgroundImage={require('./texture.png')}
  ecl="H"
/>
```

<img src="./assets/example-background-image.png" height="220" />

### RTL support

```tsx
<QRCode
  content="https://example.com"
  isRTL={true}
/>
```

---

## License

MIT © [Oguzhan Atalay](https://github.com/oguzhnatly)
