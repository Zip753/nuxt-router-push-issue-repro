# nuxt-router-push-issue-repro

> nuxt/nuxt.js#2737 reproduction

## Reproduction steps

1. `yarn install`
1. `yarn run dev`
1. Go to the main page (`http://localhost:3000` by default)
1. Open developer's console
1. Click **Break the app** button
1. Observe the console output

## Expected result

After pushing the button the page title should become `New title!`.

## Observed result

After pushing the button the page title doesn't change, however you can see that the URL is successfully updated and `asyncData` is executed (from console logs). Also, if you refresh the page with present `title` param you will see that the page is rendered properly, with `title` param value taken into account.
