<template>
    <ion-page>
        <ion-header>
            <ion-toolbar class="toolbar-md-primary">
                <ion-title>Parcel Scanner</ion-title>
            </ion-toolbar>
        </ion-header>
        <ion-content class="content">
            <ion-card>
                <ion-button
                    :router-link="
                        'scan?longitude=' +
                        location.longitude +
                        '&latitude=' +
                        location.latitude
                    "
                    router-direction="forward"
                >
                    SCAN
                </ion-button>
            </ion-card>
        </ion-content>
    </ion-page>
    <!-- <div class="container">
        <button v-if="location != null">
            <nuxt-link
                class="link"
                :to="{
                    path: 'scan',
                    query: {
                        longitude: location.longitude,
                        latitude: location.latitude,
                    },
                }"
                >Scan</nuxt-link
            >
        </button>
        <p v-else-if="gettingLocation">Getting location...</p>
        <p v-else-if="errorStr">Something went wrong: {{ errorStr }}</p>
    </div> -->
</template>

<script setup>
    import { onMounted, ref, onUnmounted } from "vue";
    import { Geolocation } from "@capacitor/geolocation";

    const location = ref(null);
    const errorStr = ref("");
    const gettingLocation = ref(false);
    let watcher = null;

    onMounted(async () => {
        gettingLocation.value = true;

        watcher = await Geolocation.watchPosition({}, (pos, err) => {
            if (err) {
                errorStr.value = err;
                return;
            }
            location.value = pos.coords;
            console.log("got coords ", pos.coords);
        });
        gettingLocation.value = false;
    });

    onUnmounted(async () => {
        if (watcher != null) await Geolocation.clearWatch(watcher);
    });
</script>

<style scoped>
    .container {
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
    }
    button {
        padding: 1rem 2rem;
        border-radius: 0.5rem;
        border: none;
        background-color: #f1f1f1;
        font-size: 1.5rem;
        font-weight: 600;
        cursor: pointer;
        transition: all 0.3s ease-in-out;
    }
    button:hover {
        background-color: #e1e1e1;
    }
    .link {
        text-decoration: none;
        color: #000;
    }
</style>
