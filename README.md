# Assignment-1.2

Component interface in Angular2

The above is a minor point, but here is one I feel more strongly for; Angular2 components have a really clean interface.

What do I mean? I'd argue there are three main ways in which we interface with a component:

we input data
we provide dependencies
we catch output
In Angular2, these are immediately identifiable:

@Component({ ... })
export class SceneComponent {
  constructor(private someDependency){ ... }
  @Input() someInput
  @Output() someOutput = new EventEmitter<SomeType>()
  // ...
}
Dependencies are constructor arguments, and inputs and outputs are literally marked as such. It is equally clear when we use a component - inputs are in brackets and outputs in parens:
<MyComponent [someInput]="someVar" (someOutput)="handler($event)">
And the dependencies are handled by providers defined in the NgModule container.

Component interface in React

Contrast this to React, where we simply throw everything into props. Like an animal!

let {someInput, someOutput, someDependency} = this.props;
It is equally opaque when we use a component:

<MyComponent someInput={someVar} someOutput={handler} someDependency={someDep}>
Things become somewhat cleaner if we use context to handle dependencies instead of passing them in from the parent, something I only recently began experimenting with, but that's not something you see in common usage.
