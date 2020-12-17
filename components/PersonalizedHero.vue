<template>
  <div>
    <personalize :variations="variations" tracking-event-name="heroPersonalized">
      <template v-slot:loading>
        <personalized-hero-loading />
      </template>
    </personalize>
  </div>
</template>
<script>
import { Personalize } from '@uniformdev/optimize-tracker-vue';
import { contentfulOptimizeListReader } from '@uniformdev/optimize-tracker-contentful';
import PersonalizedHeroLoading from './PersonalizedHeroLoading';

export default {
  name: 'PersonalizedHero',
  components: {
    Personalize,
    PersonalizedHeroLoading,
  },
  props: {
    fields: {
      type: Object,
      default() {
        return {
          unfrmOptP13nList: {},
        };
      },
    },
    sys: {
      type: Object,
      default() {
        return {};
      },
    },
  },
  computed: {
    variations() {
      return contentfulOptimizeListReader(this.fields.unfrmOptP13nList);
    },
  },
};
</script>
