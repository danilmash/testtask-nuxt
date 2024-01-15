<template lang="">
    <footer class='footer'>
        <div class="footer__wrapper wrapper">
            <div class="footer__links">
                <div class="footer__policies-links">
                    <NuxtLink to="/policy/1" class="footer__policy-link">
                        Политика конфиденциальности 
                    </NuxtLink >
                    <NuxtLink to="/policy/2" class="footer__policy-link">
                        Условия пользования
                    </NuxtLink >
                </div>
                <NuxtLink to="/" class="footer__logo-link logo-link">
                    <img src="../assets/img/whitelogo.svg" alt="DailyLangs">
                </NuxtLink >
            </div>
            <p class='footer__rights-reserved'>© DailyLangs | 2023. Все права защищены</p>
        </div>
    </footer>
</template>
<script>
export default {
    
}
</script>
<style lang="">
    
</style>