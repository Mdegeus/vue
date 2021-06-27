<template>
  <div v-bind="GetQuote()"></div>

  <h3 class="anime"></h3>
  <h3 class="quote">Getting Quote</h3>
</template>

<script>

export default {
  name: "AnimeQuote",
  methods: {
    GetQuote() {
      fetch("https://animechan.vercel.app/api/random")
        .then(function (response) {
          if (!response.ok) {
            return false;
          }
          return response.json();
        })
        .then(function (quote) {
          if (quote) {
            if (quote.quote.length < 150) {
            document.querySelector(".anime").textContent =
              quote.anime + ",  " + quote.character;
            document.querySelector(".quote").textContent = quote.quote;
            }else{
              document.querySelector(".quote").textContent = "Couldn't get Quote :(";
            }
        }
        }).catch(function (){
          document.querySelector(".quote").textContent = "Couldn't get Quote :(";
        })
    },
  },
};
</script>

<style>
h3 {
  font-family: "LibreFranklin-Italic", "sans-serif";
}

.anime {
  color: rgb(44, 44, 44);
  margin: 0;
  padding-top: 0.5em;
}
.quote {
  padding-top: 0.25em;
  padding-bottom: 0.5em;
  margin: 0;
}
</style>