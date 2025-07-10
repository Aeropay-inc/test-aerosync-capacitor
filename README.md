# test-aerosync-capacitor

This template should help get you started developing with Vue 3 in Vite.

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur).

## Customize configuration

See [Vite Configuration Reference](https://vite.dev/config/).

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Compile and Minify for Production

```sh
npm run build
```

### Build for Android with Capacitor

To build and deploy the app to an Android device or emulator:

```sh
npm run build              # Build the web app
npx cap copy               # Copy web build to native project
npx cap sync android       # Sync plugins and dependencies
npx cap open android       # Open Android Studio (optional)
```

Optional: Handle URL Events Manually

```sh
async onEvent(event) {
  console.log("event", event);

  // Uncomment below code if you want to launch the URL in the Capacitor browser

  // try {
  //   // Check if the app is running on a native platform (iOS or Android)
  //   if (Capacitor.isNativePlatform()) {
  //     // Verify the event payload exists and pageTitle equals "launchExternalWindow"
  //     // Also ensure onLoadApi URL is present
  //     if (
  //       event?.payload?.pageTitle === "launchExternalWindow" &&
  //       event?.payload?.onLoadApi
  //     ) {
  //       // Open the URL in Capacitor's in-app browser
  //       await Browser.open({ url: event.payload.onLoadApi });
  //     }
  //   }
  // } catch (error) {
  //   // Log any errors encountered during the open operation
  //   console.error("Failed to open URL in Capacitor Browser:", error);
  // }
}

```
