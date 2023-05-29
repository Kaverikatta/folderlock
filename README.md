# folderlock
import java.util.Timer;
import java.util.TimerTask;

public class TimerExample {
    private static int seconds = 0;
    private static Timer timer;

    public static void main(String[] args) {
        startTimer();
        startStopwatch();
    }

    public static void startTimer() {
        timer = new Timer();
        TimerTask task = new TimerTask() {
            @Override
            public void run() {
                seconds++;
                System.out.println("Timer: " + seconds + " seconds");
            }
        };

        // Schedule the task to run every second
        timer.scheduleAtFixedRate(task, 1000, 1000);
    }

    public static void startStopwatch() {
        Timer stopwatchTimer = new Timer();
        TimerTask stopwatchTask = new TimerTask() {
            @Override
            public void run() {
                System.out.println("Stopwatch: " + seconds + " seconds");
            }
        };

        // Schedule the stopwatch task to run every second
        stopwatchTimer.scheduleAtFixedRate(stopwatchTask, 0, 1000);

        // Run the stopwatch for 5 seconds
        try {
            Thread.sleep(5000);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }

        // Cancel the stopwatch task after 5 seconds
        stopwatchTimer.cancel();
        System.out.println("Stopwatch stopped.");
    }
}
