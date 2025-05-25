<!-- <script setup>
import axios from 'axios';
import { onMounted, reactive } from 'vue';
import { useRoute, useRouter } from 'vue-router';

const route = useRoute();
const router = useRouter();

const postId = route.params.id;

const form = reactive({
    title: '',
    description: ''
})

onMounted( async () => {
    try {
        const response = await axios.get(`http://localhost/belajar-api/update-data.php/posts/${postId}`);
        form.title = response.data.title;
        form.description = response.data.description;
    } catch (error) {
        console.log("Error fetching post", response);
    }
})

const handleSubmit = async () => {
    const updatePost = {
        title: form.title,
        description: form.description
    }

    try {
        const response = await axios.put(`http://localhost:8080/posts/${postId}`, updatePost);
        router.push(`/posts/${response.data.id}`);
    } catch (error) {
        console.error("Error updating post", error);
    }
}

</script>
<template>
    <RouterLink :to="`/posts`" class="btn btn-green">Return to Posts</RouterLink>
    <div>
        <form @submit.prevent="handleSubmit">
            <label for="title">Title</label>
            <input 
            v-model="form.title" 
            type="text" 
            id="title" 
            name="title" 
            placeholder="Title">
            <label for="description">Description</label>
            <textarea 
            v-model="form.description" 
            id="description" 
            name="description">
            </textarea>
            <button type="submit" class="btn btn-green">Submit</button>
        </form>
    </div>
</template>

<style scoped>
.form-container {
    max-width: 400px;
    margin: 0 auto;
}

form {
    display: flex;
    flex-direction: column;
}

label {
    margin-bottom: 5px;
    font-weight: bold;
}

input, textarea, button {
    margin-bottom: 15px;
    padding: 10px;
    font-size: 1rem;
}

textarea {
    resize: vertical;
}

button {
    background-color: #da7cb5; 
    color: white; 
    border: none; 
    border-radius: 5px; 
    cursor: pointer; 
    transition: background-color 0.3s ease; 
}

button:hover {
    background-color: #da7cb5; 
}
</style> -->

<!-- Terbaru -->

<!-- <script setup>
import axios from "axios";
import { onMounted, reactive } from "vue";
import { useRoute, useRouter } from "vue-router";

const route = useRoute();
const router = useRouter();

const postId = route.params.id;

const form = reactive({
  student_no: "",
  student_name: "",
  student_class: "",
});

onMounted(async () => {
  try {
    const response = await axios.get(
      `http://localhost/belajar-api/get-all-data.php/?id=${postId}`
    );
    form.student_no = response.data.student_no;
    form.student_name = response.data.student_name;
    form.student_class = response.data.student_class;
  } catch (error) {
    console.log("Error fetching post", response);
  }
});

const handleSubmit = async () => {
  const updatePost = {
    student_id: postId,
    student_no: form.student_no,
    student_name: form.student_name,
    student_class: form.student_class,
  };

  try {
    const response = await axios.put(
      "http://localhost/belajar-api/update-data.php",
      updatePost
    );
    console.log(response);

    router.push(`/posts/${postId}}`);
  } catch (error) {
    console.error("Error updating post", error);
  }
};
</script>
<template>
  <RouterLink :to="`/posts`" class="btn btn-green">Return to Posts</RouterLink>
  <div>
    <form @submit.prevent="handleSubmit">
      <label for="no">NO</label>
      <input
        v-model="form.student_no"
        type="text"
        id="no"
        name="no"
        placeholder="NO"
      />

      <label for="name">Name</label>
      <input
        v-model="form.student_name"
        type="text"
        id="name"
        name="name"
        placeholder="Name"
      />

      <label for="class">Class</label>
      <input
        v-model="form.student_class"
        id="class"
        name="class"
        placeholder="Class"
      />
      <button type="submit" class="btn btn-green">Submit</button>
    </form>
  </div>
</template> -->

<script setup>
import axios from "axios";
import { onMounted, reactive } from "vue";
import { useRoute, useRouter } from "vue-router";

const route = useRoute();
const router = useRouter();

const postId = route.params.id;

const form = reactive({
  student_no: "",
  student_name: "",
  student_class: "",
});

onMounted(async () => {
  try {
    const response = await axios.get(
      `http://localhost/belajar-api/get-all-data.php/?id=${postId}`
    );
    form.student_no = response.data.student_no;
    form.student_name = response.data.student_name;
    form.student_class = response.data.student_class;
  } catch (error) {
    console.log("Error fetching post", error);
  }
});

const handleSubmit = async () => {
  const updatePost = {
    student_id: postId,
    student_no: form.student_no,
    student_name: form.student_name,
    student_class: form.student_class,
  };

  try {
    const response = await axios.put(
      "http://localhost/belajar-api/update-data.php",
      updatePost
    );
    console.log(response);

    router.push(`/posts/${postId}`);
  } catch (error) {
    console.error("Error updating post", error);
  }
};
</script>

<template>
  <div class="edit-post-container">
    <div class="content">
      <h1 class="title">Edit Post</h1>
      <form @submit.prevent="handleSubmit" class="form">
        <div class="form-group">
          <label for="no">Student No</label>
          <input
            v-model="form.student_no"
            type="text"
            id="no"
            name="no"
            placeholder="Enter Student No"
            class="input"
          />
        </div>

        <div class="form-group">
          <label for="name">Student Name</label>
          <input
            v-model="form.student_name"
            type="text"
            id="name"
            name="name"
            placeholder="Enter Student Name"
            class="input"
          />
        </div>

        <div class="form-group">
          <label for="class">Student Class</label>
          <input
            v-model="form.student_class"
            id="class"
            name="class"
            placeholder="Enter Student Class"
            class="input"
          />
        </div>

        <button type="submit" class="btn btn-green">Submit</button>
      </form>
      <RouterLink :to="`/posts`" class="btn btn-gray">Return to Posts</RouterLink>
    </div>
  </div>
</template>

<style scoped>
/* Container styling */
.edit-post-container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background: linear-gradient(135deg, #4caf50, #81c784);
  color: white;
  text-align: center;
}

/* Content styling */
.content {
  max-width: 600px;
  padding: 2rem;
  background: rgba(255, 255, 255, 0.1);
  border-radius: 1rem;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

/* Title styling */
.title {
  font-size: 2.5rem;
  font-weight: bold;
  margin-bottom: 1.5rem;
}

/* Form styling */
.form {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  margin-bottom: 2rem;
}

.form-group {
  text-align: left;
}

label {
  font-size: 1rem;
  font-weight: 600;
  margin-bottom: 0.5rem;
  display: block;
}

.input {
  width: 100%;
  padding: 0.75rem;
  border-radius: 0.5rem;
  border: none;
  font-size: 1rem;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.input:focus {
  outline: none;
  box-shadow: 0 0 0 2px #2e7d32;
}

/* Button styling */
.btn {
  padding: 0.75rem 1.5rem;
  border-radius: 0.5rem;
  font-size: 1rem;
  font-weight: 600;
  text-transform: uppercase;
  transition: all 0.3s ease;
  display: inline-block;
  text-decoration: none;
}

.btn-green {
  background-color: #2e7d32;
  color: white;
}

.btn-green:hover {
  background-color: #1b5e20;
  transform: scale(1.05);
}

.btn-gray {
  background-color: #757575;
  color: white;
}

.btn-gray:hover {
  background-color: #616161;
  transform: scale(1.05);
}
</style>