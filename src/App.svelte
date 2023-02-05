<script>
  import { copy } from "svelte-copy";
  import "./btn.scss";
  let text = "Submit",
    padding = 10,
    margin = 0,
    border = 1,
    borderColor = "#000",
    borderRadius = 5,
    bgColor = "#fff",
    color = "#000",
    fontSize = 20,
    boxShadowX = 4,
    boxShadowY = 4,
    boxShadowColor = "#000",
    boxShadowBlur = 0;
  let k = 0,
    m = 0;
  let handleClick = () => {
    k = 1;
    setTimeout(() => {
      k = 0;
    }, 800);
  };
  let handleClickInLine = () => {
    m = 1;
    setTimeout(() => {
      m = 0;
    }, 800);
  };
  $: copyText =
    `<button class="btn">${text}</button> \n` +
    "<" +
    "style" +
    ">" +
    `
    .btn{
      padding:${padding}px;
      margin:${margin}px;
      border:${border}px solid ${borderColor};
      border-radius:${borderRadius}px;
      background-color:${bgColor};
      color:${color};
      font-size:${fontSize}px;
      box-shadow:${boxShadowX}px ${boxShadowY}px ${boxShadowBlur}px ${boxShadowColor};

    }
  ` +
    "</" +
    "style" +
    ">";
  $: inLineText = `
    <button  style="padding:${padding}px;margin:${margin}px;border:${border}px solid ${borderColor};border-radius:${borderRadius}px;background-color:${bgColor};color:${color};font-size:${fontSize}px;box-shadow:${boxShadowX}px ${boxShadowY}px ${boxShadowBlur}px ${boxShadowColor};">${text}</button>
    `;
</script>

<main>
  <div class="heading">
    <h1>Button Generator Using Svelte Js</h1>
  </div>
  <div class="container">
    <div class="formData">
      <div>
        <label for="Text">Text : </label>
        <input type="text" bind:value={text} />
      </div>
      <div>
        <label for="Text">Padding : </label>
        <input type="number" bind:value={padding} />
      </div>
      <div>
        <label for="Text">Margin : </label>
        <input type="number" bind:value={margin} />
      </div>
      <div>
        <label for="Text">Border : </label>
        <input type="number" bind:value={border} />
      </div>
      <div>
        <label for="Text">Border Colors : </label>
        <input type="color" bind:value={borderColor} />
      </div>
      <div>
        <label for="Text">Border-Radius : </label>
        <input type="number" bind:value={borderRadius} />
      </div>
      <div>
        <label for="Text">Background-Color : </label>
        <input type="color" bind:value={bgColor} />
      </div>
      <div>
        <label for="Text">Color : </label>
        <input type="color" bind:value={color} />
      </div>
      <div>
        <label for="Text">Font-Size : </label>
        <input type="number" bind:value={fontSize} />
      </div>
      <div>
        <label for="Text">Box-Shadow-X : </label>
        <input type="number" bind:value={boxShadowX} />
      </div>
      <div>
        <label for="Text">Box-Shadow-Y : </label>
        <input type="number" bind:value={boxShadowY} />
      </div>
      <div>
        <label for="Text">Box-Shadow-Blur : </label>
        <input type="number" bind:value={boxShadowBlur} />
      </div>
      <div>
        <label for="Text">Box-Shadow-Color : </label>
        <input type="color" bind:value={boxShadowColor} />
      </div>
    </div>
    <div class="btncopy">
      <div class="demo">
        <button
          class="btn"
          style={`padding:${padding}px;margin:${margin}px;border:${border}px solid ${borderColor};border-radius:${borderRadius}px;background-color:${bgColor};color:${color};font-size:${fontSize}px;box-shadow:${boxShadowX}px ${boxShadowY}px ${boxShadowBlur}px ${boxShadowColor};`}
        >
          {text}
        </button>
      </div>
      <button class="btn-copy" on:click={handleClick} use:copy={copyText}
        >{k === 0 ? "Copy Code" : "Copied"}</button
      >
      <button
        class="btn-copy"
        on:click={handleClickInLine}
        use:copy={inLineText}>{m === 0 ? "Inline Css" : "Copied "}</button
      >
    </div>
  </div>
</main>
