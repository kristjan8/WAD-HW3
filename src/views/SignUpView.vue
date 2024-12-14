<template>
  <div class="login">
    <HeaderCompo class="header"></HeaderCompo>
    <div class="signup-content">
      <!-- Left Sidebar -->
      <SidebarCompo class="left-sidebar"></SidebarCompo>

      <!-- Signup Form -->
      <div class="signup-form">
        <h2>Signup</h2>
        <form @submit.prevent="submitForm">
          <div class="form-group">
            <label for="email">Email:</label>
            <input
              type="email"
              id="email"
              v-model="email"
              placeholder="Enter your email"
              required
            />
            <p v-if="emailError" class="error">{{ emailError }}</p>
          </div>
          
          <div class="form-group">
            <label for="password">Password:</label>
            <input
              type="password"
              id="password"
              v-model="password"
              placeholder="Enter your password"
              required
            />
            <p v-if="passwordError" class="error">{{ passwordError }}</p>
          </div>

          <button type="submit" :disabled="!isPasswordValid">Signup</button>
        </form>
      </div>

      <!-- Right Sidebar -->
      <SidebarCompo class="right-sidebar"></SidebarCompo>
    </div>
    <FooterCompo class="footer"></FooterCompo>
  </div>
</template>

<script>
// Import the components you need
import FooterCompo from '@/components/FooterCompo.vue';
import HeaderCompo from '@/components/HeaderCompo.vue';
import SidebarCompo from '@/components/SidebarCompo.vue';

export default {
  name: 'SignupPage',
  components: {
    FooterCompo,
    HeaderCompo,
    SidebarCompo
  },
  data() {
    return {
      email: '',
      password: '',
      passwordError: ''
    };
  },
  computed: {
    // Ensure that the form can only be submitted if the password is valid
    isPasswordValid() {
      return this.passwordError === '';
    }
  },
  methods: {
    // Handle form submission
    submitForm() {
      if (this.isPasswordValid) {
        alert('Form submitted successfully!');
        // You can handle form submission, e.g., send data to an API.
      }
    },

    // Validate the password
    validatePassword() {
      const password = this.password;
      let errors = [];

      // Password validation checks
      if (password.length < 8 || password.length > 14) errors.push('Length must be between 8 and 15 characters.');
      if (!/[A-Z]/.test(password)) errors.push('Includes at least one uppercase alphabet character.');
      if ((password.match(/[a-z]/g) || []).length < 2) errors.push('Includes at least two lowercase alphabet characters.');
      if (!/\d/.test(password)) errors.push('Includes at least one numeric value.');
      if (!/^[A-Z]/.test(password)) errors.push('Password should start with an uppercase alphabet.');
      if (!/_/.test(password)) errors.push('Password should include the character “_”.');

      this.passwordError = errors.length ? 'The password is not valid - ' + errors.join(' ') : '';
    }
  },
  watch: {
    password() {
      // Validate the password whenever it changes
      this.validatePassword();
    }
  }
};
</script>

<style scoped>
/* Make the home container take the full height of the viewport */
.login {
  display: flex;
  flex-direction: column;
  height: 100vh; /* Full height of the viewport */
}

/* Ensure the main content area takes up available space */
.signup-content {
  display: flex;
  flex: 1; /* This makes the signup content area grow and fill available space */
  justify-content: center;
  align-items: flex-start;
  gap: 10px;
  margin-bottom: 20px; /* Add space for the footer */
  height: 100%; /* Ensure the content takes up full height */
}

/* Style for the form */
.signup-form {
  padding: 20px;
  border-radius: 8px;
  background-color: #f9f9f9;
  width: 100%;
  max-width: 400px;
}

/* Form group styling */
.form-group {
  margin-bottom: 15px;
}

/* Input styling */
input {
  width: 100%;
  padding: 10px;
  margin: 5px 0;
  border: 1px solid #ccc;
  border-radius: 4px;
}

/* Button styling */
button {
  padding: 10px;
  background-color: #4CAF50;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  width: 100%;
}

button:disabled {
  background-color: #ccc;
}

/* Error message styling */
.error {
  color: red;
  font-size: 12px;
}

/* Styling for footer and sidebars */
.footer, .left-sidebar, .right-sidebar {
  background: gray;
  margin: 10px;
  border-radius: 10px;
  padding: 20px;
}

/* Adjust layout for sidebars to fill the entire height */
.left-sidebar, .right-sidebar {
  flex: 1; /* Makes both sidebars take equal width */
  height: 92%; /* Ensures they take the full height of the viewport */
  display: flex;
  flex-direction: column;
  justify-content: flex-start; /* Align children to the top */
}

/* Adjust the layout for small screens */
@media all and (min-width: 600px) {
  .left-sidebar, .right-sidebar {
    flex: 1 0 0; /* These will take up equal width on larger screens */
  }
}

/* Adjust layout for medium screens and up */
@media all and (min-width: 800px) {
  .signup-content {
    flex: 3 0px; /* The content area will take up more space */
  }

  .left-sidebar {
    order: 0;
  }

  .signup-content {
    order: 2;
  }

  .right-sidebar {
    order: 3;
  }

  .footer {
    order: 4;
  }
}
</style>
