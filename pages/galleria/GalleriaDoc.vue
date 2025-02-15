<template>
    <div class="content-section documentation">
        <TabView>
            <TabPanel header="Documentation">
                <h5>Import via Module</h5>
                <pre v-code.script><code>
import Galleria from 'primevue/galleria';

</code></pre>

                <h5>Import via CDN</h5>
                <pre v-code><code>
&lt;script src="https://unpkg.com/primevue@^3/core/core.min.js"&gt;&lt;/script&gt;
&lt;script src="https://unpkg.com/primevue@^3/galleria/galleria.min.js"&gt;&lt;/script&gt;

</code></pre>

                <h5>Getting Started</h5>
                <p>Galleria requires item template and a value as an array of objects.</p>
                <pre v-code><code>
&lt;Galleria :value="images"&gt;
    &lt;template #item="slotProps"&gt;
        &lt;img :src="slotProps.item.itemImageSrc" :alt="slotProps.item.alt" /&gt;
    &lt;/template&gt;
&lt;/Galleria&gt;

</code></pre>

                <p>For the rest of the documentation, sample data below would be return from an example service e.g. PhotoService.</p>
                <div style="overflow: auto; height: 400px">
                    <pre v-code.script><code>
{
    "data":[
        {
            "itemImageSrc": "images/galleria/galleria1.jpg",
            "thumbnailImageSrc": "images/galleria/galleria1s.jpg",
            "alt": "Description for Image 1",
            "title": "Title 1"
        },
        {
            "itemImageSrc": "images/galleria/galleria2.jpg",
            "thumbnailImageSrc": "images/galleria/galleria2s.jpg",
            "alt": "Description for Image 2",
            "title": "Title 2"
        },
        {
            "itemImageSrc": "images/galleria/galleria3.jpg",
            "thumbnailImageSrc": "images/galleria/galleria3s.jpg",
            "alt": "Description for Image 3",
            "title": "Title 3"
        },
        {
            "itemImageSrc": "images/galleria/galleria4.jpg",
            "thumbnailImageSrc": "images/galleria/galleria4s.jpg",
            "alt": "Description for Image 4",
            "title": "Title 4"
        },
        {
            "itemImageSrc": "images/galleria/galleria5.jpg",
            "thumbnailImageSrc": "images/galleria/galleria5s.jpg",
            "alt": "Description for Image 5",
            "title": "Title 5"
        },
        {
            "itemImageSrc": "images/galleria/galleria6.jpg",
            "thumbnailImageSrc": "images/galleria/galleria6s.jpg",
            "alt": "Description for Image 6",
            "title": "Title 6"
        },
        {
            "itemImageSrc": "images/galleria/galleria7.jpg",
            "thumbnailImageSrc": "images/galleria/galleria7s.jpg",
            "alt": "Description for Image 7",
            "title": "Title 7"
        },
        {
            "itemImageSrc": "images/galleria/galleria8.jpg",
            "thumbnailImageSrc": "images/galleria/galleria8s.jpg",
            "alt": "Description for Image 8",
            "title": "Title 8"
        },
        {
            "itemImageSrc": "images/galleria/galleria9.jpg",
            "thumbnailImageSrc": "images/galleria/galleria9s.jpg",
            "alt": "Description for Image 9",
            "title": "Title 9"
        },
        {
            "itemImageSrc": "images/galleria/galleria10.jpg",
            "thumbnailImageSrc": "images/galleria/galleria10s.jpg",
            "alt": "Description for Image 10",
            "title": "Title 10"
        },
        {
            "itemImageSrc": "images/galleria/galleria11.jpg",
            "thumbnailImageSrc": "images/galleria/galleria11s.jpg",
            "alt": "Description for Image 11",
            "title": "Title 11"
        },
        {
            "itemImageSrc": "images/galleria/galleria12.jpg",
            "thumbnailImageSrc": "images/galleria/galleria12s.jpg",
            "alt": "Description for Image 12",
            "title": "Title 12"
        },
        {
            "itemImageSrc": "images/galleria/galleria13.jpg",
            "thumbnailImageSrc": "images/galleria/galleria13s.jpg",
            "alt": "Description for Image 13",
            "title": "Title 13"
        },
        {
            "itemImageSrc": "images/galleria/galleria14.jpg",
            "thumbnailImageSrc": "images/galleria/galleria14s.jpg",
            "alt": "Description for Image 14",
            "title": "Title 14"
        },
        {
            "itemImageSrc": "images/galleria/galleria15.jpg",
            "thumbnailImageSrc": "images/galleria/galleria15s.jpg",
            "alt": "Description for Image 15",
            "title": "Title 15"
        }
    ]
}

