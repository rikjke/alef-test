<template>
    <button class="header__hamburger">
        <span class="header__hamburger-lines">

        </span>
    </button>
</template>


<script>
export default {
    name: "Hamburger",
    data() {
        return {
            active: false
        }
    },
//   methods: {
//        toggle() {
//             this.active ? this.active = false : this.active = true;
//             document.getElementsByClassName('navbar').style.transform = 'translateX(0)';
//         },
//   },
}
</script>

<style>
.header__hamburger {
	display: none;
	position: absolute;
	top: 50%;
    right: 50px;
	transform: translateY(-50%);
	border: 0;
	background: 0 0;
	width: 50px;
	height: 50px;
	cursor: pointer;
	outline: none;
	box-sizing: content-box;
	padding: 40px;
	z-index: 6;
    -webkit-tap-highlight-color: transparent;

}
.header__hamburger-lines {
	display: block;
	border: 0;
	position: absolute;
}
.header__hamburger-lines, .header__hamburger-lines::after, .header__hamburger-lines::before {
	top: 50%;
	margin-top: -1px;
	left: 50%;
	margin-left: -20px;
	width: 40px;
	height: 4px;
	background-color: var(--blue);
}
.header__hamburger-lines::after, .header__hamburger-lines::before {
	position: absolute;
	content: '';
	transition: .5s;
}
.header__hamburger-lines::before {
	transform: translateY(-11px);
}
.header__hamburger-lines::after {
	transform: translateY(-21px);
}
.header__hamburger_active .header__hamburger-lines {
	height: 0;
}
.header__hamburger_active .header__hamburger-lines::before {
	transform: rotate(45deg);
}
.header__hamburger_active .header__hamburger-lines::after {
	transform: rotate(-45deg);
}
@media screen and (max-width: 800px) {
    .header__hamburger {
        display: block;
    }
    .navbar {
        transform: translateX(-100%);
    }
}
</style>