<template>
  <div class="app">
    <!-- 1. Template Syntax -->
    <section>
      <h2>1. Text Interpolation:</h2>
      <p>{{ message }}</p>
    </section>

    <section>
      <h2>2. Raw HTML [v-html]:</h2>
      <p v-html="rawHtml"></p>
    </section>

    <section>
      <h2>3. Attribute Bindings [v-bind:id]:</h2>
      <div :id="dynamicId">Dynamic ID Element</div>
    </section>

    <section>
      <h2>4. JavaScript Expressions:</h2>
      <p>{{ 5 + 2 }} is equal to {{ name }}</p>
    </section>

    <!-- 2. Methods -->
    <section>
      <h2>5. Method Handling:</h2>
      <button @click="incrementCounter">Increment Counter</button>
    </section>

    <!-- 3. Reactivity Fundamentals -->
    <section>
      <h2>6. Reactivity Counter:</h2>
      <p>{{ counter }}</p>
    </section>

    <!-- 4. Computed Properties -->
    <section>
      <h2>7. Computed Property:</h2>
      <p>{{ computedProperty }}</p>
    </section>

    <!-- 5. Class and Style Bindings -->
    <section>
      <h2>8. Class Binding:</h2>
      <div :class="['element', { 'active': isActive, 'error': hasError }]">Dynamic Class</div>
    </section>

    <section>
      <h2>9. Inline Style Binding:</h2>
      <div :style="{ color: textColor, fontSize: fontSize }">Dynamic Style</div>
    </section>

    <!-- 6. List Rendering -->
    <section>
      <h2>10. List Rendering:</h2>
      <ul>
        <li v-for="(item, index) in items" :key="index">{{ item }}</li>
      </ul>
    </section>

    <!-- 7. Event Handling -->
    <section>
      <h2>11. Event Handling:</h2>
      <button @click="handleClickInline">Inline Event Handler</button>
      <button @click="handleClickMethod">Method Event Handler</button>
    </section>

    <!-- 8. Form Input Bindings -->
    <section>
      <h2>12. Form Input Bindings:</h2>
      <input type="text" v-model="inputValue" placeholder="Text Input" />
      <input type="checkbox" v-model="checkboxValue" />
      <div>
        <input type="radio" id="radio1" value="option1" v-model="radioValue" />
        <label for="radio1">Option 1</label>
      </div>
      <div>
        <input type="radio" id="radio2" value="option2" v-model="radioValue" />
        <label for="radio2">Option 2</label>
      </div>
      <select v-model="selectedOption">
        <option value="option1">Option 1</option>
        <option value="option2">Option 2</option>
      </select>
      <textarea v-model="textareaValue" placeholder="Textarea"></textarea>
    </section>

    <!-- 9. Watchers -->
    <section>
      <h2>13. Watchers:</h2>
      <input v-model="watchedValue" @input="handleWatchedValueChange" placeholder="Watched Input" />
    </section>

    <!-- 10. Components -->
    <section>
      <h2>14. Custom Component:</h2>
      <custom-component :propValue="customProp" @custom-event="handleCustomEvent">
        <template v-slot:slotName>
          Slot Content
        </template>
      </custom-component>
    </section>
  </div>
</template>

<script>
import { ref, computed, watch } from 'vue';

export default {
  data() {
    return {
      message: 'Hello Vue 3!',
      rawHtml: '<span style="color: red;">This is raw HTML</span>',
      dynamicId: 'my-element',
      counter: ref(0),
      isActive: true,
      hasError: false,
      textColor: 'blue',
      fontSize: '18px',
      items: ['Item 1', 'Item 2', 'Item 3'],
      inputValue: '',
      checkboxValue: false,
      radioValue: 'option1',
      selectedOption: 'option1',
      textareaValue: '',
      watchedValue: '',
      customProp: 'Custom Prop Value',
    };
  },
  methods: {
    incrementCounter() {
      this.counter++;
    },
    handleClickInline() {
      console.log('Inline Event Handler');
    },
    handleClickMethod() {
      console.log('Method Event Handler');
    },
    handleWatchedValueChange(newValue) {
      console.log('Watched Value Changed:', newValue);
    },
    handleCustomEvent(payload) {
      console.log('Custom Event:', payload);
    },
  },
  computed: {
    computedProperty() {
      return this.isActive ? 'Active' : 'Inactive';
    },
  },
  watch: {
    watchedValue(newValue) {
      console.log('Watched Value Changed:', newValue);
    },
  },
};
</script>

<style scoped>
/* Add your component-specific styles here */
.app {
  font-family: Arial, sans-serif;
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
}

section {
  margin-bottom: 20px;
}

h2 {
  font-size: 1.5rem;
  margin-bottom: 10px;
}

.element {
  padding: 10px;
  border: 1px solid #ccc;
}

.active {
  background-color: lightgreen;
}

.error {
  color: red;
}
</style>
