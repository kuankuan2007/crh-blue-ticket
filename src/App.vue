<template>
  <div class="root-box">
    <div class="front">
      <div class="content">
        <div class="ticket-id" contenteditable>G123456</div>
        <div class="box-1">
          <div class="from">
            <div class="chinese">
              <div class="station-name" contenteditable>重庆西</div>
              <div class="station">站</div>
            </div>
            <div class="english" contenteditable>Chongqingxi</div>
          </div>
          <div class="arrow-area">
            <div class="train-id" contenteditable>G9999</div>
            <img class="arrow" src="@/assets/arrow.svg"></img>
          </div>
          <div class="to">
            <div class="chinese">
              <div class="station-name" contenteditable>重庆北</div>
              <div class="station">站</div>
            </div>
            <div class="english" contenteditable>Chongqingbei</div>
          </div>
        </div>
        <div class="box-2">
          <div class="departure-time">
            <div class="year number" contenteditable>2025</div>
            <div class="year-char gap">年</div>
            <div class="month number" contenteditable>05</div>
            <div class="month-char gap">月</div>
            <div class="day number" contenteditable>01</div>
            <div class="day-char gap">日</div>
            <div class="clock number" contenteditable>09</div>
            <div class="clock-char gap">:</div>
            <div class="minute number" contenteditable>31</div>
            <div class="departure-char gap">开</div>
          </div>
          <div class="seat">
            <div class="carriage number" contenteditable>20</div>
            <div class="carriage gap">车</div>
            <div class="row number" contenteditable>99</div>
            <div class="seat-id number" contenteditable>E</div>
            <div class="seat-char gap">号</div>
          </div>
        </div>
        <div class="box-3">
          <div class="price-box">
            <div class="currency">¥</div>
            <div class="number" contenteditable>114514.0</div>
            <div class="price-char">元</div>
          </div>
          <div class="seat-type">二等座</div>
        </div>
        <div class="warning">本页面仅做纪念，无实际意义</div>
        <div class="box-4">
          <div class="left">
            <div class="passenger">
              <div class="passenger-id" contenteditable>100203123456781234</div>
              <div class="passenger-name" contenteditable>张三</div>
            </div>
            <div class="warning-box">
              仅做纪念 你爱补不补<br />不得用于实际场景
            </div>
          </div>
          <img :src="qrCode" alt="qr-code" class="qr-code" />
        </div>
        <div class="footer">
          <div class="security-code">别看我 别看我 别看我 别看我 别看我 别看我 别看我 别看我 别看我 别看我 别看我 别看我 别看我 别看我 别看我 别看我 别看我 别看我 别看我 别看我 别看我
            别看我 别看我 别看我 别看我 别看我 别看我 别看我 别看我 别看我 别看我 别看我 别看我 别看我 别看我 别看我 别看我 别看我 别看我 别看我</div>
          <div class="verify-code" contenteditable>123456789012345A0123456 BC</div>
        </div>
      </div>
      <div class="fill-bg"></div>
      <svg class="text-watermark">
        <defs>
          <pattern id="fake-watermark" patternUnits="userSpaceOnUse" width="120" height="60"
            patternTransform="rotate(-45)">
            <text x="0" y="40" font-size="32" fill="#000" font-family="sans-serif" font-weight="bold">假的</text>
          </pattern>
        </defs>
        <rect width="100%" height="100%" fill="url(#fake-watermark)" />
      </svg>
      <img src="@/assets/bg-watermark.svg" alt="" class="bg-watermark">
    </div>
    <div class="back">
      <div class="content">
        <div class="title">报销个寂寞</div>
        <div class="text">
          <p>☆我管你需不需要报销凭证，反正财务拿着这个票包骂死你的。如果财务这都没看出来，请帮他挂个眼科然后走公账报销</p>
          <p>☆要劫自即韩土啊文之，同一丑个得完说游而人逃一帝了谢行，变说吾只服低人，德光则着尝绪中妙李太的吞，之入游场百话挟何范不，的己重皇谓是完说苦侯书，牙要于留爻仁与盲登回，老狱夹。</p>
          <p>☆也洪宋时是未不，不杨秦到斯解罚人，一预哉已，辜他会始。</p>
          <p>☆迷若土笔别的不，不他我章不人则德是韩有单不云日量皇何，得君流，联作忧两拢人领人了够地了，竟弟胆屯极分，薪未非使的人也己为。</p>
          <p>☆重变生小恩未，国化轻有赐着诗我家，他洪第，杂馆。不是你真在看啊，四单惜望，的太。</p>
        </div>
      </div>

    </div>
    <div class="print-tip">本页面支持打印，按 Ctrl/Command + P 打印，打印时请选择“无边距”</div>
  </div>
</template>
<script setup lang="ts">
import QRCode from 'qrcode';
import { ref, watch } from 'vue';
const qrCodeText = ref('https://crh-blue-ticket.pages.kuankuan.site/');
const qrCode = ref('');
watch(qrCodeText, async () => {
  qrCode.value = await QRCode.toDataURL(qrCodeText.value, {
    margin: 0,
    color: {
      light: '#ffffff',
      dark: '#000000',
    },
  });
}, {
  immediate: true,
})
</script>
<style scoped lang="scss">
*[contenteditable] {
  outline: 0px none;
  border: 0px none;
  white-space: pre;
}

