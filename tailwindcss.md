# TailwindCSS

Tailwind is a library designed to move most of the css into the html class attribute, as well as allow for css selectors to apply html classes. While this may clutter the html file, it makes it easy to find where something goes wrong. 

## Benefits

Tailwind moves much of the CSS into the HTML. The [benefits](https://webartisan.info/the-pros-and-cons-of-tailwindcss) of this include less context switching between HTML and CSS, [built in media queries](https://tailwindcss.com/docs/hover-focus-and-other-states), more consistency in colors and sizes, easier caching, easier style overwrite, easier style extraction, and, in setups with a build process, automatic CSS pruning. Tailwind also makes it very easy to maintain. With the css definition contained within the class attribute, you know exactly which element is using it.

## Negatives

Obviously, cramming the CSS into the HTML can make it harder to decode the html itself, as well as making the files larger. Production Tailwind also requires a build step. making it harder to learn and setup. On top of this, Tailwind requires learning the class and naming conventions, and can obfuscate some of the finer points of CSS.

## Installation

While Tailwind can be used as a [plugin for many popular frameworks](https://tailwindcss.com/docs/installation/framework-guides), or [from the command line](https://tailwindcss.com/docs/installation), it can also be used as a [linked script](https://tailwindcss.com/docs/installation/play-cdn), though this method is not recommended for production.

## Extraction

One of the biggest issues with Tailwind is finding patterns that could be extracted into its own css class. If you cannot create a component (as in React, Svelte, or Vue) or a template partial (Blade, ERB, Twig, Nunjucks), you can use the @apply directive. This, however, goes against the intentions of the Tailwind ethos.

```CSS
@tailwind base;
@tailwind components;
@tailwind utilities;

@layer components {
  .btn-primary {
    @apply py-2 px-4 bg-blue-500 text-white font-semibold rounded-lg shadow-md hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-400 focus:ring-opacity-75;
  }
}
```

## Random Others

Tailwind can be used alongside [Alpine JS](alpinejs.md) with the :class directive as in:

```
<span
  x-data="{ isOn: false }"
  @click="isOn = !isOn"
  :aria-checked="isOn"
  :class="{'bg-indigo-600': isOn, 'bg-gray-200': !isOn }"
  class="bg-gray-200 relative inline-block flex-shrink-0 h-6 w-11 border-2 border-transparent rounded-full cursor-pointer transition-colors ease-in-out duration-200 focus:outline-none focus:shadow-outline"
  role="checkbox"
  tabindex="0"
>
  <span
    aria-hidden="true"
    :class="{'translate-x-5': isOn, 'translate-x-0': !isOn }"
    class="translate-x-0 inline-block h-5 w-5 rounded-full bg-white shadow transform transition ease-in-out duration-200"
  ></span>
</span>
``` 

Before trying to make your own them in Tailwind, please red the official [Theme Configuration](https://tailwindcss.com/docs/theme) article.