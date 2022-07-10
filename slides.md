---
theme: seriph
background: https://source.unsplash.com/collection/94734566/1920x1080
class: text-center
highlighter: shiki
lineNumbers: false
info: |
  ## Frontend Structure
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
drawings:
  persist: false
title: Frontend Structure
---

# Frontend Structure

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Touch your heart 🤍 for next page <carbon:arrow-right class="inline"/>
  </span>
</div>

<div class="abs-br m-6 flex gap-2">
  <button @click="$slidev.nav.openInEditor()" title="Open in Editor" class="text-xl icon-btn opacity-50 !border-none !hover:text-white">
    <carbon:edit />
  </button>
  <a href="https://github.com/slidevjs/slidev" target="_blank" alt="GitHub"
    class="text-xl icon-btn opacity-50 !border-none !hover:text-white">
    <carbon-logo-github />
  </a>
</div>

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---

# Agenda

Today's lesson

- 🤹 **`Vite`** - Next Generation Frontend Tooling
- 🧑‍💻 **`Vue 3`** - An approachable, performant and versatile framework for building web user interfaces.
- 🎨 **`Atom Design Pattern`** - Frontend Structure Methodology
- 🛠 **`Pinia`** - The Vue Store that you will enjoy using (State Management)

---
layout: center
---

<img
  class="opacity-80 w-70"
  m="auto"
  hover="opacity-100"
  src="https://vitejs.dev/logo.svg"
/>
<p class="text-center text-4xl pt-4">Vite</p>
<p class="text-center textxl pt-2">French word for "quick", pronounced /vit/, like "veet"</p>

---

# [Vite](https://vitejs.dev/)

<div grid="~ cols-3 gap-2" m="t-10">
  <div>
    <div class="text-bold text-xl">
    💡 Instant Server Start
    </div>
    <div m="t-1" class="text-sm text-gray-500">
      On demand file serving over native ESM, no bundling required!
    </div>
  </div>

  <div>
    <div class="text-bold text-xl">
    ⚡️ Lightning Fast HMR
    </div>
    <div m="t-1" class="text-sm text-gray-500">
      Hot Module Replacement (HMR) that stays fast regardless of app size.
    </div>
  </div>

  <div>
    <div class="text-bold text-xl">
    🛠️ Rich Features  
    </div>
    <div m="t-1" class="text-sm text-gray-500">
      Out-of-the-box support for TypeScript, JSX, CSS and more.
    </div>
  </div>
</div>
<div grid="~ cols-3 gap-2" m="t-10">
  <div>
    <div class="text-bold text-xl">
    📦 Optimized Build
    </div>
    <div m="t-1" class="text-sm text-gray-500">
      Pre-configured Rollup build with multi-page and library mode support.
    </div>
  </div>
  <div>
    <div class="text-bold text-xl">
    🔩 Universal Plugins
    </div>
    <div m="t-1" class="text-sm text-gray-500">
      Rollup-superset plugin interface shared between dev and build.
    </div>
  </div>
  <div>
    <div class="text-bold text-xl">
    🔑 Fully Typed API
    </div>
    <div m="t-1" class="text-sm text-gray-500">
      Flexible programmatic APIs with full TypeScript typing.
    </div>
  </div>
</div>


---
layout: center
---

<img
  m="auto"
  class="w-50 rounded-full "
  src="https://avatars.githubusercontent.com/u/499550"
/>

## Meaning from `Evan You`

---

1. During dev, vite is a dev server that compiles source files as they are requested by the browser. No bundling is required, and compilation is truly on-demand. Unchanged files return 304 so browsers don't even request it. This is what makes it start fast and stay fast.
   
2. Vite supports Hot Module Replacement, which is fundamentally different from "simply reload the page". It's a world of difference in terms of DX. Vue components and CSS HMR are supported out of the box, and 3rd party frameworks can leverage the HMR API.
   
3. Vite supports a number of webpack-inspired features like  importing `.css` files from js (a la css-loader), referencing assets based on fs relative paths (a la file-loader, the final public deployed path is auto taken care of by simply specifying `--base` during build)
   
