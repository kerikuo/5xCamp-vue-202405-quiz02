<script setup>
import { ref, defineProps, defineEmits } from 'vue';

// 接收從父元件傳遞的屬性
const props = defineProps({
    modelValue: String
});

// 發送事件
const emit = defineEmits(['update:modelValue']);

// 建立本地的搜尋文字
const localSearchText = ref(props.modelValue);

// 監聽輸入變化並觸發父元件更新
const updateSearchText = () => {
    emit('update:modelValue', localSearchText.value);
};
</script>
<template>
    <p>
        站點名稱搜尋: <input type="text" v-model="localSearchText" @input="updateSearchText">
    </p>
</template>