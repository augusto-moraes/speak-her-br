<template>
  <div class="mt-5">
    <h2>
      {{ $t('faq.title') }}
    </h2>
    <br>
    <div
      v-for="q in questions"
      :key="q.question()"
    >
      <h3>{{ q.question() }}</h3>
      <p>{{ q.answer() }}</p>
    </div>
    <div>
      <h3>{{ $t('faq.correctionQ') }}</h3>
      <i18n
        path="faq.correctionA"
        tag="p"
      >
        <a
          :href="contact"
          target="_blank"
        >{{ contact }}</a>
      </i18n>
    </div>
  </div>
</template>


<script>

export default {
  data() {
    return {
      contact: 'https://tuttiq.me/contact',
      questions: [
        {
          question: () => this.$t('faq.whyQ'),
          answer: () => this.$t('faq.whyA'),
        },
        {
          question: () => this.$t('faq.qualifyQ'),
          answer: () => this.$t('faq.qualifyA'),
        },
        {
          question: () => this.$t('faq.obligationQ'),
          answer: () => this.$t('faq.obligationA'),
        },
        {
          question: () => this.$t('faq.freeQ'),
          answer: () => this.$t('faq.freeA'),
        },
        {
          question: () => this.$t('faq.whoQ'),
          answer: () => this.$t('faq.whoA'),
        },
      ],
    };
  },
};
</script>
