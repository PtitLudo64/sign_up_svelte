<script>
	import {texts} from './Texts.svelte';
	import LangSelect from "./LangSelect.svelte";

	let id=0;
	const changeAllTexts = (event) => {
		id=event.detail.globalTexts.id;
	}
    const changeMode = (e) => {
        const root = document.documentElement;
        if (document.querySelector('#mode').checked) { // Light mode
            root.style.setProperty('--clr-primary_400', 'var(--light-clr-primary_400)');
            root.style.setProperty('--clr-primary_700', 'var(--light-clr-primary_700)');
            root.style.setProperty('--clr-neutral', 'var(--light-clr-neutral');
            root.style.setProperty('--clr-accent_900', 'var(--light-clr-accent_900)');
            root.style.setProperty('--clr-accent_400', 'var(--light-clr-accent_400)');
            root.style.setProperty('--clr-accent_200', 'var(--light-clr-accent_200)');
            root.style.setProperty('--filter-grayscale', 'var(--light-filter-grayscale)');
        }
        else { // Dark mode
            root.style.setProperty('--clr-primary_400', 'var(--dark-clr-primary_400)');
            root.style.setProperty('--clr-primary_700', 'var(--dark-clr-primary_700)');
            root.style.setProperty('--clr-neutral', 'var(--dark-clr-neutral');
            root.style.setProperty('--clr-accent_900', 'var(--dark-clr-accent_900)');
            root.style.setProperty('--clr-accent_400', 'var(--dark-clr-accent_400)');
            root.style.setProperty('--clr-accent_200', 'var(--dark-clr-accent_200)');
            root.style.setProperty('--filter-grayscale', 'var(--dark-filter-grayscale)');
        }
    }
    //Browser Dark Mode?
    const isDarkMode = () =>
	    globalThis.matchMedia?.("(prefers-color-scheme:dark)").matches ?? false;

    window.onload = () => {
        if (!isDarkMode()) {
            document.querySelector('#mode').checked = true;
            changeMode();
        }
    }

</script>


<div id="leftSide">
	<img id="abstract" src="assets/img/abstract.png" alt="Formes en 3D">
	<div id="greetings">
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 36.57 37.05" id="C_logo">
            <path d="M 24.335 37.0461 C 31.492 34.2654 36.5652 27.3104 36.5652 19.1705 C 36.5652 8.58292 27.9823 0 17.3947 0 C 9.68964 0 3.0462 4.54572 0 11.1017 C 2.59131 9.33377 6.03668 8.26401 10.4772 8.26401 C 21.9012 8.26401 26.4132 12.824 27.0852 21.992 H 18.3972 C 18.0132 17.672 16.1892 15.176 10.6212 15.176 C 4.8132 15.176 2.31723 18.488 2.31723 25.064 C 2.31723 31.544 4.62122 34.904 10.3812 34.904 C 16.0932 34.904 18.1572 32.504 18.4932 27.848 H 27.2772 C 26.9668 31.8053 26.0685 34.8376 24.335 37.0461Z" fill="currentColor"/>
        </svg>
		<h1>{texts[id].h1}</h1>
	</div>
</div>
<div id="rightSide">


	<form action="">
        <div id="rightOfTheRight">
            <div id="modeInput">
                <label for="mode">
                    <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 21 21"><path fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2px" d="M11.5 3.5c1.328 0 2.57.37 3.628 1.012a6 6 0 0 0-.001 11.977A7 7 0 1 1 11.5 3.5z"/></svg>
                    <input type="checkbox" name="mode" id="mode" on:change={changeMode}>
                    <div id="frameMode">
                        <div id="sliderMode"></div>
                    </div>
                    <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 21 21"><g fill="none" fill-rule="evenodd" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2px"><path d="M10.5 14.5c2.219 0 4-1.763 4-3.982a4.003 4.003 0 0 0-4-4.018c-2.219 0-4 1.781-4 4c0 2.219 1.781 4 4 4zM4.136 4.136L5.55 5.55m9.9 9.9l1.414 1.414M1.5 10.5h2m14 0h2M4.135 16.863L5.55 15.45m9.899-9.9l1.414-1.415M10.5 19.5v-2m0-14v-2" opacity=".3"/><g transform="translate(-210 -1)"><path d="M220.5 2.5v2m6.5.5l-1.5 1.5"/><circle cx="220.5" cy="11.5" r="4"/><path d="m214 5l1.5 1.5m5 14v-2m6.5-.5l-1.5-1.5M214 18l1.5-1.5m-4-5h2m14 0h2"/></g></g></svg>
                </label>
            </div>

            <LangSelect on:chgTexts={changeAllTexts}/>
        </div>
		<h2>{texts[id].h2}</h2>
		<div id="social">
			<div id="google">
				<img src="assets/img/google_icon.svg" alt="Logo Google">
				<p>{texts[id].btn_google}</p>
			</div>
			<div id="facebook">
				<img src="assets/img/facebook_icon.svg" alt="Logo Facebook">
				<p>{texts[id].btn_facebook}</p>
			</div>
		</div>
		<h3>{texts[id].or}</h3>
		<div id="form">
			<input type="text" name="name" id="name" placeholder={texts[id].form_name}>
			<input type="email" name="mail" id="mail" placeholder={texts[id].form_mail}>
			<span id="pwdInput"><input type="password" name="pwd" id="pwd" placeholder={texts[id].form_pwd}></span>
			<input type="submit" value={texts[id].form_create} id="sub">
		</div>
		<p id="signIn">{texts[id].sign_in} <span>{texts[id].sign_in_span}</span></p>
	</form>
	
