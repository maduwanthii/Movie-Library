<template>
  <div class="reach">
    <div class="top">
      <div class="top-name">How to reach us</div>
    </div>

    <p class="small-description">Lorem ipsum dolor sit amet, consetetur.</p>

    <div class="reach-content">
      
      <form class="contact-form" @submit.prevent="handleSubmit">
        <div class="form-row">
          <div class="form-group">
            <label>First name *</label>
            <input
              type="text"
              v-model="form.firstName"
              :class="{ error: errors.firstName }"
            />
            <span class="error-message" v-if="errors.firstName">{{ errors.firstName }}</span>
          </div>
          <div class="form-group">
            <label>Last name *</label>
            <input
              type="text"
              v-model="form.lastName"
              :class="{ error: errors.lastName }"
            />
            <span class="error-message" v-if="errors.lastName">{{ errors.lastName }}</span>
          </div>
        </div>

        <div class="form-group">
          <label>Email *</label>
          <input
            type="email"
            v-model="form.email"
            :class="{ error: errors.email }"
          />
          <span class="error-message" v-if="errors.email">{{ errors.email }}</span>
        </div>

        <div class="form-group">
          <label>Telephone</label>
          <input type="tel" v-model="form.telephone" />
        </div>

        <div class="form-group">
          <label>Message *</label>
          <textarea
            rows="4"
            v-model="form.message"
            :class="{ error: errors.message }"
          ></textarea>
          <span class="error-message" v-if="errors.message">{{ errors.message }}</span>
        </div>

        <p class="required-note">* Required fields</p>

       <div class="form-footer">
  <label class="checkbox">
    <input type="checkbox" v-model="form.agree" />
    I agree to the <a href="#" target="_blank">Terms & Conditions</a>
  </label>

  <div class="submit-container">
    <button type="submit" class="submit-btn">SUBMIT</button>
  </div>
</div>
      </form>

    
      <div class="map-container">
        <iframe
          src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3036.402331182533!2d-3.636257984603628!3d40.44978247936026!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0xd422f0734b31d13%3A0xa3f4452558e095a0!2sC.%20Salvador%20de%20Madariaga%2C%201%2C%2028027%20Madrid%2C%20Spain!5e0!3m2!1sen!2slk!4v1692966528931!5m2!1sen!2slk"
          width="100%"
          height="100%"
          style="border:0;"
          allowfullscreen=""
          loading="lazy"
        ></iframe>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Reach",
  data() {
    return {
      form: {
        firstName: "",
        lastName: "",
        email: "",
        telephone: "",
        message: "",
        agree: false,
      },
      errors: {},
    };
  },
  methods: {
    handleSubmit() {
      this.errors = {};

      if (!this.form.firstName.trim()) {
        this.errors.firstName = "First name is required";
      }
      if (!this.form.lastName.trim()) {
        this.errors.lastName = "Last name is required";
      }
      if (!this.form.email.trim()) {
        this.errors.email = "Email is required";
      } else if (!/\S+@\S+\.\S+/.test(this.form.email)) {
        this.errors.email = "Invalid email format";
      }
      if (!this.form.message.trim()) {
        this.errors.message = "Message is required";
      }

      if (Object.keys(this.errors).length === 0) {
        alert(`
          First Name: ${this.form.firstName}
          Last Name: ${this.form.lastName}
          Email: ${this.form.email}
          Telephone: ${this.form.telephone}
          Message: ${this.form.message}
        `);
      }
    },
  },
};
</script>

<style scoped>

.submit-container {
  width: 100%;
  display: flex;
  justify-content: flex-end; /* Align button to right */
}

.reach {
  background: #000;
  color: white;
  padding: 0.5rem 1.5rem;
  font-size: 0.9rem;
  display: flex;
  flex-direction: column;
  gap: 1rem;
}



.top-name {
  font-family: 'Trebuchet MS', sans-serif;
  font-weight: bold;
  font-size: 25px;
  margin-top: 1rem;
  text-align: left;
  margin-bottom: 0rem;
  color: white; /* keep visible */
}


.small-description {
  font-family: 'Lucida Sans Unicode', sans-serif;
  font-size: 0.85rem;
  color: #ccc;
  text-align: left;
  margin-top: -0.5rem;
}

.reach-content {
  display: flex;
  gap: 2rem;
  margin-top: 1rem;
   text-align: left;
    font-family: 'Lucida Sans Unicode', sans-serif;

}

.contact-form {
  flex: 1;
  display: flex;
  flex-direction: column;
  gap: 1rem;
   font-family: 'Lucida Sans Unicode', sans-serif;
}

.map-container {
  flex: 2;
  height:410px;
  min-height: 550px;
}

.form-row {
  display: flex;
  gap: 1rem;
  flex-wrap: wrap;
}

.form-group {
  margin-bottom: 0.4rem;
  
  display: flex;
  flex-direction: column;
}

.form-group label {
  margin-bottom: 0.2rem;
  font-size: 0.75rem;
}


input,
textarea {
  padding: 0.5rem;
  border: 1px solid #444;
  border-radius: 4px;
  background: #1a1a1a;
  color: white;
}

input.error,
textarea.error {
  border-color: red;
}

.error-message {
  font-size: 0.75rem;
  color: red;
  margin-top: 0.2rem;
  
}

.required-note {
  font-size: 0.75rem;
  
}


.form-footer {
  display: flex;
  flex-direction: column; /* stack children vertically */
  align-items: flex-start; 
  gap: 0.5rem;
}


.checkbox {
  font-size: 0.79rem;
   font-family: 'Lucida Sans Unicode', sans-serif;
}

.checkbox a {
  color: #eceff3ff;
   text-decoration: underline;
}

.submit-btn {
  background: #BA8E23;
  color: white;
  border: none;
  padding: 0.6rem 1.5rem;
  border-radius: 4px;
  align-self: right;
   max-width: 500px; 
}

@media (max-width: 768px) {
  .reach-content {
    flex-direction: column;
  }
  .map-container {
    min-height: 400px;
    max-height: 300px;
  }

   .form-row {
    flex-direction: column; /* stack inputs vertically on mobile */
  }

  .form-group {
    flex: none; /* disable flex-grow to full width */
    width: 100%; /* full width */
  }

  .map-container iframe {
    min-height: 400px;
    max-height: 300px;
  }
   

  .submit-container {
    justify-content: center; /* Center the button */
  }
}
</style>