</code></pre>
                </div>

                <pre v-code.script><code>
export default class PhotoService {

	getImages() {
        return fetch('demo/data/photos.json').then(res => res.json())
                .then(d => d.data);
    }
}

</code></pre>

                <pre v-code.script><code>
export default {
    data() {
        return {
            images: null
        }
    },
    galleriaService: null,
	created() {
		this.galleriaService = new PhotoService();
	},
	mounted() {
        this.galleriaService.getImages().then(data => this.images = data);
    }
}

</code></pre>

                <h5>Items per page</h5>
                <p>Number of items per page is defined using the <i>numVisible</i> property.</p>

                <pre v-code><code>
&lt;Galleria :value="images" :numVisible="5"&gt;
    &lt;template #item="slotProps"&gt;
        &lt;img :src="slotProps.item.itemImageSrc" :alt="slotProps.item.alt" style="width: 100%" /&gt;
    &lt;/template&gt;
    &lt;template #thumbnail="slotProps"&gt;
        &lt;img :src="slotProps.item.thumbnailImageSrc" :alt="slotProps.item.alt" /&gt;
    &lt;/template&gt;
&lt;/Galleria&gt;

</code></pre>

                <h5>Responsive</h5>
                <p>For responsive design, <i>numVisible</i> can be defined using the <i>responsiveOptions</i> property which references an array of objects whose breakpoint defines the max-width to apply the settings.</p>

                <pre v-code><code>
&lt;Galleria :value="images" :responsiveOptions="responsiveOptions" :numVisible="5"&gt;
    &lt;template #item="slotProps"&gt;
        &lt;img :src="slotProps.item.itemImageSrc" :alt="slotProps.item.alt" style="width: 100%" /&gt;
    &lt;/template&gt;
    &lt;template #thumbnail="slotProps"&gt;
        &lt;img :src="slotProps.item.thumbnailImageSrc" :alt="slotProps.item.alt" /&gt;
    &lt;/template&gt;
&lt;/Galleria&gt;

</code></pre>

                <pre v-code.script><code>
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

</code></pre>

                <h5>Header and Footer</h5>
                <p>Custom content projection is available using the <i>header</i> and <i>footer</i> properties.</p>
                <pre v-code><code>
&lt;Galleria :value="images" :responsiveOptions="responsiveOptions" :numVisible="5" containerStyle="max-width: 640px"&gt;
    &lt;template #header&gt;
        &lt;h1&gt;Header&lt;/h1&gt;
    &lt;/template&gt;
    &lt;template #item="slotProps"&gt;
        &lt;img :src="slotProps.item.itemImageSrc" :alt="slotProps.item.alt" style="width: 100%" /&gt;
    &lt;/template&gt;
    &lt;template #footer&gt;
        &lt;h1&gt;Footer&lt;/h1&gt;
    &lt;/template&gt;
&lt;/Galleria&gt;

</code></pre>

                <h5>Indicators</h5>
                <p>
                    Indicators allow quick navigation between the items. Set <i>showIndicators</i> to display indicators which can be customized further with the <i>changeItemOnIndicatorHover</i>, <i>showIndicatorsOnItem</i> and
                    <i>indicatorsPosition</i> properties.
                </p>
                <pre v-code><code>
&lt;Galleria :value="images" :showIndicators="true"&gt;
    &lt;template #item="slotProps"&gt;
        &lt;img :src="slotProps.item.itemImageSrc" :alt="slotProps.item.alt" /&gt;
    &lt;/template&gt;
&lt;/Galleria&gt;