.root-box {
  position: fixed;
  display: flex;
  inset: 0;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  $card-width: 8.56;
  $card-height: 5.398;
  $gap: 1;

  @media print {
    font-size: 1cm;
  }

  $showScale: 0.9;

  @media screen {
    font-size: min(100vw * $showScale / $card-width,
        100vh * $showScale / (2 * $card-height + $gap));
  }

  gap: 1em;

  .front,
  .back {
    width: $card-width * 1em;
    height: $card-height * 1em;
    overflow: hidden;
    position: relative;
    border-radius: 0.3em;

    .content {
      width: 100%;
      height: 100%;
      text-align: left;
    }

    img.example {
      position: absolute;
      inset: 0;
      opacity: 0.5;
      width: 100%;
      pointer-events: none;
      z-index: 1;
    }
  }
  .print-tip {
    font-size: 1.3rem;
    position: absolute;
    bottom: 1em;
    width: 100%;
    text-align: center;
    @media print {
      display: none;
    }
  }
}

.front {

  .bg-watermark {
    position: absolute;
    z-index: -1;
    opacity: 0.4;
    bottom: 0.5em;
    right: 0em;
    height: 3.5em;
    user-select: none;
    pointer-events: none;
  }

  .text-watermark {
    position: absolute;
    z-index: -1;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    opacity: 0.05;
    user-select: none;
    pointer-events: none;
  }

  .fill-bg {
    position: absolute;
    z-index: -1;
    inset: 0;
    background: #e9e9e9;
  }

  .content {
    font-size: 0.5em;
    display: flex;
    flex-direction: column;

    .ticket-id {
      font-size: 0.95em;
      font-family: Arial;
      padding-top: 0.43em;
      padding-left: 0.95em;
    }

    .box-1 {
      margin-top: -0.45em;
      display: flex;
      padding-left: 1.6em;

      .english {
        font-size: 0.66em;
        text-align: left;
        margin-top: -0.3em;
        padding-left: 0.45em;
        font-weight: bold;
        font-family: FangSong_GB2312;
      }

      .chinese {
        display: flex;
        align-items: center;
        gap: 0.1em;

        .station {
          font-size: 0.8em;
          font-family: FangSong_GB2312;
          font-weight: bold;
        }

        .station-name {
          width: 3.4em;
          text-align: justify;
          text-align-last: justify;
        }
      }

      .arrow-area {
        width: 3em;
        padding-left: 1.1em;
        padding-right: 0.6em;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-self: center;

        .train-id {
          font-family: FangSong_GB2312;
          font-weight: bold;
          padding: 0 0.2em;
        }

        .arrow {
          margin-top: -0.1em;
          padding-bottom: 0.27em;
        }
      }
    }

    .box-2 {
      margin-top: -0.1em;
      display: flex;

      .departure-time,
      .seat {
        display: flex;
        align-items: center;

        .number {
          font-size: 0.8em;
        }

        .gap {
          font-size: 0.5em;
          font-family: FangSong_GB2312;
          font-weight: bold;
        }

      }

      .departure-time {
        padding-left: 1em;

        .year {
          width: 2.2em;
        }

        .month {
          padding-left: 0.2em;
          width: 1.15em;
        }

        .day {
          padding-left: 0.2em;
          width: 1.15em;
        }

        .clock {
          padding-left: 0.2em;
          width: 1.15em;
        }

        .clock-char {
          font-size: 0.8em;
        }
      }

      .seat {
        padding-left: 1.6em;

        .carriage {
          width: 1em;
        }

        .row {
          padding-left: 0.1em;
          width: 1.05em;
        }

        .seat-id {
          font-size: 0.7em;
          font-family: FangSong_GB2312;
          font-weight: bold;
          width: 0.5em;
        }
      }
    }

    .box-3 {
      margin-top: -0.1em;
      display: flex;
      align-items: center;
      padding-right: 2.8em;

      .price-box,
      .seat-type {
        display: flex;
        font-family: FangSong_GB2312;
        font-weight: bold;
        font-size: 0.85em;
        align-items: center;

        .currency {
          font-weight: 400;
          font-family: serif;
        }
      }

      .price-box {
        padding-left: 1.5em;

        .price-char {
          font-size: 0.6em;
        }
      }

      .seat-type {
        margin-left: auto;
        font-size: 0.75em;
      }
    }

    .warning {
      font-family: FangSong_GB2312;
      font-weight: bold;
      font-size: 0.6em;
      padding-left: 1.5em;
      margin-top: auto;
    }

    .box-4 {
      display: flex;
      align-items: start;
      padding-top: 0.2em;
      padding-left: 1em;

      .left {
        display: flex;
        flex-direction: column;
        width: 12em;
        gap: 0.1em;

        .passenger {
          display: flex;
          font-family: FangSong_GB2312;
          font-weight: bold;
          align-items: center;
          font-size: 0.8em;
          gap: 0.2em;
        }

        .warning-box {
          margin-left: 1em;
          margin-right: 2em;
          border: dashed 0.1em black;
          text-align: center;
          font-size: 0.6em;
          font-family: FangSong_GB2312;
          font-weight: bold;
        }
      }

      .qr-code {
        margin-top: -0.1em;
        height: 2.7em;
        mix-blend-mode: darken;
      }
    }

    .footer {
      width: 100%;
      $footer-color: rgb(215, 215, 255);

      .security-code {
        white-space: nowrap;
        font-size: 0.25em;
        color: $footer-color;
        user-select: none;
      }

      .verify-code {
        background-color: $footer-color;
        font-family: FangSong_GB2312;
        font-size: 0.6em;
        font-weight: bold;
        padding-top: 0.2em;
        padding-bottom: 0.3em;
        padding-left: 1.5em;
      }
    }
  }
}

.back {
  background: #000;
  color: #888;

  .content {
    .title {
      padding-top: 1em;
      text-align: center;
      font-size: 0.4em;
      font-weight: bold;
    }

    .text {
      line-height: 1.4em;
      font-size: 0.24em;
      padding: 0 2em;

      p {
        margin: 0.2em 0;
        text-indent: 2em;
      }
    }
  }
}
</style>
