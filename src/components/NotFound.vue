<template>
    <section class="container">
        <article id="not-found" class="card not-found-card">
            <div class="not-found-text">
                <h1>This product is unavailable to show</h1>
                <button class="not-found-btn" @click="next">Next Product</button>
            </div>
        </article>
    </section>
</template>

<script>
export default {
  props: ['next']
}
</script>