<script>
  import { onMount } from "svelte";
  import * as d3 from "d3";

  onMount(() => {
    const width = window.innerWidth;
    const height = window.innerHeight;
    const rectWidth = 60;
    const rectHeight = 60;
    const cols = 10;
    const rows = 10;
    const spacing = 20;
    const gridWidth = cols * rectWidth + (cols - 1) * spacing;
    const gridHeight = rows * rectHeight + (rows - 1) * spacing;
    const startX = (width - gridWidth) / 2;
    const startY = (height - gridHeight) / 2;

    const svg = d3
      .select("#svg-title-container")
      .append("svg")
      .attr("width", "100%")
      .attr("height", "100%")
      .attr("viewBox", `0 0 ${width} ${height}`)
      .style("border", "1px solid black");

    for (let row = 0; row < rows; row++) {
      for (let col = 0; col < cols; col++) {
        svg
          .append("rect")
          .attr("width", rectWidth)
          .attr("height", rectHeight)
          .attr("x", startX + col * (rectWidth + spacing))
          .attr("y", startY + row * (rectHeight + spacing))
          .attr("fill", "none")
          .attr("stroke", "black");
      }
    }
  });
</script>

<div id="svg-title-container"></div>

<style>
  #svg-title-container {
    width: 100vw;
    height: 100vh;
    overflow: hidden;
  }
</style>
