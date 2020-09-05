<template>
            <div>
      <Navigation></Navigation>
        <mdb-container>
    <mdb-line-chart
      :data="lineChartData"
      :options="lineChartOptions"
      :width="800"
      :height="500"
    ></mdb-line-chart>
  </mdb-container>
    </div>
    
</template>

<script>
  import { mdbLineChart, mdbContainer } from "mdbvue";
  import Navigation from '@/components/Navigation'
  export default {
    name: "ChartPage",
    components: {
      mdbLineChart,
      mdbContainer,
      Navigation
    },
    created(){
      // this.datasets[0].data=  [5, 7, 6, 81, 56, 55, 40]
      console.log(JSON.parse(localStorage.getItem("GraphData")));
      for(let i=0;i<7;i++){
          this.lineChartData.datasets[0]['data'].push(JSON.parse(localStorage.getItem("GraphData"))[i].count);
      }
      for(let i=7;i<14;i++){
        this.lineChartData.datasets[1]['data'].push(JSON.parse(localStorage.getItem("GraphData"))[i].count);
      }
      //this.lineChartData.datasets[0]['data']=[5, 7, 6, 81, 56, 55, 40];
      //this.lineChartData.datasets[0]['data'].push(45);
       console.log(this.lineChartData.datasets[0]['data']);
       console.log(this.lineChartData.datasets[1]['data']);
    },
    data() {
      return {
        lineChartData: {
          labels: [
            "January",
            "February",
            "March",
            "April",
            "May",
            "June",
            "July"
          ],
          datasets: [
            {
              label: "Death Case",
              backgroundColor: "rgba(255, 99, 132, 0.1)",
              borderColor: "rgba(255, 99, 132, 1)",
              borderWidth: 0.7,
              data:[]
            },
            {
              label: "Alive",
              backgroundColor: "rgba(151,187,205,0.2)",
              borderColor: "rgba(151,187,205,1)",
              borderWidth: 0.8,
              data: []
            }
          ]
        },
        lineChartOptions: {
          responsive: false,
          maintainAspectRatio: false,
          scales: {
            xAxes: [
              {
                gridLines: {
                  display: true,
                  color: "rgba(0, 0, 0, 0.1)"
                }
              }
            ],
            yAxes: [
              {
                gridLines: {
                  display: true,
                  color: "rgba(0, 0, 0, 0.1)"
                }
              }
            ]
          }
        }
      };
    }
  };
</script>
<style>

</style>