4. Vite supports .(t|j)sx? files out of the box via esbuild, which is astonishingly fast, so even with TS transpilation the HMR is still literally instant.
   
5. Vite uses Rollup for production builds, with an internal config that mirrors the dev server features. The production build output is a directory of traditional static assets that can be deployed anywhere (and can be polyfilled to support older browsers).
   
6. Vite is also extensible at core (config/plugin format pending) - you can add support for custom file transforms by adding a Koa middleware (for dev) + a Rollup plugin (for build).

<!--
1. 
Vite เป็น Dev Server ที่ Compile File ที่จะ Request ไปหา Browser แต่
ไม่ต้องพึ่งการ Bundling หรือ webpack ใด ๆ 
มีแต่ไฟล์ที่มีมาเพื่อการ Compile เท่านั้น จะถึงให้ไวมาก ๆ

2. 
Vite รองรับ Hot module Replacement (HMR) ซึ่งจะต่างจากการ Reload page ทั่วไปจากที่เราคุ้นเคย 
อีกทั้ง Vue Components และ CSS HMR ค่อนข้างใช้งานง่าย 
พร้อมทั้งมี API ที่สามารถใช้กับ 3rd Party ตัวอื่น ๆ ได้

3. 
Vite ยังรองรับ Feature ต่าง ๆ ที่คล้ายกับ webpack 
เช่น css-loader, assets releative path เป็นต้น

4. 
Vite รองรับทั้ง TSX และ JSX ที่ทำงานได้ไวมาก ๆ 
ถึงแม้ว่าจะมีการแปลงโค้ดจาก TS แต่ HMR ก็ยังทำงานได้อย่างคงที่

5. 
Vite ใช้ Rollup สำหรับ Production Build ด้วย Config ภายในที่เหมือนกับ Dev Server ทุกประการ 
และผลลัพท์จากการ Build เป็น Static Asset ทั่วไป 
สามารถ Deploy ได้ทุกที่ 
และยังมี Polyfill รองรับกับ Browser รุ่นเก่า

6. 
Vite ยังสามารถ Extend ตัว Config หรือ Plugin ได้ 
โดยการสร้าง Custom File ในรูปแบบของ Koa Middleware 
พร้อมกับ Rollup Plugin สำหรับ Build
-->

---
layout: center
---

<div class="text-3xl text-green-500">No-bundle Dev Server for Vue 3 Single-File Components</div>
<!-- Vite เป็น Dev Server ที่ Compile File โดยไม่ต้องพึ่งการ bundle หรือ webpack ใด ๆ -->
---

# Let get start it !

> Vite requires Node.js version >=12.2.0.

With NPM:

```
$ npm create vite@latest
```

With Yarn:

```
$ yarn create vite
```

With PNPM:

```
$ pnpm create vite
```

---

# Project Structure

✔ Project name: … vite-project <br>
✔ Select a framework: › vue <br>
✔ Select a variant: › vue <br>
```
├── README.md
├── index.html
├── package.json
├── public
│   └── favicon.ico
├── src
│   ├── App.vue
│   ├── assets
│   │   └── logo.png
│   ├── components
│   │   └── HelloWorld.vue
│   └── main.js
└── vite.config.js
```

---
layout: center 
---

<img
  class=" w-100"
  m="auto"
  src="https://xd.adobe.com/ideas/wp-content/uploads/2020/06/atomic_design_principles_and-methodolgy101.jpg.webp"
/>
<p class="text-center text-2xl pt-4">Atomic Design Principles & Methodology 101</p>


---
layout: center
---

# What is Atomic Design?

The concept of atomic design was introduced by Brad Frost in 2013

This methodology is called Atomic Design because it’s very idea is founded in that of Chemistry, and the study of the composition of matter. The universe is made up of a fixed set of ‘atomic elements’ – known to many of us as the periodic table of elements. These elements are the building blocks of everything around us.

