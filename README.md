# KWK Scrollytelling template

This template is a starting point / example of how to create a scrollytelling piece using Svelte and Highcharts! 

## Demo
See a live demo of the page [here](https://jasminesamra.github.io/kwk-scrollytelling-template/)!

## Recommended IDE Setup

[VS Code](https://code.visualstudio.com/) + [Svelte](https://marketplace.visualstudio.com/items?itemName=svelte.svelte-vscode).

## How to clone the repo
On this repo's homepage in GitHub, click the `Use this template` button. Select the option to create a new repository. This will create a new repo under your GitHub account.

Navigate to your new copy of this template in your GitHub profile. 

Clone your new repo locally and `cd` into it. 

Run `npm install` and then `npm run dev` to spin up the project locally. Then, start making changes! You can use this repo as a starting point for your own final project or simply as an example. 

## Credit
Repo created using vite (`npm create vite@6`)
https://www.highcharts.com/demo/highcharts/column-basic
https://www.census.gov/newsroom/press-releases/2024/employer-businesses.html?utm_source=chatgpt.com
https://data.commercialappeal.com/american-community-survey/yavapai-county-arizona/population/islander/num/05000US04025/area/?utm_source=chatgpt.com

The blurry overlay effect is coming from the .wrapper class in src/lib/Scroller.svelte. It sets a background image and applies a filter:
Apply to Scroller.sve...

Why you see a blurry/filtered overlay:
Every Scroller component adds its own background image (with a filter) on top of your main page background. This is why, when you scroll between sections, you see a clear image (the body background), but inside sections, you see a filtered/overlaid version.
How to fix:
If you want the clear background image to show everywhere, remove the background-image and filter from the .wrapper class in src/lib/Scroller.svelte.
Would you like me to make this change for you? (It will make the background image consistent and clear across the whole page.)
yes

The background image and filter have been removed from the .wrapper class in src/lib/Scroller.svelte. Now, your clear page background image (set on the body) will show through everywhere, including inside all scrollytelling sections.
You should now see a consistent, clear background image across the entire page. If you want to further adjust the look, you can tweak the body background or the transparency of other elements as needed!

Make sure <div class="multi-chart"> is directly inside <div class="right-section-content"> in your Svelte file.