<template>
  <div class="container">
    <div class="row">
      <div class="col col-md-6 offset-md-3">
        <base-card class="mt-5">
          <template #cardContent>
            <h3 class="card-title text-info">Real-time Character Counter</h3>
            <textarea
              name="character"
              id=""
              class="form-control mt-4"
              placeholder="Please write your text here..."
              v-model="character"
              @input="handleEnterChar"
              maxlength="50"
            ></textarea>
            <div class="card-footer d-flex justify-content-between mt-3">
              <span class="card-text"
                >Total Characters: <span class="text-info h3">{{ totalCharacter }}</span></span
              >
              <span class="card-text"
                >Remaining: <span class="text-danger h3">{{ remaining }}</span></span
              >
            </div>
          </template>
        </base-card>
      </div>
    </div>
  </div>
</template>

<script>
import BaseCard from './components/BaseCard.vue'
export default {
  data() {
    return {
      remaining: 50,
      totalCharacter: 0,
      character: null
    }
  },
  components: {
    BaseCard
  },
  methods: {
    handleEnterChar() {
      this.totalCharacter = this.character.length
    }
  },
  watch: {
    totalCharacter(newVal, oldVal) {
      if (newVal < oldVal) {
        this.remaining++
      } else if (newVal > oldVal) {
        this.remaining--
      }
    }
  }
}
</script>

<style lang="scss" scoped></style>
