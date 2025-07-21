<script>
// @ts-nocheck

    import * as Highcharts from "highcharts";
    import "highcharts/modules/exporting";
    import { Chart } from "@highcharts/svelte";
    import Scroller from "../lib/Scroller.svelte";
    import ArticleText from "../lib/ArticleText.svelte";

    // Reusable chart options function
    let chartOptions = (chartType, chartTitle, chartData, categories=[]) => /** @type {any} */ ({
        chart: {
            type: chartType,
            spacing: [20, 20, 20, 20],
            height: 300
        },
        colors: chartTitle === 'Business Formations' ? ['#9a6226', '#564154'] : ['#9a6226', '#564154'],
        title: { text: null },
        xAxis: chartType === 'column' ? {
            categories: categories,
            crosshair: true
        } : undefined,
        yAxis: chartType === 'column' ? {
            min: 0,
            title: { text: null }
        } : undefined,
        plotOptions: chartType === 'pie' ? {
            pie: {
                size: '150px',
                innerSize: chartTitle === 'Business Formations' ? '60%' : '0%', 
                allowPointSelect: true,
                dataLabels: {
                    enabled: true,
                    format: "{point.percentage:.1f}%",
                    style: {
                        fontSize: "1.2em",
                        textOutline: "none",
                    }
                }
            }
        } : {
            column: {
                pointPadding: 0.2,
                borderWidth: 0
            }
        },
        series: [{
            type: chartType,
            name: chartTitle,
            data: chartData
        }]
    });

    // Example data (replace with your actual data)
    let chart1Categories = ["Yavapai County", "national"];
    let chart1Data = [ 
        { y: 403400, color: "#9a6226" },
        { y: 337000, color: "#564154" }
    ];
    let chart2Data = [
        { y: 1500, color: "#9a6226" },
        { y: 194585, color: "#564154" }
    ];
    let chart3Data = [
        { y: 1.2, color: "#9a6226" },
        { y: 13.7, color: "#564154" }
    ];
</script>

<Scroller layout="right">
    <div class="right-section-content">
        <div class="section-title">
            WEALTH INDICATORS FOR<br>
            <span class="legend">
                <span class="legend-square" style="background-color: #9a6226;"></span>
                Yavapai County /
                <span class="legend-square" style="background-color: #564154;"></span>
                national
            </span>
        </div>

        <div class="multi-chart">
            <div class="chart-section">
                <h3>MEDIAN HOME VALUE (2023)</h3>
                <Chart options={chartOptions("column", "Median Home Value", chart1Data, chart1Categories)} highcharts={Highcharts} />
            </div>
            <div class="chart-section">
                <h3>NUMBER OF BUSINESS FORMATIONS (2023)</h3>
                <Chart options={chartOptions("pie", "Business Formations", chart2Data)} highcharts={Highcharts} />
            </div>
            <div class="chart-section">
                <h3>BLACK POPULATION PERCENTAGE (2023)</h3>
                <Chart options={chartOptions("pie", "Population", chart3Data)} highcharts={Highcharts} />
            </div>
        </div>
    </div>

    <ArticleText>According to recent data, the median household income for Black households in Yavapai County is $47,250. This represents a 5% decrease from previous estimates of $47,386, but remains 20.7% higher than earlier levels of $41,935, reflecting some longer-term gains despite recent declines.</ArticleText>
    <ArticleText>In 2023, there were an estimated 194,585 Black or African American-owned businesses with paid employees across the United States, according to the U.S. Census Bureau. In Yavapai County, only about 1,500 Black-owned businesses were reported that year, reflecting a significant disparity compared to the national landscape.</ArticleText>
    <ArticleText>In 2023, the Black population made up approximately 13.7% of the total U.S. population. During the same year, in Yavapai County, Arizona, Black residents represented just 1% of the population, compared to the national average—highlighting a stark demographic contrast. </ArticleText>
</Scroller>

<style>
.right-section-content {
    border: 2px solid black;
    background-image: url('/public/sedonaYavapaiBackgroundImage.jpg');
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
    background-color: transparent; /* or remove if not needed */
    padding: 2rem;
    max-width: 1000px;
    margin: 0 auto;
    margin-top: 55rem;
}

.section-title {
    font-size: 1.5rem;
    font-weight: bold;
    text-align: center;
    margin-bottom: 2rem;
    line-height: 1.4;
}

.legend {
    font-size: 1rem;
}

.legend-square {
    display: inline-block;
    width: 12px;
    height: 12px;
    border-radius: 2px;
    margin: 0 5px;
}

.multi-chart {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 2rem;
}

.chart-section {
    width: 60%;
    text-align: center;
}

.chart-section h3 {
    font-size: 1rem;
    margin-bottom: 0.5rem;
}
</style>
