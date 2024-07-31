<script>
  import { onMount } from "svelte";
  import * as d3 from "d3";
  import scrollama from "scrollama";

  onMount(() => {
    const width = window.innerWidth;
    const height = window.innerHeight;
    const rectWidth = 90;
    const rectHeight = 90;
    const cols = 12;
    const rows = 8;
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
    console.log("script of scrollytelling");
    var main = document.querySelector("main");
    var scrolly = main.querySelector("#scrolly");
    var sticky = scrolly.querySelector(".sticky-thing");
    var article = scrolly.querySelector("article");
    var steps = article.querySelectorAll(".step");

    var scroller = scrollama();

    function handleStepEnter(response) {
      var el = response.element;
      console.log(el);
      steps.forEach((step) => step.classList.remove("is-active"));
      el.classList.add("is-active");
      //   sticky.querySelector("p").innerText = el.dataset.step;
    }

    function init() {
      scroller
        .setup({
          step: "#scrolly article .step",
          offset: 0.33,
          debug: true,
        })
        .onStepEnter(handleStepEnter);

      window.addEventListener("resize", scroller.resize);
    }
    init();
  });
</script>

<main>
  <section id="intro">
    <h1 style="margin-bottom: 300px;">How Same or Different Are We</h1>
    <!-- <p class="intro__dek">Start scrolling to see how it works.</p> -->
  </section>

  <section id="scrolly">
    <article>
      <div class="step" data-step="1">
        <p>
          Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do
          eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad
          minim veniam, quis nostrud exercitation ullamco laboris nisi ut
          aliquip ex ea commodo consequat.
        </p>
      </div>
      <div class="step" data-step="2">
        <p>
          Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do
          eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad
          minim veniam, quis nostrud exercitation ullamco laboris nisi ut
          aliquip ex ea commodo consequat.
        </p>
      </div>
      <div class="step" data-step="3">
        <p>
          Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do
          eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad
          minim veniam, quis nostrud exercitation ullamco laboris nisi ut
          aliquip ex ea commodo consequat.
        </p>
      </div>
      <div class="step" data-step="4">
        <p>
          Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do
          eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad
          minim veniam, quis nostrud exercitation ullamco laboris nisi ut
          aliquip ex ea commodo consequat.
        </p>
      </div>
    </article>

    <div class="sticky-thing" id="svg-title-container"></div>
  </section>

  <section id="outro"><div>this is outside the scrollying</div></section>
</main>

<style>
  #svg-title-container {
    width: 100vw;
    height: 100vh;
    overflow: hidden;
  }

  #scrolly {
    position: relative;
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    background-color: #f3f3f3;
    padding: 1rem;
  }

  #scrolly > * {
    -webkit-box-flex: 1;
    -ms-flex: 1;
    flex: 1;
  }

  article {
    position: relative;
    padding: 0 1rem;
    max-width: 20rem;
  }

  .sticky-thing {
    position: -webkit-sticky;
    position: sticky;
    width: 100%;
    margin: 0;
    /* background-color: #8a8a8a; */
    z-index: 0;
    top: 12.5vh;
    /* height: 75vh; */
    /* Center everything inside */
    display: flex;
    align-items: center;
    justify-content: center;
  }

  /* .sticky-thing p {
    padding: 1rem;
    font-size: 8rem;
    font-weight: 900;
    color: #fff;
  } */

  .step {
    margin: 0 auto 2rem auto;
    background-color: #3b3b3b;
    color: #fff;
  }

  .step:last-child {
    margin-bottom: 0;
  }

  .step.is-active {
    background-color: goldenrod;
    color: #3b3b3b;
  }

  .step p {
    text-align: center;
    padding: 1rem;
    font-size: 1.5rem;
  }
</style>
