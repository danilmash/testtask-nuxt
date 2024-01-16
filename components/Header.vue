<template lang="">
    <header class="header">
        <div class="header__wrapper wrapper">
            <NuxtLink to="/" class="header__logo-link logo-link">
                <img src="../assets/img/logo.svg" alt="DailyLangs">
            </NuxtLink >
            <div class='header__mobile-content'>
                <NuxtLink class="header__mobile-profile" to="/profile">
                            <img src="../assets/img/profile.svg" alt="Profile">
                </NuxtLink>
                <div class="header__burger-button burger-button">
                    <input class="burger-button__toggle" id="burger-toggle" type="checkbox" />
                    <label class='burger-button__container' for="burger-toggle">
                    <div class='burger-button__svg'></div>
                    </label>
                </div>
            </div>
            <nav class="header__navigation navigation">
                <ul class='navigation__link-list'>
                    <li class="navigation__list-item">
                        <NuxtLink to="/courses" class="navigation__link link">Курсы</NuxtLink >
                    </li>
                    <li class="navigation__list-item">
                        <NuxtLink to="/articles" class="navigation__link link">Статьи</NuxtLink >
                    </li>
                    <li class="navigation__list-item">
                        <NuxtLink to="/qanda" class="navigation__link link">Вопросы</NuxtLink >
                    </li>
                </ul>
                <div class="header__buttons-group">
                    <button class='header__search button'>
                        <img src="../assets/img/search.svg" alt="Search">
                    </button>
                    <NuxtLink class="header__desktop-profile" to="/profile">
                        <img src="../assets/img/profile.svg" alt="Profile">
                    </NuxtLink>
                    <select class="header__select header-select" value="ru">
                        <option class="header-select__option" value="en">EN</option>
                        <option class="header-select__option" value="ru">RU</option>
                    </select>
                </div>
            </nav>
            
            
            
        </div> 
    </header>
</template>
<script>
export default {};
</script>
<style lang="">
</style>