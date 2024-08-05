<template>
  <div class="white-window-container">
    <div
      id="white-window"
      class="white-window"
      :class="[
        partNum === 4 || partNum === 5 ? 'explain-page center-text' : '',
        partNum === 5 ? 'page5-flex' : '',
      ]"
      :style="{ '--thePos': partNum === 4 ? '20rem' : '8rem' }"
    >
      <div class="center-text" v-if="partNum === 0">
        <p class="explain-text">
          בלומדה זו נתמקד ב-2 השלבים הראשונים ממעגל החניכה:
        </p>
        <p class="bold-text">הכנה עצמית</p>
        <p class="explain-text">ו-</p>
        <p class="bold-text">תדריך</p>
      </div>

      <div
        class="center-text hanica-circle-info"
        v-if="partNum === 1 || partNum === 2"
      >
        <div>
          <img src="../../src/assets/media/bell.svg" class="bell" alt="bell" />
          <p class="explain-text reminder-text">תזכורת למעגל החניכה:</p>
        </div>

        <!-- the circles -->
        <!-- <div class="circle-container">
        <div
          v-for="(item, index) in arrayAgo"
          :key="index"
          class="circle"
          :class="getCircleClass(index)"
        >
          {{ arrayAgo[index] }}
        </div>
        <img
          v-for="i in 5"
          :key="i"
          class="arrow"
          :class="getArrowClass(i)"
          src="../../src/assets/media/arrow.svg"
        />
      </div> -->
        <svg
          class="svg-circle-container"
          viewBox="0 0 454 410"
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
        >
          <g clip-path="url(#clip0_471_35)">
            <rect width="454" height="410" fill="white" />
            <path
              d="M46.7226 240.371L41.0312 244.616C40.3019 245.179 39.2901 244.99 38.7788 244.318C38.221 243.585 38.4104 242.566 39.079 242.051L47.7483 235.508C48.0522 235.274 48.3954 235.155 48.7708 235.204C48.8244 235.211 48.878 235.218 48.9317 235.226C48.9853 235.233 49.0389 235.24 49.1462 235.254L49.2534 235.268L49.3607 235.282C49.6217 235.372 49.8684 235.569 50.0007 235.807L56.4868 244.52C57.0445 245.253 56.8551 246.271 56.1866 246.787C55.4573 247.35 54.4455 247.161 53.9342 246.489L49.951 241.128C46.6233 251.014 48.2543 260.128 54.8798 268.201C58.1764 272.153 62.1558 275.481 66.6786 278.002C67.4938 278.439 67.8014 279.414 67.3724 280.181C66.9363 281.002 65.9674 281.313 65.2059 280.883C60.322 278.204 55.9957 274.61 52.4202 270.292C47.2893 264.12 42.2511 253.95 46.7226 240.371Z"
              fill="#777777"
            />
            <path
              d="M137.135 79.2525L132.238 74.1116C131.592 73.4551 131.658 72.4279 132.264 71.8397C132.924 71.198 133.958 71.2638 134.55 71.8656L142.086 79.6873C142.355 79.9609 142.514 80.2873 142.51 80.666C142.51 80.72 142.509 80.7741 142.508 80.8282C142.508 80.8823 142.507 80.9364 142.506 81.0446L142.505 81.1528L142.503 81.261C142.446 81.5308 142.28 81.7994 142.06 81.9592L134.188 89.4439C133.527 90.0856 132.493 90.0198 131.901 89.418C131.255 88.7615 131.321 87.7343 131.927 87.1461L136.771 82.5485C126.557 80.4309 117.704 83.1437 110.485 90.6899C106.957 94.4369 104.131 98.7869 102.17 103.58C101.834 104.441 100.903 104.864 100.09 104.53C99.2227 104.195 98.7976 103.271 99.1335 102.463C101.207 97.2931 104.256 92.5669 108.114 88.499C113.626 82.6647 123.117 76.4426 137.135 79.2525Z"
              fill="#777777"
            />
            <path
              d="M350.053 96.8142L352.052 90.0014C352.297 89.1135 353.22 88.6566 354.032 88.8865C354.918 89.1373 355.379 90.0654 355.154 90.8793L352.155 101.318C352.053 101.688 351.85 101.989 351.52 102.175C351.473 102.202 351.426 102.228 351.379 102.255C351.331 102.281 351.284 102.308 351.19 102.361L351.096 102.414L351.001 102.467C350.739 102.552 350.423 102.543 350.175 102.433L339.755 99.3638C338.869 99.113 338.408 98.185 338.633 97.3711C338.878 96.4832 339.8 96.0263 340.613 96.2562L347.018 98.1487C343.738 88.2466 336.959 81.9405 326.812 79.4677C321.803 78.2892 316.622 78.0195 311.492 78.7213C310.577 78.8613 309.746 78.2671 309.628 77.3961C309.483 76.4777 310.071 75.6468 310.938 75.5334C316.452 74.7406 322.069 75.0143 327.522 76.3182C335.332 78.1696 345.469 83.2722 350.053 96.8142Z"
              fill="#777777"
            />
            <path
              d="M395.986 280.635L402.945 282.047C403.85 282.215 404.384 283.095 404.224 283.924C404.05 284.829 403.164 285.367 402.334 285.212L391.678 283.113C391.301 283.043 390.983 282.867 390.77 282.554C390.739 282.509 390.709 282.464 390.678 282.42C390.648 282.375 390.617 282.33 390.556 282.241L390.496 282.151L390.435 282.062C390.327 281.808 390.31 281.492 390.399 281.235L392.568 270.592C392.742 269.688 393.628 269.15 394.458 269.304C395.363 269.472 395.897 270.352 395.737 271.181L394.398 277.724C403.984 273.613 409.69 266.321 411.289 256.001C412.036 250.909 411.863 245.724 410.727 240.672C410.509 239.773 411.03 238.894 411.888 238.702C412.791 238.48 413.669 238.994 413.856 239.849C415.115 245.275 415.322 250.895 414.487 256.439C413.308 264.379 409.088 274.914 395.986 280.635Z"
              fill="#777777"
            />
            <path
              d="M208.774 357.6L210.177 364.56C210.373 365.46 209.77 366.293 208.944 366.468C208.043 366.659 207.203 366.052 207.023 365.227L204.817 354.593C204.735 354.218 204.774 353.856 204.979 353.538C205.009 353.493 205.038 353.447 205.067 353.402C205.097 353.357 205.126 353.311 205.185 353.22L205.244 353.129L205.302 353.038C205.495 352.841 205.779 352.702 206.05 352.684L216.7 350.548C217.601 350.357 218.441 350.964 218.621 351.789C218.818 352.689 218.214 353.523 217.388 353.697L210.839 355.005C218.352 362.241 227.288 364.665 237.418 362.129C242.401 360.839 247.111 358.666 251.324 355.656C252.068 355.106 253.081 355.245 253.591 355.961C254.146 356.706 254.013 357.715 253.299 358.219C248.788 361.488 243.689 363.862 238.257 365.247C230.483 367.245 219.136 367.449 208.774 357.6Z"
              fill="#777777"
            />
            <circle
              class="circle-svg"
              cx="227.5"
              cy="70.5"
              r="49.5"
              fill="#EB5781"
              @mouseover="increaseRadius"
              @mouseout="decreaseRadius"
            />
            <path
              d="M217.469 63V57.0781C217.469 56.4531 217.318 55.9948 217.016 55.7031C216.719 55.4115 216.25 55.2656 215.609 55.2656H211.992V53.7109H215.734C216.938 53.7109 217.857 54.0052 218.492 54.5938C219.133 55.1823 219.453 56.0365 219.453 57.1562V63H217.469ZM211.984 63V59.8203C211.984 59.2266 212.042 58.7865 212.156 58.5C212.276 58.2083 212.383 57.987 212.477 57.8359H214.062C214.016 58.0547 213.977 58.3099 213.945 58.6016C213.914 58.888 213.898 59.2344 213.898 59.6406V63H211.984ZM222.688 63.1562C222.396 63.1562 222.122 63.138 221.867 63.1016C221.612 63.0703 221.336 63.0234 221.039 62.9609L221.062 61.4531C221.417 61.5104 221.794 61.5391 222.195 61.5391C222.586 61.5391 222.878 61.4297 223.07 61.2109C223.263 60.9922 223.359 60.6536 223.359 60.1953V55.2656H221.641V53.7109H225.344V60.3516C225.344 61.2526 225.112 61.9453 224.648 62.4297C224.185 62.9141 223.531 63.1562 222.688 63.1562ZM229.93 63.1406C229.523 63.1406 229.096 63.1068 228.648 63.0391C228.206 62.9714 227.742 62.8776 227.258 62.7578L227.562 61.2969C228.391 61.5 229.104 61.599 229.703 61.5938C230.516 61.5833 231.117 61.3906 231.508 61.0156C231.904 60.6354 232.102 60.0911 232.102 59.3828V55.2656H227.602V53.7109H234.086V59.0078C234.086 59.9661 233.914 60.75 233.57 61.3594C233.227 61.9688 232.745 62.4193 232.125 62.7109C231.505 62.9974 230.773 63.1406 229.93 63.1406ZM242.047 63V57.0781C242.047 56.4531 241.896 55.9948 241.594 55.7031C241.297 55.4115 240.828 55.2656 240.188 55.2656H236.57V53.7109H240.312C241.516 53.7109 242.435 54.0052 243.07 54.5938C243.711 55.1823 244.031 56.0365 244.031 57.1562V63H242.047ZM236.562 63V59.8203C236.562 59.2266 236.62 58.7865 236.734 58.5C236.854 58.2083 236.961 57.987 237.055 57.8359H238.641C238.594 58.0547 238.555 58.3099 238.523 58.6016C238.492 58.888 238.477 59.2344 238.477 59.6406V63H236.562ZM211.109 77.7109C212.328 77.7109 213.245 78.0052 213.859 78.5938C214.479 79.1823 214.789 80.0651 214.789 81.2422V87H212.82L212.805 81.0938C212.805 80.4635 212.669 80.0026 212.398 79.7109C212.128 79.4141 211.701 79.2656 211.117 79.2656H209.867C209.742 79.5521 209.643 79.8906 209.57 80.2812C209.503 80.6667 209.469 81.0495 209.469 81.4297V84.3125C209.469 85.2135 209.24 85.9062 208.781 86.3906C208.328 86.8698 207.685 87.1094 206.852 87.1094C206.664 87.1094 206.487 87.1016 206.32 87.0859C206.159 87.0703 205.987 87.0495 205.805 87.0234V85.4688C205.893 85.4792 205.982 85.487 206.07 85.4922C206.159 85.4922 206.245 85.4922 206.328 85.4922C206.74 85.4922 207.044 85.3854 207.242 85.1719C207.44 84.9583 207.539 84.625 207.539 84.1719V81.6016C207.539 81.2161 207.589 80.8047 207.688 80.3672C207.792 79.9245 207.945 79.5573 208.148 79.2656H206.562V77.7109H211.109ZM217.883 82.9531V79.2656H216.312V77.7109H219.867V82.9531H217.883ZM222.359 87L223.008 81.4531C223.06 81.0312 223.172 80.6302 223.344 80.25C223.521 79.8698 223.727 79.5755 223.961 79.3672C223.982 79.3464 224.003 79.3281 224.023 79.3125C224.049 79.2917 224.07 79.276 224.086 79.2656L224.078 79.2344C223.865 79.2708 223.599 79.3333 223.281 79.4219C222.964 79.5052 222.682 79.5911 222.438 79.6797L222.008 78.2266C222.409 78.0807 222.852 77.9557 223.336 77.8516C223.826 77.7422 224.323 77.6562 224.828 77.5938C225.339 77.5312 225.82 77.5 226.273 77.5C227.612 77.5 228.63 77.849 229.328 78.5469C230.026 79.2396 230.378 80.2604 230.383 81.6094V87H226.43V85.4453H228.406V81.3594C228.406 80.6406 228.25 80.0911 227.938 79.7109C227.63 79.3255 227.193 79.1328 226.625 79.1328C226.151 79.1328 225.768 79.3177 225.477 79.6875C225.185 80.0521 225.005 80.5625 224.938 81.2188L224.312 87H222.359ZM232.5 87V85.4375H237.078L231.828 77.7109H234.047L236.68 81.8125L239.625 86.0703V87H232.5ZM237.086 83.3594L235.859 81.7734L237.922 77.7109H240.148L237.086 83.3594ZM244.586 87.2109C244.07 87.2109 243.518 87.1589 242.93 87.0547C242.341 86.9557 241.721 86.7865 241.07 86.5469L241.508 85.0859C242.049 85.2943 242.552 85.4505 243.016 85.5547C243.484 85.6536 243.914 85.7057 244.305 85.7109C245.107 85.7109 245.747 85.5026 246.227 85.0859C246.706 84.6641 246.945 84.0469 246.945 83.2344V77.7109H248.922V83.1484C248.922 84.0339 248.74 84.7786 248.375 85.3828C248.01 85.987 247.5 86.4427 246.844 86.75C246.193 87.0573 245.44 87.2109 244.586 87.2109ZM241.531 77.7109H243.516L244.953 84.4062C245.026 84.75 245.115 85.0495 245.219 85.3047C245.323 85.5599 245.474 85.7917 245.672 86L244.156 85.9844C243.917 85.8073 243.688 85.5703 243.469 85.2734C243.25 84.9766 243.096 84.6302 243.008 84.2344L241.531 77.7109Z"
              fill="white"
            />
            <circle
              class="circle-svg"
              cx="71.5"
              cy="175.5"
              r="49.5"
              fill="#EB5781"
              @mouseover="increaseRadius"
              @mouseout="decreaseRadius"
            />
            <path
              d="M53.8047 180V178.438H58.5547L60.5312 178.367L61.6328 178.508V180H53.8047ZM58.5547 179.547V174.078C58.5547 173.453 58.4062 172.995 58.1094 172.703C57.8125 172.411 57.3411 172.266 56.6953 172.266H54.3125V170.711H56.8281C58.0208 170.711 58.9349 171.005 59.5703 171.594C60.2109 172.182 60.5312 173.036 60.5312 174.156V179.547H58.5547ZM63.5625 180V172.266H62.625V170.711H65.5469V180H63.5625ZM70.1562 170.711V178.039C70.6198 178.237 71.1172 178.396 71.6484 178.516C72.1849 178.63 72.6901 178.688 73.1641 178.688C73.888 178.688 74.5339 178.586 75.1016 178.383C75.6745 178.174 76.125 177.854 76.4531 177.422C76.7865 176.99 76.9531 176.438 76.9531 175.766V170.711H78.875V175.977C78.875 176.695 78.7266 177.323 78.4297 177.859C78.1328 178.396 77.724 178.844 77.2031 179.203C76.6875 179.557 76.0911 179.823 75.4141 180C74.737 180.172 74.0156 180.258 73.25 180.258C72.4427 180.258 71.6042 180.161 70.7344 179.969C69.8646 179.771 69.0339 179.484 68.2422 179.109V170.711H70.1562ZM72.1172 177.227C72.263 177.023 72.3724 176.74 72.4453 176.375C72.5234 176.01 72.5625 175.607 72.5625 175.164V170.711H74.4844V174.766C74.4844 175.292 74.4219 175.771 74.2969 176.203C74.1719 176.635 73.987 176.984 73.7422 177.25L72.1172 177.227ZM81.5 180L82.1484 174.453C82.2005 174.031 82.3125 173.63 82.4844 173.25C82.6615 172.87 82.8672 172.576 83.1016 172.367C83.1224 172.346 83.1432 172.328 83.1641 172.312C83.1901 172.292 83.2109 172.276 83.2266 172.266L83.2188 172.234C83.0052 172.271 82.7396 172.333 82.4219 172.422C82.1042 172.505 81.8229 172.591 81.5781 172.68L81.1484 171.227C81.5495 171.081 81.9922 170.956 82.4766 170.852C82.9661 170.742 83.4635 170.656 83.9688 170.594C84.4792 170.531 84.9609 170.5 85.4141 170.5C86.7526 170.5 87.7708 170.849 88.4688 171.547C89.1667 172.24 89.5182 173.26 89.5234 174.609V180H85.5703V178.445H87.5469V174.359C87.5469 173.641 87.3906 173.091 87.0781 172.711C86.7708 172.326 86.3333 172.133 85.7656 172.133C85.2917 172.133 84.9089 172.318 84.6172 172.688C84.3255 173.052 84.1458 173.562 84.0781 174.219L83.4531 180H81.5Z"
              fill="white"
            />
            <circle
              class="circle-svg"
              cx="128.5"
              cy="315.5"
              r="49.5"
              fill="#EB5781"
              @mouseover="increaseRadius"
              @mouseout="decreaseRadius"
            />
            <path
              d="M110.914 310.711H118.648V312.266H117.055V320H115.07V312.266H110.914V310.711ZM120.781 320V312.266H119.844V310.711H122.766V320H120.781ZM124.555 320V318.438H129.305L131.281 318.367L132.383 318.508V320H124.555ZM129.305 319.547V314.078C129.305 313.453 129.156 312.995 128.859 312.703C128.562 312.411 128.091 312.266 127.445 312.266H125.062V310.711H127.578C128.771 310.711 129.685 311.005 130.32 311.594C130.961 312.182 131.281 313.036 131.281 314.156V319.547H129.305ZM134.68 315.953V312.266H133.109V310.711H136.664V315.953H134.68ZM141.867 320.211C141.352 320.211 140.799 320.159 140.211 320.055C139.622 319.956 139.003 319.786 138.352 319.547L138.789 318.086C139.331 318.294 139.833 318.451 140.297 318.555C140.766 318.654 141.195 318.706 141.586 318.711C142.388 318.711 143.029 318.503 143.508 318.086C143.987 317.664 144.227 317.047 144.227 316.234V310.711H146.203V316.148C146.203 317.034 146.021 317.779 145.656 318.383C145.292 318.987 144.781 319.443 144.125 319.75C143.474 320.057 142.721 320.211 141.867 320.211ZM138.812 310.711H140.797L142.234 317.406C142.307 317.75 142.396 318.049 142.5 318.305C142.604 318.56 142.755 318.792 142.953 319L141.438 318.984C141.198 318.807 140.969 318.57 140.75 318.273C140.531 317.977 140.378 317.63 140.289 317.234L138.812 310.711Z"
              fill="white"
            />
            <circle
              class="circle-svg"
              cx="321.5"
              cy="315.5"
              r="49.5"
              fill="#EB5781"
              @mouseover="increaseRadius"
              @mouseout="decreaseRadius"
            />
            <path
              d="M304.891 310.711C306.109 310.711 307.026 311.005 307.641 311.594C308.26 312.182 308.57 313.065 308.57 314.242V320H306.602L306.586 314.094C306.586 313.464 306.451 313.003 306.18 312.711C305.909 312.414 305.482 312.266 304.898 312.266H303.648C303.523 312.552 303.424 312.891 303.352 313.281C303.284 313.667 303.25 314.049 303.25 314.43V317.312C303.25 318.214 303.021 318.906 302.562 319.391C302.109 319.87 301.466 320.109 300.633 320.109C300.445 320.109 300.268 320.102 300.102 320.086C299.94 320.07 299.768 320.049 299.586 320.023V318.469C299.674 318.479 299.763 318.487 299.852 318.492C299.94 318.492 300.026 318.492 300.109 318.492C300.521 318.492 300.826 318.385 301.023 318.172C301.221 317.958 301.32 317.625 301.32 317.172V314.602C301.32 314.216 301.37 313.805 301.469 313.367C301.573 312.924 301.727 312.557 301.93 312.266H300.344V310.711H304.891ZM311.664 315.953V312.266H310.094V310.711H313.648V315.953H311.664ZM319.547 320.18C319.062 320.18 318.531 320.133 317.953 320.039C317.375 319.945 316.823 319.807 316.297 319.625L316.672 318.164C317.172 318.31 317.669 318.419 318.164 318.492C318.659 318.56 319.081 318.594 319.43 318.594C320.232 318.583 320.841 318.391 321.258 318.016C321.68 317.641 321.891 317.096 321.891 316.383V312.266H318.68C318.544 312.557 318.438 312.883 318.359 313.242C318.281 313.602 318.242 313.966 318.242 314.336V314.914C318.362 314.951 318.505 314.977 318.672 314.992C318.844 315.008 319.039 315.016 319.258 315.016V316.477C318.846 316.513 318.466 316.521 318.117 316.5C317.768 316.474 317.445 316.417 317.148 316.328C316.857 316.24 316.583 316.12 316.328 315.969L316.305 314.953C316.305 314.438 316.362 313.94 316.477 313.461C316.596 312.982 316.763 312.583 316.977 312.266H315.93V310.711H323.867V316.062C323.867 317.021 323.677 317.805 323.297 318.414C322.917 319.018 322.401 319.466 321.75 319.758C321.099 320.044 320.365 320.185 319.547 320.18ZM326.219 320V318.438H330.797L325.547 310.711H327.766L330.398 314.812L333.344 319.07V320H326.219ZM330.805 316.359L329.578 314.773L331.641 310.711H333.867L330.805 316.359ZM339.703 310.711C340.922 310.711 341.839 311.005 342.453 311.594C343.073 312.182 343.383 313.065 343.383 314.242V320H341.414L341.398 314.094C341.398 313.464 341.263 313.003 340.992 312.711C340.721 312.414 340.294 312.266 339.711 312.266H338.461C338.336 312.552 338.237 312.891 338.164 313.281C338.096 313.667 338.062 314.049 338.062 314.43V317.312C338.062 318.214 337.833 318.906 337.375 319.391C336.922 319.87 336.279 320.109 335.445 320.109C335.258 320.109 335.081 320.102 334.914 320.086C334.753 320.07 334.581 320.049 334.398 320.023V318.469C334.487 318.479 334.576 318.487 334.664 318.492C334.753 318.492 334.839 318.492 334.922 318.492C335.333 318.492 335.638 318.385 335.836 318.172C336.034 317.958 336.133 317.625 336.133 317.172V314.602C336.133 314.216 336.182 313.805 336.281 313.367C336.385 312.924 336.539 312.557 336.742 312.266H335.156V310.711H339.703Z"
              fill="white"
            />
            <circle
              class="circle-svg"
              cx="379.5"
              cy="175.5"
              r="49.5"
              fill="#EB5781"
              @mouseover="increaseRadius"
              @mouseout="decreaseRadius"
            />
            <path
              d="M364.789 183.25V172.266H360.453V170.711H366.742V183.25H364.789ZM370.07 175.953V172.266H368.5V170.711H372.055V175.953H370.07ZM378.086 180V173.703C378.086 173.25 377.956 172.898 377.695 172.648C377.435 172.393 377.068 172.266 376.594 172.266H373.641V170.711H376.711C377.758 170.711 378.578 170.984 379.172 171.531C379.771 172.078 380.07 172.841 380.07 173.82V180H378.086ZM381.648 170.711H389.383V172.266H387.789V180H385.805V172.266H381.648V170.711ZM395.281 170.711C396.5 170.711 397.417 171.005 398.031 171.594C398.651 172.182 398.961 173.065 398.961 174.242V180H396.992L396.977 174.094C396.977 173.464 396.841 173.003 396.57 172.711C396.299 172.414 395.872 172.266 395.289 172.266H394.039C393.914 172.552 393.815 172.891 393.742 173.281C393.674 173.667 393.641 174.049 393.641 174.43V177.312C393.641 178.214 393.411 178.906 392.953 179.391C392.5 179.87 391.857 180.109 391.023 180.109C390.836 180.109 390.659 180.102 390.492 180.086C390.331 180.07 390.159 180.049 389.977 180.023V178.469C390.065 178.479 390.154 178.487 390.242 178.492C390.331 178.492 390.417 178.492 390.5 178.492C390.911 178.492 391.216 178.385 391.414 178.172C391.612 177.958 391.711 177.625 391.711 177.172V174.602C391.711 174.216 391.76 173.805 391.859 173.367C391.964 172.924 392.117 172.557 392.32 172.266H390.734V170.711H395.281Z"
              fill="white"
            />
          </g>
          <defs>
            <clipPath id="clip0_471_35">
              <rect width="454" height="410" fill="white" />
            </clipPath>
          </defs>
        </svg>

        <!-- the openning window -->
        <div v-if="partNum === 2">
          <!-- the blur bg -->
          <div class="hide-bg"></div>
          <div class="jumping-window">
            <p class="adjust">
              שלבי הכנה עצמאית ועיבוד הם שלבים עצמאים של החונך.
            </p>
            <button
              id="expBtn"
              style="height: 30%"
              class="startBtn posCenterBtn"
              @click="nextPart"
            >
              הבא
            </button>
          </div>
        </div>
      </div>

      <div v-if="partNum === 3">
        <p
          v-for="(text, index) in array1"
          :key="text"
          :class="{
            'talk-text': index === 0 || index === 2,
            'info-text-goal': index !== 0 && index !== 2,
          }"
          :style="{
            'font-size': index === 0 || index === 2 ? '2.5rem' : '1.5rem',
          }"
        >
          {{ text }}
        </p>
      </div>

      <div
        style="
          position: absolute;
          top: 50%;
          left: 50%;
          transform: translate(-50%, -50%);
          width: 100%;
        "
        v-if="partNum === 4"
      >
        <p class="explain-text">{{ openningSubjArray[subjNum][0] }}</p>
        <p class="talk-text margin-auto">{{ openningSubjArray[subjNum][1] }}</p>
        <p class="explain-text">כדי להמשיך בלמידת החומר לחצ\י הבא</p>
        <p style="font-size: 2.3rem; color: #aa336a">בהצלחה!</p>
      </div>

      <div class="explain-subj-container" v-if="partNum === 5">
        <p class="explain-text">קודם כל -</p>
        <p class="bold-text">{{ arrayExplain[subjNum][0] }}</p>
        <br /><br /><br />

        <div class="the-type-writer type-writer">
          <p
            v-for="(text, index) in arrayExplain[subjNum].slice(1)"
            :key="text"
            :style="{
              '--delay': `${index * 3.2}s`,
              '--width': `${text.length}ch`,
              'font-size': '1.41rem',
            }"
            class="explain-text"
          >
            {{ text }}
          </p>
        </div>
      </div>

      <button
        v-if="partNum !== 2 && showNextBtn"
        id="expBtn"
        class="startBtn"
        :class="{
          posLeftBtn: partNum === 1 || partNum === 3,
          posCenterBtn: partNum !== 1 && partNum !== 3,
          'fade-in': partNum === 5 && showNextBtn,
        }"
        @click="nextPart"
      >
        הבא
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "white-window",
  components: {},
  props: ["subjNum"],
  data() {
    return {
      partNum: 0,
      titleIndex: 0,
      showNextBtn: true,
      arrayExplain: [
        [
          "מהי הכנה עצמית?",
          "השלב הראשון במעגל החניכה, בו החונך מתכונן לתדריך. ",
          "שלב זה שייך רק לחונך והוא מבצע אותו לבד.",
        ],
        [
          "מהו תדריך?",
          "השלב הבא אחרי הכנה עצמית, בשלב זה החונך מתדרך ",
          "את הנחנך לקראת התצפית (השלב הבא).",
        ],
      ],
      array1: [
        "מטרת על",
        'החניך יבצע הכנה עצמית ויתדרך לביצוע עפ"י העקרונות שנלמדו.',
        "מטרות ביניים",
        "החניך יציין את שלבי מעגל החניכה.",
        "החניך יפרט את תחומי ההכנה העצמית.",
        "החניך יסביר את מטרות התדריך, עקרונותיו ודגשיו.",
        "החניך יתרגל תדריך לקראת תצפית.",
      ],
      openningSubjArray: [
        ["נתחיל בנושא הראשון במעגל החניכה", "הכנה עצמית"],
        ["עכשיו נעבור לנושא השני של הלומדה", "תדריך"],
      ],
      arrayAgo: ["משוב", "עיבוד", "תצפית", "תדריך", "הכנה עצמית"],
    };
  },
  mounted() {
    if (this.subjNum === 1) {
      this.partNum = 4;
    }
  },
  methods: {
    nextPart() {
      if (this.partNum === 4) {
        this.showNextBtn = false;
        let timer = setTimeout(() => {
          this.showNextBtn = true;
          clearTimeout(timer);
        }, 6000);
      } else if (this.partNum === 5) {
        this.$emit("hideWW", this.partNum);
      }
      this.partNum++;
    },
    getCircleClass(index) {
      return "circle" + index;
    },
    getArrowClass(index) {
      return "arrow" + index;
    },
    increaseRadius(event) {
      event.currentTarget.setAttribute("r", 60);
    },
    decreaseRadius(event) {
      event.currentTarget.setAttribute("r", 49);
    },
  },
};
</script>

