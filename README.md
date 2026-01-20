import java.util.ArrayList;
import java.util.Collections;

// @author ewheatley2027

// Priority interface
interface Priority {
    void setPriority(int priority);
    int getPriority();
}

// Complexity interface (from MiniQuiz)
interface Complexity {
    void setComplexity(int complexity);
    int getComplexity();
}

// Task class
class Task implements Priority, Complexity, Comparable<Task> {

    private String name;
    private int priority;
    private int complexity;

    // Constructor
    public Task(String name, int priority, int complexity) {
        this.name = name;
        this.priority = priority;
        this.complexity = complexity;
    }

    // Priority methods
    @Override
    public void setPriority(int priority) {
        this.priority = priority;
    }

    @Override
    public int getPriority() {
        return priority;
    }

    // Complexity methods
    @Override
    public void setComplexity(int complexity) {
        this.complexity = complexity;
    }

    @Override
    public int getComplexity() {
        return complexity;
    }

    // Compare tasks by priority first, then complexity
    @Override
    public int compareTo(Task other) {
        if (this.priority != other.priority) {
            return other.priority - this.priority; // higher priority first
        }
        return other.complexity - this.complexity; // higher complexity first
    }

    // For printing tasks
    @Override
    public String toString() {
        return name + " | Priority: " + priority + " | Complexity: " + complexity;
    }
}

// Driver class with main method
public class TaskDriver {
    public static void main(String[] args) {

        ArrayList<Task> tasks = new ArrayList<>();

        // Instantiate tasks
        tasks.add(new Task("Math Homework", 4, 6));
        tasks.add(new Task("English Essay", 5, 8));
        tasks.add(new Task("Laundry", 2, 2));
        tasks.add(new Task("Science Project", 5, 9));
        tasks.add(new Task("Study for Test", 4, 7));

        // Rank tasks
        Collections.sort(tasks);

        // Display results
        System.out.println("Ranked Task List:");
        for (Task t : tasks) {
            System.out.println(t);
        }
    }
}
