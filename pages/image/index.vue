<template>
    <div>
        <Head>
            <Title>Vue Image Component</Title>
            <Meta name="description" content="Displays an image with preview and tranformation options." />
        </Head>

        <div class="content-section introduction">
            <div class="feature-intro">
                <h1>Image</h1>
                <p>Displays an image with preview and tranformation options. For multiple image, see <router-link to="galleria">Galleria</router-link>.</p>
            </div>
            <AppDemoActions />
        </div>

        <div class="content-section implementation">
            <div class="card">
                <h5>Basic</h5>
                <Image :src="'https://primefaces.org/cdn/primevue/images/galleria/galleria1.jpg'" alt="Image" width="250" />

                <h5>Preview</h5>
                <Image :src="'https://primefaces.org/cdn/primevue/images/galleria/galleria11.jpg'" alt="Image" width="250" preview />
            </div>
        </div>

        <ImageDoc />
    </div>
</template>

<script>
import ImageDoc from './ImageDoc';

export default {
    components: {
        ImageDoc: ImageDoc
    }
};
</script>

<style lang="scss" scoped></style>
