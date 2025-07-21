<script>
    import * as Highcharts from "highcharts";
    import "highcharts/modules/exporting";
    import { Chart } from "@highcharts/svelte";
    import Scroller from "../lib/Scroller.svelte";
    import ArticleText from "../lib/ArticleText.svelte";

    // Reusable chart options function
    let chartOptions = (chartTitle, chartData) => /** @type {any} */ ({
        chart: {
            type: "pie",
            spacing: [20, 20, 20, 20],
            height: 260
        },
        title: { text: null },
        plotOptions: {
            pie: {
                size: '200px',
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
        },
        series: [{
            type: "pie",
            name: chartTitle,
            data: chartData
        }]
    });

    // Example data (replace with your actual data)
    let chart1Data = [ { name: "A", y: 40 }, { name: "B", y: 60 } ];
    let chart2Data = [ { name: "C", y: 30 }, { name: "D", y: 70 } ];
    let chart3Data = [ { name: "E", y: 50 }, { name: "F", y: 50 } ];
    let chart4Data = [ { name: "G", y: 25 }, { name: "H", y: 75 } ];
</script>

<Scroller layout="right">
    {#snippet sticky()}
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
                    <Chart options={chartOptions("Median Home Value", chart1Data)} highcharts={Highcharts} />
                </div>
                <div class="chart-section">
                    <h3>Median Income for Black Households (2023)</h3>
                    <Chart options={chartOptions("Median Income", chart2Data)} highcharts={Highcharts} />
                </div>
                <div class="chart-section">
                    <h3>PPP Dollar Amount Received by Black Businesses per Black Capita (2020-2021)</h3>
                    <Chart options={chartOptions("PPP Dollars", chart3Data)} highcharts={Highcharts} />
                </div>
                <div class="chart-section">
                    <h3>Expected Annual Loss Per Capita Due to Natural Hazards (2022)</h3>
                    <Chart options={chartOptions("Expected Loss", chart4Data)} highcharts={Highcharts} />
                </div>
            </div>
        </div>
    {/snippet}

    {#snippet scrolly()}
        <ArticleText>Median home values have increased significantly in recent years...</ArticleText>
        <ArticleText>Black households in Yavapai County earn median incomes below national averages...</ArticleText>
        <ArticleText>PPP funding disparities highlight systemic inequities...</ArticleText>
        <ArticleText>Natural hazard losses pose financial risks in marginalized communities...</ArticleText>
    {/snippet}
</Scroller>

<style>
.right-section-content {
    border: 2px solid black;
    background-color: transparent;
    padding: 2rem;
    max-width: 1000px;
    margin: 0 auto;
    margin-top: 45rem;
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
