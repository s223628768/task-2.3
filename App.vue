<template>
  <div>
    <!-- 1. Template Syntax -->
    <p>{{ message }}</p>
    <p v-html="rawHTML"></p>
    <button :id="buttonId">Click me</button>
    <p>{{ message + ' ' + name }}</p>

    <!-- 2. Methods -->
    <button @click="sayHello">Say Hello</button>

    <!-- 3. Reactivity Fundamentals [ref(), <script setup>] -->
    <p>{{ count }}</p>
    <button @click="increment">Increment</button>

    <!-- 4. Computed Properties -->
    <p>{{ fullName }}</p>

    <!-- 5. Class and Style Bindings -->
    <p :class="{'highlight': isHighlighted}">Class Binding</p>
    <p :style="{ color: textColor }">Style Binding</p>

    <!-- 6. List Rendering -->
    <ul>
      <li v-for="item in items" :key="item.id">{{ item.name }}</li>
      <li v-for="num in 5" :key="num">{{ num }}</li>
      <template v-for="item in itemsWithConditions" :key="item.id">
        <li v-if="item.show">{{ item.name }}</li>
      </template>
      <child-component v-for="comp in components" :key="comp.id" :name="comp.name" />
    </ul>

    <!-- 7. Event Handling: Listening to Events -->
    <button @click="handleClick">Click me</button>

    <!-- 8. Form Input Bindings -->
    <input type="text" v-model="textInput" />
    <input type="checkbox" v-model="isChecked" />
    <input type="radio" v-model="radioValue" />
    <select v-model="selectedOption">
      <option value="option1">Option 1</option>
      <option value="option2">Option 2</option>
    </select>
    <textarea v-model="textareaValue"></textarea>

    <!-- 9. Watchers -->
    <p>Watched Value: {{ watchedValue }}</p>

    <!-- 10. Components -->
    <child-component :prop-data="propData" @custom-event="handleCustomEvent">
      <template #slotName>{{ slotText }}</template>
    </child-component>

    <!-- 11. Router -->
    <router-link :to="{ name: 'about' }">About</router-link>
  </div>
</template>

<script>
export default {
  data() {
    return {
      // Template Syntax
      message: "Hello, Vue!",
      rawHTML: "<strong>Bold Text</strong>",
      buttonId: "my-button",
      name: "John",

      // Methods
      count: 0,

      // Computed Properties
      firstName: "John",
      lastName: "Doe",

      // Class and Style Bindings
      isHighlighted: true,
      textColor: "blue",

      // List Rendering
      items: [
        { id: 1, name: "Item 1" },
        { id: 2, name: "Item 2" },
        { id: 3, name: "Item 3" }
      ],
      itemsWithConditions: [
        { id: 1, name: "Item 1", show: true },
        { id: 2, name: "Item 2", show: false },
        { id: 3, name: "Item 3", show: true }
      ],
      components: [
        { id: 1, name: "Component A" },
        { id: 2, name: "Component B" }
      ],

      // Event Handling
      textInput: "",
      isChecked: false,
      radioValue: "",
      selectedOption: "",
      textareaValue: "",

      // Watchers
      watchedValue: "",

      // Components
      propData: "Data from parent",
      slotText: "Slot content"
    };
  },
  methods: {
    sayHello() {
      alert("Hello, Vue!");
    },
    increment() {
      this.count++;
    },
    handleClick() {
      alert("Button clicked!");
    },
    handleCustomEvent(payload) {
      console.log("Custom event received:", payload);
    }
  },
  computed: {
    fullName() {
      return `${this.firstName} ${this.lastName}`;
    }
  },
  watch: {
    watchedValue(newValue) {
      console.log("Watched value changed to:", newValue);
    }
  }
};
</script>
