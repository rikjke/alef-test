<template>
    <footer class="footer">
        <div class="footer__inner">
            <div class="footer__text">
                <h2>Успей купить</h2>
                <p>Подпишись и успей словить все акции</p>
            </div>

            <form class="footer__form">
                <div class="form-group">
                     <input data-validation="email" class="email-input" type="email" placeholder="Email">
                     <input class="subcribe" type="button" value="Подписаться">
                </div>
                <input class="checkbox" id="cb" type="checkbox">
                <label for="cb">Подписаться на новости</label>
            </form>
        </div>
    </footer>
</template>

<script>
export default {
    
}
</script>

<style scoped>
    .footer__inner {
        display: flex;
        justify-content: space-between;
    }
    .footer {
        padding: 85px 80px;
        max-width: 1280px;
        margin: 80px auto 0;
        background-color: black;
        background-color: var(--black);
        color: #fff;

    }
    .form-group {
        display: flex;
        align-items: center;
        margin-bottom: 25px;
    }
    input {
        padding: 22px 35px;
        border: 2px solid transparent;
        border-radius: 10px;
        margin-right: 15px;
    }
    input:last-child {
        margin-right: 0px;
    }
    input:focus {
        outline: none;
    }
    .email-input {
        width: 300px;
    }
    .subcribe {
        width: 250px;
        background-color: lightblue;
        background-color: var(--blue);
        color: #fff;
        font-weight: bold;
        transition: .4s ease all;
        cursor: pointer;
    }
    .subcribe:hover {
        border: 2px solid var(--blue);
        background-color: #fff;
        color: lightblue;
        color: var(--blue);
    }

    .checkbox {
        position: absolute;
        z-index: -1;
        opacity: 0;
    }
    .checkbox+label {
        display: inline-flex;
        align-items: center;
        user-select: none;
        cursor: pointer;
    }
    .checkbox+label::before {
        content: '';
        display: inline-block;
        width: 1em;
        height: 1em;
        flex-shrink: 0;
        flex-grow: 0;
        border: 1px solid var(--blue);
        border-radius: .25em;
        margin-right: .5em;
        transition: .4s ease;
        background-color: #fff;
        background-repeat: no-repeat;
        background-position: center center;
        background-size: 50% 50%;
    }
    .checkbox:checked+label::before {
        border-color: transparent;
        background-color: var(--blue);
        background-image: url('../assets/checkbox.svg');
        color: var(--blue);
    }
    .checkbox:not(:disabled):not(:checked)+label:hover::before {
        transform: scale(0.75)
    }
    @media screen and (max-width: 900px) {
        .footer__inner {
            flex-direction: column;
        }
        .footer__text {
            margin-bottom: 45px;
        }
        .form-group {
            flex-wrap: wrap;
        }
        .email-input {
            margin-bottom: 30px;
        }
    }
</style>