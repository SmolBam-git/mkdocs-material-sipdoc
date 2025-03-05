<style>
    [data-md-component="palette"] {
        display: none !important;
    }

    /* [data-md-color-scheme="slate"] {
    --md-logo-image: url(/assets/logoCut_alt.png);
    } */

    .md-logo{
    --md-logo-image: url(/assets/logoCut_alt.png);
    }

    .md-ellipsis{
        color: white;
    }

    .md-tabs {
    background: transparent;
    color: white;
    display: block;
    line-height: 1.3;
    overflow: auto;
    width: 100%;
    z-index: 3;
    }

    .md-tabs__item--active{
        color: white;
    }

    .md-search{
        display: none !important;
    }

    body {
        position: relative;
        overflow: hidden;
    }

    .background-container {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        z-index: -1;
    }

    .background-image {
        position: absolute;
        width: 100%;
        height: 100%;
        background-size: cover;
        background-position: center;
        background-attachment: fixed;
        transition: opacity 1s ease-in-out;
    }

    .md-header,
    .md-main,
    .md-tabs,
    .md-footer,
    .md-footer-meta {
        background: transparent !important;
        box-shadow: none !important;
    }

    
    .md-footer__link,
    .md-footer__link--next{
        display: none !important;
    }

    .md-footer-nav{
        color: red
    }

    .md-sidebar--primary {
        display: none !important;
    }

    .welcome-container {
        border-radius: 5px;
        background-color: rgba(0, 0, 0, 0.36);
        backdrop-filter: blur(5px);
        max-width: 300px;
        margin-left: -100px;
        margin-right: 50px;
        margin-top: 0.25em;
        padding: 20px;
        color: white;
        text-align: left;
    }

    .welcome-container h1 {
        background: none;
        color: white;
        display: inline-block;
        font-weight: bold;
        border-radius: 5px;
    }

    .welcome-container p {
        color: white;
        display: inline-block;
        border-radius: 5px;
    }


    .welcome-button {
        display: inline-block;
        padding: 10px 30px;
        border-radius: 5px;
        text-decoration: none;
        font-weight: bold;
        color: white !important;
    }

    .start-button {
        background-color: #d42323;
    }

    .learn-more-button {
        background: transparent !important;
        border: none;
    }
</style>

<div class="background-container">
    <div class="background-image" id="bg1"></div>
    <div class="background-image" id="bg2" style="opacity: 0;"></div>
</div>

<div class="welcome-container">
    <h1>Bienvenido a SIP</h1>
    <div>
        <p>
        En esta página encontrarás toda la documentación de SIP, tu guía completa para entender y aprovechar cada función de la aplicación web. Explora cada sección para conocer a fondo sus características y cómo utilizarla de manera eficiente.
        </p>
        <a href="/inicio/" class="welcome-button start-button">Comenzar</a>
    </div>
</div>

<script>
    const images = ["biumedia.jpg", "adios.jpg", "muroAtlas.jpg", "arteExpuesto.jpg", "gazelle.jpg", "didi.jpg", "bienvenidaBG.jpg"];
    let index = 1;
    let intervalId;

    function updateBackground() {
        const bg1 = document.getElementById("bg1");
        const bg2 = document.getElementById("bg2");

        if (!bg1 || !bg2) return; // Evita errores si los elementos no están presentes aún

        const nextImage = `../../assets/fondos/${images[index]}`;

        const fadingIn = bg1.style.opacity == "1" ? bg2 : bg1;
        const fadingOut = bg1.style.opacity == "1" ? bg1 : bg2;

        fadingIn.style.backgroundImage = `url('${nextImage}')`;
        fadingIn.style.opacity = "1";
        fadingOut.style.opacity = "0";

        index = (index + 1) % images.length;
    }

    function startImageRotation() {
        const bg1 = document.getElementById("bg1");
        const bg2 = document.getElementById("bg2");

        if (!bg1 || !bg2) return;

        bg1.style.backgroundImage = `url('../../assets/fondos/${images[0]}')`;
        bg1.style.opacity = "1";
        bg2.style.opacity = "0";
        index = 1;

        if (!intervalId) {
            intervalId = setInterval(updateBackground, 10000);
        }
    }

    function resetAndStart() {
        setTimeout(startImageRotation, 100); // Pequeño retraso para asegurar que se cargue bien
    }

    document.addEventListener("visibilitychange", () => {
        if (!document.hidden) {
            resetAndStart();
        }
    });

    // Observa cambios en la carga de la página (para MkDocs)
    const observer = new MutationObserver((mutations) => {
        mutations.forEach((mutation) => {
            if (mutation.type === "childList") {
                if (document.querySelector(".background-container")) {
                    resetAndStart();
                }
            }
        });
    });

    observer.observe(document.body, { childList: true, subtree: true });

    document.addEventListener("DOMContentLoaded", resetAndStart);
</script>