> `Atomic design is not a linear process, 
> but rather a mental model to help us think of our user interfaces as both a cohesive whole and a collection of parts at the same time.`

In Chemistry, these atomic elements have fixed properties that define them. Oxygen and Hydrogen on their own are atoms with independent properties. However when these elements are combined, they create molecules, which take on their own unique characteristics, made up of the atoms they contain. In the case of hydrogen and oxygen, pairing two hydrogen atoms with oxygen creates what we know as the water molecule.

<!--
You can have `style` tag in markdown to override the style for the current page.
Learn more: https://sli.dev/guide/syntax#embedded-styles
-->

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

<!--
วิธีการนี้เรียกว่า Atomic Design 
เนื่องจากแนวคิดนี้มีพื้นฐานมาจากวิชาเคมี และการศึกษาองค์ประกอบของสสาร

 จักรวาลประกอบด้วยชุดของ 'ธาตุอะตอม' คงที่ ซึ่งพวกเราหลายคนรู้จักในชื่อตารางธาตุ องค์ประกอบเหล่านี้เป็นส่วนประกอบสำคัญของทุกสิ่งรอบตัวเรา


Atom ไม่ใช่กระบวนการที่ตายตัว แต่เป็นแบบจำลองทางจิตที่ช่วยให้เรานึกถึงส่วนต่อประสานผู้ใช้ของเราเป็นทั้งส่วนที่เชื่อมโยงกันและส่วนรวมในเวลาเดียวกัน

ในวิชาเคมี ธาตุอะตอมเหล่านี้มีคุณสมบัติคงที่ที่กำหนดองค์ประกอบเหล่านี้ ออกซิเจนและไฮโดรเจนเป็นอะตอมที่มีคุณสมบัติอิสระ อย่างไรก็ตาม เมื่อองค์ประกอบเหล่านี้รวมกัน พวกมันจะสร้างโมเลกุลซึ่งมีลักษณะเฉพาะของตัวเองซึ่งประกอบด้วยอะตอมที่มีอยู่ ในกรณีของไฮโดรเจนและออกซิเจน การจับคู่ไฮโดรเจนสองอะตอมกับออกซิเจนจะสร้างสิ่งที่เราเรียกว่าโมเลกุลของน้ำ
-->

---

# The elements of Atomic Design

There are five distinct stages of the Atomic Design methodology, with the first three modelled after their equivalents in the Chemistry world. Each stage builds on the previous, acting as an aggregate of items from the preceding stages.

<img
  class="pt-6 w-[600px]"
  m="auto"
  src="https://xd.adobe.com/ideas/wp-content/uploads/2021/07/1618031644-0.png.webp"
/>

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

<!--
มีห้าขั้นตอน โดยสามขั้นตอนแรกถูกจำลองตามแบบที่เทียบเท่ากันในโลกเคมี แต่ละขั้นตอนสร้างขึ้นจากขั้นตอนก่อนหน้า โดยทำหน้าที่เป็นการรวมรายการจากขั้นตอนก่อนหน้า
-->

---

# Atoms

Just like in Chemistry, atoms are the smallest building blocks in our system. Rather than atoms like Oxygen or Hydrogen, in design we have buttons, inputs, labels and other small elements that get used throughout our design. Iconography fits in this category, whether it is a menu icon, or avatar as they’re small elements that come together to form the next stage – molecules.

<img
  class="pt-4 w-[600px]"
  m="auto"
  src="https://xd.adobe.com/ideas/wp-content/uploads/2021/07/1618031645-1.png.webp"
/>

<!--
เช่นเดียวกับในวิชาเคมี อะตอมเป็นหน่วยการสร้างที่เล็กที่สุดในระบบของเรา แทนที่จะเป็นอะตอมอย่างออกซิเจนหรือไฮโดรเจน 
ในการออกแบบเรามี buttons, inputs, labels  และองค์ประกอบเล็กๆ อื่นๆ ที่ใช้ในการออกแบบของเรา
-->

---

# Molecules

