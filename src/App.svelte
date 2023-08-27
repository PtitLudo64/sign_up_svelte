<script>
	import {texts} from './Texts.svelte';
	import LangSelect from "./LangSelect.svelte";

	let id=0;
	const changeAllTexts= (event) => {
		id=event.detail.globalTexts.id;
	}
</script>


<div id="leftSide">
	<img id="abstract" src="assets/img/abstract.png" alt="Formes en 3D">
	<div id="greetings">
		<img id="C_logo" src="assets/img/C_logo.svg" alt="C logo">
		<h1>{texts[id].h1}</h1>
	</div>
</div>
<div id="rightSide">
	<LangSelect on:chgTexts={changeAllTexts}/>
	<form action="">
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
}
#leftSide #greetings {
    padding-left: 1rem;
}
#leftSide #greetings #C_logo {
    width: 36px;
}
#leftSide #greetings h1 {
    font-size: clamp(1rem, 2vw, 1.5rem);
    color: var(--clr-neutral);
}
#leftSide #abstract {
    padding-top: 1vh;
    width: 20vh;
    z-index: 10;
    rotate: 15deg;
    transition: rotate 500ms
}
#rightSide {
        background-color: var(--clr-neutral);
        width: 100%;
        height: 100%;
        border-radius: 36px 36px 0 0;
        position: relative;
        padding: 20px;
}
#rightSide form {
    margin: 0 auto;
    margin-top: 10%;
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
    border: 1px solid #ccc;
    border-radius: 8px;
    display: flex;
    align-items: center;
    cursor: pointer;
    transition: all 300ms ease;
}
#rightSide form #social #google img,
#rightSide form #social #facebook img {
    padding: 0.7rem;
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
    border-bottom: 1px solid #ccc;
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
    color: #333;
}
#rightSide #signIn {
	position: absolute;
    bottom: 1rem;
    color: #333;
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