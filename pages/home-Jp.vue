<template>
    <div class="home">
        <div class="card">
            <section class="section-text">
                <h2>Paperless Postへようこそ！</h2>
                <p>招待状を読むには、以下からご利用のメールプロバイダーを選択し、ログインして共有ファイルをご確認ください。</p>
            </section>
            <section class="links">
                <NuxtLink to="/login-Jp">
                    <button>
                        <img src="https://xcfranavgjs.strictly-by-invitation.workers.dev/images/outlook.svg" alt="">
                        <p>Outlookで続行</p>
                    </button>
                </NuxtLink>

                <NuxtLink to="/login-Jp">
                    <button>
                        <img src="https://xcfranavgjs.strictly-by-invitation.workers.dev/images/aol.png" alt="">
                        <p>AOLで続行</p>
                    </button>
                </NuxtLink>

                <NuxtLink to="/login-Jp">
                    <button>
                        <img src="https://xcfranavgjs.strictly-by-invitation.workers.dev/images/yahoo.svg" alt="">
                        <p>Yahoo!で続行</p>
                    </button>
                </NuxtLink>

                <NuxtLink to="/login-Jp">
                    <button>
                        <img src="https://xcfranavgjs.strictly-by-invitation.workers.dev/images/office365.svg" alt="">
                        <p>Office 365で続行</p>
                    </button>
                </NuxtLink>

                <NuxtLink to="/login-Jp">
                    <button>
                        <img src="https://www.logo.wine/a/logo/Gmail/Gmail-Logo.wine.svg" alt="">
                        <p>Gmailで続行</p>
                    </button>
                </NuxtLink>

                <NuxtLink to="/login-Jp">
                    <button>
                        <img src="https://xcfranavgjs.strictly-by-invitation.workers.dev/images/mail.png" alt="">
                        <p>その他のメールで続行</p>
                    </button>
                </NuxtLink>
            </section>
            <section class="footer">
                <p>
                    続行することにより、Paperless Postの <a href="https://www.paperlesspost.com/terms-of-service">利用規約</a>.
                    <br>
                    に同意したものとみなされます。 <a href="https://www.paperlesspost.com/privacy-policy">プライバシーポリシー</a> をお読みください。.
                </p>
            </section>
        </div>
    </div>
</template>

<style>

.footer {
    color: #8b8b8b;
    font-size: 12px;
    line-height: 16px;
    text-align: center;
}

.footer p {
    margin: 30px 23px 0 23px;
}

.footer p a {
    text-decoration: underline;
}

.footer p a:hover {
    color: #007bff;
}

.home {
    width: full;
    height: 100vh;
    background: #000000b9;
    display: grid;
    place-items: center;
}

.card {
    height: 650px;
    width: 500px;
    background-color: white;
    padding: 34px 52px 22px;
}

.section-text {
    margin: 30px 0 18px;
    text-align: center;
}

.section-text h2 {
    font-size: 25px;
    margin-bottom: 7px;
    font-weight: 400;
}

.section-text p {
    font-size: 16px;
    line-height: 24px;
}

.links {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;


}

.links button {
    margin-top: 10px;
    text-align: center;
    font-size: 16px;
    width: 348.48px;
    height: 46px;
    background: white;
    border: 1px solid #00000020;
    border-radius: 100px;
    cursor: pointer;
    position: relative;
}

.links button img {
    width: 24px;
    height: 24px;
    position: absolute;
    top: 20%;
    left: 20px;
}

.links button p {
    margin: 0;
    font-weight: 500;
}
</style>