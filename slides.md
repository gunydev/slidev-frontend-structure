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
    Touch your heart ๐ค for next page <carbon:arrow-right class="inline"/>
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

- ๐คน **`Vite`** - Next Generation Frontend Tooling
- ๐งโ๐ป **`Vue 3`** - An approachable, performant and versatile framework for building web user interfaces.
- ๐จ **`Atom Design Pattern`** - Frontend Structure Methodology
- ๐  **`Pinia`** - The Vue Store that you will enjoy using (State Management)

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
    ๐ก Instant Server Start
    </div>
    <div m="t-1" class="text-sm text-gray-500">
      On demand file serving over native ESM, no bundling required!
    </div>
  </div>

  <div>
    <div class="text-bold text-xl">
    โก๏ธ Lightning Fast HMR
    </div>
    <div m="t-1" class="text-sm text-gray-500">
      Hot Module Replacement (HMR) that stays fast regardless of app size.
    </div>
  </div>

  <div>
    <div class="text-bold text-xl">
    ๐ ๏ธ Rich Features  
    </div>
    <div m="t-1" class="text-sm text-gray-500">
      Out-of-the-box support for TypeScript, JSX, CSS and more.
    </div>
  </div>
</div>
<div grid="~ cols-3 gap-2" m="t-10">
  <div>
    <div class="text-bold text-xl">
    ๐ฆ Optimized Build
    </div>
    <div m="t-1" class="text-sm text-gray-500">
      Pre-configured Rollup build with multi-page and library mode support.
    </div>
  </div>
  <div>
    <div class="text-bold text-xl">
    ๐ฉ Universal Plugins
    </div>
    <div m="t-1" class="text-sm text-gray-500">
      Rollup-superset plugin interface shared between dev and build.
    </div>
  </div>
  <div>
    <div class="text-bold text-xl">
    ๐ Fully Typed API
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
Vite เนเธเนเธ Dev Server เธเธตเน Compile File เธเธตเนเธเธฐ Request เนเธเธซเธฒ Browser เนเธเน
เนเธกเนเธเนเธญเธเธเธถเนเธเธเธฒเธฃ Bundling เธซเธฃเธทเธญ webpack เนเธ เน 
เธกเธตเนเธเนเนเธเธฅเนเธเธตเนเธกเธตเธกเธฒเนเธเธทเนเธญเธเธฒเธฃ Compile เนเธเนเธฒเธเธฑเนเธ เธเธฐเธเธถเธเนเธซเนเนเธงเธกเธฒเธ เน

2. 
Vite เธฃเธญเธเธฃเธฑเธ Hot module Replacement (HMR) เธเธถเนเธเธเธฐเธเนเธฒเธเธเธฒเธเธเธฒเธฃ Reload page เธเธฑเนเธงเนเธเธเธฒเธเธเธตเนเนเธฃเธฒเธเธธเนเธเนเธเธข 
เธญเธตเธเธเธฑเนเธ Vue Components เนเธฅเธฐ CSS HMR เธเนเธญเธเธเนเธฒเธเนเธเนเธเธฒเธเธเนเธฒเธข 
เธเธฃเนเธญเธกเธเธฑเนเธเธกเธต API เธเธตเนเธชเธฒเธกเธฒเธฃเธเนเธเนเธเธฑเธ 3rd Party เธเธฑเธงเธญเธทเนเธ เน เนเธเน

3. 
Vite เธขเธฑเธเธฃเธญเธเธฃเธฑเธ Feature เธเนเธฒเธ เน เธเธตเนเธเธฅเนเธฒเธขเธเธฑเธ webpack 
เนเธเนเธ css-loader, assets releative path เนเธเนเธเธเนเธ

4. 
Vite เธฃเธญเธเธฃเธฑเธเธเธฑเนเธ TSX เนเธฅเธฐ JSX เธเธตเนเธเธณเธเธฒเธเนเธเนเนเธงเธกเธฒเธ เน 
เธเธถเธเนเธกเนเธงเนเธฒเธเธฐเธกเธตเธเธฒเธฃเนเธเธฅเธเนเธเนเธเธเธฒเธ TS เนเธเน HMR เธเนเธขเธฑเธเธเธณเธเธฒเธเนเธเนเธญเธขเนเธฒเธเธเธเธเธตเน