<style scoped>
.white-window-container {
  width: 100vw;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}
/* typewriter */

.type-writer > p {
  animation: typeWrite 2s var(--delay) steps(44) normal both,
    blink 400ms var(--delay) steps(45) 5;
}

.the-type-writer > p {
  display: block;
  width: fit-content;
  white-space: nowrap;
  text-align: right;
  overflow: hidden;
  border-left: solid 3px transparent;
  max-width: fit-content;
  margin-block: 3%;
}

.the-type-writer {
  position: relative;
  height: fit-content;
  flex-direction: column;
  /* text-align: center; */
  display: flex;
  /* justify-content: center;
  align-items: center; */
  left: 50%; /* Center horizontally */
  transform: translateX(-50%); /* Center horizontally */
}

@keyframes typeWrite {
  from {
    width: 0%;
  }

  to {
    width: var(--width);
  }
}

@keyframes blink {
  to {
    border-left-color: black;
  }

  from {
    border-left-color: transparent;
  }
}

/* end-typewriter */

.reminder-text {
}

.hanica-circle-info {
  display: grid;
}

.jumping-window {
  background-color: white;
  width: 39rem;
  height: 30%;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.adjust {
  font-weight: bold;
  font-size: 1.2rem;
  position: absolute;
  top: 20%;
  left: 50%;
  transform: translateX(-50%);
  width: 100%;
}

.bell {
  display: inline;
  width: 2rem;
  height: 2rem;
  margin-left: 2rem;
  -webkit-animation: ring 4s 0.7s ease-in-out infinite;
  -webkit-transform-origin: 50% 4px;
  -moz-animation: ring 4s 0.7s ease-in-out infinite;
  -moz-transform-origin: 50% 4px;
  animation: ring 4s 0.7s ease-in-out infinite;
  transform-origin: 50% 4px;
}

@-webkit-keyframes ring {
  0% {
    -webkit-transform: rotateZ(0);
  }
  1% {
    -webkit-transform: rotateZ(30deg);
  }
  3% {
    -webkit-transform: rotateZ(-28deg);
  }
  5% {
    -webkit-transform: rotateZ(34deg);
  }
  7% {
    -webkit-transform: rotateZ(-32deg);
  }
  9% {
    -webkit-transform: rotateZ(30deg);
  }
  11% {
    -webkit-transform: rotateZ(-28deg);
  }
  13% {
    -webkit-transform: rotateZ(26deg);
  }
  15% {
    -webkit-transform: rotateZ(-24deg);
  }
  17% {
    -webkit-transform: rotateZ(22deg);
  }
  19% {
    -webkit-transform: rotateZ(-20deg);
  }
  21% {
    -webkit-transform: rotateZ(18deg);
  }
  23% {
    -webkit-transform: rotateZ(-16deg);
  }
  25% {
    -webkit-transform: rotateZ(14deg);
  }
  27% {
    -webkit-transform: rotateZ(-12deg);
  }
  29% {
    -webkit-transform: rotateZ(10deg);
  }
  31% {
    -webkit-transform: rotateZ(-8deg);
  }
  33% {
    -webkit-transform: rotateZ(6deg);
  }
  35% {
    -webkit-transform: rotateZ(-4deg);
  }
  37% {
    -webkit-transform: rotateZ(2deg);
  }
  39% {
    -webkit-transform: rotateZ(-1deg);
  }
  41% {
    -webkit-transform: rotateZ(1deg);
  }

  43% {
    -webkit-transform: rotateZ(0);
  }
  100% {
    -webkit-transform: rotateZ(0);
  }
}

@keyframes ring {
  0% {
    transform: rotate(0);
  }
  1% {
    transform: rotate(30deg);
  }
  3% {
    transform: rotate(-28deg);
  }
  5% {
    transform: rotate(34deg);
  }
  7% {
    transform: rotate(-32deg);
  }
  9% {
    transform: rotate(30deg);
  }
  11% {
    transform: rotate(-28deg);
  }
  13% {
    transform: rotate(26deg);
  }
  15% {
    transform: rotate(-24deg);
  }
  17% {
    transform: rotate(22deg);
  }
  19% {
    transform: rotate(-20deg);
  }
  21% {
    transform: rotate(18deg);
  }
  23% {
    transform: rotate(-16deg);
  }
  25% {
    transform: rotate(14deg);
  }
  27% {
    transform: rotate(-12deg);
  }
  29% {
    transform: rotate(10deg);
  }
  31% {
    transform: rotate(-8deg);
  }
  33% {
    transform: rotate(6deg);
  }
  35% {
    transform: rotate(-4deg);
  }
  37% {
    transform: rotate(2deg);
  }
  39% {
    transform: rotate(-1deg);
  }
  41% {
    transform: rotate(1deg);
  }

  43% {
    transform: rotate(0);
  }
  100% {
    transform: rotate(0);
  }
}

.explain-page {
  position: relative;
}

.arrow {
  width: 4rem;
  /* position: absolute; */
}

.arrow1 {
  grid-column: 3 / 4;
  grid-row: 1 / 2;
  transform: rotate(150deg);
}

.arrow2 {
  grid-column: 6 /7;
  grid-row: 1 / 2;
  transform: rotate(100deg);
}

.arrow3 {
  grid-column: 6 / 7;
  grid-row: 3 / 4;
  /* align-self: flex-end; */
  transform: rotate(-10deg);
}

.arrow4 {
  grid-column: 4 /5;
  grid-row: 5/6;
  transform: rotate(-60deg);
}

.arrow5 {
  grid-column: 2 / 3;
  grid-row: 3 /4;
  transform: rotate(240deg);
}

.circle {
  width: 7rem;
  height: 7rem;
  margin-top: 1rem;
  border-radius: 10rem;
  text-align: center;
  color: white;
  font-size: 1.5rem;
  font-weight: 550;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 1.6%;
  transition: all 0.3s ease;
  /* animation: floatAnimation 3s ease-in-out infinite; */
  box-shadow: 0 5px 7px rgba(0, 0, 0, 0.2);
  background-color: #eb5781;
}

.circle:hover {
  box-shadow: 0 15px 9px rgba(0, 0, 0, 0.4);
  width: 8rem;
  height: 8rem;
  padding: 2%;
}

.circle-container {
  /* position: absolute;
  top: 20%;
  left: 50%;
  transform: translateX(-50%); */
  width: 100%; /* Adjust the width to fit your design */
  height: 27rem; /* Adjust the height to fit your design */
  margin-inline: auto; /* Center the container */
  margin-top: 1rem;
  display: grid;
  grid-template-columns: repeat(7, 14.3%);
  grid-template-rows: repeat(5, 20%);
}

.svg-circle-container {
  width: 100%; /* Adjust the width to fit your design */
  height: 28rem; /* Adjust the height to fit your design */
  transition: all 0.3s ease;
}

.circle-svg {
  transition: all 0.3s ease;
  filter: drop-shadow(0 5px 7px rgba(0, 0, 0, 0.2));
  animation-play-state: paused;
  /* box-shadow: 0 5px 7px rgba(0, 0, 0, 0.2); */
}

.circle-svg:hover {
  filter: drop-shadow(0 15px 9px rgba(0, 0, 0, 0.4));
  /* transform: scale(1.7); */
  padding: 2%;
  stroke: #eb5781;
  stroke-width: 3;
}

.circle0 {
  grid-column-start: 6;
  grid-row-start: 2;
}

.circle1 {
  grid-column-start: 5;
  grid-row-start: 4;
}

.circle2 {
  grid-column-start: 3;
  grid-row-start: 4;
}

.circle3 {
  grid-column-start: 2;
  grid-row-start: 2;
}

.circle4 {
  grid-column-start: 4;
  grid-row-start: 0;
}

@keyframes floatAnimation {
  0% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-8px);
  }
  100% {
    transform: translateY(0);
  }
}

