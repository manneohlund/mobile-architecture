---?image=assets/bg_start.png

@title[Mobile Architecture]

## Mobile Architecture

---

@title[Agenda]

Points in workshop

- To OOP or not to OOP 🤔
- Why so picky?
- Coding patterns
- UML Examples
- Project structure
- Teamwork
- Discussion

---

@title[Salt and pepper]

> "Adding objects to your code is like adding salt to a dish: use a little, add too much and it utterly ruins the meal"

---

@title[To OOP or not to OOP]

🤔
> "To OOP or not to OOP"

@ul

- Avoid complex hierarchies (Less is more)
- Favor composition over inheritance
- Avoid Base classes

@ulend

+++

### Favor composition over inheritance

- More flexible
- Avoid tight coupling
- Multiple inheritance?
  
+++

@title[Composition over inheritance]

### So how should we think?

Think of **inheritance** as an **is a** relationship. 
<p><font size="5">A car **"is a"** vehicle, an employee **"is a"** person, etc.</font></p>

Think of **composition** as a **has a** relationship.
<p><font size="5">A car **"has an"** engine, a person **"has a"** name, etc.</font></p>

+++

@title[Inheritance & Composition]

**Inheritance** - <font size="5">I am of a type</font>

<font size="5">Foo is a type of Bar.</font>

```java
class Foo extends Bar {

}
```

**Composition** - <font size="5">I own an object</font>

<font size="5">Foo is responsible for its lifetime, when Foo dies, so does Bar</font>

```kotlin
class Foo {
  Bar bar = new Bar()
}
```

+++

@title[Association & Aggregation]

**Association** - <font size="5">I have a relationship with an object</font>

<font size="5">Foo uses Bar</font>

```java
class Foo { 
  void Baz(Bar bar) {
    // Do something
  } 
}
```

**Aggregation** - <font size="5">I have an object which I've borrowed from someone else</font>

<font size="5">When Foo dies, Bar may live on</font>

```java
class Foo { 
  Bar bar
  Foo(Bar bar) { 
    this.bar = bar
  }
}
```

+++

### Complex data structures

Games dev with ex characters uses all technics.

```java
class Employee 
  extends Person 
    implements ProjectManager, CoffeeSpecialist, Janitor
```

+++

### Why is all this important?

OOP is a pushed on industy standard for some reason (C++, Java)

We want to reuse code, but sometimes it can go wrong and we need to refactor.

@ul

- Why do we have som many utils for example?
- Look at C and Unix

@ulend

---

## Why so picky?

Good architecture leads to:

@ul

- Uniform team, projects and vision
- Better code
- Less refactoring

@ulend

---

@title[Coding patterns]

Coding patterns

![Coding patters](https://github.com/manneohlund/mobile-architecture/blob/master/assets/img-mvc-mvp-mvvm.png?raw=true)

+++

@title[MVVM]

**Frost** will use **MVVM** pattern in both iOS and Android

@ul

- **Model** <font size="4">Data as is</font>
- **View** <font size="4">What user sees. Minor logic, maybe animations</font>
- **ViewModel** <font size="4">Switch for model data and view states. "State of the data in the Model"</font>
- **ViewController/Fragment** <font size="4">View orchestrator & controls async tasks, viewmodel logic</font>
- **DataProvider/Repository** <font size="4">Networking, DB, Cache reuse. Subscribers? 🤔</font>

@ulend

+++

@title[iOS MVVM]

<img src="https://github.com/manneohlund/mobile-architecture/blob/master/assets/ios-mvvm.png?raw=true" alt="IOS MVVM" height="500" width="600">

+++

@title[Android MVVM]

<img src="https://github.com/manneohlund/mobile-architecture/blob/master/assets/android-mvvm.png?raw=true" alt="Android MVVM" height="500" width="600">

---

@title[Project structure]

**Feature** based structure of the project

+++

@title[iOS Android uniform]

<font size="3">
<table>
  <tbody>
    <tr><th>iOS</th><th>Android</th></tr>
    <tr>
      <!-- iOS -->
      <td>
        <ul>
          <li>Coordinators</li>
          <li>Features</li>
          <ul>
            <li><b>FeatureName</b></li>
            <ul>
              <li>Storyboard</li>
              <li>ViewController</li>
              <li>ViewModels</li>
              <li>View</li>
              <li>(Helpers / Handlers / Wrappers)</li>
            </ul>
            <li>Shared</li>
          </ul>
          <li>Managers</li>
          <li>Models (Datatypes / Nomenclature)</li>
          <li>Network</li>
          <li>Storage</li>
          <li>Utils (Parsers / Decoders / Helpers / Handlers)</li>
          <li>Extensions</li>
        </ul>
      </td>
      <td>
        <ul> 
          <li>features</li>
          <ul>
            <li><b>feature_name</b></li>
            <ul>
              <li>activity</li>
              <li>fragment</li>
              <li>view_model</li>
              <li>view</li>
              <li>(helper / handler / wrapper)</li>
            </ul>
            <li>shared</li>
          </ul>
          <li>manager</li>
          <li>model (datatype / nomenclature)</li>
          <li>network</li>
          <li>storage</li>
          <li>utils (parser / decoder / helper / handler)</li>
          <li>extension</li>
        </ul>
      </td>
    </tr>
    <tr><th align="left">AppDelegate</th><th align="left">Application</th></tr>
    <tr><th align="left"></th><th align="left">AppCoordinator 🤔</th></tr>
    <tr><th align="left">DataProvider/Repository</th><th align="left">DataProvider/Repository</th></tr>
  </tbody>
</table>
</font>

---

# Teamwork

- Substitut Base class with composition.
- Make UML where MVVM can be used.

---

@title[Links]

[Frost Mobile Architecture and Component naming](https://github.com/FrostDigital/frost-mobile-guide/wiki/Frost-Mobile-Architecture-and-Component-naming)

---

@title[The End]

Happy coding! 👋
