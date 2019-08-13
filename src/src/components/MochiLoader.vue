<template>
  <div class="loader">Loading...</div>
</template>

<script>
export default {
  name: "mochi-loader"
};
</script>

<style lang="scss" scoped>
$mochi_color: rgb(22, 150, 50);
$mochi_border_color: rgba(22, 150, 50, 0.2);
$border_width: 8px;
$size: 32px;

.loader,
.loader:after {
  border-radius: 50%;
  width: $size;
  height: $size;
}
.loader {
  margin: 0;
  font-size: 10px;
  position: relative;
  text-indent: -9999em;
  border-top: $border_width solid $mochi_border_color;
  border-right: $border_width solid $mochi_border_color;
  border-bottom: $border_width solid $mochi_border_color;
  border-left: $border_width solid $mochi_color;
  -webkit-transform: translateZ(0);
  -ms-transform: translateZ(0);
  transform: translateZ(0);
  -webkit-animation: load8 1.1s infinite linear;
  animation: load8 1.1s infinite linear;
}
@-webkit-keyframes load8 {
  0% {
    -webkit-transform: rotate(0deg);
    transform: rotate(0deg);
  }
  100% {
    -webkit-transform: rotate(360deg);
    transform: rotate(360deg);
  }
}
@keyframes load8 {
  0% {
    -webkit-transform: rotate(0deg);
    transform: rotate(0deg);
  }
  100% {
    -webkit-transform: rotate(360deg);
    transform: rotate(360deg);
  }
}
</style>