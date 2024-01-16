<template lang="">
    <div class="minmax-slider" ref="slider">
        <input class="min-slider"
            type="range"
            name="min"
            id="min"
            :min="min"
            :max="max"
            :value="minValue"
            :step="step"
            @input="({ target }) => (sliderMinValue = parseFloat(target.value))"
            />
        <input class="max-slider"
            type="range"
            name="max"
            id="max"
            :min="min"
            :max="max"
            :value="maxValue"
            :step="step"
            @input="({ target }) => (sliderMaxValue = parseFloat(target.value))"
        />
    </div>
</template>
<script setup>
import { ref, watchEffect } from "vue";

const props = defineProps({
    step: {
        type: Number,
        default: 1,
    },
    min: {
        type: Number,
        default: 1,
    },
    max: {
        type: Number,
        default: 6,
    },
    minValue: {
        type: Number,
        default: 1,
    },
    maxValue: {
        type: Number,
        default: 6,
    },
    adjustment: {
        type: Number,
        default: 1,
    }
})

const emit = defineEmits(['update:minValue', 'update:maxValue'])

const sliderMinValue = ref(props.minValue)
const sliderMaxValue = ref(props.maxValue)
const slider = ref(null)

const getPercent = (value, min, max) => {
    return (Math.abs(value - min) / (max - min)) * 100;
};

const setCSSProps = (width, left, right) => {
    if (100-right>left) {
        slider.value.style.setProperty("--sliderWidth", `${width}%`);
        slider.value.style.setProperty("--progressLeft", `${left}%`);
        slider.value.style.setProperty("--progressRight", `${right}%`);
    } else {
        slider.value.style.setProperty("--sliderWidth", `${width}%`);
        slider.value.style.setProperty("--progressLeft", `${100-right}%`);
        slider.value.style.setProperty("--progressRight", `${left}%`);
    }
    
};

const sliderDifference = computed(() => {
    if (sliderMinValue.value>sliderMaxValue.value) {
            return Math.abs(sliderMinValue.value - sliderMaxValue.value + props.adjustment);
        } else {
            return Math.abs(sliderMaxValue.value - sliderMinValue.value + props.adjustment);
        }
});

watchEffect(() => {
    if (slider.value) {
        if (sliderMinValue.value>sliderMaxValue.value) {
            emit('update:minValue', sliderMaxValue.value)
            emit('update:maxValue', sliderMinValue.value)
        } else {
            emit("update:minValue", sliderMinValue.value);
            emit("update:maxValue", sliderMaxValue.value);
        }


        const differencePercent = getPercent(sliderDifference.value, props.min, props.max);
        const leftPercent = getPercent(sliderMinValue.value, props.min, props.max);
        const rightPercent = 100 - getPercent(sliderMaxValue.value, props.min, props.max);
        setCSSProps(differencePercent, leftPercent, rightPercent);
    }
})

</script>