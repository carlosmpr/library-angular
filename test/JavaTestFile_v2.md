---
  title: 'JavaTestFile.java'
  description: 'component description'
  pubDate: 'July 28, 2024'
  author: 'Carlos P'
  ---
  
  
  
  # JavaTestFile.java
  # BMI Chart Explanation

The provided code is a Java program that generates a BMI (Body Mass Index) trend chart using the JFreeChart library. Below is a breakdown of the code:

### Libraries Used
- **JFreeChart**: A popular Java library for creating a variety of charts including pie charts, bar charts, line charts, etc.
- **Swing**: Java's GUI toolkit for creating graphical user interfaces.

### Class: BMIChart
- **Extends ApplicationFrame**: The `BMIChart` class extends `ApplicationFrame`, which is a Swing container that represents the main window of the application.

### Constructor: BMIChart(String title)
- **Parameters**: `title` - The title of the BMI chart.
- **Operation**: Initializes the BMIChart by setting up the chart panel with the created dataset.
- **ChartPanel**: A panel that displays the chart.
- **Dimension**: Sets the preferred size of the chart panel.

### Method: createDataset()
- **Return Type**: XYSeriesCollection
- **Operation**: Creates a dataset containing BMI data for two persons (Person 1 and Person 2) over time.
- **XYSeries**: Represents a series of data points.
- **XYSeriesCollection**: A collection of XYSeries objects.

### Method: createChart(XYSeriesCollection dataset)
- **Parameters**: `dataset` - The dataset containing the BMI data.
- **Return Type**: JFreeChart
- **Operation**: Creates an XY line chart using the provided dataset.
- **ChartFactory.createXYLineChart**: Creates an XY line chart with specified parameters like title, axis labels, dataset, orientation, and rendering options.
- **XYPlot**: Represents the plot (graph area) of the chart.
- **XYLineAndShapeRenderer**: Renders lines and shapes for data points on the plot.

### Method: main(String[] args)
- **Operation**: Entry point of the program.
- **SwingUtilities.invokeLater()**: Executes the BMIChart creation on the Event Dispatch Thread to ensure thread safety.
- **BMIChart example**: Creates an instance of BMIChart with a title.
- **setSize(), setLocationRelativeTo(), setDefaultCloseOperation(), setVisible()**: Sets the size, position, close operation, and visibility of the BMIChart window.

### Example Usage
```java
public static void main(String[] args) {
    SwingUtilities.invokeLater(() -> {
        BMIChart example = new BMIChart("BMI Trend Chart");
        example.setSize(800, 600);
        example.setLocationRelativeTo(null);
        example.setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
        example.setVisible(true);
    });
}
```

### Conclusion
The code generates a BMI trend chart for two persons over time using JFreeChart in Java Swing. It demonstrates how to create a chart, set up a dataset, and display the chart in a Swing application.
  
  ## Component Code
  ```jsx
  import org.jfree.chart.ChartFactory;
import org.jfree.chart.ChartPanel;
import org.jfree.chart.JFreeChart;
import org.jfree.chart.plot.PlotOrientation;
import org.jfree.chart.plot.XYPlot;
import org.jfree.chart.renderer.xy.XYLineAndShapeRenderer;
import org.jfree.data.xy.XYSeries;
import org.jfree.data.xy.XYSeriesCollection;
import org.jfree.ui.ApplicationFrame;

import javax.swing.*;
import java.awt.*;

public class BMIChart extends ApplicationFrame {

    public BMIChart(String title) {
        super(title);
        JFreeChart xylineChart = createChart(createDataset());
        ChartPanel chartPanel = new ChartPanel(xylineChart);
        chartPanel.setPreferredSize(new Dimension(800, 600));
        setContentPane(chartPanel);
    }

    private XYSeriesCollection createDataset() {
        XYSeries series1 = new XYSeries("Person 1");
        series1.add(1, 22.5);
        series1.add(2, 23.0);
        series1.add(3, 22.8);
        series1.add(4, 23.5);

        XYSeries series2 = new XYSeries("Person 2");
        series2.add(1, 25.0);
        series2.add(2, 25.4);
        series2.add(3, 25.1);
        series2.add(4, 26.0);

        XYSeriesCollection dataset = new XYSeriesCollection();
        dataset.addSeries(series1);
        dataset.addSeries(series2);

        return dataset;
    }

    private JFreeChart createChart(XYSeriesCollection dataset) {
        JFreeChart chart = ChartFactory.createXYLineChart(
                "BMI Trends",
                "Time (Months)",
                "BMI",
                dataset,
                PlotOrientation.VERTICAL,
                true, true, false);

        XYPlot plot = chart.getXYPlot();
        XYLineAndShapeRenderer renderer = new XYLineAndShapeRenderer();
        plot.setRenderer(renderer);
        return chart;
    }

    public static void main(String[] args) {
        SwingUtilities.invokeLater(() -> {
            BMIChart example = new BMIChart("BMI Trend Chart");
            example.setSize(800, 600);
            example.setLocationRelativeTo(null);
            example.setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
            example.setVisible(true);
        });
    }
}
  ```
  