</div>

<style>
#leftSide {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: flex-start;
    position: relative;
    width: 100%;
    height: 20%;
    padding: 20px 20px 0 0;
    color: var(--clr-neutral);
}
#leftSide #greetings {
    padding-left: 1rem;
}
#leftSide #greetings #C_logo {
    width: 36px;
}
#leftSide #greetings h1 {
    font-size: clamp(1rem, 2vw, 1.5rem);
}
#leftSide #abstract {
    padding-top: 1vh;
    width: 20vh;
    z-index: 10;
    rotate: 15deg;
    transition: rotate 500ms;
    filter: var(--filter-grayscale);
}
#rightSide {
        background-color: var(--clr-neutral);
        width: 100%;
        height: 100%;
        border-radius: 36px 36px 0 0;
        position: relative;
        padding: 20px;
}
#rightSide #rightOfTheRight {
    margin: 0 auto;
    display: flex;
    flex-direction: column;
    align-items: flex-end;
    gap: 0.5rem;
}
#rightSide #rightOfTheRight #modeInput {
    width: 75px;
    color: var(--clr-primary_700);
}
#rightSide #rightOfTheRight #modeInput label {
    display: flex;
}
#rightSide #rightOfTheRight #modeInput label input[type='checkbox'] {
    visibility: hidden;
    width: 0;
}
#rightSide #rightOfTheRight #modeInput label #frameMode {
    width: 32px;
    border: 1px solid var(--clr-primary_400);
    border-radius: 100px;
    margin-right: 5px;
}
#rightSide #rightOfTheRight #modeInput label #frameMode #sliderMode {
    width: 16px;
    height: 100%;
    background-color: var(--clr-primary_700);
    border-radius: 50%;
    transition: transform 300ms ease;
}
#rightSide #rightOfTheRight #modeInput label input[type='checkbox']:checked ~ #frameMode #sliderMode {
    transform: translateX(100%);
}

#rightSide form {
    margin: 0 auto;
    margin-top: 10%;
}
#rightSide h2 {
    color: var(--clr-accent_900);
}
#rightSide form #social {
    margin-top: 2rem;
    display: flex;
    flex-wrap: wrap;
}
#rightSide form #social #google,
#rightSide form #social #facebook {
    min-width: 240px;
    margin: 0 auto;
    margin-bottom: 1rem;
    width: 48%;
    border: 1px solid var(--clr-accent_200);
    border-radius: 8px;
    display: flex;
    align-items: center;
    cursor: pointer;
    color: var(--clr-accent_900);
    transition: all 300ms ease;
}
#rightSide form #social #google img,
#rightSide form #social #facebook img {
    padding: 0.7rem;
    /* filter: var(--filter-grayscale); */
}
#rightSide form #social #google p,
#rightSide form #social #facebook p {
	font-size: 0.8rem;
    font-weight: 300;
}
#rightSide form #social #google:hover,
#rightSide form #social #facebook:hover {
    background-color: var(--clr-primary_700);
    color: var(--clr-neutral);
}
#rightSide form h3 {
    text-align: center;
    font-weight: 200;
    padding: 2rem 0;
    color: var(--clr-accent_900);
}
#rightSide #form {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    height: 30vh;
}
#rightSide #form input:not([type='submit']) {
    border: none;
    outline: none;
    border-bottom: 1px solid var(--clr-accent_200);
    padding: 0.5rem 0.2rem;
    background-color: var(--clr-neutral);
    color: var(--clr-accent_900);
}
#rightSide #form input:not([type='submit'])::placeholder {
    color: var(--clr-accent_900);
}
#rightSide #form input[type='submit'] {
    background-color: var(--clr-primary_700);
    color: var(--clr-neutral);
    font-weight: 700;
    border: none;
    padding: 0.5rem 0;
    border-radius: 5px;
    cursor: pointer;
    border: 2px solid var(--clr-primary_400);
    transition: 300ms ease;
}
#rightSide #form #pwdInput {
    width: 100%;
}
#rightSide #form #pwdInput input{
	width: 100%;
}
#rightSide #form input[type='submit']:hover {
    background-color: var(--clr-neutral);
    color: var(--clr-accent_900);
}
#rightSide #signIn {
	position: absolute;
    bottom: 1rem;
    color: var(--clr-accent_900);
    font-weight: 500;
    font-size: 0.9rem;
}
#rightSide #signIn span {
	color:var(--clr-primary_700);
	cursor: pointer;
}
#rightSide #signIn span:hover {
	color:var(--clr-primary_400);
}

@media (min-width: 720px) {
    #leftSide {
		max-width: 360px;
        height: 100% !important;
	}
	#leftSide #greetings {
        height: 20% !important;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
    }
	#leftSide #abstract {
        position: absolute;
        right: -60px;
        bottom: 0;
        rotate: 0deg !important;
        width: 100% !important;
    }
	#rightSide {
        min-width: 360px;
        max-width: calc(100% - 360px);
        border-radius: 36px 0 0 36px !important;
	}
	#rightSide form {
        width: 80%;
    }
}
</style>