<template>
  <div class="content__dough">
    <div class="sheet">
      <h2 class="title title--small sheet__title">Выберите тесто</h2>

      <div class="sheet__content dough">
        <label
          v-for="dough in items"
          :key="dough.id"
          :class="`dough__input dough__input--${dough.class}`"
        >
          <input
            type="radio"
            name="dought"
            :value="dough.value"
            class="visually-hidden"
            :checked="dough.value === modelValue"
            @input="emit('update:modelValue', dough.value)"
          />
          <img :src="getImage(dough.image)" :alt="dough.name" />
          <b>{{ dough.name }}</b>
          <span>{{ dough.description }}</span>
        </label>
      </div>
    </div>
  </div>
</template>

<script setup>
import { getImage } from "@/common/helpers/image";

defineProps({
  modelValue: {
    type: String,
    default: "",
  },
  items: {
    type: Array,
    default: () => [],
  },
});

const emit = defineEmits(["update:modelValue"]);
</script>

<style lang="scss" scoped>
@import "@/assets/scss/ds-system/ds.scss";
@import "@/assets/scss/mixins/mixins.scss";

* {
  box-sizing: border-box;
}

.content__dough {
  width: 527px;
  margin-top: 15px;
  margin-right: auto;
  margin-bottom: 15px;
}

.dough {
  &__input {
    position: relative;
    margin: 0 0 20px 0;
    padding-left: 50px;
    cursor: pointer;

    &:not(:last-child) {
      margin: 0 8% 20px 0;
    }

    &:hover {
      img {
        box-shadow: $shadow-regular;
      }
    }
  }

  input {
    &:checked + img {
      box-shadow: $shadow-large;
    }
  }

  img {
    @include p_center-v;
    width: 36px;
    height: 36px;
    transition: 0.3s;
    border-radius: 50%;
  }

  b {
    @include r-s16-h19;
  }

  span {
    @include l-s11-h13;
    display: block;
  }
}
</style>
