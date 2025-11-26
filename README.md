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
[add img]

## Sample results
| Data Size | Time Taken (ms) |
|-----------|-----------------|
| 10k       | 38.05           |
| 50k       | 49.44           |
| 100k      | 67.94           |

## Troubleshooting

### Path Too Long Exception

If you are facing a "Path too long" exception when building this example project, close Visual Studio and rename the repository to a shorter name before building the project.