.posCenterBtn {
  /* position: absolute;
  bottom: 5%;
  left: 50%;
  transform: translateX(-50%); */
  margin-top: var(--thePos);
}
.posLeftBtn {
  /* margin-left:5rem; */
  margin-left: -28rem;
}

.startBtn {
  border: none;
  cursor: pointer;
  width: 6rem;
  height: 3rem;
  color: #ffffff;
  background-color: #ff87ab;
  font-size: 1.6rem;
  border-radius: 100px;
  min-width: 4rem;
}
.startBtn {
  animation: borderPulse 4000ms infinite ease-out;
}

.startBtn:hover,
.startBtn:focus {
  animation: borderPulse 4000ms infinite ease-out, hoverShine 200ms;
}
@keyframes borderPulse {
  0% {
    box-shadow: inset 0px 0px 0px 5px rgba(255, 255, 255, 0.4),
      0px 0px 0px 0px rgba(255, 255, 255, 1);
  }
  35% {
    box-shadow: inset 0px 0px 0px 3px rgba(117, 117, 255, 0.2),
      0px 0px 0px 10px rgba(255, 255, 255, 0);
  }
  50% {
    box-shadow: inset 0px 0px 0px 5px rgba(255, 255, 255, 0.4),
      0px 0px 0px 0px rgba(255, 255, 255, 1);
  }
  75% {
    box-shadow: inset 0px 0px 0px 3px rgba(117, 117, 255, 0.2),
      0px 0px 0px 10px rgba(255, 255, 255, 0);
  }
  100% {
    box-shadow: inset 0px 0px 0px 5px rgba(255, 255, 255, 0.4),
      0px 0px 0px 0px rgba(255, 255, 255, 1);
  }
}

