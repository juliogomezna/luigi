# Luigi Core API

## Luigi Config

<!-- Generated by documentation.js. Update this documentation by updating the source code. -->

### Configuration

#### setConfig

Sets the configuration for Luigi initially. Can also be called at a later point in time again to update the configuration.

##### Parameters

-   `configInput` **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** the Luigi Core configuration object

##### Examples

```javascript
Luigi.setConfig({
  navigation: {
    nodes: () => [
      {
        pathSegment: 'home',
        label: 'Home',
        children: [
          {
            pathSegment: 'hello',
            label: 'Hello Luigi!',
            viewUrl: '/assets/basicexternal.html'
          }
        ]
      }
    ]
  },
  routing: {
    useHashRouting: true
  }
})
```

#### getConfig

Returns the current active configuration

##### Examples

```javascript
Luigi.getConfig()
```

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** configuration object

#### getConfigValue

Gets value of the given property on Luigi config object. Target can be a value or a synchronous function.

##### Parameters

-   `property` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** the object traversal path

##### Examples

```javascript
Luigi.getConfigValue('auth.use')
Luigi.getConfigValue('settings.sideNavFooterText')
```

#### getConfigBooleanValue

Gets boolean value of the given property on Luigi config object.
Function return true if the property value is equal true or 'true'. Otherwise the function returns false.

##### Parameters

-   `property` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** the object traversal path

##### Examples

```javascript
Luigi.getConfigBooleanValue('settings.hideNavigation')
```

#### getConfigValueAsync

Gets value of the given property on the Luigi config object.
If the value is a Function it is called (with the given parameters) and the result of that call is the value.
If the value is not a Promise it is wrapped to a Promise so that the returned value is definitely a Promise.

##### Parameters

-   `property` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** the object traversal path
-   `parameters` **mixed** optional parameters that are used if the target is a function

##### Examples

```javascript
Luigi.getConfigValueAsync('navigation.nodes')
Luigi.getConfigValueAsync('navigation.profile.items')
Luigi.getConfigValueAsync('navigation.contextSwitcher.options')
```

#### isAuthorizationEnabled

Detects if authorization is enabled via configuration.

Returns **[boolean](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** returns true if authorization is enabled. Otherwise returns false.

**Meta**

-   **deprecated**: now located in Luigi.auth() instead of Luigi

## Luigi.elements()

<!-- Generated by documentation.js. Update this documentation by updating the source code. -->

### Elements

Use these functions to get DOM elements.

#### getShellbar

Returns the shellbar component.

##### Examples

```javascript
Luigi.elements().getShellbar();
```

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** the shellbar DOM element.

**Meta**

-   **since**: 0.4.12

#### getShellbarActions

Returns the shellbar actions component.

##### Examples

```javascript
Luigi.elements().getShellbarActions();
```

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** the shellbar actions DOM element.

**Meta**

-   **since**: 0.4.12

#### getMicrofrontendIframes

Returns all micro frontend iframes including the iframe from the modal if it exists.

##### Examples

```javascript
Luigi.elements().getMicrofrontendIframes();
```

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** an array of all micro frontend iframes from the DOM.

**Meta**

-   **since**: 0.4.12

#### getCurrentMicrofrontendIframe

Returns the active micro frontend iframe.
If there is a modal, which includes the micro frontend iframe, the function returns this iframe.

##### Examples

```javascript
Luigi.elements().getCurrentMicrofrontendIframe();
```

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** the active micro frontend iframe DOM element.

**Meta**

-   **since**: 0.4.12

## Luigi.auth()

<!-- Generated by documentation.js. Update this documentation by updating the source code. -->

### Authorization

Authorization helpers

#### isAuthorizationEnabled

Detects if authorization is enabled via configuration.

##### Examples

```javascript
Luigi.auth().isAuthorizationEnabled();
```

Returns **[boolean](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** true if authorization is enabled. Otherwise returns false.

## Luigi.navigation()

<!-- Generated by documentation.js. Update this documentation by updating the source code. -->

### LuigiNavigation

Use these functions for navigation-related features.

#### updateTopNavigation

Refreshes top navigation badge counters by rendering the navigation again.

##### Examples

```javascript
Luigi.navigation().updateTopNavigation();
```