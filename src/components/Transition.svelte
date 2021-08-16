<script>
  import { springIn, springOut } from "svelte-helpers/spring-transitions";

  const currentYTranslation = (node) => {
    const existingTransform = getComputedStyle(node).transform;
    return existingTransform == "none" ? 0 : new DOMMatrix(existingTransform).f;
  };

  const SPRING_IN = { stiffness: 0.1, damping: 0.1 };
  const animateIn = (node) => {
    const { duration, tickToValue } = springIn(-40, 5, SPRING_IN);
    return {
      duration: duration,
      css: (t) => `transform: translateY(${tickToValue(t)}px)`,
    };
  };

  const SPRING_OUT = { stiffness: 0.3, damping: 0.5, precision: 10 };
  const animateOut = (node) => {
    const current = currentYTranslation(node);
    const { duration, tickToValue } = springOut(
      current ? current : 0,
      30,
      SPRING_OUT
    );

    return {
      duration: duration,
      css: (t) => `transform: translateY(${tickToValue(t)}px)`,
    };
  };
</script>

<div in:animateIn out:animateOut class="wrapper" style="padding-bottom: 5em;">
  <slot />
</div>
