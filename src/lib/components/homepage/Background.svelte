<div class="tech-background">
    <div class="tech-shape tech-shape-2"></div>
    <div class="halftone"></div>
    <div class="scanlines"></div>
</div>


<style>
  .tech-background {
  position: fixed;
  inset: 0;
  overflow: hidden;
  pointer-events: none;
  z-index: 0;

  background:
    radial-gradient(
      ellipse at 50% 45%,
      #ffffff 0%,
      #eeeeec 35%,
      #d8d8d5 70%,
      #c9c9c6 100%
    );

  filter: contrast(1.15);
}


  .tech-shape {
    position: absolute;
    width: 55vw;
    height: 75vh;

    background:
      radial-gradient(
        ellipse,
        rgba(10, 15, 25, 0.95) 0%,
        rgba(30, 35, 45, 0.75) 18%,
        rgba(80, 85, 90, 0.35) 38%,
        transparent 68%
      );

    filter: blur(28px);

    opacity: 0.8;

    mix-blend-mode: multiply;
  }


  .tech-shape-2 {
    right: -25%;
    top: 15%;

    width: 70vw;
    height: 90vh;

    transform:
      rotate(35deg)
      scaleY(1.4);

    border-radius: 50% 20% 60% 30%;

    background:
      radial-gradient(
        ellipse at 30% 50%,
        rgba(0, 0, 0, 0.9) 0%,
        rgba(30, 35, 45, 0.65) 15%,
        rgba(100, 105, 110, 0.25) 35%,
        transparent 65%
      );
  }
.scanlines {
    position: absolute;
    inset: 0;

    background:
      repeating-linear-gradient(
        to bottom,
        rgba(0, 0, 0, 0.018) 0px,
        rgba(0, 0, 0, 0.018) 1px,
        transparent 1px,
        transparent 4px
      );

    opacity: 0.65;

    mix-blend-mode: multiply;
  }

  .halftone {
    position: absolute;
    inset: 0;

    background-image:
      radial-gradient(
        rgba(0, 0, 0, 0.32) 0.7px,
        transparent 0.8px
      );

    background-size:8px 8px;

    opacity: 0.22;

    mix-blend-mode: multiply;
  }
</style>