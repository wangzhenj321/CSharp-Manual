## When to add a Component Class vs User Control?

In WPF and Windows Forms, both, the main difference is that a UserControl is meant to be a collection of controls - a reusable, single object "composed" from multiple controls themselves.

You'd impelemnt a Component/CustomControl/Control instead of a UserControl if you are making a single, primitive control with new behavior, instead of making a "control" that's composed of smaller controls. Component usually is a non-visual behavior, where a CustomControl/Control is usually for a visual control.

## Differences between a control and a component

A component is a class that implements the IComponent interface or that derives directly or indirectly from a class that implements IComponent.

A component does not draw itself on the form, but a control draws itself on the form or on another control. Both the Components and the Controls can be dropped onto a design surface. If you double click the item on the toolbox and it will get placed inside the form then it the item known as Controls, where as the item placed below the form area (component tray) then it is known as Component.

e.g. Timer is a component and that has no visual representation during runtime, but you can see it in the component tray during the design time. Progress Bar is a control and it has visual representation in both design time and runtime.

All controls are also components, but not all components are controls.

You can create a component if you want to provide functionality without UI such as with the BackgroundWorker component, then you would only need to derive from Component directly. e.g. Timer , Data Source etc.. You can create a custom control if you want to make a component where you have full control over its visual appearance. e.g. Textbox , Button etc..

## References

1. [When to add a Component Class vs User Control?](https://stackoverflow.com/questions/1455998/when-to-add-a-component-class-vs-user-control)

2. [Differences between a control and a component](http://net-informations.com/faq/net/control-component.htm)