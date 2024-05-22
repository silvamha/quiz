/**
 * Component for displaying the result of the quiz.
 *
 * @props {Array} results - An array of objects representing the possible quiz results.
 * @props {Number} totalCorrect - The total number of correct answers in the quiz.
 *
 * @computed {Number} resultIndex - The index of the result object that matches the totalCorrect value.
 * @returns {Number} - The index of the matching result object.
 */
<template>
    <div class="result">
        <div class="title">
            {{ results[resultIndex].title }}
        </div>
        <!-- <div class="score">
            You got {{ totalCorrect }} / {{ results[resultIndex] }}
        </div> -->
        <div class="desc">{{ results[resultIndex].desc }}.</div>
    </div>
</template>

<script>
export default {
    props: ["results", "totalCorrect"],
    computed: {
        resultIndex() {
            let index = 0;
            this.results.forEach((e, i) => {
                if (e.min <= this.totalCorrect && e.max >= this.totalCorrect) {
                    index = i;
                }
            });
            return index;
        },
    },
    methods: {},
};
</script>

<style></style>
