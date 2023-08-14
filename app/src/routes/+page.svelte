<!-- Example -->
<!-- URL: https://www.google.com/search?q=site%3Aytn.co.kr+%22Corn%22&sca_esv=556766949&sxsrf=AB5stBh6umVNjc7EIXb70JcofM10lQKqjw%3A1692022015372&source=lnt&tbs=cdr%3A1%2Ccd_min%3A1%2F1%2F2011%2Ccd_max%3A12%2F31%2F2019&tbm= -->
<script lang="ts">
  // your script goes here
  import type { IKeyword } from '../@types';
  let searchWebsite = ''; // site:

  let searchKeywords: IKeyword[] = [
    {
      keyword: '',
      strict: false
    }
  ]

  let fromTime = ''; // after:
  let toTime = ''; // before:

  let addKeyword = () => {
    searchKeywords = [
      ...searchKeywords,
      {
        keyword: '',
        strict: false
      }
    ]
  };

  let clearKeyword = (keyword: IKeyword) => {
    alert('This Feature is not available yet');
  }

  let removeKeyword = (index: number) => {
    if(searchKeywords.length === 1) {
      alert('You cannot remove because you have only one keyword');
      return;
    }
    searchKeywords = searchKeywords.filter((keyword, i) => i !== index);
  };

  let handleSearch = () => {
    // Web
    let processFromTime = `${fromTime.trim().split('-')[1]}/${fromTime.trim().split('-')[2]}/${fromTime.trim().split('-')[0]}`;
    let processToTime = `${toTime.trim().split('-')[1]}/${toTime.trim().split('-')[2]}/${toTime.trim().split('-')[0]}`;

    let resultWeb = '';
    let resultTime = '';

    if(searchWebsite !== '') {
      resultWeb = `site:${searchWebsite}`;
    }

    // From Time
    if(fromTime !== '' && toTime !== '') {
      resultTime = `&tbs=cdr:1,cd_min:${processFromTime},cd_max:${processToTime}&tbm=`;
    } else if(fromTime !== '') {
      resultTime = `&tbs=cdr:1,cd_min:${processFromTime}&tbm=`;
    } else if(toTime !== '') {
      resultTime = `&tbs=cdr:1,cd_max:${processToTime}&tbm=`;
    } else {
      resultTime = '';
    }

    // Keywords
    let processSearchKeywords = searchKeywords
      .filter((keyword: IKeyword) => keyword.keyword.trim() !== '')
      .map((keyword: IKeyword) => keyword.strict ? `"${keyword.keyword}"` : keyword.keyword)

    let keywords = processSearchKeywords.join('+%2B+');



    let urlResult = `https://google.com/search?q=${resultWeb}+${keywords}${resultTime}`;
    window.open(urlResult, '_blank');
  }

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
      <input type="url" name="website" id="input-website" bind:value={searchWebsite}>
      <br>
      <label for="fromTime">From</label>
      <input type="date" name="fromTime" id="input-fromTime" bind:value={fromTime}>
      <label for="toTime">To</label>
      <input type="date" name="toTime" id="input-toTime" bind:value={toTime}>
      <br>
      {#each searchKeywords as keyword, index}
      <div id="keyword">
        <label for="keyword">Search Keyword</label>
        <input type="text" name="keyword" id="input-keyword" bind:value={searchKeywords[index].keyword}>
        <input type="checkbox" name="isStrict" id="input-check-isstrict" bind:checked={searchKeywords[index].strict}>
        <button on:click={() => clearKeyword(keyword)}>Clear</button>
        <button on:click={() => removeKeyword(index)}>Remove</button>
        <br>
      </div>
      {/each}
    </section>
    <br><br>
    <section id="action-section">
      <button on:click={addKeyword}>Add Keyword</button>
      <button id="search-button" on:click={handleSearch}>
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
    cursor: pointer;
  }

  main {
    text-align: center;
  }

  input {
    outline: none;
    border: none;
    border-radius: 10px;
    padding: 5px;
    font-size: 20px;
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
    background-color: rgb(255, 255, 255);
  }

  footer p {
    font-size: 17px;
  }
</style>

<!-- markup (zero or more items) goes here -->
