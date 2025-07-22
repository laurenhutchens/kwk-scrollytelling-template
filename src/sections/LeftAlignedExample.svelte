<script>
// @ts-nocheck

    import * as Highcharts from "highcharts";
    import "highcharts/modules/exporting";
    import { Chart } from "@highcharts/svelte";
    import Scroller from "../lib/Scroller.svelte";
    import ArticleText from "../lib/ArticleText.svelte";

    // Chart data for Yavapai County and National
    let chartCategories = ["Yavapai County (AZ)", "National"];
    let chartData = [50700, 53400]; // $50.7K and $53.4K

    let options = {
        chart: {
            type: "column",
            backgroundColor: "#e3ff00",
            borderColor: "#007052",
            borderWidth: 5,
            borderRadius: 20,
        },
        title: {
            text: "Median Income for Black Households (2023)",
        },
        xAxis: {
            categories: chartCategories,
            title: { text: null },
        },
        yAxis: {
            min: 0,
            title: { text: "Income (USD)" },
            labels: {
                formatter: function() { return `$${(this.value/1000).toFixed(1)}K`; }
            }
        },
        series: [{
            name: "Median Income",
            data: chartData,
            colorByPoint: true,
            colors: ["#9a6226", "#564154"]
        }],
        legend: { enabled: false },
        tooltip: {
            pointFormatter: function() {
                return `<b>$${(this.y/1000).toFixed(1)}K</b>`;
            }
        }
    };
</script>

<Scroller layout="left">
  <div class="two-column">
    <div class="left-section-content">
      <div class="section-title">
        MEDIAN INCOME (2023)
      </div>
      <div class="multi-chart">
        <div class="chart-section">
          <Chart {options} highcharts={Highcharts} />
        </div>
      </div>
    </div>
  </div>
</Scroller>

<style>
.two-column {
  display: flex;
  flex-direction: row;
  align-items: flex-start;
  width: 100%;
  min-height: 100vh;
}

.left-section-content {
  max-width: 500px;
  flex: 0 0 500px;
  padding: 2rem;
  margin-top: -20rem; /* or adjust this value as needed */
}

.section-title {
  font-size: 1.5rem;
  font-weight: bold;
  text-align: center;
  margin-bottom: 2rem;
  line-height: 1.4;
}

.multi-chart {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 2rem;
}

.chart-section {
  width: 90%;
  text-align: center;
}

.left-scroll {
  flex: 1 1 0;
  height: 100vh;
  overflow-y: auto;
  margin: 0;
  max-width: none;
  padding: 0 2rem;
  background: transparent;
  border-radius: 0;
  box-shadow: none;
}
</style>
