<template>
  <div>
    <h1>Enrollment System</h1>
    <form @submit.prevent="submitEnrollment">
      <label>
        Name:
        <input type="text" v-model="enrollment.name"/>
      </label>
      <label>
        Email:
        <input type="email" v-model="enrollment.email"/>
      </label>
      <label>
        Course:
        <select v-model="enrollment.course">
          <option v-for="course in courses" :key="course">{{ course }}</option>
        </select>
      </label>
      <button type="submit">Enroll</button>
    </form>
    <p v-if="message">{{ message }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      enrollment: {
        name: '',
        email: '',
        course: ''
      },
      courses: ['Web Development', 'Cross-Platform Development Technology', 'Mobile Development'],
      message: ''
    }
  },
  methods: {
    submitEnrollment() {
      if (this.enrollment.name && this.enrollment.email && this.enrollment.course) {
        this.message = 'Enrollment submitted successfully'
        this.enrollment = { name: '', email: '', course: '' }
      } else {
        this.message = 'Please fill in all fields'
      }
    }
  }
}
</script>
