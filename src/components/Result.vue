<template>
    <h2 class="outPutMessage" :class="{success: isSuccess }"> {{ message }} </h2>
</template>

<script>
    export default {
        props: ['message', 'isSuccess'],
    }
</script>