# Introduction
WebFlow is a collaborative rich text editor built on top of the Fluid SharedString distributed data structure.

# Components
There are three primary components:
* The FlowDocument, a Fluid component that encapsulates the SharedString and exposes APIs convenient for editing.
* The Editor, a JavaScript class that renders the editing surface and updates the FlowDocument in response to user input.
* The Host, an example Fluid component that creates a FlowDocument and attaches an Editor.

# Examples
To host an instance of the Editor, your Fluid component will need to create an instance of a FlowDocument.  In the Host example, this is done in host/host.ts:
```ts
    const docP = this.createAndAttachComponent<FlowDocument>(this.docId, FlowDocument.type);
```
On subsequent loads, you'll want to open the same flow document:
```ts
    const docP = this.getComponent<FlowDocument>(this.docId);
```
When the document resolves, pass it to a new Editor instance, along with the HTML DOM node you want the Editor to attach itself to (see 'host/host.ts':)
```ts
    const editor = new Editor(await docP, root, htmlFormatter);
```
host/host.ts also demonstrates how to connect an application's UI (e.g., toolbar) to editor functionality.