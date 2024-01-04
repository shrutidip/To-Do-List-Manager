import javax.persistence.*;
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.data.jpa.repository.JpaRepository;
import org.springframework.stereotype.Repository;
import org.springframework.web.bind.annotation.*;
import java.util.List;
import java.util.Scanner;

@Entity
class Task {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    private String description;

    public Task() {}

    public Task(String description) {
        this.description = description;
    }

    // Getters and setters...
}

@Repository
interface TaskRepository extends JpaRepository<Task, Long> {
}

@RestController
@RequestMapping("/tasks")
class TaskController {
    private final TaskRepository taskRepository;

    public TaskController(TaskRepository taskRepository) {
        this.taskRepository = taskRepository;
    }

    @GetMapping
    public List<Task> getTasks() {
        return taskRepository.findAll();
    }

    @PostMapping
    public Task addTask(@RequestBody Task task) {
        return taskRepository.save(task);
    }

    @DeleteMapping("/{id}")
    public void deleteTask(@PathVariable Long id) {
        taskRepository.deleteById(id);
    }
}

@SpringBootApplication
public class ToDoListApplication {
    public static void main(String[] args) {
        SpringApplication.run(ToDoListApplication.class, args);

        Scanner scanner = new Scanner(System.in);

        while (true) {
            System.out.println("\nMenu:");
            System.out.println("1. Add Task");
            System.out.println("2. Delete Task");
            System.out.println("3. Display Tasks");
            System.out.println("4. Exit");
            System.out.print("Enter your choice: ");

            int choice = scanner.nextInt();
            scanner.nextLine(); // Consume newline character

            switch (choice) {
                case 1:
                    System.out.print("Enter task to add: ");
                    String taskDescription = scanner.nextLine();
                    Task task = new Task(taskDescription);
                    // Save task to the database using TaskRepository
                    // For simplicity, you can create an instance of TaskRepository here and use it
                    break;
                case 2:
                    System.out.print("Enter id of task to delete: ");
                    Long taskId = scanner.nextLong();
                    // Delete task from the database using TaskRepository
                    break;
                case 3:
                    // Display tasks from the database using TaskRepository
                    break;
                case 4:
                    System.out.println("Exiting...");
                    System.exit(0);
                default:
                    System.out.println("Invalid choice! Please try again.");
            }
        }
    }
}
