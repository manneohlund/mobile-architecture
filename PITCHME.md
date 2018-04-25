---?image=assets/bg_start.png

@title[Mobile Architecture]

## Mobile Architecture

---

@title[Agenda]

Points in workshop

- Why so picky?
- Coding patterns
- Project structure
- UML Examples
- Teamwork
- Discussion

---

@title[Salt and pepper]

> "Adding objects to your code is like adding salt to a dish: use a little, add too much and it utterly ruins the meal"

---

@title[OOP or not OOP]

🤔
> "To OOP or not OOP"

@ul

- Avoid complex hierarchies (Less is more)
- Avoid Base classes
- Favor composition over inheritance

@ulend

+++

### Favor composition over inheritance

- More flexible
- Avoid tight coupling
- Multiple inheritance is not working
  
+++

@title[Composition over inheritance]

ViewController = Fragment/Activity

+++

@title[Inheritance]

Inheritance

```kotlin
class BaseViewController {
  fun startOtherViewController(name: String)
}
```

```kotlin
class ViewController : BaseViewController {
  // invoke startOtherViewController() 
}
```

+++

@title[Composition]

Composition

```kotlin
class ViewControllerCoordinator {
  fun startOtherViewController(name: String)
}
```

```kotlin
class ViewController {
  val coordinator: ViewControllerCoordinator
  
  Car(coordinator: ViewControllerCoordinator) {
    this.coordinator = coordinator
  }
  
  // invoke coordinator.startOtherViewController()
}
```

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

Frost will use MVVM pattern in both iOS and Android

@ul

- **Model** <font size="4">Data as is</font>
- **View** <font size="4">No logic, maybe animations</font>
- **ViewModel** <font size="4">Switch for model data and view states</font>
- **ViewController/Fragment** <font size="4">View orchestrator & controls async tasks and logic</font>
- **DataProvider/AppRepository** <font size="4">Networking, DB, Cache reuse. Subscribers? 🤔</font>

@ulend

+++

![IOS MVVM](https://github.com/manneohlund/mobile-architecture/blob/master/assets/img-mvc-mvp-mvvm.png?raw=true)

+++

![Android MVVM](https://github.com/manneohlund/mobile-architecture/blob/master/assets/img-mvc-mvp-mvvm.png?raw=true)

---

@title[Project structure]

**Feature** based structure of the project

+++

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
    <tr><th align="left">DataProvider/AppRepository</th><th align="left">DataProvider/AppRepository</th></tr>
  </tbody>
</table>
</font>

---

@title[The End]

Happy coding! 👋