@keyframes hoverShine {
  0% {
    background-image: linear-gradient(
      135deg,
      rgba(255, 255, 255, 0.4) 0%,
      rgba(255, 255, 255, 0) 50%,
      rgba(255, 255, 255, 0) 100%
    );
  }
  50% {
    background-image: linear-gradient(
      135deg,
      rgba(255, 255, 255, 0) 0%,
      rgba(255, 255, 255, 0.4) 50%,
      rgba(255, 255, 255, 0) 100%
    );
  }
  100% {
    background-image: linear-gradient(
      135deg,
      rgba(255, 255, 255, 0) 0%,
      rgba(255, 255, 255, 0) 50%,
      rgba(255, 255, 255, 0.4) 100%
    );
  }
}
/* Declare border pulse animation */

.white-window {
  width: 39rem;
  height: 35rem;
  background: #fff;
  border-radius: 3rem;
  box-shadow: 0 15px 20px -20px rgba(0, 0, 0, 0.4);
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}

.hide-bg {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background: #c7c5c5;
  opacity: 0.8;
  width: 39rem;
  height: 35rem;
  border-radius: 3rem;
}

.explain-text {
  font-size: 1.4rem;
  color: rgb(79, 77, 77);
  margin: 0;
  display: inline;
  text-align: center;
}

