<script setup></script>

<template>
  <div class="licencePlate">
    <div class="border"><div></div></div>

    <!-- <img src="/img/reference1.png" alt="plate reference" class="reference" /> -->
    <!-- <img src="/img/reference2.png" alt="plate reference" class="reference" /> -->
    <!-- <img src="/img/reference3.png" alt="plate reference" class="reference" /> -->
    <div class="screws">
      <div>
        <div class="seal">
          <div>
            <span>東</span>
          </div>
        </div>
      </div>
      <div>
        <div></div>
      </div>
    </div>
    <div class="topRow">
      <!-- <p>品川</p> -->
      <!-- <p class="office">富士山</p> -->
      <p class="office">岐阜</p>
      <!-- <p class="classification">33</p> -->
      <!-- <p class="classification wide">３３</p> -->
      <p class="classification">330</p>
    </div>
    <div class="bottomRow">
      <!-- <p class="kana"><span>ぬ</span></p> -->
      <p class="kana"><span>は</span></p>
      <div class="serial">
        <div class="number"><span>3</span></div>
        <div class="number"><span>6</span></div>
        <div class="separator"><span></span></div>
        <div class="number"><span>8</span></div>
        <div class="number"><span>0</span></div>
      </div>
      <!-- <div class="serial">
        <div class="number dot"><span></span></div>
        <div class="number dot"><span></span></div>
        <div class="separator" style="opacity: 0;"></div>
        <div class="number dot"><span></span></div>
        <div class="number"><span>8</span></div>
      </div> -->
      <!-- <div class="serial">
        <div class="number"><span>7</span></div>
        <div class="number"><span>7</span></div>
        <div class="separator"><span></span></div>
        <div class="number"><span>7</span></div>
        <div class="number"><span>7</span></div>
      </div> -->
    </div>
  </div>
</template>

