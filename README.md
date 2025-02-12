# 🛠️ Project Management App - React & Tailwind  

## 📚 Overview  

The **Project Management App** is a simple and efficient **React-based task and project management tool**. It allows users to **create projects, add tasks, and manage them effectively**. The app is built with **React 19**, utilizes **state management with hooks**, and employs **Tailwind CSS** for styling.    

---  

## 🚀 Features  

- **Project Management** - Add, delete, and manage projects effortlessly.  
- **Task Tracking** - Assign tasks to projects and manage them dynamically.  
- **React 19** - Uses the latest features, including **automatic ref forwarding**.  
- **Reusable Components** - Modular component structure for scalability.  
- **State Management with `useState`** - Simple yet effective state handling.  
- **Dynamic UI with Tailwind CSS** - Clean and responsive interface.  
- **Custom Modal Handling** - Built-in modal component for user interactions.  

---  

## 💻 Technologies Used  

- **React 19** - Modern React with hooks-based state management.  
- **Tailwind CSS** - Utility-first CSS framework for styling.  
- **Vite** - Fast development server and build tool.  
- **JavaScript (ES6+)** - Core logic and state handling.  
- **JSX** - Component-based UI rendering.  

---  

## 📸 Project Preview  

 ![image](https://github.com/user-attachments/assets/c01b89b0-e348-4ac1-ab0d-e2188e4b8642)
 ![image](https://github.com/user-attachments/assets/17f32fdd-542b-408a-ac68-52c385c0b431)

  ![image](https://github.com/user-attachments/assets/d8db5fcc-ff63-49a0-ab85-5839ab63a3d2)




---  

## 📂 Project Structure  

```  
project-management-app/  
├── src/  
│   ├── components/               # Reusable UI components  
│   │   ├── Button.js             # Reusable button component  
│   │   ├── Input.js              # Input field component (supports text and textarea)  
│   │   ├── Modal.js              # Reusable modal component  
│   │   ├── NewProject.js         # Form for adding new projects  
│   │   ├── NewTask.js            # Input field for adding tasks  
│   │   ├── NoProjectSelected.js  # UI when no project is selected  
│   │   ├── ProjectsSideBar.js    # Sidebar for selecting projects  
│   │   ├── SelectedProject.js    # Displays project details and tasks  
│   │   ├── Tasks.js              # Task management component  
│   ├── App.js                    # Main application component  
│   ├── index.js                  # Entry point of the app  
├── public/                        # Static assets (icons, images)  
├── package.json                   # Project dependencies and scripts  
├── tailwind.config.js              # Tailwind CSS configuration  
├── vite.config.js                  # Vite configuration for faster builds  
├── .gitignore                      # Files to ignore in Git  
└── README.md                       # Project documentation  
```  

---  

## 💾 Installation & Setup  

### 1️⃣ Clone the Repository  

```sh  
git clone https://github.com/Caiko/project-management-app.git  
cd project-management-app  
```  

### 2️⃣ Install Dependencies  

```sh  
npm install  
```  

### 3️⃣ Start the Development Server  

```sh  
npm run dev  
```  

Then open [**localhost:5173**](http://localhost:5173) (default for Vite) in your browser.  

---  

## ⚙️ Usage  

### **1. Creating a New Project**  
- Click **"Add Project"** in the sidebar.  
- Enter **title, description, and due date**, then click **Save**.  

### **2. Selecting and Viewing a Project**  
- Click on a project in the sidebar to view details and associated tasks.  

### **3. Managing Tasks**  
- Add tasks in the project details view.  
- Click **"Clear"** to remove a task.  

### **4. Deleting a Project**  
- Click **"Delete"** inside a project to remove it permanently.   

---  

## 🎯 Features Breakdown  

### **1. State Management with `useState()`**  
```jsx  
const [projectsState, setProjectsState] = useState({  
  selectedProjectId: undefined,  
  projects: [],  
  tasks: [],  
});  
```  
- Handles project selection, list of projects, and tasks.  
- Ensures changes update dynamically across components.  

### **2. Adding and Managing Projects Dynamically**  
```jsx  
function handleAddProject(projectData) {  
  setProjectsState((prevState) => {  
    const projectId = Math.random();  
    const newProject = { ...projectData, id: projectId };  

    return {  
      ...prevState,  
      selectedProjectId: undefined,  
      projects: [...prevState.projects, newProject],  
    };  
  });  
}  
```  
- Creates a new project with a unique ID.  
- Updates the UI dynamically by modifying state.  

### **3. Dynamic Task Management**  
```jsx  
function handleAddTask(text) {  
  setProjectsState((prevState) => {  
    const taskId = Math.random();  
    const newTask = { text, projectId: prevState.selectedProjectId, id: taskId };  

    return { ...prevState, tasks: [newTask, ...prevState.tasks] };  
  });  
}  
```  
- Assigns tasks to projects dynamically.  
- Preserves existing tasks while adding new ones.  

### **4. Modal for Validation Messages**  
```jsx  
<Modal ref={modal} buttonCaptionProp="Okay">  
  <h2 className="text-xl font-bold text-stone-700 mt-4 my-4">Invalid Input</h2>  
  <p className="text-stone-600 mb-4">Oops... Please fill all fields!</p>  
</Modal>  
```  
- Shows a warning when users forget to enter required data.  
- Uses `useImperativeHandle` for external control of the modal.  

