<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Simple Task Demo</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        /* Custom styles for Inter font and basic body styling */
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f0f4f8; /* Light blue-gray background */
            display: flex;
            justify-content: center;
            align-items: flex-start; /* Align items to the start to prevent vertical centering issues on shorter content */
            min-height: 100vh; /* Ensure body takes full viewport height */
            padding: 2rem; /* Add some padding around the content */
        }
        .container {
            max-width: 600px;
            width: 100%;
            background-color: #ffffff;
            padding: 2rem;
            border-radius: 1rem; /* More rounded corners */
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1); /* Softer, larger shadow */
        }
        .task-item {
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 0.75rem 1rem;
            margin-bottom: 0.75rem;
            background-color: #f8fafc; /* Lighter background for task items */
            border-radius: 0.5rem;
            border: 1px solid #e2e8f0; /* Subtle border */
        }
        .task-item.completed .description {
            text-decoration: line-through;
            color: #64748b; /* Gray out completed tasks */
        }
        .task-item .actions button {
            padding: 0.4rem 0.8rem;
            border-radius: 0.5rem;
            font-size: 0.875rem;
            transition: background-color 0.2s ease-in-out;
        }
        .task-item .actions .complete-btn {
            background-color: #3b82f6; /* Blue for complete */
            color: white;
        }
        .task-item .actions .complete-btn:hover {
            background-color: #2563eb;
        }
        .task-item .actions .delete-btn {
            background-color: #ef4444; /* Red for delete */
            color: white;
            margin-left: 0.5rem;
        }
        .task-item .actions .delete-btn:hover {
            background-color: #dc2626;
        }
        .form-input {
            border: 1px solid #cbd5e1;
            border-radius: 0.5rem;
            padding: 0.75rem 1rem;
            width: 100%;
            box-sizing: border-box; /* Include padding in element's total width and height */
        }
        .form-button {
            background-color: #10b981; /* Green for add button */
            color: white;
            padding: 0.75rem 1.5rem;
            border-radius: 0.5rem;
            font-weight: 600;
            transition: background-color 0.2s ease-in-out;
        }
        .form-button:hover {
            background-color: #059669;
        }
    </style>
</head>
<body class="antialiased">
    <div class="container">
        <h1 class="text-4xl font-extrabold text-center text-gray-900 mb-8">Simple Task Manager</h1>

        <form action="{{ url_for('add_task') }}" method="post" class="mb-8 flex flex-col sm:flex-row gap-4">
            <input type="text" name="task_description" placeholder="Add a new task..." required
                   class="form-input flex-grow focus:ring-2 focus:ring-blue-500 focus:border-transparent">
            <button type="submit" class="form-button">Add Task</button>
        </form>

        <div class="space-y-4">
            {% if tasks %}
                {% for task in tasks %}
                    <div class="task-item {% if task.completed %}completed{% endif %}">
                        <span class="description text-lg text-gray-800">{{ task.description }}</span>
                        <div class="actions flex items-center">
                            <a href="{{ url_for('complete_task', task_id=task.id) }}" class="complete-btn">
                                {% if task.completed %}
                                    Undo
                                {% else %}
                                    Complete
                                {% endif %}
                            </a>
                            <a href="{{ url_for('delete_task', task_id=task.id) }}" class="delete-btn">
                                Delete
                            </a>
                        </div>
                    </div>
                {% endfor %}
            {% else %}
                <p class="text-center text-gray-500 text-lg">No tasks yet! Add one above.</p>
            {% endif %}
        </div>
    </div>
</body>
</html>
