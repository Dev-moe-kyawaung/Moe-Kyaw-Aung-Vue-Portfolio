<template>
  <div class="contact-page">
    <div class="container">
      <div class="contact-card">
        <h1 class="section-title">Get In Touch</h1>
        <p class="contact-subtitle">Let's discuss your next project</p>
        
        <form @submit.prevent="handleSubmit" class="contact-form">
          <div class="form-group">
            <input v-model="form.name" type="text" placeholder="Your Name" required>
          </div>
          <div class="form-group">
            <input v-model="form.email" type="email" placeholder="Your Email" required>
          </div>
          <div class="form-group">
            <textarea v-model="form.message" placeholder="Your Message" rows="5" required></textarea>
          </div>
          <button type="submit" class="submit-btn">Send Message</button>
        </form>

        <div v-if="success" class="success-msg">✓ Message sent successfully!</div>

        <div class="direct-contact">
          <p class="direct-label">Or contact directly:</p>
          <p class="direct-email">moekyawaung@programmer.net</p>
          <p class="direct-phone">+95 9 889 000 889</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, reactive } from 'vue'

const form = reactive({ name: '', email: '', message: '' })
const success = ref(false)

const handleSubmit = () => {
  success.value = true
  form.name = ''
  form.email = ''
  form.message = ''
  setTimeout(() => success.value = false, 4000)
}
</script>

<style scoped>
.contact-page {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 100px 20px;
}

.container { max-width: 600px; width: 100%; }

.contact-card {
  padding: 50px;
  background: var(--glass);
  border: 1px solid var(--glass-border);
  border-radius: 30px;
  backdrop-filter: blur(20px);
}

.section-title {
  font-family: 'Orbitron', monospace;
  font-size: 38px;
  margin-bottom: 10px;
  background: linear-gradient(135deg, var(--secondary), var(--accent));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.contact-subtitle {
  color: var(--text-muted);
  margin-bottom: 35px;
  font-size: 17px;
}

.contact-form { display: flex; flex-direction: column; gap: 20px; }

.form-group input,
.form-group textarea {
  width: 100%;
  padding: 15px;
  background: rgba(255,255,255,0.05);
  border: 1px solid rgba(255,255,255,0.2);
  border-radius: 12px;
  color: #fff;
  font-size: 16px;
  outline: none;
  font-family: inherit;
  transition: border-color 0.3s;
}

.form-group input:focus,
.form-group textarea:focus {
  border-color: var(--primary);
}

.submit-btn {
  width: 100%;
  padding: 18px;
  background: linear-gradient(135deg, var(--primary), var(--secondary));
  border: none;
  border-radius: 12px;
  color: #fff;
  font-weight: 700;
  font-size: 17px;
  cursor: pointer;
  transition: all 0.3s;
  text-transform: uppercase;
  letter-spacing: 1px;
}

.submit-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 10px 40px rgba(0, 240, 255, 0.4);
}

.success-msg {
  margin-top: 20px;
  padding: 15px;
  background: rgba(0, 255, 136, 0.1);
  border: 1px solid rgba(0, 255, 136, 0.3);
  border-radius: 10px;
  color: #00ff88;
  text-align: center;
}

.direct-contact {
  margin-top: 35px;
  text-align: center;
  padding-top: 25px;
  border-top: 1px solid var(--glass-border);
}

.direct-label {
  color: var(--text-muted);
  margin-bottom: 10px;
  font-size: 14px;
}

.direct-email {
  color: var(--primary);
  font-size: 18px;
  font-weight: 600;
  margin-bottom: 5px;
}

.direct-phone {
  color: var(--text-muted);
  font-size: 16px;
}
</style>