</code></pre>

                <h5>Properties</h5>
                <p>Any property as style and class are passed to the main container element. Following are the additional properties to configure the component.</p>
                <div class="doc-tablewrapper">
                    <table class="doc-table">
                        <thead>
                            <tr>
                                <th>Name</th>
                                <th>Type</th>
                                <th>Default</th>
                                <th>Description</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td>id</td>
                                <td>string</td>
                                <td>null</td>
                                <td>Unique identifier of the element.</td>
                            </tr>
                            <tr>
                                <td>value</td>
                                <td>array</td>
                                <td>null</td>
                                <td>An array of objects to display.</td>
                            </tr>
                            <tr>
                                <td>activeIndex</td>
                                <td>number</td>
                                <td>0</td>
                                <td>Index of the first item.</td>
                            </tr>
                            <tr>
                                <td>fullScreen</td>
                                <td>boolean</td>
                                <td>false</td>
                                <td>Whether to display the component on fullscreen.</td>
                            </tr>
                            <tr>
                                <td>visible</td>
                                <td>boolean</td>
                                <td>false</td>
                                <td>Specifies the visibility of the mask on fullscreen mode.</td>
                            </tr>
                            <tr>
                                <td>numVisible</td>
                                <td>number</td>
                                <td>3</td>
                                <td>Number of items per page.</td>
                            </tr>
                            <tr>
                                <td>responsiveOptions</td>
                                <td>any</td>
                                <td>null</td>
                                <td>An array of options for responsive design.</td>
                            </tr>
                            <tr>
                                <td>showItemNavigators</td>
                                <td>boolean</td>
                                <td>false</td>
                                <td>Whether to display navigation buttons in item section.</td>
                            </tr>
                            <tr>
                                <td>showThumbnailNavigators</td>
                                <td>boolean</td>
                                <td>true</td>
                                <td>Whether to display navigation buttons in thumbnail container.</td>
                            </tr>
                            <tr>
                                <td>showItemNavigatorsOnHover</td>
                                <td>boolean</td>
                                <td>false</td>
                                <td>Whether to display navigation buttons on item hover.</td>
                            </tr>
                            <tr>
                                <td>changeItemOnIndicatorHover</td>
                                <td>boolean</td>
                                <td>false</td>
                                <td>When enabled, item is changed on indicator hover.</td>
                            </tr>
                            <tr>
                                <td>circular</td>
                                <td>boolean</td>
                                <td>false</td>
                                <td>Defines if scrolling would be infinite.</td>
                            </tr>
                            <tr>
                                <td>autoPlay</td>
                                <td>boolean</td>
                                <td>false</td>
                                <td>Items are displayed with a slideshow in autoPlay mode.</td>
                            </tr>
                            <tr>
                                <td>transitionInterval</td>
                                <td>number</td>
                                <td>4000</td>
                                <td>Time in milliseconds to scroll items.</td>
                            </tr>
                            <tr>
                                <td>showThumbnails</td>
                                <td>boolean</td>
                                <td>true</td>
                                <td>Whether to display thumbnail container.</td>
                            </tr>
                            <tr>
                                <td>thumbnailsPosition</td>
                                <td>string</td>
                                <td>bottom</td>
                                <td>Position of thumbnails. Valid values are "bottom", "top", "left" and "right".</td>
                            </tr>
                            <tr>
                                <td>verticalThumbnailViewPortHeight</td>
                                <td>string</td>
                                <td>300px</td>
                                <td>Height of the viewport in vertical thumbnail.</td>
                            </tr>
                            <tr>
                                <td>showIndicators</td>
                                <td>boolean</td>
                                <td>false</td>
                                <td>Whether to display indicator container.</td>
                            </tr>
                            <tr>
                                <td>showIndicatorsOnItem</td>
                                <td>boolean</td>
                                <td>false</td>
                                <td>When enabled, indicator container is displayed on item container.</td>
                            </tr>
                            <tr>
                                <td>indicatorsPosition</td>
                                <td>string</td>
                                <td>bottom</td>
                                <td>Position of indicators. Valid values are "bottom", "top", "left" and "right".</td>
                            </tr>
                            <tr>
                                <td>baseZIndex</td>
                                <td>number</td>
                                <td>0</td>
                                <td>Base zIndex value to use in layering.</td>
                            </tr>
                            <tr>
                                <td>maskClass</td>
                                <td>string</td>
                                <td>null</td>
                                <td>Style class of the mask on fullscreen mode.</td>
                            </tr>
                            <tr>
                                <td>containerStyle</td>
                                <td>any</td>
                                <td>null</td>
                                <td>Inline style of the component on fullscreen mode. Otherwise, the 'style' property can be used.</td>
                            </tr>
                            <tr>
                                <td>containerClass</td>
                                <td>any</td>
                                <td>null</td>
                                <td>Style class of the component on fullscreen mode. Otherwise, the 'class' property can be used.</td>
                            </tr>
                            <tr>
                                <td>containerProps</td>
                                <td>object</td>
                                <td>null</td>
                                <td>Uses to pass all properties of the HTMLDivElement to the container element on fullscreen mode.</td>
                            </tr>
                            <tr>
                                <td>prevButtonProps</td>
                                <td>object</td>
                                <td>null</td>
                                <td>Uses to pass all properties of the HTMLButtonElement to the previous navigation button.</td>
                            </tr>
                            <tr>
                                <td>nextButtonProps</td>
                                <td>object</td>
                                <td>null</td>
                                <td>Uses to pass all properties of the HTMLButtonElement to the next navigation button.</td>
                            </tr>
                        </tbody>
                    </table>
                </div>

                <h5>Slots</h5>
                <div class="doc-tablewrapper">
                    <table class="doc-table">
                        <thead>
                            <tr>
                                <th>Name</th>
                                <th>Parameters</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td>header</td>
                                <td>-</td>
                            </tr>
                            <tr>
                                <td>footer</td>
                                <td>-</td>
                            </tr>
                            <tr>
                                <td>item</td>
                                <td>item: Item instance</td>
                            </tr>
                            <tr>
                                <td>caption</td>
                                <td>item: Item instance</td>
                            </tr>
                            <tr>
                                <td>thumbnail</td>
                                <td>item: Item instance</td>
                            </tr>
                            <tr>
                                <td>indicator</td>
                                <td>index: Index of the indicator item</td>
                            </tr>
                        </tbody>
                    </table>
                </div>

                <h5>Styling</h5>
                <p>Following is the list of structural style classes, for theming classes visit <router-link to="/theming">theming</router-link> page.</p>
                <div class="doc-tablewrapper">
                    <table class="doc-table">
                        <thead>
                            <tr>
                                <th>Name</th>
                                <th>Element</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td>p-galleria</td>
                                <td>Container element.</td>
                            </tr>
                            <tr>
                                <td>p-galleria-header</td>
                                <td>Header section.</td>
                            </tr>
                            <tr>
                                <td>p-galleria-footer</td>
                                <td>Footer section.</td>
                            </tr>
                            <tr>
                                <td>p-galleria-item-wrapper</td>
                                <td>Item wrapper element. It contains item container and indicators.</td>
                            </tr>
                            <tr>
                                <td>p-galleria-item-container</td>
                                <td>Container of the item wrapper. It contains navigation buttons, items and caption content.</td>
                            </tr>
                            <tr>
                                <td>p-galleria-indicators</td>
                                <td>Container of the indicators. It contains indicator items.</td>
                            </tr>
                            <tr>
                                <td>p-galleria-thumbnail-content</td>
                                <td>Thumbnail content element.</td>
                            </tr>
                            <tr>
                                <td>p-galleria-thumbnail-container</td>
                                <td>Container of the thumbnail content. It contains navigation buttons and thumbnail items.</td>
                            </tr>
                            <tr>
                                <td>p-galleria-caption</td>
                                <td>Content of the item caption.</td>
                            </tr>
                        </tbody>
                    </table>
                </div>

                <h5>Accessibility</h5>
                <h6>Screen Reader</h6>
                <p>
                    Galleria uses <i>region</i> role and since any attribute is passed to the main container element, attributes such as <i>aria-label</i> and <i>aria-roledescription</i> can be used as well. The slides container has
                    <i>aria-live</i> attribute set as "polite" if galleria is not in autoplay mode, otherwise "off" would be the value in autoplay.
                </p>

                <p>
                    A slide has a <i>group</i> role with an aria-label that refers to the <i>aria.slideNumber</i> property of the <router-link to="/locale">locale</router-link> API. Similarly <i>aria.slide</i> is used as the
                    <i>aria-roledescription</i> of the item. Inactive slides are hidden from the readers with <i>aria-hidden</i>.
                </p>

                <p>
                    Next and Previous navigators are button elements with <i>aria-label</i> attributes referring to the <i>aria.prevPageLabel</i> and <i>aria.nextPageLabel</i> properties of the <router-link to="/locale">locale</router-link> API by
                    default respectively, you may still use your own aria roles and attributes as any valid attribute is passed to the button elements implicitly by using <i>nextButtonProps</i> and <i>prevButtonProps</i>.
                </p>

                <p>
                    Quick navigation elements and thumnbails follow the tab pattern. They are placed inside an element with a <i>tablist</i> role whereas each item has a <i>tab</i> role with <i>aria-selected</i> and <i>aria-controls</i> attributes.
                    The <i>aria-label</i> attribute of a quick navigation item refers to the <i>aria.pageLabel</i> of the <router-link to="/locale">locale</router-link> API. Current page is marked with <i>aria-current</i>.
                </p>

                <p>
                    In full screen mode, modal element uses <i>dialog</i> role with <i>aria-modal</i> enabled. The close button retrieves <i>aria-label</i> from the <i>aria.close</i> property of the <router-link to="/locale">locale</router-link> API.
                </p>

                <h6>Next/Prev Keyboard Support</h6>
                <div class="doc-tablewrapper">
                    <table class="doc-table">
                        <thead>
                            <tr>
                                <th>Key</th>
                                <th>Function</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td>
                                    <i>tab</i>
                                </td>
                                <td>Moves focus through interactive elements in the carousel.</td>
                            </tr>
                            <tr>
                                <td>
                                    <i>enter</i>
                                </td>
                                <td>Activates navigation.</td>
                            </tr>
                            <tr>
                                <td>
                                    <i>space</i>
                                </td>
                                <td>Activates navigation.</td>
                            </tr>
                        </tbody>
                    </table>
                </div>

                <h6>Quick Navigation Keyboard Support</h6>
                <div class="doc-tablewrapper">
                    <table class="doc-table">
                        <thead>
                            <tr>
                                <th>Key</th>
                                <th>Function</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td>
                                    <i>tab</i>
                                </td>
                                <td>Moves focus through the active slide link.</td>
                            </tr>
                            <tr>
                                <td>
                                    <i>enter</i>
                                </td>
                                <td>Activates the focused slide link.</td>
                            </tr>
                            <tr>
                                <td>
                                    <i>space</i>
                                </td>
                                <td>Activates the focused slide link.</td>
                            </tr>
                            <tr>
                                <td>
                                    <i>right arrow</i>
                                </td>
                                <td>Moves focus to the next slide link.</td>
                            </tr>
                            <tr>
                                <td>
                                    <i>left arrow</i>
                                </td>
                                <td>Moves focus to the previous slide link.</td>
                            </tr>
                            <tr>
                                <td>
                                    <i>home</i>
                                </td>
                                <td>Moves focus to the first slide link.</td>
                            </tr>
                            <tr>
                                <td>
                                    <i>end</i>
                                </td>
                                <td>Moves focus to the last slide link.</td>
                            </tr>
                        </tbody>
                    </table>
                </div>

                <h5>Dependencies</h5>
                <p>None.</p>
            </TabPanel>

            <TabPanel header="Source">
                <a href="https://github.com/primefaces/primevue/tree/master/src/views/galleria" class="btn-viewsource" target="_blank" rel="noopener noreferrer">
                    <span>View on GitHub</span>
                </a>
                <pre v-code><code>
&lt;Galleria :value="images" :responsiveOptions="responsiveOptions" :numVisible="5" containerStyle="max-width: 640px"&gt;
    &lt;template #item="slotProps"&gt;
        &lt;img :src="slotProps.item.itemImageSrc" :alt="slotProps.item.alt" style="width: 100%" /&gt;
    &lt;/template&gt;
    &lt;template #thumbnail="slotProps"&gt;
        &lt;img :src="slotProps.item.thumbnailImageSrc" :alt="slotProps.item.alt" /&gt;
    &lt;/template&gt;
&lt;/Galleria&gt;

</code></pre>

                <pre v-code.script><code>
import PhotoService from '../../service/PhotoService';

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
        }
    },
    galleriaService: null,
	created() {
		this.galleriaService = new PhotoService();
	},
	mounted() {
		this.galleriaService.getImages().then(data => this.images = data);
    }
}

</code></pre>
            </TabPanel>
        </TabView>
    </div>
</template>
