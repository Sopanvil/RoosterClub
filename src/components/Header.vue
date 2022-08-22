<template>
    <div class="header">
        <div class="container">
            <div class="header-main">
                <div class="header-main-logo">
                    <img src="../assets/img/main-logo.png" width="80">
                    <p class="logo-text">ROOSTERS <br/> GAMBLIBG CLUB</p>
                </div>
                <div class="header-main-links">
                    <router-link to="/" class="header-link">Home</router-link>
                    <router-link to="/roll-dice" class="header-link">Roll</router-link>
                    <router-link to="/" class="header-link">PigRoll</router-link>
                    <router-link to="/" class="header-link">Twitter</router-link>
                    <router-link to="/" class="header-link">Discord</router-link>
                    <router-link to="/" class="header-link">Cash</router-link>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {

}
</script>

<style lang="scss" scoped>
@import '/node_modules/modern-normalize/modern-normalize.css';

.header{
    .container{
        width: 100%;
        padding: 10px 0;
    }
    &-main {
        display: flex;
        align-items: center;
        justify-content: space-between;
        max-width: 1380px;
        margin: 0 auto;
        &-logo {
            display: flex;
            align-items: center;
            color: #f5f5f5;
            .logo-text {
                margin-left: 15px;
                font-weight: 600;
                font-size: 24px;
            }
        }
        &-links {
            display: flex;
            gap: 0 30px;
            font-size: 20px;
            .header-link {
                color: #f5f5f5;
                padding: 5px 15px;
                background: #00000000;
                border-radius: 5px;
                transition: 0.2s;
                
                &:hover{
                    background: #f1f1f123;
                }
            }
        }
    }
}
</style>