5. 
Vite เนเธเน Rollup เธชเธณเธซเธฃเธฑเธ Production Build เธเนเธงเธข Config เธ เธฒเธขเนเธเธเธตเนเนเธซเธกเธทเธญเธเธเธฑเธ Dev Server เธเธธเธเธเธฃเธฐเธเธฒเธฃ 
เนเธฅเธฐเธเธฅเธฅเธฑเธเธเนเธเธฒเธเธเธฒเธฃ Build เนเธเนเธ Static Asset เธเธฑเนเธงเนเธ 
เธชเธฒเธกเธฒเธฃเธ Deploy เนเธเนเธเธธเธเธเธตเน 
เนเธฅเธฐเธขเธฑเธเธกเธต Polyfill เธฃเธญเธเธฃเธฑเธเธเธฑเธ Browser เธฃเธธเนเธเนเธเนเธฒ

6. 
Vite เธขเธฑเธเธชเธฒเธกเธฒเธฃเธ Extend เธเธฑเธง Config เธซเธฃเธทเธญ Plugin เนเธเน 
เนเธเธขเธเธฒเธฃเธชเธฃเนเธฒเธ Custom File เนเธเธฃเธนเธเนเธเธเธเธญเธ Koa Middleware 
เธเธฃเนเธญเธกเธเธฑเธ Rollup Plugin เธชเธณเธซเธฃเธฑเธ Build
-->

---
layout: center
---

<div class="text-3xl text-green-500">No-bundle Dev Server for Vue 3 Single-File Components</div>
<!-- Vite เนเธเนเธ Dev Server เธเธตเน Compile File เนเธเธขเนเธกเนเธเนเธญเธเธเธถเนเธเธเธฒเธฃ bundle เธซเธฃเธทเธญ webpack เนเธ เน -->
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

