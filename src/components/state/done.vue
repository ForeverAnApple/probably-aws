<template>
    <div class="w-full">
        <div class="center">
            <div class="box">
                <h2 class="text-2xl text-center">
                    <span class="font-semibold">Probably</span>
                    AWS...?
                </h2>

                <p class="my-6">
                    You managed to guess <b>{{ props.correct }}</b> out of <b>{{ total }}</b> correctly.
                </p>

                <p v-if="(props.correct / total) < 0.35">
                    Somehow you managed to do worse than guessing at random. remarkable.
                </p>
                <p v-else-if="(props.correct / total) > 0.8">
                    How you managed to guess so many correctly is beyond my comprehension.
                </p>

                <button class="w-full button" @click="emit('state', 'PLAY')">Guess Again</button>
            </div>
        </div>
    </div>
</template>

<script setup>
import { computed } from "@vue/reactivity";

    const emit = defineEmits([ 'state' ]);

    let props = defineProps({
        correct: Number,
        wrong: Number,
    });

    let total = computed(() => props.correct + props.wrong);
</script>