---
layout: post
title: Change Value Using Keypath
categories: [swift, keypath, TCA]
---

One of requirement to understand TCA (The Composable Architecture) is to understand how to change value using keypath. Here is the example

{% highlight swift %}
struct State {
    var innerState: Int
}
var globalState = State(innerState: 1) 

func updateValue<GlobalState, LocalState>(
    state: inout GlobalState, 
    localState: WritableKeyPath<GlobalState, LocalState>, 
    newValue: LocalState) 
-> Void {
    state[keyPath: localState] = newValue
}
updateValue(state: &globalState, localState: \.innerState, newValue: 9)
print(globalState) // will print State(innerState: 9)
{% endhighlight %}
