# Performance metrics sample for Syncfusion .NET MAUI charts
This repository provides a quick-start example to analyze the loading performance of Syncfusion .NET MAUI charts. It includes three buttons to generate and load different amounts of data: 10K, 50K, and 100K, respectively. Upon generating the data, a timer starts and records the elapsed time once the series is rendered. Here utilized the FastLineSeries of SfCartesianChart. This example allows you to understand the time taken to load varying amounts of data in .NET MAUI charts.

## Steps to Run the Demo
**Step 1**: Clone or download the `dot_net_MAUI_Chart_Performance_Analysis` repository. 

**Step 2**: Open the solution in your preferred IDE. 

**Step 3**: Build and run the project. 

**Step 4**: Click on the buttons (Load 10K Data, Load 50K Data, Load 100K Data) to generate data. 
> Each button calls the LoadData method of the `DataGenerator` class, which builds a collection of Model objects (XValue, YValue). Values are randomized around a starting point to mimic realistic chart data. Based on the button clicked, [LoadData](https://github.com/SyncfusionExamples/dot_net_MAUI_Chart_Performance_Analysis/blob/3d3619a16c42dc8c914be5778050f793af9c5025/PerformanceMetrics/DataGenerator.cs#L71C9-L71C63) method generates `10000`, `50000`, or `100000` points, then binds them to the chart’s FastLineSeries to measure performance with different dataset sizes.

**Step 5**: Observe the elapsed time displayed in the label once the chart series is rendered.

## Output
<img width="1420" height="640" alt="image" src="https://github.com/user-attachments/assets/d0ce8ef0-8f08-4fd2-9d1e-8ae842bb5ad5" />

## Sample results
| Data Size | Time Taken (ms) |
|-----------|-----------------|
| 10k       | 38.05           |
| 50k       | 49.44           |
| 100k      | 67.94           |

### Specifications
| | |
|-----------|-----------------|
| .NET version               | .NET 10.0        |
| Syncfusion Charts version  | 31.2.15          |
| RAM      | 16 GB        |

### Guidelines to Optimize Performance in Syncfusion® MAUI Charts
1. **Disable Anti-Aliasing**
    - Description: Anti-aliasing smooths out jagged edges on lines but can increase rendering time.
    - Implementation: Set the [EnableAntiAliasing](https://help.syncfusion.com/cr/maui/Syncfusion.Maui.Charts.FastLineSeries.html#Syncfusion_Maui_Charts_FastLineSeries_EnableAntiAliasing) property to false.
    - Benefit: Disabling anti-aliasing reduces the rendering overhead, improving performance without significantly compromising visual quality.
    ```xml
    <chart:FastLineSeries  
                    ItemsSource="{Binding DataCollection}"
                    XBindingPath="Date"
                    YBindingPath="Value"
                    EnableAntiAliasing="False">
    </chart:FastLineSeries> 
    ```  

2.  **Reduce Stroke Width**
    - Description: Thicker lines require more rendering effort.
    - Implementation: Reduce the series [StrokeWidth](https://help.syncfusion.com/cr/maui/Syncfusion.Maui.Charts.XYDataSeries.html#Syncfusion_Maui_Charts_XYDataSeries_StrokeWidth) property to 1.
    - Benefit: Using a thinner line ensures faster rendering while retaining clarity in the chart.
    ```xml
    <chart:FastLineSeries 
                    ItemsSource="{Binding DataCollection}"
                    XBindingPath="Date"
                    StrokeWidth="1"
                    YBindingPath="Value">
    </chart:FastLineSeries> 
    ```

3. **Remove Data Labels**
    - Description: Displaying data labels for each data point can significantly slow down rendering, especially with large datasets.
    - Implementation: Avoid using data labels with the FastLine series. Set the [ShowDataLabels](https://help.syncfusion.com/cr/maui/Syncfusion.Maui.Charts.ChartSeries.html#Syncfusion_Maui_Charts_ChartSeries_ShowDataLabels) property to false.
    - Benefit: Eliminating data labels speeds up rendering and reduces visual clutter in high-density charts.
    ```xml
    <chart:FastLineSeries 
                    ItemsSource="{Binding DataCollection}"
                    XBindingPath="Date"
                    ShowDataLabels="False"
                    YBindingPath="Value">
    </chart:FastLineSeries> 
    ```

4. **Choose the Appropriate Axis**
    - Description: The choice of axis affects rendering performance. A CategoryAxis processes each label individually, which can be slower compared to NumericalAxis or DateTimeAxis.
    - Implementation: Use DateTimeAxis or NumericalAxis based on the data type.
    - Benefit: These axes streamline data processing, resulting in faster chart updates.
    ```xml
    <chart:SfCartesianChart.XAxes>
        <chart:DateTimeAxis>
        </chart:DateTimeAxis>
    </chart:SfCartesianChart.XAxes>

    <chart:SfCartesianChart.YAxes>
        <chart:NumericalAxis>
        </chart:NumericalAxis>
    </chart:SfCartesianChart.YAxes> 
    ```

By following these strategies, you can optimize the performance of the [FastLine Series](https://help.syncfusion.com/maui/cartesian-charts/fastline) in .NET MAUI Cartesian Chart Control.

## Troubleshooting

### Path Too Long Exception

If you are facing a "Path too long" exception when building this example project, close Visual Studio and rename the repository to a shorter name before building the project.
