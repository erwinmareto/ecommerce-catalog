<template>
    <section class="container">
        <article class="card">

            <img class="card-img" :src="item?.image" alt="product image" />

            <div>
                <!-- Header -->
                <div>
                    <h1 :class="`title ${type}-text`">
                        {{ item?.title }}
                    </h1>
                    <div class="detail-section">
                        <p class="detail-text">{{ item?.category }}</p>
                        <div class="ratings-container">
                            <p class="detail-text">{{ item?.rating?.rate }}/5</p>
                            <div class="ratings-container" v-for="i in 5" :key="i">
                                <div
                                    :class="i <= item?.rating?.rate ? `filled-rating ${type}-bg` : `blank-rating ${type}-border`" />
                            </div>
                        </div>
                    </div>
                </div>


                <p class="description">{{ item?.description }}</p>


                <h1 :class="`price ${type}-text`">${{ item?.price }}</h1>


                <div class="card-footer">
                    <button :class="`buy-btn ${type}-bg`">Buy Now</button>
                    <button :class="`next-btn ${type}-text ${type}-border ${type}-next`" @click="next">Next
                        Product</button>
                </div>
            </div>
        </article>
    </section>
</template>

<script>
export default {
    props: ['item', 'next', 'type'],
    data() {
        return {
            textType: ''

        }
    }
}
</script>