In the molecule stage, we take our independent atomic design elements, each with their own characteristics, style, format, and begin to bring them together into new groupings. Take for instance our avatar atom. If we combine the avatar atom with name and title labels, other atomic elements, we can create a profile molecule.

> Just like in Chemistry, we can combine the same atoms in different ways to create unique molecules for use in our design.

<img
  class="w-[500px]"
  m="auto"
  src="https://xd.adobe.com/ideas/wp-content/uploads/2021/07/1618031646-2.png.webp"
/>

<!--
ในขั้นตอนของโมเลกุล เรานำองค์ประกอบเหล่านี้มารวมกันเป็นกลุ่มใหม่ ยกตัวอย่างอะตอมของอวาตาร์ของเรา ถ้าเรารวมอะตอมของอวาตาร์เข้ากับป้ายชื่อและชื่อเรื่อง องค์ประกอบอะตอมอื่นๆ เราสามารถสร้างโมเลกุลโปรไฟล์ได้

> เช่นเดียวกับในวิชาเคมี เราสามารถรวมอะตอมเดียวกันในรูปแบบต่างๆ เพื่อสร้างโมเลกุลที่มีเอกลักษณ์เฉพาะเพื่อใช้ในการออกแบบของเรา
-->

---

# Organisms

Our collections of atoms and molecules now become more complex than at the molecular level. Take for instance our ‘profile’ molecule. It was a simple element comprising an avatar and a pair of label elements. As we bring that into an organism, we may be adding that into an app header for a profile page, complete with navigation, a background cover photo and some other molecules. This creates our header organism.

> The organism is not yet a complete design, but is a component that can be reused across designs, or layout templates.

<img
  class="w-[500px]"
  m="auto"
  src="https://xd.adobe.com/ideas/wp-content/uploads/2021/07/1618031647-3.png.webp"
/>

<!--
> organism ยังไม่ได้สมบูรณ์ 100% แต่เป็นส่วนประกอบที่สามารถนำมาใช้ซ้ำระหว่างการออกแบบ หรือเทมเพลตเลย์เอาต์
-->

---

# Templates

The template is the first stage of the Atomic Design methodology that does not align to a stage in the molecular world, but is important for Atomic Design. A template is where we begin to curate our organisms and other elements into a cohesive design.

> Think of templates as the blueprint for our future finished page designs. At this point they’re still the elements, and won’t contain real data – much like a wireframe.

<img
  class="w-[500px]"
  m="auto"
  src="https://xd.adobe.com/ideas/wp-content/uploads/2021/07/1618031648-4.png.webp"
/>

---

# Pages

Pages are the final stage of the Atomic Design methodology. This is where instances of templates are created. In the design process you may not design out pages for every instance, but it is helpful to create a few variations.

> As your data changes, different profile information, or languages may impact your template design. Building out to the page stage allows you to test for these variations and make adaptations globally to your templates.

<img
  class="w-[500px]"
  m="auto"
  src="https://xd.adobe.com/ideas/wp-content/uploads/2021/07/1618031649-5.png.webp"
/>

---

# In development

## Atom
Atoms are the smallest components that do not include other components. They also can not have a slot field.
Any modification of the component is done via props.

```
components
└── atoms
    ├── alert
    ├── badge
    ├── button
    ├── checkbox
    ├── datepicker
    ├── icon
    ├── image
    ├── input
    ├── link
    ├── pagination
    ├── radio
    ├── select
    ├── textarea

```

---

# In development

## Molecules
Molecules are components that have no logic like atoms, yet are more complect than an atom and can be composed of atoms and molecules.

```
components
└── molecules
    ├── account-menu
    ├── account-new
    ├── account-success
    ├── breadcrumb
    ├── button-group
    ├── contact
    ├── dropdown
    ├── input-group
    ├── list-group
    ├── logo
    ├── media
    ├── menu
    ├── rating
    ├── review
    ├── tabs
```

---

# In development

## Organisms
Organisms are components that carry most of the logic like login forms and cart, yet most of the styling is and html is added vie composing atoms molecules.

