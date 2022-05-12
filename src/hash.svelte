<script>


import { onMount } from "svelte";
import axios from "axios"
import {sha256} from "js-sha256"


export let keyword;
let data = {};

$:getKeyword(keyword)



const getKeyword = async(keyword) => {
    const keywordHash = sha256(keyword)

    try {
    const response = await axios.get(`http://127.0.0.1:8000/api/v2/index/${keywordHash}`)
    data = response.data
}
catch(error) {
    console.log(error);
}
}

</script>

<table id="myTable">

    <tr>
      <th>Source</th>
      <th>Datahash</th>
      <th>Rotation</th>
      <th>Nonce</th>
      <th>Target</th>
      <th>User</th>
      <th>TimeStamp</th>
    </tr>
    {#each Object.values(data) as row}

    <tr>
    <td>{row.source}</td>
    <td>{row.datahash}</td>
    <td>{row.rotation}</td>
    <td>{row.n}</td>
    <td>{row.target}</td>
    <td>{row.user}</td>
    <td>{row.timestamp}</td>
    </tr>



    {/each}
  

</table>







