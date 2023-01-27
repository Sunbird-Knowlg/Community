# Interactive Editor Plugin Guide

## Overview

Version 2.0 of the template framework unifies all types of templates into a common, programmable structure that allows developers to create and contribute templates that can be directly embedded in the authoring tool. Currently, the item data are created via the portal the corresponding templates are embedded in the content during authoring.&#x20;

This doesn't give an author a lot of control over configuring the template, and its behavior. Moreover, it is also limited to the data available as part of an item. The template v2.0 frameworks make it possible for templates to be directly configured from within the authoring tool. Developers can write the custom runtime logic, custom configuration editor, and custom editing experience (WYSIWYG) to make it easier for authors to discover and reuse these templates

These templates can include informational aspects such as a Flashcard that presents the word details or include engaging tasks such as exploring a noun and its related nouns, verbs, etc. Such templates are used for enabling learning tasks - Reading, Writing/Scribbling, Recording, Exploring, Interacting, and so on. The actual templates can range from simple single stage tasks (flashcard, scribble pad, recorder activity) to complex multi-stage tasks that guide the learner through a pre-configured learning activity.

The following aspects of extensions in the authoring tool are described:

<details>

<summary>Registration and lifecycle </summary>

Registering a plugin associates a class (prototype) with a custom plugin object. The element provides callbacks to manage its lifecycle. Uses behaviors to share code.

The plugins core is implemented in its plugin.js file. The file is loaded by the plugin manager and initialized during the load time. The plugins themselves are instantiated when the user creates that object in the editor.

_Namespaces: Proposed namespace is editor.\* for Editor plugins, renderer.\* for Renderer plugins. The community contributed plugins should follow the same convention - org.editor.\* and org.renderer.\*_

```javascript
var editor.Plugin = Class.extend({
    initialize: function(data) {}, // When the plugin is registered, it can set up its dependencies
    properties: function(data) {}, // The attributes of the plugin
    converter: function(instance) {}, // returns the converter object for this plugin
    editor: function(instance) {}, // returns the canvas editor object for the given instance
    views: function(instance) {}, // returns the views associated with this plugin
    behaviors: function(instance) {}, // returns the behavior mixins for the given instance
    create: function(data) {}, // Instantiate an object of the plugin's type (e.g on canvas)
    remove: function(data) {} // When the object of the plugin's type is deleted from canvas
// TODO - base class methods
})
```

</details>

<details>

<summary>Properties</summary>

For content plugins only, the properties exposed by the plugin are declared. This allows the plugin to inherit the default behaviors related to rendering the properties. Properties are declared by the plugin as follows:

<pre class="language-javascript"><code class="lang-javascript"><strong>[
</strong>    {
        "propertyName": "", // Name of the property
        "title": "", // Display label
        "description": "", // Tooltip text
        "category": "", // Category of the property for rendring        
        "dataType": "Text", // Data type (number, text, word, wordlist, color)
        "encoding": "", // How the property is saved (attribute, json, cdata)
        "required": true,
        "displayProperty": "Editable",
        "defaultValue": "",    
        "renderingHints": "{'editor': 'colorpicker'}"
    },
    ... // other properties
]
</code></pre>

The base plugin declares the default properties for all plugins:

1. Bounding Box - x, y, w, h
2. Border - stroke (border color), stroke-width (border size)
3. Shadow - shadow, offsetX, offsetY, blur

Each custom plugin can extend the properties list and add its own declarable properties. Any other config is generated and handled directly by the plugin and added to its CDATA section config.

</details>

<details>

<summary>Converter &#x26; Parser</summary>

Converter modifies the content DOM tree and adds the current instance to the DOM. Any cross-plugin modifications (e.g. horizontal concerns) should not be implemented as converters, but as converter behavior that can receive and apply across multiple instances.

```javascript
var editor.Converter = Class.extend({
    // Converts the current object to ECML. Passes the ECML DOM object
    toECML: function(instance, dom) {}
    // Converts the ECML node into the appropriate plugin object
    fromECML: function(node, dom) {}
})
```

</details>

<details>

<summary>Editing</summary>

Editor is the base class for all canvas editor plugins. The base class extends the Fabric.js rendering system and provides default functionality to render the editor object on canvas. Default for any editor shows a thumbnail for that object on the canvas.

```javascript
var editor.Editor = Class.extend({
    // Returns the native fabric object to render this plugin's editor
    canvasObject: function(instance) {}
})
```

</details>

<details>

<summary>View</summary>

View is a visual widget (non-canvas) that is placed in the layout. View is instantiated by the plugin and is manipulated by its behaviors. Any actions within the view are handled by its own handlers. It may or may not fire events for its actions. The view is expected to be bound to its object and update the state internally.

