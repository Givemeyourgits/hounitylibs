As of now, HOUnityLibs is composed of different projects, each of which generates a separate and independent assembly (you can find the compiled files inside each bin directory). It is still in pre-alpha: everything works, and I will add stuff to it while I go on, but it's yet to be fully documented and I might change parts of the API.


---

# HOEditorGUIFramework #

### HOGUILayout ###
A static class used to draw and layout content, inspired by [Breno Azevedo](https://twitter.com/brenoazevedo)'s GUILayout alternative. It contains various methods to draw special GUI elements (drag&drop areas, buttons, toolbars, toggles, foldouts, etc.), and is also meant to replace any Unity vertical/horizontal/disabled GUILayout block, as this examples shows:
```
// instead of this:
GUILayout.BeginHorizontal();
/* code lines */
GUILayout.EndHorizontal();

// You can do this
HOGUILayout.Horizontal(() => {
  /* code lines */
});
// Pro: way more readable and less prone to errors
// Con: you can't simply exit an action
```

### HOGUIDrag ###
Allows dragging of elements inside a panel.

### HOGUIStyle ###
Various ready-made styles to use with the GUI.

### HOEditorUndoManager ###
Allows to manage undo easily and effectively on every custom panel/window.

### ExtensionMethods ###
Useful extension methods.


---

# HOEditorUtils #
Simple utils for use in UnityEditor.


---

# HODebugFramework #
Components and utils for debugging purposes.


---

# HO2DToolkit #
Framework for [Unikron's 2D Toolkit](http://www.unikronsoftware.com/2dtoolkit/). It allows to easily use sprites as GUI elements. To use it, you have to implement some interfaces in 2D Toolkit (nothing special: just add the interfaces and the implementation is already done):
  * Holoville.HO2DToolkit.IHOtk2dSprite interface in 2D Toolkit's tk2dBaseSprite class
  * Holoville.HO2DToolkit.IHOtk2dTextMesh interface in 2D Toolkit's tk2dTextMesh class
  * Holoville.HO2DToolkit.IHOtk2dSlicedSprite interface in 2D Toolkit's tk2dSlicedSprite class
Also, you'll need to add this as the first line of tk2dBaseSprite:
`public string GetSpriteName() { return CurrentSprite.name; } `

**Requires the open-source [DOTween tweening library](http://dotween.demigiant.com/) to be in your Unity project**

### HOtk2dButton ###
Attach this component to a sprite, in order to manage it as a button. Can automatically add animations, correctly manages layered elements in a realistic way (by avoiding the activation of buttons when other elements are on top of them), can be set as a toggle, and can be included in a "toggleGroup" (which works like radio buttons, where selecting one will deselect the others).

Event listeners for every button action can be added directly to the button, or to HOtk2dGUIManager, which will dispatch an event when any button action happens.