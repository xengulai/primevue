<template>
    <div>
        <Head>
            <Title>Vue Gallery Component</Title>
            <Meta name="description" content="Galleria is a content gallery component." />
        </Head>

        <div class="galleria-demo">
            <div class="content-section introduction">
                <div class="feature-intro">
                    <h1>Galleria</h1>
                    <p>Galleria is an advanced content gallery component.</p>
                </div>
            </div>

            <div class="content-section implementation">
                <div class="card">
                    <Galleria :value="images" :responsiveOptions="responsiveOptions" :numVisible="5" containerStyle="max-width: 640px">
                        <template #item="slotProps">
                            <img :src="slotProps.item.itemImageSrc" :alt="slotProps.item.alt" style="width: 100%" />
                        </template>
                        <template #thumbnail="slotProps">
                            <img :src="slotProps.item.thumbnailImageSrc" :alt="slotProps.item.alt" />
                        </template>
                    </Galleria>
                </div>
            </div>

            <GalleriaDoc />
        </div>
    </div>
</template>

<script>
import PhotoService from '../../service/PhotoService';
import GalleriaDoc from './GalleriaDoc';

export default {
    data() {
        return {
            images: null,
            responsiveOptions: [
                {
                    breakpoint: '1024px',
                    numVisible: 5
                },
                {
                    breakpoint: '768px',
                    numVisible: 3
                },
                {
                    breakpoint: '560px',
                    numVisible: 1
                }
            ]
        };
    },
    galleriaService: null,
    created() {
        this.galleriaService = new PhotoService();
    },
    mounted() {
        this.galleriaService.getImages().then((data) => (this.images = data));
    },
    components: {
        GalleriaDoc: GalleriaDoc
    }
};
</script>
