<!-- Example -->
<!-- URL: https://www.google.com/search?q=site%3Aytn.co.kr+%22Corn%22&sca_esv=556766949&sxsrf=AB5stBh6umVNjc7EIXb70JcofM10lQKqjw%3A1692022015372&source=lnt&tbs=cdr%3A1%2Ccd_min%3A1%2F1%2F2011%2Ccd_max%3A12%2F31%2F2019&tbm= -->
<script lang="ts">
  // your script goes here

</script>

<svelte:head>
  <title>Specific Search</title>
</svelte:head>

<div>
  <header>
    <h1>Specific Search</h1>
  </header>
  <main>
    <section id="input-section">
      <label for="website">Website</label>
      <input type="url" name="website" id="input-website">
      <br>
      <label for="keyword">Search Keyword</label>
      <input type="text" name="keyword" id="input-keyword">
    </section>
    <section id="action-section">
      <button id="search-button">
        Search
      </button>
    </section>
  </main>
  <footer>
    <p>Copyright 2023, Made by <a href="https://github.com/lebrancconvas" target="_blank">Poom Yimyuean (@lebrancconvas)</a></p>
  </footer>
</div>

<style>
  /* your styles go here */
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'Noto Sans JP', sans-seif
  }

  header {
    text-align: center;
  }

  button {
    outline: none;
    border: none;
    border-radius: 10px;
    padding: 5px;
    background-color: rgb(27, 193, 27);
    font-size: 28px;
    cursor: pointer;
  }

  main {
    text-align: center;
  }

  button:active {
    transform: scale(0.98);
  }

  footer {
    text-align: center;
    position: fixed;
    bottom: 0;
    left: 0;
    width: 100%;
    height: 50px;
  }

  footer p {
    font-size: 17px;
  }
</style>

<!-- markup (zero or more items) goes here -->
