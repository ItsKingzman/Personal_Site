<div class="flex content-center justify-center h-screen">
	<ul class="m-auto text-4xl leading-loose text-center dark:text-cyan-50">
		<li class="gradient-border"><a href="fun/gradients">GRADIENTS</a></li>
		<li><a href="fun/circular">CIRCULAR</a></li>
		<li><a href="fun/m1">M1 &#8249;-&#8250; CK</a></li>
		<li><a href="fun/zeal">ZEAL</a></li>
	</ul>
</div>

<style>
.gradient-border {
  --borderWidth: 3px;
  background: #1D1F20;
  position: relative;
  border-radius: var(--borderWidth);
}
.gradient-border:after {
  content: '';
  position: absolute;
  top: calc(-1 * var(--borderWidth));
  left: calc(-1 * var(--borderWidth));
  height: calc(100% + var(--borderWidth) * 2);
  width: calc(100% + var(--borderWidth) * 2);
  background: linear-gradient(60deg, #f79533, #f37055, #ef4e7b, #a166ab, #5073b8, #1098ad, #07b39b, #6fba82);
  border-radius: calc(2 * var(--borderWidth));
  z-index: -1;
  animation: animatedgradient 3s ease alternate infinite;
  background-size: 300% 300%;
}


@keyframes animatedgradient {
  0% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
  100% {
    background-position: 0% 50%;
  }
}


</style>