<style lang="css" scoped>
.licencePlate {
  position: relative;
  box-shadow: 5mm 10mm 25mm black;
  border: 2px solid rgba(0 0 0 / 20%);
  border-radius: 10mm;
  background-color: #d7d8d5;
  aspect-ratio: 2;
  width: 330mm;
  height: 165mm;
  color: #194a17;

  .border {
    position: absolute;
    inset: 3mm;
    box-shadow:
      inset 1mm 1mm 2mm rgba(255, 255, 255, 0.5),
      inset -1mm -1mm 2mm rgba(0, 0, 0, 0.25),
      1mm 1mm 1mm rgba(0, 0, 0, 0.2),
      -1mm -1mm 1mm rgba(255, 255, 255, 0.5);
    border-radius: 7mm;
    background-color: #d7d8d5;

    > div {
      position: absolute;
      inset: 4mm;
      box-shadow:
        1mm 1mm 2mm rgba(255, 255, 255, 0.5),
        -1mm -1mm 2mm rgba(0, 0, 0, 0.1),
        inset 1mm 1mm 1mm rgba(0, 0, 0, 0.1),
        inset -1mm -1mm 1mm rgba(255, 255, 255, 0.5);
      border-radius: 3mm;
      background-color: #d7d8d5;
    }
  }

  .reference {
    position: absolute;
    opacity: 0.25;
    inset: 0;
    width: 100%;
    height: 100%;
  }

  .screws {
    /* background-color: blue; */
    display: flex;
    position: relative;
    top: 25mm;
    justify-content: space-between;
    align-items: center;
    z-index: 1;
    margin: auto;
    width: 210mm;

    > * {
      display: grid;
      position: relative;
      place-items: center;

      > * {
        position: absolute;
        border-radius: 100%;
        background-color: black;
        width: 8mm;
        height: 8mm;
      }

      .seal {
        display: grid;
        place-items: center;
        box-shadow:
          inset -1mm -1mm 3mm rgba(0, 0, 0, 0.4),
          2mm 2mm 4mm rgba(0, 0, 0, 0.2),
          inset 0 0 1mm 1mm rgba(0, 0, 0, 0.4),
          inset -1mm -1mm 2mm 1mm rgba(0, 0, 0, 0.25),
          inset 1mm 1mm 1mm 2mm white;
        /* background: linear-gradient(to bottom right, white 0%, grey); */
        background-image: conic-gradient(
          from 320deg at 50% 50%,
          #ffffffff 3%,
          #a4a4a4ff 35%,
          #fafafaff 52%,
          #5f5f5fff 87%,
          #ffffffff 100%
        );
        background-color: grey;
        width: 28mm;
        height: 28mm;
        font-weight: 700;
        font-family: "Zen Maru Gothic", serif;

        > div {
          display: grid;
          position: relative;
          place-items: center;
          box-shadow:
            0.25mm 0.25mm 0.5mm 0.25mm rgba(0, 0, 0, 0.75),
            1mm 1mm 1mm rgba(255, 255, 255, 0.6),
            -0.5mm -0.5mm 1mm rgba(0, 0, 0, 0.75),
            inset 0.25mm 0.25mm 0.25mm white,
            inset -0.25mm -0.25mm 1mm rgba(0, 0, 0, 1);
          border-radius: 100%;
          /* background: linear-gradient(to bottom right, grey 0%, #ddd 30%, silver 50%, silver 70%, white); */
          background-image: conic-gradient(
            from 320deg at 50% 50%,
            #ffffffff 3%,
            #a4a4a4ff 35%,
            #fafafaff 52%,
            grey 87%,
            #ffffffff 100%
          );
          background-color: silver;
          width: 21mm;
          height: 21mm;

          &::before {
            display: block;
            position: absolute;
            inset: 2mm;
            box-shadow:
              -0.25mm -0.25mm 0.25mm rgba(0, 0, 0, 0.25),
              inset 0.25mm 0.25mm 0.25mm white,
              inset -0.25mm -0.25mm 0.25mm rgba(0, 0, 0, 0.25);
            border-radius: 100%;
            content: "";
          }

          span {
            position: relative;
            top: -1mm;
            color: silver;
            font-size: 12mm;
            line-height: 0;
            text-shadow:
              0.25mm 0.25mm 0.25mm white,
              -0.2mm -0.2mm 0.5mm black;
          }
        }
      }
    }
  }

  .topRow,
  .bottomRow {
    display: flex;
    position: relative;
    justify-content: center;
    align-items: center;
    margin: auto;
  }

  .topRow {
    top: 13.5mm;
    left: 2.5mm;
    width: 190mm;
    height: 40mm;
    /* background-color: rgba(0, 255, 0, 0.25); */
    white-space: nowrap;

    .office {
      /* background-color: rgba(0, 0, 255, 0.1); */
      flex-grow: 1;
      transform-origin: center left;
      filter: url("#drop-shadow");

      font-weight: 500;
      font-size: 48mm;
      /* font-family: "Kiwi Maru", serif; */
      /* font-family: "Kosugi Maru", serif; */
      /* font-family: "Zen Maru Gothic", serif; */
      font-family: "M PLUS Rounded 1c", serif;
      letter-spacing: -4mm;

      &.narrow {
        transform: scale(0.85, 1);
        margin-inline-end: -10%;
      }
    }

    .classification {
      position: relative;
      top: 4mm;
      flex-grow: 1;
      font-size: 49mm;
      /* background-color: rgba(0, 0, 255, 0.1); */
      font-family: "TrmFontJB";
      letter-spacing: -1mm;
    }
  }

  .bottomRow {
    display: flex;
    position: absolute;
    bottom: 12mm;
    justify-content: space-between;
    inset-inline-end: 15mm;
    inset-inline-start: 15mm;
    height: 85mm;
    font-weight: 600;
    font-size: 95mm;
    line-height: 85mm;

    .kana {
      display: grid;
      place-items: center;
      /* background-color: rgba(0, 0, 255, 0.1); */
      width: 42mm;
      font-weight: 900;
      font-size: 45mm;
      font-family: "Noto Serif JP", serif;
      font-optical-sizing: auto;

      span {
        position: relative;
        /* inset-inline-start: -4mm; */
        inset-block-start: -2mm;
      }
    }

    .serial {
      display: flex;
      gap: 7.5mm;
      /* background-color: rgba(0, 255, 0, 0.1); */
      height: 80mm;
      font-family: "TrmFontJB";
      letter-spacing: 3mm;

      .number {
        display: grid;
        place-items: center;
        /* background-color: rgba(255, 128, 0, 0.15); */
        width: 47mm;

        &:not(.dot) span {
          position: relative;
          top: 4mm;
          left: -4mm;
        }

        &.dot {
          span {
            display: block;
            border-radius: 100%;
            background-color: currentColor;
            width: 14mm;
            height: 14mm;
          }
        }
      }

      .separator {
        display: grid;
        place-items: center;
        /* background-color: rgba(255, 0, 128, 0.15); */
        width: 25mm;

        span {
          border-radius: 2mm;
          background-color: currentColor;
          width: 20mm;
          height: 12mm;
        }
      }
    }
  }
}
</style>