โ Project name: โฆ vite-project <br>
โ Select a framework: โบ vue <br>
โ Select a variant: โบ vue <br>
```
โโโ README.md
โโโ index.html
โโโ package.json
โโโ public
โย ย  โโโ favicon.ico
โโโ src
โย ย  โโโ App.vue
โย ย  โโโ assets
โย ย  โย ย  โโโ logo.png
โย ย  โโโ components
โย ย  โย ย  โโโ HelloWorld.vue
โย ย  โโโ main.js
โโโ vite.config.js
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

This methodology is called Atomic Design because itโs very idea is founded in that of Chemistry, and the study of the composition of matter. The universe is made up of a fixed set of โatomic elementsโ โ known to many of us as the periodic table of elements. These elements are the building blocks of everything around us.

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
เธงเธดเธเธตเธเธฒเธฃเธเธตเนเนเธฃเธตเธขเธเธงเนเธฒ Atomic Design 
เนเธเธทเนเธญเธเธเธฒเธเนเธเธงเธเธดเธเธเธตเนเธกเธตเธเธทเนเธเธเธฒเธเธกเธฒเธเธฒเธเธงเธดเธเธฒเนเธเธกเธต เนเธฅเธฐเธเธฒเธฃเธจเธถเธเธฉเธฒเธญเธเธเนเธเธฃเธฐเธเธญเธเธเธญเธเธชเธชเธฒเธฃ

 เธเธฑเธเธฃเธงเธฒเธฅเธเธฃเธฐเธเธญเธเธเนเธงเธขเธเธธเธเธเธญเธ 'เธเธฒเธเธธเธญเธฐเธเธญเธก' เธเธเธเธตเน เธเธถเนเธเธเธงเธเนเธฃเธฒเธซเธฅเธฒเธขเธเธเธฃเธนเนเธเธฑเธเนเธเธเธทเนเธญเธเธฒเธฃเธฒเธเธเธฒเธเธธ เธญเธเธเนเธเธฃเธฐเธเธญเธเนเธซเธฅเนเธฒเธเธตเนเนเธเนเธเธชเนเธงเธเธเธฃเธฐเธเธญเธเธชเธณเธเธฑเธเธเธญเธเธเธธเธเธชเธดเนเธเธฃเธญเธเธเธฑเธงเนเธฃเธฒ


Atom เนเธกเนเนเธเนเธเธฃเธฐเธเธงเธเธเธฒเธฃเธเธตเนเธเธฒเธขเธเธฑเธง เนเธเนเนเธเนเธเนเธเธเธเธณเธฅเธญเธเธเธฒเธเธเธดเธเธเธตเนเธเนเธงเธขเนเธซเนเนเธฃเธฒเธเธถเธเธเธถเธเธชเนเธงเธเธเนเธญเธเธฃเธฐเธชเธฒเธเธเธนเนเนเธเนเธเธญเธเนเธฃเธฒเนเธเนเธเธเธฑเนเธเธชเนเธงเธเธเธตเนเนเธเธทเนเธญเธกเนเธขเธเธเธฑเธเนเธฅเธฐเธชเนเธงเธเธฃเธงเธกเนเธเนเธงเธฅเธฒเนเธเธตเธขเธงเธเธฑเธ

เนเธเธงเธดเธเธฒเนเธเธกเธต เธเธฒเธเธธเธญเธฐเธเธญเธกเนเธซเธฅเนเธฒเธเธตเนเธกเธตเธเธธเธเธชเธกเธเธฑเธเธดเธเธเธเธตเนเธเธตเนเธเธณเธซเธเธเธญเธเธเนเธเธฃเธฐเธเธญเธเนเธซเธฅเนเธฒเธเธตเน เธญเธญเธเธเธดเนเธเธเนเธฅเธฐเนเธฎเนเธเธฃเนเธเธเนเธเนเธเธญเธฐเธเธญเธกเธเธตเนเธกเธตเธเธธเธเธชเธกเธเธฑเธเธดเธญเธดเธชเธฃเธฐ เธญเธขเนเธฒเธเนเธฃเธเนเธเธฒเธก เนเธกเธทเนเธญเธญเธเธเนเธเธฃเธฐเธเธญเธเนเธซเธฅเนเธฒเธเธตเนเธฃเธงเธกเธเธฑเธ เธเธงเธเธกเธฑเธเธเธฐเธชเธฃเนเธฒเธเนเธกเนเธฅเธเธธเธฅเธเธถเนเธเธกเธตเธฅเธฑเธเธฉเธเธฐเนเธเธเธฒเธฐเธเธญเธเธเธฑเธงเนเธญเธเธเธถเนเธเธเธฃเธฐเธเธญเธเธเนเธงเธขเธญเธฐเธเธญเธกเธเธตเนเธกเธตเธญเธขเธนเน เนเธเธเธฃเธเธตเธเธญเธเนเธฎเนเธเธฃเนเธเธเนเธฅเธฐเธญเธญเธเธเธดเนเธเธ เธเธฒเธฃเธเธฑเธเธเธนเนเนเธฎเนเธเธฃเนเธเธเธชเธญเธเธญเธฐเธเธญเธกเธเธฑเธเธญเธญเธเธเธดเนเธเธเธเธฐเธชเธฃเนเธฒเธเธชเธดเนเธเธเธตเนเนเธฃเธฒเนเธฃเธตเธขเธเธงเนเธฒเนเธกเนเธฅเธเธธเธฅเธเธญเธเธเนเธณ
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
เธกเธตเธซเนเธฒเธเธฑเนเธเธเธญเธ เนเธเธขเธชเธฒเธกเธเธฑเนเธเธเธญเธเนเธฃเธเธเธนเธเธเธณเธฅเธญเธเธเธฒเธกเนเธเธเธเธตเนเนเธเธตเธขเธเนเธเนเธฒเธเธฑเธเนเธเนเธฅเธเนเธเธกเธต เนเธเนเธฅเธฐเธเธฑเนเธเธเธญเธเธชเธฃเนเธฒเธเธเธถเนเธเธเธฒเธเธเธฑเนเธเธเธญเธเธเนเธญเธเธซเธเนเธฒ เนเธเธขเธเธณเธซเธเนเธฒเธเธตเนเนเธเนเธเธเธฒเธฃเธฃเธงเธกเธฃเธฒเธขเธเธฒเธฃเธเธฒเธเธเธฑเนเธเธเธญเธเธเนเธญเธเธซเธเนเธฒ
-->

---

# Atoms

Just like in Chemistry, atoms are the smallest building blocks in our system. Rather than atoms like Oxygen or Hydrogen, in design we have buttons, inputs, labels and other small elements that get used throughout our design. Iconography fits in this category, whether it is a menu icon, or avatar as theyโre small elements that come together to form the next stage โ molecules.

<img
  class="pt-4 w-[600px]"
  m="auto"
  src="https://xd.adobe.com/ideas/wp-content/uploads/2021/07/1618031645-1.png.webp"
/>

<!--
เนเธเนเธเนเธเธตเธขเธงเธเธฑเธเนเธเธงเธดเธเธฒเนเธเธกเธต เธญเธฐเธเธญเธกเนเธเนเธเธซเธเนเธงเธขเธเธฒเธฃเธชเธฃเนเธฒเธเธเธตเนเนเธฅเนเธเธเธตเนเธชเธธเธเนเธเธฃเธฐเธเธเธเธญเธเนเธฃเธฒ เนเธเธเธเธตเนเธเธฐเนเธเนเธเธญเธฐเธเธญเธกเธญเธขเนเธฒเธเธญเธญเธเธเธดเนเธเธเธซเธฃเธทเธญเนเธฎเนเธเธฃเนเธเธ 
เนเธเธเธฒเธฃเธญเธญเธเนเธเธเนเธฃเธฒเธกเธต buttons, inputs, labels  เนเธฅเธฐเธญเธเธเนเธเธฃเธฐเธเธญเธเนเธฅเนเธเน เธญเธทเนเธเน เธเธตเนเนเธเนเนเธเธเธฒเธฃเธญเธญเธเนเธเธเธเธญเธเนเธฃเธฒ
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
เนเธเธเธฑเนเธเธเธญเธเธเธญเธเนเธกเนเธฅเธเธธเธฅ เนเธฃเธฒเธเธณเธญเธเธเนเธเธฃเธฐเธเธญเธเนเธซเธฅเนเธฒเธเธตเนเธกเธฒเธฃเธงเธกเธเธฑเธเนเธเนเธเธเธฅเธธเนเธกเนเธซเธกเน เธขเธเธเธฑเธงเธญเธขเนเธฒเธเธญเธฐเธเธญเธกเธเธญเธเธญเธงเธฒเธเธฒเธฃเนเธเธญเธเนเธฃเธฒ เธเนเธฒเนเธฃเธฒเธฃเธงเธกเธญเธฐเธเธญเธกเธเธญเธเธญเธงเธฒเธเธฒเธฃเนเนเธเนเธฒเธเธฑเธเธเนเธฒเธขเธเธทเนเธญเนเธฅเธฐเธเธทเนเธญเนเธฃเธทเนเธญเธ เธญเธเธเนเธเธฃเธฐเธเธญเธเธญเธฐเธเธญเธกเธญเธทเนเธเน เนเธฃเธฒเธชเธฒเธกเธฒเธฃเธเธชเธฃเนเธฒเธเนเธกเนเธฅเธเธธเธฅเนเธเธฃเนเธเธฅเนเนเธเน

> เนเธเนเธเนเธเธตเธขเธงเธเธฑเธเนเธเธงเธดเธเธฒเนเธเธกเธต เนเธฃเธฒเธชเธฒเธกเธฒเธฃเธเธฃเธงเธกเธญเธฐเธเธญเธกเนเธเธตเธขเธงเธเธฑเธเนเธเธฃเธนเธเนเธเธเธเนเธฒเธเน เนเธเธทเนเธญเธชเธฃเนเธฒเธเนเธกเนเธฅเธเธธเธฅเธเธตเนเธกเธตเนเธญเธเธฅเธฑเธเธฉเธเนเนเธเธเธฒเธฐเนเธเธทเนเธญเนเธเนเนเธเธเธฒเธฃเธญเธญเธเนเธเธเธเธญเธเนเธฃเธฒ
-->

---

# Organisms

Our collections of atoms and molecules now become more complex than at the molecular level. Take for instance our โprofileโ molecule. It was a simple element comprising an avatar and a pair of label elements. As we bring that into an organism, we may be adding that into an app header for a profile page, complete with navigation, a background cover photo and some other molecules. This creates our header organism.

> The organism is not yet a complete design, but is a component that can be reused across designs, or layout templates.

<img
  class="w-[500px]"
  m="auto"
  src="https://xd.adobe.com/ideas/wp-content/uploads/2021/07/1618031647-3.png.webp"
/>

<!--
> organism เธขเธฑเธเนเธกเนเนเธเนเธชเธกเธเธนเธฃเธเน 100% เนเธเนเนเธเนเธเธชเนเธงเธเธเธฃเธฐเธเธญเธเธเธตเนเธชเธฒเธกเธฒเธฃเธเธเธณเธกเธฒเนเธเนเธเนเธณเธฃเธฐเธซเธงเนเธฒเธเธเธฒเธฃเธญเธญเธเนเธเธ เธซเธฃเธทเธญเนเธเธกเนเธเธฅเธเนเธฅเธขเนเนเธญเธฒเธเน
-->

---

# Templates

The template is the first stage of the Atomic Design methodology that does not align to a stage in the molecular world, but is important for Atomic Design. A template is where we begin to curate our organisms and other elements into a cohesive design.

> Think of templates as the blueprint for our future finished page designs. At this point theyโre still the elements, and wonโt contain real data โ much like a wireframe.

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
โโโ atoms
    โโโ alert
    โโโ badge
    โโโ button
    โโโ checkbox
    โโโ datepicker
    โโโ icon
    โโโ image
    โโโ input
    โโโ link
    โโโ pagination
    โโโ radio
    โโโ select
    โโโ textarea

```

