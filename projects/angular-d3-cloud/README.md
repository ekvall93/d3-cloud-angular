# Angular D3 Word Cloud
D3 Cloud component for Angular built upon d3-cloud

<img src="./demo.png">

# Installation
```
npm install --save angular-d3-cloud
```
# Usage
First import the package to your app module
```ts
// app.module.ts
import { AngularD3CloudModule } from 'angular-d3-cloud'
@NgModule({
  imports: [
    AngularD3CloudModule
  ],
  ...
})
```
Now the component is ready to use.

```html
<!-- app.component.html -->
<angular-d3-cloud
  [data]="data"
  [width]="700"
  [height]="600"
  [padding]="5"
  font="serif"
  [rotate]="0"
  [autoFill]="true"
  (wordClick)="onWorkClick($event)"
></angular-d3-cloud>
```
```ts
// app.component.ts
export class AppComponent {
  data = [
    "Hello", "world", "normally", "you", "want", "more", "words",
    "than", "this"].map(function (d) {
      return { text: d, value: 10 + Math.random() * 90};
    })
}
```
# Props
| Name           | Description                                                                                                | Type                                          | Required | Default             |
|----------------|------------------------------------------------------------------------------------------------------------|-----------------------------------------------|----------|---------------------|
| data           | The input data for rendering                                                                               | Array<{ text: string, value: number }>        |     ✓    |                     |
| width          | Width of component (px)                                                                                    | number                                        |          | 700                 |
| height         | Height of component (px)                                                                                   | number                                        |          | 600                 |
| fontSizeMapper | Map each element of data to font size (px)                                                                 | Function: (word: string, idx: number): number |          | word => word.value; |
| rotate         | Map each element of data to font rotation degree. Or simply provide a number for global rotation. (degree) | Function \| number                            |          | 0                   |
| padding        | Map each element of data to font padding. Or simply provide a number for global padding. (px)              | Function \| number                            |          | 5                   |
| font           | The font of text shown                                                                                     | Function \| string                            |          | serif               |
| autoFill       | Whether texts should be fill with random color or not                                                      | boolean                                       |          | false               |

# Events
| Name          | Description                                              | Payload                           |
|---------------|----------------------------------------------------------|-----------------------------------|
| wordClick     | Event triggered when click event triggered on a word     | { event: MouseEvent, word: Word } |
| wordMouseOver | Event triggered when mouseover event triggered on a word | { event: MouseEvent, word: Word } |
| wordMouseOut  | Event triggered when mouseout event triggered on a word  | { event: MouseEvent, word: Word } |

> The `Word` interface imported from `d3-cloud`
# Example
Run the following commands to start sample project:
```
ng build angular-d3-cloud --watch
npm start # in a separate terminal
```
# Thanks
This project is built with the idea of [React D3 Cloud](https://github.com/Yoctol/react-d3-cloud)