```
components
└── organisms
    ├── category-grid
    ├── category-info
    ├── category-product
    ├── compare-actions
    ├── contact-form
    ├── currency
    ├── location-grid
    ├── login-form
    ├── password-form
    ├── register-form
    ├── review-form
    ├── review-list
    ├── search-form
    ├── search-inline-form
```

---

# In development

## Templates
Templates are used to compose the final page. You most often won't need to modify this as it is a simple combination of Component elements. You may use this folder to add new custom templates.

```
components
└── templates
    ├── account
    │   ├── account
    │   ├── address
    │   ├── addressCreate
    │   ├── addressEdit
    │   ├── login
    │   ├── password
    │   ├── register
    ├── common
        ├── contact
        ├── error
        ├── layout
        ├── page
        └── search
```

---

# In development

## Pages
Pages are components that use Templates to organize the data. They carry most of the logic on the page and use the store to fetch data and display it.

```
components
└── pages
    ├── account
    │   ├── account
    │   ├── address
    │   ├── addressCreate
    │   ├── addressEdit
    │   ├── login
    │   ├── password
    │   ├── register
    ├── common
        ├── contact
        ├── error
        ├── layout
        ├── page
        └── search
```

---

# In development

## Extensions (Widgets)
Extensions (Widgets) are components that can be positioned on a page via the vuefront.config.js file. They can carry logic like organisms or be as simple as an atom. Third-party apps will use this folder to add their custom components.

```
components
└── extensions
    ├── blog
    │   ├── category
    │   ├── latest-post
    │   └── search-post
    └── store
        ├── category
        ├── checkout
        ├── featured-product
        ├── latest-product
        ├── related-product
        ├── search-product
        └── special-product
```

---

# By concept

### Dumb components
<br>

> Dumb components are those components that have no logic such as a button or a form field. On its own they do nothing.

<br>

- Atoms
- Molecules
- Templates

### Smart components
<br>

> Smart components actually include logic such as a login form.

<br>

- Organisms
- Pages
- Extensions

---
layout: center
---

<img
  class="opacity-80 w-40"
  m="auto"
  hover="opacity-100"
  src="https://pinia.vuejs.org/logo.svg"
/>
<p class="text-center text-4xl pt-4">Pinia</p>
<p class="text-center textxl pt-2">Pinia (pronounced /piːnjʌ/, like "peenya" in English)</p>
<p class="text-center textxl"> is the closest word to piña (pineapple in Spanish)</p>


---

# [Pinia](https://pinia.vuejs.org/)
The Vue Store that you will enjoy using

<div grid="~ cols-3 gap-2" m="t-10">
  <div>
    <div class="text-bold text-xl">
    💡 Intuitive
    </div>
    <div m="t-1" class="text-sm text-gray-500">
      Stores are as familiar as components. API designed to let you write well organized stores.
    </div>
  </div>

  <div>
    <div class="text-bold text-xl">
    🔑 Type Safe
    </div>
    <div m="t-1" class="text-sm text-gray-500">
      Types are inferred, which means stores provide you with autocompletion even in JavaScript!
    </div>
  </div>

  <div>
    <div class="text-bold text-xl">
    ⚙️ Devtools support
    </div>
    <div m="t-1" class="text-sm text-gray-500">
      Pinia hooks into Vue devtools to give you an enhanced development experience in both Vue 2 and Vue 3.
    </div>
  </div>
</div>
<div grid="~ cols-3 gap-2" m="t-10">
  <div>
    <div class="text-bold text-xl">
    🔌 Extensible
    </div>
    <div m="t-1" class="text-sm text-gray-500">
      React to store changes to extend Pinia with transactions, local storage synchronization, etc.
    </div>
  </div>
  <div>
    <div class="text-bold text-xl">
    🏗 Modular by design
    </div>
    <div m="t-1" class="text-sm text-gray-500">
      Build multiple stores and let your bundler code split them automatically.
    </div>
  </div>
  <div>
    <div class="text-bold text-xl">
    📦 Extremely light
    </div>
    <div m="t-1" class="text-sm text-gray-500">
      Pinia weighs around 1kb, you will forget it's even there!
    </div>
  </div>