---

# In development

## Molecules
Molecules are components that have no logic like atoms, yet are more complect than an atom and can be composed of atoms and molecules.

```
components
โโโ molecules
    โโโ account-menu
    โโโ account-new
    โโโ account-success
    โโโ breadcrumb
    โโโ button-group
    โโโ contact
    โโโ dropdown
    โโโ input-group
    โโโ list-group
    โโโ logo
    โโโ media
    โโโ menu
    โโโ rating
    โโโ review
    โโโ tabs
```

---

# In development

## Organisms
Organisms are components that carry most of the logic like login forms and cart, yet most of the styling is and html is added vie composing atoms molecules.

```
components
โโโ organisms
    โโโ category-grid
    โโโ category-info
    โโโ category-product
    โโโ compare-actions
    โโโ contact-form
    โโโ currency
    โโโ location-grid
    โโโ login-form
    โโโ password-form
    โโโ register-form
    โโโ review-form
    โโโ review-list
    โโโ search-form
    โโโ search-inline-form
```

---

# In development

## Templates
Templates are used to compose the final page. You most often won't need to modify this as it is a simple combination of Component elements. You may use this folder to add new custom templates.

```
components
โโโ templates
    โโโ account
    โ   โโโ account
    โ   โโโ address
    โ   โโโ addressCreate
    โ   โโโ addressEdit
    โ   โโโ login
    โ   โโโ password
    โ   โโโ register
    โโโ common
        โโโ contact
        โโโ error
        โโโ layout
        โโโ page
        โโโ search
```