```javascript
var editor.View = Class.extend({
    // Renders the view
    render: function(instance) {}
})
```

</details>

<details>

<summary>Actions and Events</summary>

Actions are executables that are defined by a plugin. Action can be bound to a toolbar, menu bar etc. When the action is clicked, the callback method is called allowing the action to perfom its task. In addition, the action also fires the custom action event to allow any other behaviors to respond to the action. Clicking the action would generally show/hide a view, or add/edit state on the canvas.

```javascript
var editor.Action = Class.extend({
    // Returns the metadata about the action that is handled by the toolbar
    descriptor: function(instance) {},
    // Renders the action on the toolbar. The default action renderer renders the action on toolbar
    // based on the metadata descriptor. Only if the action requires custom rendering,
    // would a plugin need to override the render function
    render: function(instance) {}
    //
})
```

#### Action Data

```
[
    {
    "icon": "", // Name of the property
    "title": "", // Display label
    "description": "", // Tooltip text
    "category": "", // Category of the property for rendring
    "state": "", // Current state of the action (e.g. selected tool)
    "enabled": true, // Whether the action in toolbar is enabled or not
    "visible": true, // Whether the action in toolbar is visible or not
    "type": "" // Type of action (button, dropdown, dropdown with selection, custom)
    "view": object // Show the view object on click of this action
    "event": "" // Custom event name for this action
    "handler": function() {} // Handler function reference to call on click
    },
    ... // other properties
]
```

Note: There may be a need to bind the action to some specific property. E.g. when we put a color selector action, bind it to the color property automatically. Need to think this through.

</details>

<details>

<summary>Behaviors</summary>

The basic interfaces are as follows:

#### Text Provider

Text providers are plugins that expose a textual representation of their content. This allows the authoring tool and other plugins to work with the text and leverage the language platform (e.g. to work with the parser API).

```javascript
var editor.SamplePlugin = editor.Behavior.extend({
    text: function(data) {}, // Returns a plain-text extract of the object
    // E.g. a Read-Along plugin can return the text value of the contents
    // A complex plugin could return a concatenated string representation
});
```

#### State Listener

Listener for state in the authoring tool. The callback pattern allows the behavior to listen for events while the action is happening (e.g. rotating), or after the action is completed (e.g. rotated). If the action is cancelled, the end event is called with state=CANCELLED. Understandably, the progress events are called on every tick while the end event is called once per action (on finished or cancelled).

```javascript
var editor.SamplePlugin = editor.Behavior.extend({
    selected: function(instances[], state) {}, // Called when the object(s) is selected
    exited: function(instances[], state) {}, // Called when selection is ended
    editing: function(instances[], state) {}, // Called when the object is being edited (config view i
    changed: function(instances[], state, data) {}, // Called after the editing is completed
    moving: function(instances[], state) {}, // Called when object(s) are being moved
    moved: function(instances[], state) {}, // Called after the move is completed
    resizing: function(instances[], state) {}, // Called when selection is resizing
    resized: function(instances[], state) {}, // Called when resizing is completed
    rotating: function(instances[], state) {}, // Called when selection is being rotated
    rotated: function(instances[], state) {}, // Called when selection is rotated
});
```

#### Clipboard Listener

Listener for clipboard events - when an object is copied on the clipboard or when it is pasted.

```javascript
var editor.SamplePlugin = editor.Behavior.extend({
    // Called when the selected objects are being copied
    // (allows plugin to control the state it copies to clipboard)
    copy: function(instances[], state) {},
    // Called after the objects are copied to clipboard
    // (e.g. allows plugins to enable the paste button)
    afterCopy: function(instances[], state) {},
    // Called before paste
    // (e.g. allows plugins to transform data before pasting)
    // (e.g. read-along was copied to clipboard, when pasting in text, its text is copied)
    paste: function(instances[], state) {},
    // Called after the paste is completed
    // (e.g. allows plugins to respond to the paste operation)
    // (e.g. invoke the language parse API after text is pasted)
    afterPaste: function(instances[], state, data) {}
});
```

#### Action Listener

Listener for custom actions. E.g. when read-along editing is completed, it fires the event, that is handled by the appropriate listener.

```javascript
var editor.SamplePlugin = editor.Behavior.extend({
    // Called after the custom action has finished executing
on: function(event, state) {}
});
```

_**Note:** This mechanism doesn't allow listeners to prevent the action from happening (there is no "beforeXX" event callback and no way defined to cancel an event). This is intentional. If an action has to be disabled based on some condition, the listener should observe the condition and disable the action itself (prevent the user from taking the action rather than trying to cancel it)._

