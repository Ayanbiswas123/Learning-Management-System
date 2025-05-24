# 🎓 LMS Frontend

This is the **frontend** of a Learning Management System (LMS) built with **React**, **Tailwind CSS**, and **CSS Modules**. It offers a modern, responsive, and secure platform for students and instructors to interact, manage courses, attend lectures, and more.

---

## 🚀 Features

- 🧑‍🎓 User and Admin Role-based Access
- 📚 Browse and manage courses
- 🧾 Secure authentication (JWT-based)
- 💳 Payment integration with success/failure handling
- 🎥 Lecture display and upload
- 📝 Course reviews and feedback system
- 👨‍🏫 Profile management
- 💻 Online Code Editor (like CodePen)
- 🔒 Protected routes with role checks
- 📱 Fully responsive UI

---

## 🛠️ Tech Stack

- **Framework:** React
- **Routing:** React Router
- **Styling:** Tailwind CSS, CSS Modules
- **State Management:** Redux Toolkit, Context API
- **API Calls:** Axios
- **Authentication:** JWT stored in cookies (via backend)
- **UI Components:** Chakra UI
- **Editor:** Monaco-based Code Editor
- **Others:** React Hook Form, React Player, Chart.js

---

## 📁 Folder Structure (Simplified)

```
src/
├── App.js
├── index.js
├── Pages/
│   ├── Course/
│   ├── Dashboard/
│   ├── Payments/
│   ├── Revievs/
│   └── User/
├── Components/
│   └── Auth/
├── CodeOnline/
│   └── components/
├── Redux/
│   ├── store.js
│   └── Slices/
│       ├── AuthSlice.js
│       ├── CourseSlice.js
│       ├── PaymentSlice.js
│       └── LectureSlice.js
```

---

## 🔗 Key Routes

| Path                     | Component           | Access      |
|--------------------------|---------------------|-------------|
| `/`                      | HomePage            | Public      |
| `/login`                 | Login               | Public      |
| `/signup`                | Signup              | Public      |
| `/courses`               | CourseList          | Public      |
| `/course/description`    | CourseDescription   | Public      |
| `/user/profile`          | Profile             | Protected   |
| `/user/editprofile`      | EditProfile         | Protected   |
| `/course/create`         | CreateCourse        | Admin Only  |
| `/course/update`         | UpdateCourse        | Admin Only  |
| `/course/displaylectures`| DisplayLecture      | Protected   |
| `/course/addlecture`     | AddLecture          | Admin Only  |
| `/checkout`              | Subscribe           | Protected   |
| `/checkout/success`      | CheckoutSuccess     | Protected   |
| `/checkout/fail`         | CheckoutFailure     | Protected   |
| `/code-online`           | CodeEditor          | Public      |
| `/addreview`             | SubmitReview        | Protected   |
| `/allreview`             | AllReviews          | Public      |
| `*`                      | NotFound            | Fallback    |

---

## 🧪 Setup & Run Instructions

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/lms-frontend.git
   cd lms-frontend
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Add environment variables**

   Create a `.env` file and include any necessary frontend env variables (e.g., API base URL):

   ```env
   REACT_APP_API_BASE_URL=https://your-backend-api.com/api
   ```

4. **Start the development server**
   ```bash
   npm start
   ```

---

## 📦 Redux Configuration

The Redux store is configured in `Redux/store.js`:

```js
import { configureStore } from "@reduxjs/toolkit";
import AuthSliceReducer from "./Slices/AuthSlice";
import courseSliceReducer from "./Slices/CourseSlice";
import paymentSliceReducer from "./Slices/PaymentSlice";
import lectureSliceReducer from "./Slices/LectureSlice";

const store = configureStore({
  reducer: {
    auth: AuthSliceReducer,
    course: courseSliceReducer,
    payments: paymentSliceReducer,
    lecture: lectureSliceReducer
  },
  devTools: true
});

export default store;
```

---

## 📄 License

This project is licensed under the MIT License - feel free to use and contribute.

---

## 🙌 Contributions

Feel free to fork, open issues, or submit pull requests to enhance the project. 💙

