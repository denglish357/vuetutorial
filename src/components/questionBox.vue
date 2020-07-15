<template>
    <div class="question-box-container">
        <div>
            <b-jumbotron>
                <template v-slot:lead>
         {{ currentQuestion.question }}
</template>

    <hr class="my-4">


    <b-list-group>
  <b-list-group-item v-for="(answer, index) in answers" :key="index" @lick="selectAnswer(index)">
  {{answer}}
  </b-list-group-item >
</b-list-group>
    
    <b-button variant="primary" href="#">Submit</b-button>
    <b-button variant="success" href="#" @click="next">Next</b-button>
  </b-jumbotron>
</div>
    </div>
</template>


<script>
export default {
    props: {
        currentQuestion: Object,
        next: Function
    },
    computed: {
        answers() {
            let answers = [...this.currentQuestion.incorrect_answers]
            answers.push(this.currentQuestion.corrrect_answer)
            return answers
        }
    },
    methods: {
        selectAnswer(index) {
            console.log(index);
        }
    }
}
</script>


<style scoped>
.list-group {
    margin-bottom: 15px;
}

.btn {
    margin: 0 5px;
}
</style>