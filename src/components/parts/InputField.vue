<template>
    <div class="input-style">
        <p>
            {{ props.msg }}
        </p>
        <input 
            type="text" 
            :id=props.id 
            :placeholder=props.placeholder 
            v-model=value 
            @input="inputedEmit"
        >
    </div>
</template>

<script setup>
// インポート
import { ref } from 'vue'

// 親から受け取る変数の定義
const props = defineProps({
  msg: {
    type: String,
    required: true
  },
  id: {
    type: String,
    required: true
  },
  placeholder: {
    type: String,
    default: "input here"
  },
  value: {
    type: String
  }
})

const value = ref(props.value)
const id = ref(props.id)

// Emit の定義
const emit = defineEmits(['inputedEvent'])

const inputedEmit = () => {
    emit('inputedEvent', {key:id.value, value:value.value})
}

</script>
