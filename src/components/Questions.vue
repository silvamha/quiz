/**
 * Component: Questions
 * Description: This component displays a set of questions and their corresponding answers.
 * Props:
 *   - questions: An array of objects representing the questions and their answers.
 *   - questionsAnswered: The number of questions that have been answered.
 * Emits:
 *   - question-answered: Event emitted when a question is answered. Passes a boolean value indicating whether the answer is correct.
 * Methods:
 *   - selectAnswer: Method called when an answer is selected. Emits the "question-answered" event.
 */
<template>
  <div class="questions-ctr">
    <div class="progress">
      <div
        class="bar"
        :style="{ width: `${(questionsAnswered / questions.length) * 100}%` }"
      ></div>
      <div class="status">
        {{ questionAnswered }} out of {{ questions.length }} questions answered
      </div>
    </div>
    <transition-group name="fade">
      <div
        class="single-question"
        v-for="(question, qi) in questions"
        :key="question.q"
        v-show="questionsAnswered === qi"
      >
        <div class="question">
          {{ question.q }}
        </div>
        <div class="answers">
          <div
            class="answer"
            v-for="answer in question.answers"
            :key="answer.text"
            @click.prevent="selectAnswer(answer.is_correct)"
          >
            {{ answer.text }}
          </div>
          <!-- <div class="answer">Sample Answer 2</div>
                <div class="answer">Sample Answer 3</div>
                <div class="answer">Sample Answer 4</div> -->
        </div>
      </div>
    </transition-group>
  </div>
</template>

<script>
export default {
  props: ["questions", "questionsAnswered"],
  emits: ["question-answered"],
  methods: {
    selectAnswer(is_correct) {
      this.$emit("question-answered", is_correct);
    },
  },
};
</script>

<style></style>