.bold-text {
  font-size: 2.5rem;
  font-weight: bold;
  display: inline;
  margin: 1rem;
}

.center-text {
  text-align: center;
  width: 35rem;
}

.goalBtn {
  position: absolute;
  bottom: 5%;
  left: 5%;
}

.info-text-goal {
  background-color: none;
  border-radius: 30px;
  height: 6%;
  transition: background-color 0.3s ease;
  margin: 2%;
  padding: 0.5%;
}

.info-text-goal:hover {
  background-color: #dbdbdb;
}

.fade-in {
  /* animation: fade 2s linear; */
}

@keyframes fade {
  from {
    opacity: 0; /* Start with opacity 0 (fully transparent) */
  }
  to {
    opacity: 1; /* End with opacity 1 (fully opaque) */
  }
}

.explain-subj-container {
  margin-top: 0rem;
}

.talk-text {
  margin: 3%;
  animation: floatAnimation 3s ease-in-out infinite;
  color: #ff5d8f;
  font-size: 3rem;
  border-radius: 10px;
  top: 1.5%;
  text-decoration: none;
  position: relative;
  cursor: default;
  width: fit-content;
}
.talk-text:hover {
  color: #ff5d8f;
}

.talk-text:hover::before {
  visibility: visible;
  transform: scaleX(1);
}

.talk-text::before {
  content: "";
  position: absolute;
  width: 100%;
  height: 2px;
  bottom: 0;
  background-color: #ff5d8f;
  visibility: hidden;
  transform: scaleX(0);
  transition: all 0.3s ease-in-out 0s;
}

.page5-flex {
  justify-content: flex-start;
  flex-direction: column;
  padding-top: 5rem;
  box-sizing: border-box;
}

.margin-auto {
  margin: auto;
}
</style>