#### Reusable Views/Plugin Artifacts

1. PropertyConfigFormView - Popup that generates a form based on properties data. For most simple widgets, this form view might be sufficient to configure them
2. DefaultButtonAction - Default toolbar action (simple button).
3. WordSelectorView - Uses APIs and provides UI to select a single word from repo
4. WordlistSelectorView - Uses APIs and provides a UI to select multiple words from repo

#### Property Observer

Handles the property change notifications for the plugins

```javascript
var editor.SamplePlugin = editor.Behavior.extend({
    changed: function(property, data) {}, // Called when a property value is modified
});
```

</details>

<details>

<summary>Examples/Illustrations</summary>

#### 1. Read-Along Widget (Content Plugin)

Plugin.js

```javascript
var editor.ReadAlongPlugin = editor.TextPlugin.extend({
    initialize: function() {
        // Instantiate ReadAlongConfigAction
        var data = {
        "name": "Attach Read-Along",
        "icon": "fa-link",
        "view": "ReadAlongConfigView"
        }
        var action = new DefaultButtonAction(data);
        // Add the action to ContextToolbar, for all TextPlugins and their derivatives
        toolbarManager.add(ContextToolbar, action, "TextPlugin");
        },
        // INHERITED - Reuses available primitive text editor on canvas
        editor: function() {
        return new TextCanvasEditor(this);
        }
        // Custom view that configures the read-along text
        views: function() {
        return new ReadAlongConfigView();
    }// Converter functions
    // -------------------
    // Produces the following output
    //
    // <htext xywh color...>
    //
    <cdata[[read along config]]>
    // </htext>
    //
    toECML: function(instance, dom) {}
    // Parses the htext cdata section
    fromECML: function(node, dom) {}
    // Behaviors
    // ----------------------
    // INHERITED - returns the plain text value of the text plugin
    text: function(data) {},
})
```

ReadAlongConfigView.js

```javascript
var editor.ReadAlongConfigView = editor.View.extend({
// Renders the read along creator view, sets the configuration of the read-along on the
// instance object passed to it
// If the view is launched on a TextPlugin object, replace it with the ReadAlongPlugin object
render: function(instance) {}
})
```

#### 2. Editor Extension - Word Complexity Provider

plugin.js

```javascript
var editor.WordComplexityPlugin = editor.Plugin.extend({
    initialize: function() {
    // Instantiate WordComplexityView
    // Register event listeners
    // Register word complexity listener for all TextPlugin objects
    // Read-along also inherits from TextPlugin (all text plugin and its derivatives)
    eventManager.register("TextPlugin", new WordComplexityListener());
    },
    // Custom view that configures the read-along text
    views: function() {
    return new WordComplexityView(); // TODO: Configure where the view docks?
    }
})
```

WordComplexityListener.js

```javascript
var editor.SamplePlugin = editor.Behavior.extend({
    selected: function(instances[], state) {
    // If parsed result of the instance available, activate view with the parsed results
    // If not, make API call for parse API
    },
    exited: function(instances[], state) {
    // Hide the view
    },
    changed: function(instances[], state, data) {
    // Fire the API call, cache the results for this instance
    },
});
```

WordComplexityView.js

```javascript
var editor.WordComplexityView = editor.View.extend({
    // Renders the sidebar view
    render: function(instance) {}
})
```

#### 3. ECML Template

Example of a template that has read-along and recorder widgets on the same page.

```html
<theme>
    <manifest>
    <!-- All the assets used in the read-along or recorders (e.g. recorder icon), plugins -->
    </manifest>
    <template id="xxx">
        <htext>Click here to edit</htext>
        <recorder>...</recorder>
    </template>
</theme>
```

plugin.js

```javascript
var editor.DefaultTemplatePlugin = editor.Plugin.extend({
    initialize: function() {
    // Instantiate DefaultTemplateSelectorView
    },
    // Custom view that allows user to select templates
    views: function() {
    return new DefaultTemplateSelectorView();
    }
    // Editor - Since the template consists of other elements, they are available for editing
    // via their respective plugins
    // TODO - PluginManager needs to discover embedded plugins via their ECML name, and then
    // load them (invoke the plugin lifecycle)
})
```

DefaultTemplateSelectorView.js

```javascript
var editor.DefaultTemplateSelectorView = editor.View.extend({
    // Renders the template selector popup
    // Upon selection of a template, calls an internal merge function
    render: function(instance) {}
    // Takes the selected template body, and merges its manifest with the ECML DOM
    // Adds template DOM contents on the current stage for that template
    merge: function(instance) {}
})
```

</details>