---

# In development

## Pages
Pages are components that use Templates to organize the data. They carry most of the logic on the page and use the store to fetch data and display it.

```
components
โโโ pages
    โโโ account
    โ   โโโ account
    โ   โโโ address
    โ   โโโ addressCreate
    โ   โโโ addressEdit
    โ   โโโ login
    โ   โโโ password
    โ   โโโ register
    โโโ common
        โโโ contact
        โโโ error
        โโโ layout
        โโโ page
        โโโ search
```

---

# In development

## Extensions (Widgets)
Extensions (Widgets) are components that can be positioned on a page via the vuefront.config.js file. They can carry logic like organisms or be as simple as an atom. Third-party apps will use this folder to add their custom components.

```
components
โโโ extensions
    โโโ blog
    โ   โโโ category
    โ   โโโ latest-post
    โ   โโโ search-post
    โโโ store
        โโโ category
        โโโ checkout
        โโโ featured-product
        โโโ latest-product
        โโโ related-product
        โโโ search-product
        โโโ special-product
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
<p class="text-center textxl pt-2">Pinia (pronounced /piหnjส/, like "peenya" in English)</p>
<p class="text-center textxl"> is the closest word to piรฑa (pineapple in Spanish)</p>


---

# [Pinia](https://pinia.vuejs.org/)
The Vue Store that you will enjoy using

<div grid="~ cols-3 gap-2" m="t-10">
  <div>
    <div class="text-bold text-xl">
    ๐ก Intuitive
    </div>
    <div m="t-1" class="text-sm text-gray-500">
      Stores are as familiar as components. API designed to let you write well organized stores.
    </div>
  </div>

  <div>
    <div class="text-bold text-xl">
    ๐ Type Safe
    </div>
    <div m="t-1" class="text-sm text-gray-500">
      Types are inferred, which means stores provide you with autocompletion even in JavaScript!
    </div>
  </div>

  <div>
    <div class="text-bold text-xl">
    โ๏ธ Devtools support
    </div>
    <div m="t-1" class="text-sm text-gray-500">
      Pinia hooks into Vue devtools to give you an enhanced development experience in both Vue 2 and Vue 3.
    </div>
  </div>
</div>
<div grid="~ cols-3 gap-2" m="t-10">
  <div>
    <div class="text-bold text-xl">
    ๐ Extensible
    </div>
    <div m="t-1" class="text-sm text-gray-500">
      React to store changes to extend Pinia with transactions, local storage synchronization, etc.
    </div>
  </div>
  <div>
    <div class="text-bold text-xl">
    ๐ Modular by design
    </div>
    <div m="t-1" class="text-sm text-gray-500">
      Build multiple stores and let your bundler code split them automatically.
    </div>
  </div>
  <div>
    <div class="text-bold text-xl">
    ๐ฆ Extremely light
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