</div>

---

# Basic example - Store

<div grid="~ cols-2 gap-4" m="t-10">
<div>

- Defining a Store

```js
// stores/counter.js
import { defineStore } from 'pinia'

// useStore could be anything like useUser, useCart
// the first argument is a unique id 
// of the store across your application
export const useTodoStore = defineStore('todos', {
  // other options...
})

```

</div>
<div>

- Using the store


```js
import { useTodoStore } from '@/stores/todos'

const store = useTodoStore()
```
</div>
</div>

---

# Basic example - State

<div grid="~ cols-2 gap-4" m="t-10">
<div>

- Defining a State

```js
import { defineStore } from 'pinia'

const useTodoStore = defineStore('todos', {
  state: () => {
    todos: [],
    filter: 'all',
    nextId: 0,
  },
})
```

</div>
<div>

- Using the State

```js {all|5-7}
import { useTodoStore } from '@/stores/todos'

const store = useTodoStore()

store.nextId++

const foo = store.todos.filter((todo) => todo.isFinished)
```
</div>
</div>

- Tick 

```js
/** @type {{ text: string, id: number, isFinished: boolean }[]} */
todos: [],
/** @type {'all' | 'finished' | 'unfinished'} */
filter: 'all',
// type will be automatically inferred to number
nextId: 0,
```

---

# Basic example - Getters

<div grid="~ cols-2 gap-4" m="t-10">
<div>

- Defining a Getters

```js
import { defineStore } from 'pinia'

export const useTodoStore = defineStore('todos', {
  state: () => {
    todos: [],
    filter: 'all',
    nextId: 0,
  },
  getters: {
    finishedTodos: (state) => state.todos.filter(
      (todo) => todo.isFinished),
    unfinishedTodos: (state) => state.todos.filter(
      (todo) => !todo.isFinished)  
  },
  
})
```

</div>
<div>

- Using the Getters

```js {all|7|8-9}
import { useTodoStore } from '@/stores/todos'

const store = useTodoStore()

store.nextId+++

const foo = store.todos.filter((todo) => todo.isFinished)
const finished = store.finishedTodos
const unfinished = store.unfinishedTodos

```
</div>
</div>

---

# Basic example - Actions

<div grid="~ cols-2 gap-4" m="t-10">
<div>

- Defining a Actions

```js
import { defineStore } from 'pinia'

export const useTodoStore = defineStore('todos', {
  state: () => {
    todos: [],
    filter: 'all',
    nextId: 0,
  },
  actions: {
     /**
     * Add item to the cart
     * @param {string} name
     */
    addTodo(text: string) {
      // you can directly mutate the state
      this.todos.push({ text, 
      id: this.nextId++, isFinished: false })
    },
  },
})
```

</div>
<div>

- Using the Actions

```js {all|11-13}
import { useTodoStore } from '@/stores/todos'

const store = useTodoStore()

store.nextId+++

// const foo = store.todos.filter((todo) => todo.isFinished)
const finished = store.finishedTodos
const unfinished = store.unfinishedTodos

const onClick = (text: string) => {
  store.addTodo(text)
}

```
</div>
</div>

---


# Actions for APIs

```js {all|1-3|5|6-9|11-12|14,7|15|17-19|all}
import { mande } from 'mande'

const api = mande('/api/users')

export const useUsers = defineStore('users', {
  state: () => ({
    userData: null,
    // ...
  }),

  actions: {
    async registerUser(login, password) {
      try {
        this.userData = await api.post({ login, password })
        showTooltip(`Welcome back ${this.userData.name}!`)
      } catch (error) {
        showTooltip(error)
        // let the form component display the error
        return error
      }
    },
  },
})

```

---
layout: center
---

<img
  class="w-[100%]"
  m="auto"
  src="https://miro.medium.com/max/700/1*5pz0ih6TUClcPyS9yF-Wmg.png"
/>


---
layout: center
class: text-center
---

# Q & A
