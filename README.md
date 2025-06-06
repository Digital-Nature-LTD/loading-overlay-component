# Digital Nature - Loading Overlay Web Component
This package contains a loading overlay web component.

The component supports adding and removing of messages, and will rotate through the given messages in a loop.


## Usage

### Simple usage
Import the component, this will register the custom element `<digital-nature-loading-overlay>`.
```javascript
// js
import DigitalNatureLoadingOverlayComponent from '@digital-nature-ltd/loading-overlay-component';
```

### Populating with message(s)

#### Using slots
You can set the slot content directly.
```html
<!-- html file -->
<digital-nature-loading-overlay class="populated">
    <p slot="upper-text">Loading...</p>
    <p slot="lower-text">Please wait while we process your request.</p>
</digital-nature-loading-overlay>
```

#### Using data attributes
Set one or more messages by using the `data-messages` attribute.

If there are several messages specified then this will rotate through them on a loop.
```html
<!-- html file -->
<digital-nature-loading-overlay data-messages='["loading, please wait...", "Please wait while we process your request.", "Gaw, this is taking a while..."]' class="populated"></digital-nature-loading-overlay>
```

#### Using JavaScript
You can also set the messages using JavaScript.
```javascript
// js
import DigitalNatureLoadingOverlayComponent from '@digital-nature-ltd/loading-overlay-component';

let loadingOverlay = DigitalNatureLoadingOverlayComponent.create();
loadingOverlay.addMessage(message);
```


### Deleting messages
Messages can be removed individually, by passing the message string to the `deleteMessage` method.

**Once all messages are removed, the loading overlay itself will be removed.**
```javascript
// js
const myMessage = "This message will be removed.";
// message will be removed after 5 seconds
loadingOverlay.addMessage(myMessage);

setTimeout(() => {
    loadingOverlay.deleteMessage(myMessage);
}, 5000);
```


## Slots
The component supports the following slots:

### `upper-text`
Text that will be displayed in the upper part of the loading overlay. This is typically used for a short message or title.

### `lower-text`
Text that will be displayed in the lower part of the loading overlay. This is typically used for a longer message or description.


## Styling the component
Some aspects of the component can be styled using CSS variables.

The following variables are available:
```css
digital-nature-loading-overlay {
    --font-size-paragraph-small: 0.8rem;
    --font-size-paragraph: 1rem;
}
```

The `:before` psuedo element is added to the centre of the overlay. It can be used to add an image:
```css
digital-nature-loading-overlay {
    &:before {
        background: transparent url(your-image-here.svg) no-repeat center center;
        background-size: 100px;
    }
}
```


