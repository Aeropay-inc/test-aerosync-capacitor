<script setup>
import { initAeroSyncWidget } from "aerosync-web-sdk";
import { Browser } from "@capacitor/browser";

const handleClick = () => {
  // Initialize the widget with configuration options
  let widgetControls = initAeroSyncWidget({
    elementId: "widget", // 👈 ID of the target div in your HTML
    iframeTitle: "Connect", // 🔒 Used for accessibility
    environment: "sandbox", // 🌍 Set to 'sandbox' for testing, 'production' for live
    token: "XXXXXX", // 🔑 Your secure AeroSync token
    theme: "light", // 🎨 Choose between 'light' or 'dark' theme
    deeplink: "aerosync://capacitor",
    // 📦 Event listener for all widget events
    async onEvent(event) {
      console.log("event", event);
      // uncomment below code if you want to launch the URL in the capacitor browser
      // try {
      //   // Check if the app is running on a native platform (iOS or Android)
      //   if (Capacitor.isNativePlatform()) {
      //     // Verify the event payload exists and pageTitle equals "oauthURL"
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
    },

    // 🚀 Fires when the widget is fully loaded
    onLoad() {
      console.log("onload");
    },

    // ✅ Called after the user successfully connects a bank and closes the widget
    onSuccess(event) {
      console.log("onSuccess", event);
      // ...
      // Handle success (e.g., update UI, send data to backend, etc.)
    },

    // ❌ Fires when the widget is closed manually by the user
    onClose() {
      console.log("widget closed");
    },

    // ⚠️ Catch and handle widget errors
    onError(event) {
      console.log("onError", event);
    },
  });

  // 🧭 Launch the widget
  widgetControls.launch();
};
</script>

<template>
  <div class="centered-container">
    <h1 class="title">Aerosync Web SDK</h1>
    <div id="widget"></div>
    <button id="openBank" class="action-button" @click="handleClick">
      Launch Widget
    </button>
  </div>
</template>

<style scoped>
.centered-container {
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 1.5rem;
  padding: 1rem;
  text-align: center;
}

.title {
  font-size: 2.5rem;
  margin: 0;
  font-weight: 700;
  color: #2c3e50;
}

.action-button {
  padding: 0.75rem 2rem;
  font-size: 1.1rem;
  border: none;
  border-radius: 6px;
  background-color: #42b983;
  color: white;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.action-button:hover {
  background-color: #36976e;
}
</style>
