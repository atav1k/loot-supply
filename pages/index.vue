<template>
  <article>
    <div class="cols minvh-100 logomark bg-blend-overlay">
      <div class="col-12 flex">
        <svg id="loot" class="bg-blend-overlay" width="100%" height="100%" viewBox="0 0 1000 250" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" xml:space="preserve" xmlns:serif="http://www.serif.com/" style="fill-rule:evenodd;clip-rule:evenodd;stroke-linejoin:round;stroke-miterlimit:1.41421;">
          <g transform="matrix(1.19279,0,0,1.19279,-206.799,-449.822)">
            <path d="M173.373,382.84L237.021,382.84L237.021,530.296L338.685,530.296L338.685,580.984L173.373,580.984L173.373,382.84Z" style="fill-rule:nonzero;"/>
            <path d="M538.269,405.592C556.893,423.064 566.205,448.504 566.205,481.912C566.205,515.32 556.893,540.76 538.269,558.232C519.645,575.704 493.245,584.44 459.069,584.44C424.893,584.44 398.541,575.752 380.013,558.376C361.485,541 352.221,515.512 352.221,481.912C352.221,448.312 361.485,422.824 380.013,405.448C398.541,388.072 424.893,379.384 459.069,379.384C493.245,379.384 519.645,388.12 538.269,405.592ZM427.965,439.288C420.861,447.544 417.309,458.68 417.309,472.696L417.309,491.128C417.309,505.144 420.861,516.28 427.965,524.536C435.069,532.792 445.437,536.92 459.069,536.92C472.701,536.92 483.117,532.792 490.317,524.536C497.517,516.28 501.117,505.144 501.117,491.128L501.117,472.696C501.117,458.68 497.517,447.544 490.317,439.288C483.117,431.032 472.701,426.904 459.069,426.904C445.437,426.904 435.069,431.032 427.965,439.288Z" style="fill-rule:nonzero;"/>
            <path d="M778.173,405.592C796.797,423.064 806.109,448.504 806.109,481.912C806.109,515.32 796.797,540.76 778.173,558.232C759.549,575.704 733.149,584.44 698.973,584.44C664.797,584.44 638.445,575.752 619.917,558.376C601.389,541 592.125,515.512 592.125,481.912C592.125,448.312 601.389,422.824 619.917,405.448C638.445,388.072 664.797,379.384 698.973,379.384C733.149,379.384 759.549,388.12 778.173,405.592ZM667.869,439.288C660.765,447.544 657.213,458.68 657.213,472.696L657.213,491.128C657.213,505.144 660.765,516.28 667.869,524.536C674.973,532.792 685.341,536.92 698.973,536.92C712.605,536.92 723.021,532.792 730.221,524.536C737.421,516.28 741.021,505.144 741.021,491.128L741.021,472.696C741.021,458.68 737.421,447.544 730.221,439.288C723.021,431.032 712.605,426.904 698.973,426.904C685.341,426.904 674.973,431.032 667.869,439.288Z" style="fill-rule:nonzero;"/>
            <path d="M946.941,433.528L946.941,580.984L883.293,580.984L883.293,433.528L818.205,433.528L818.205,382.84L1011.74,382.84L1011.74,433.528L946.941,433.528Z" style="fill-rule:nonzero;"/>
          </g>
        </svg>
      </div>
    </div>
  </article>
</template>
<style>
:root {
  --font-family: 'Archivo Black', sans-serif;
  --columns-width: 120rem;
  --column-gutter: var(--space-4);
  --red: #E84058;
  --yellow: #F8A828;
  --blue: #5048F0
}

* {
}

.logomark {
  position: relative;
  overflow: hidden;
  --color: var(--red);
}

.logomark:before {
  content: "";
  position: absolute;
  width: 200%;
  height: 200%;
  top: -50%;
  left: -50%;
  z-index: -1;
  background: url('https://s3-us-west-2.amazonaws.com/s.cdpn.io/1908563/bg-loot.svg');
  background-size: 180px 150px;
  transform: rotate(-15deg);
  background-color: var(--color);
}

#loot path:hover {
  --color: var(--black);
}

div {
  align-items: center;
}

#loot path {
  fill: var(--color);
  opacity: 1;
  transition: fill 2s;
  mix-blend-mode: difference;
}
</style>
<script>
export default {
  mounted: function() {
    const svg = document.getElementById('loot')
    const warp = new Warp(svg)

    warp.interpolate(2)
    warp.transform(([ x, y ]) => [ x, y, y ])

    let offset = 0
    function animate()
    {
    	warp.transform(([ x, y, oy ]) => [ x, oy + 4 * Math.sin(x / 24 + offset), oy ])
    	offset += 0.15
    	requestAnimationFrame(animate)
    }

    animate()
  },
};
</script>
