<template>
    <div class="col-full" :class="$style.centered">
        <h1 :class="$style.headingLarge">Not found</h1>
        <p :class="$style.textLarge">We couldn't find, what you've been looking for.
            <router-link :to="{ name: 'Home' }">
                Why don't you go home?
            </router-link>
        </p>
    </div>
</template>

<script>
export default {
    
}
</script>

<style module>
.headingLarge {
    font-size: 100px;
}

.textLarge {
    font-size: 50px;
    font-weight: 100 
}

.centered {
    text-align: center
}
</style>


