<script>
  import { defaultExample, formatExample } from "$lib/modules/formatting";
  import TiDeleteOutline from "svelte-icons/ti/TiDeleteOutline.svelte";
  export let formats;
  export let deleteHandler;
</script>

<table>
  <thead>
    <th class="align_left narrow_column">Format Tag</th>
    <th class="align_left wide_column">Format Code</th>
    <th class="align_left wide_column">Example Input</th>
    <th class="align_right wide_column">Example Output</th>
    <th><!--actions --></th>
  </thead>
  {#each formats as format}
    <tr>
      <td>{format.formatTag} </td>
      <td>{format.formatCode} </td>
      <td>
        <input
          id="id_format_row{format.formatTag}"
          placeholder={format.exampleInput || defaultExample(format.valueType)}
          bind:value={format.userInput}
          on:blur={(format.userInput = undefined)}
          class="align_left input_box"
        />
      </td>
      <td class="align_right">{formatExample(format)}</td>
      <td>
        <button type=button on:click={() => deleteHandler(format)} tooltip="Remove">
          <div class="deleteIcon"><TiDeleteOutline /></div>
        </button>
    </td>
    </tr>
  {/each}
</table>

<style>
  .deleteIcon {
    color: var(--red-600);
    width: 16px;
    cursor: pointer;
  }
  
  button {
    background: none;
    border: none;
    cursor: pointer;
    vertical-align: middle;
  }

  .deleteIcon:hover {
    color: var(--red-700);
  }

  table {
  font-size: 14px;
  border-collapse: collapse;
  font-family: sans-serif;
  /* Offset the cell padding to get the outside edges aligned w/ the parent */
  margin-left: -8px;
  width: calc(100% + 16px);
}
th {
  max-width: 1px;
  font-weight: 600;
  padding: 0px 8px;
  text-overflow: ellipsis;
  overflow: hidden;
}
td {
  padding: 4px 8px;
  overflow: hidden;
  text-overflow: ellipsis;
}
/* tr:hover {
  background-color: rgb(247, 249, 250);
} */
.align_left {
  text-align: left;
}
.align_right {
  text-align: right;
}
.wide_column {
  min-width: 120px;
}
.narrow_column {
  max-width: 60px;
}
.input_box {
  width: 100%;
}

input {
  box-sizing: border-box;
  border-radius: 4px 4px 4px 4px;
  border: 1px solid var(--grey-300);
  padding: 0.25em 0.25em 0.25em 0.25em;
  margin-left: auto;
  width: 65%;
  padding: 0.35em;
  color: var(--grey-999);
  -webkit-appearance: none;
  -moz-appearance: none;
  vertical-align: middle;
  font-size: 12px;
}
input:required {
  box-shadow: none;
}
input:focus {
  outline: none;
}


</style>
