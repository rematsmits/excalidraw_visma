I used Curor for this task with Auto model selection.

**3+ prompts you used to understand the codebase:**

1. Explain the full structure an flow for this project on how the elements are selected, drawn on map and which classes, function are used
2. Find where arrow element type, setup and configuration is located in this codebase
3. How the object creation flow looks for single-headed arrow?
4. Where all type definitions for arrow element are located in this codebase?
5. Where to create DoubleEnded arrow element?

**2+ prompts for implementation help:**

1. How to add multiple inherited types for {reference} arrow element?
2. How to create new type that inherings from ExcalidrawArrowElement and ExcalidrawElbowArrowElement nad is used only as placeholder enum element?
3. @packages/excalidraw/components/icons.tsx:369-378 Change the style to display double-ended arrow
4. And many more lookups and questions about typescript syntax and specifications
5. Many {reference to terminal} and error messsage lookups and fixes/fix explanations

```
And check this error
[TypeScript] Argument of type '"selection" | "rectangle" | "diamond" | "ellipse" | "double_headed_arrow" | "embeddable"' is not assignable to parameter of type '"selection" | "rectangle" | "diamond" | "ellipse" | "embeddable"'. Type '"double_headed_arrow"' is not assignable to type '"selection" | "rectangle" | "diamond" | "ellipse" | "embeddable"'.
/Users/matiss/Apps/excalidraw_visma/packages/excalidraw/components/App.tsx:7316:9
    7314 |      {
    7315 |       this.createGenericElementOnPointerDown(
  > 7316 |         this.state.activeTool.type,
         |         ^^^^^^^^^^^^^^^^^^^^^^^^^^
    7317 |         pointerDownState,
    7318 |       );
    7319 |     }
```

**2+ prompts that failed and how you refined it:**

1. Add double_arrow as type for element in all palces necessary (FAILED - started to create new type from scratch, without inheritance from ExcalidrawArrowElement)

Fixed to: Create artificial type ExcalidrawDoubleArrowElement, that inherits from ExcalidrawArrowElement

2. Fix this error {translation key error} (FAILED - AI started to patch-fix the code, but did not added the missing keys in localisation files) Fixed to: Add mappping to translation files, not patch-fix in the code {reference to error message}
