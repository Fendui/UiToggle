# UiToggle
A wrapper component that provides an easy way to switch between two states

## Features ✨

 <ul>
  <li>Vue 3</li>
  <li>Renders no wrapper element</li>
  <li>Simple API</li>
 <li>Can be controlled or uncontrolled</li>
 </ul>
 
## Props ⚙

<table>
 <thead>
  <tr>
    <th>Name</th><th>Type</th><th>Default</th><th>Description</th>
  </tr>
 </thead>
 <tbody>
  <tr>
    <td>modelValue</td><td><code>Boolean</code></td><td>undefined</td><td>Used internally by <code>v-model</code></td>
  </tr>
  <tr>
   <tr>
   <td>disabled</td><td><code>Boolean</code></td><td>undefined</td><td>This is used to completely disable the UiToggle component from trigerring a change</td>
  </tr>
 </tbody>
</table>


## Structure 🏗

<pre><code>&lt;slot /&gt;</code></pre>

## Slot 🎰 

<table>
 <thead>
  <tr>
    <th>Name</th><th>Payload</th><th>Description</th>
  </tr>
 </thead>
 <tbody>
  <tr>
    <td>default</td><td>
    <pre><code>{ 
  active: Boolean,
  toggle: Function
}
</code></pre></td><td>This is a required slot that <strong><em>should have only 1 wrapper element</em></strong></td>
  </tr>
 </tbody>
</table>

## Examples 💁‍♂️

<em>Simplest form</em>
 
<pre><code>&lt;div id='app'&gt;
 &lt;UiToggle v-slot="{toggle, active}"&gt;
  &lt;button @click="toggle"&gt;
    I am active: {{active}}
  &lt;/button&gt;
 &lt;/UiToggle&gt;
&lt;/div&gt;
</code></pre>

<em>With v-model</em>
 
<pre><code>&lt;div id='app'&gt;
 &lt;UiToggle v-slot="{toggle}" v-model='toggleState'&gt;
  &lt;button @mouseenter="toggle" &gt;
    I am active: {{toggleState}}
  &lt;/button&gt;
 &lt;/UiToggle&gt;
&lt;/div&gt;
</code></pre>

<em>With an active class</em>
 
<pre><code>&lt;div id='app'&gt;
 &lt;UiToggle v-slot="{toggle, active}"&gt;
  &lt;button @click="toggle" :class="{'is-active primary': active}"&gt;
    {{active ? 'Yup' : 'Nope'}}
  &lt;/button&gt;
 &lt;/UiToggle&gt;
&lt;/div&gt;
</code></pre>

<em>With two seperate elements to set the state of </em><code>toggleState</code>
 
<pre><code>&lt;div id='app'&gt;
 &lt;UiToggle v-slot="{toggle}" v-model='toggleState'&gt;
  &lt;div :class="{primary: toggleState}"&gt;
    &lt;button @click='()=> toggle(true)'&gt;
      I set the state to <strong>true</strong>!
    &lt;/button&gt;
    
    &lt;div @mouseenter='()=> toggle(false)'&gt;
      I set the state to <strong>false</strong>!
    &lt;/div&gt;
  &lt;/div&gt;
 &lt;/UiToggle&gt;
&lt;/div&gt;
</code></pre>

