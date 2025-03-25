# THM-Clicker: Idle-Game Development with Vue.js

## Project Overview

This project involves creating an idle-game similar to Cookie Clicker using Vue.js. The game, named THM-Clicker, requires players to help students graduate manually at first. As players accumulate graduates, they receive budget from the state to hire tutors, teachers, and professors who automatically manage the teaching process. The project involves setting up the Vue.js environment, creating interactive components, and implementing state management and transitions.

## Task 1: Setting Up the Vue.js Project

- **Create a Vue.js Project**: Generate a new Vue.js project using the CLI.
- **Clean Up Project Structure**: Remove the assets and components folders, leaving only the App.vue component.
- **Clear Template Content**: Delete all template contents from App.vue.
- **Install Bootstrap**: Add Bootstrap to the project for styling.
- **Create Navbar**: Implement a Bootstrap navbar in App.vue with the title "THM-Clicker".

## Task 2: StudentClicker Component

- **Create Component**: Generate a StudentClicker component.
- **Add Button**: Add a button in StudentClicker.vue displaying a student emoji with the CSS class fs-1.
- **Define Click Event**: Set up a click event in StudentClicker.vue triggered by the button.
- **Initialize State Variable**: Create a state variable nStudents (number) in App.vue and initialize it to 0.
- **Bind Component**: Integrate StudentClicker.vue into App.vue.
- **Increment Students**: The click event in StudentClicker.vue should increment the nStudents variable in App.vue by 1.

## Task 3: DataOutput Component

- **Create Component**: Generate a DataOutput component.
- **Pass Props**: Implement the component to accept nStudents as props.
- **Display Students**: Display nStudents in the component template using Math.floor(...).
- **Format Numbers**: Adjust the display to abbreviate numbers over 1,000 as "k" and numbers over 1,000,000 as "M" (e.g., "4.5k" or "1.5M").
- **Bind Component**: Integrate DataOutput.vue into App.vue and pass nStudents as props to display the value.

## Task 4: BuyMenu Component

- **Extend State**: Add number variables nTutors, nTeachers, and nProfessors in App.vue, initializing them to 0.
- **Create Component**: Generate a BuyMenu component.
- **Add Buttons**: Create buttons for purchasing Tutors, Teachers, and Professors.
- **Define Events**: Set up events for each button to handle purchases.
- **Bind Component**: Integrate BuyMenu.vue into App.vue and handle purchase events by incrementing the respective counters (nTutors, nTeachers, nProfessors).
- **Implement Pricing**: Ensure items can only be purchased with students as currency. Calculate prices in BuyMenu.vue and pass them as event parameters:
  - priceTutor = 10 + nTutors^2
  - priceTeacher = 200 + nTeachers^2.5
  - priceProfessor = 10000 + nProfessors^3
- **Disable/Hide Buttons**: Ensure users cannot purchase items they cannot afford by disabling or hiding the buttons.
- **Extend DataOutput**: Update DataOutput.vue to display nTutors, nTeachers, and nProfessors.

## Task 5: Ticker

- **Setup Interval**: In the onMounted lifecycle hook of App.vue, create an interval timer using setInterval(() => { ... }, ...) with a callback running 60 times per second. Store the TimerID in the component state and disable it with clearInterval(...) in onBeforeUnmount.
- **Implement Item Functions**: In the interval callback, update the number of students (nStudents) based on the items:
  - nStudents += (1/60 * tutorSPS * nTutors)
  - nStudents += (1/60 * teacherSPS * nTeachers)
  - nStudents += (1/60 * professorSPS * nProfessors)
- **SPS Constants**: tutorSPS = 2, teacherSPS = 20, professorSPS = 100

## Task 6: Transitions

- **Implement Transitions**: Use <Transition> for displaying items in DataOutput.vue. When an item (e.g., Teacher) is purchased for the first time, it should slide in from left to right using CSS properties transform: translateX(-50px); and opacity: 0;.

## Technologies & Keywords

Vue.js, JavaScript, TypeScript, Bootstrap, Idle-Game, Component-Based Architecture, State Management, Transitions, Interactive Design, Cookie Clicker

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur) + [TypeScript Vue Plugin (Volar)](https://marketplace.visualstudio.com/items?itemName=Vue.vscode-typescript-vue-plugin).

## Type Support for `.vue` Imports in TS

TypeScript cannot handle type information for `.vue` imports by default, so we replace the `tsc` CLI with `vue-tsc` for type checking. In editors, we need [TypeScript Vue Plugin (Volar)](https://marketplace.visualstudio.com/items?itemName=Vue.vscode-typescript-vue-plugin) to make the TypeScript language service aware of `.vue` types.

If the standalone TypeScript plugin doesn't feel fast enough to you, Volar has also implemented a [Take Over Mode](https://github.com/johnsoncodehk/volar/discussions/471#discussioncomment-1361669) that is more performant. You can enable it by the following steps:

1. Disable the built-in TypeScript Extension
    1) Run `Extensions: Show Built-in Extensions` from VSCode's command palette
    2) Find `TypeScript and JavaScript Language Features`, right click and select `Disable (Workspace)`
2. Reload the VSCode window by running `Developer: Reload Window` from the command palette.

## Customize configuration

See [Vite Configuration Reference](https://vitejs.dev/config/).

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Type-Check, Compile and Minify for Production

```sh
npm run build
```
