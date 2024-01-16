<template lang="">
    <main>
        <section class='courses'>
            <div class="courses__wrapper wrapper">
                <div class="courses__left-column">
                    <div class="courses__buttons">
                        <div ref="select" class="courses-filters__select courses-select" @click="handleOpenSelect">
                                <div class="courses-select__shown">
                                    <p class="courses-select__selected">{{ selectedLanguage }}</p>
                                    <img class="courses-select__arrow" src="../../assets/img/whitedown.svg" alt="">
                                </div>
                                <ul class="courses-select__options" @click='handleSelect' >
                                    <li class="courses-select__option">Английский</li>
                                    <li class="courses-select__option">Русский</li>
                                </ul>
                        </div>

                        <button class="courses__filters-open">
                            <img src="../../assets/img/filters.svg" alt="Filters">
                        </button>
                    </div>
                    <div class="courses__filters courses-filters">
                        <div class="courses-filters__slider-filter">
                            <h4 class="courses-filters__header">Продолжительность</h4>
                            <div class='courses-filters__inputs'>
                                <p class="courses-filters__text">От {{minSliderValue}} до {{maxSliderValue}} мес.</p>
                                <MinMaxSlider class="courses-filters__slider" :step="1" v-model:minValue="minSliderValue" v-model:maxValue="maxSliderValue"></MinMaxSlider>
                            </div>
                        </div>
                    
                        <div class="courses-filters__difficulty-filter">
                            <h4 class="courses-filters__header">Сложность</h4>
                            <div class='courses-filters__inputs'>
                                <div v-for="difficulty in difficultyList"  class='courses-filters__input-container'>
                                    <RadioInput  :value='difficulty.difficulty' :label="difficulty.name" :name="'difficultySelect'" :id='difficulty.difficulty'/>
                                </div>
                            </div>
                        </div>
                    
                        <div class="courses-filters__skills-filter">
                            <h4 class="courses-filters__header">Навыки</h4>
                            <div class='courses-filters__inputs'>
                                <div v-for="skill in skills" class="courses-filters__input">
                                    <Checkbox v-model="selectedSkills" :value="skill.skill" :label="skill.name" :id="skill.skill"/>
                                </div>
                            </div>
                        </div>
                        
                        
                    </div>
                </div>
                <div class="courses__right-column">
                    <h2 class='courses__header page-header'>Курсы <span class='language-highlight'>английского языка</span></h2>
                    <div class="courses__cards">
                        <div v-for="card in courseCards" class="courses__card course-card" :key="card.id" :style="{backgroundImage: `url(${card.background})`}">
                            <h3 class='course-card__header small-header'>{{card.course}}<br><span class="course-card__highlight">{{card.title}}</span></h3>
                            <p class="course-card__author">{{card.author}}</p>
                            <img class="course-card__language" src="../../assets/img/english-flag.svg" alt="">
                            <div class="course-card__price-container">
                                <p class="course-card__discount-price">{{card.price}}</p>
                                <p class="course-card__price">{{card.startPrice}}<span class='course-card__discount'>{{card.discount}}</span></p>
                            </div>
                            <a class="course-card__link link">Подробнее<img src="../../assets/img/arrow.svg" alt="arrow"></a>
                        </div>
                    </div>
                </div>
            </div>
        </section>
    </main>
</template> 


<script setup>
import { ref } from 'vue';
import cardBackground1 from '../../assets/img/card-background-1.png'
import cardBackground2 from '../../assets/img/card-background-2.png'
definePageMeta({
  layout: 'base'
})
let selectedLanguage = ref('Язык')
const select = ref(null)
const handleOpenSelect = (event) => {
    select.value.classList.toggle('opened')
}
const handleSelect = (event) => {
    selectedLanguage.value = event.target.innerHTML 
}

let minSliderValue = ref(1)
let maxSliderValue = ref(6)

const difficultyList = [
    {
        difficulty: 'every',
        name: "Для всех",
    },
    {
        difficulty: 'easy',
        name: "Для начинающих",
    },
    {
        difficulty: 'advanced',
        name: "Для продвинутых",
    }
]

const skills = [
    {
        skill: 'grammar',
        name: 'Грамматика',
    },
    {
        skill: 'vocabulary',
        name: 'Лексика',
    },
    {
        skill: 'syntax',
        name: 'Синтаксис',
    },
    {
        skill: 'phonetics',
        name: 'Фонетика',
    },
    {
        skill: 'punctuation',
        name: 'Пунктуация',
    },
]

const courseCards = [
    {
        course: 'Английский шаг за шагом:',
        title: 'Базовый уровень',
        author: 'Полина Коваленко',
        price: '2940',
        discount: '-51%',
        startPrice: '6000',
        languageFlag: 'english',
        background: cardBackground1,
        id: 1,
    },
    {
        course: 'Английский шаг за шагом:',
        title: 'Базовый уровень',
        author: 'Полина Коваленко',
        price: '2940',
        discount: '-51%',
        startPrice: '6000',
        languageFlag: 'english',
        background: cardBackground1,
        id: 1,
    },
    {
        course: 'Английский шаг за шагом:',
        title: 'Вводно-фонетический курс',
        author: 'Полина Коваленко',
        price: '2940',
        discount: '-51%',
        startPrice: '6000',
        languageFlag: 'english',
        background: cardBackground2,
        id: 1,
    },
    {
        course: 'Английский шаг за шагом:',
        title: 'Вводно-фонетический курс',
        author: 'Полина Коваленко',
        price: '2940',
        discount: '-51%',
        startPrice: '6000',
        languageFlag: 'english',
        background: cardBackground2,
        id: 1,
    }
]

const selectedSkills = ref([])
</script>
<style lang="scss">
    
</style>