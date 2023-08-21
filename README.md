# Creating a GIF using JavaScript

A basic example of creating and displaying an animated GIF using canvas content.

1. Include the necessary libraries:

    ```html
    <script type="text/javascript" src="LZWEncoder.js"></script>
    <script type="text/javascript" src="NeuQuant.js"></script>
    <script type="text/javascript" src="GIFEncoder.js"></script>
    <script type="text/javascript" src="b64.js"></script>
    ```
    
2. Add multiple canvases to the document:

    ```html
    <canvas id="canvas1" width="100" height="100"></canvas>
    <canvas id="canvas2" width="100" height="100"></canvas>
    <canvas id="canvas3" width="100" height="100"></canvas>
    ```

3. Add a container:

    ```html
    <div id="container"></div>
    ```

4. Use JavaScript to add the content from the canvases to a `gif`:

    ```javascript
    const canvas1 = document.getElementById('canvas1');
    const context1 = canvas1.getContext('2d');
    
    context1.fillStyle = "red";
    context1.fillRect(0, 0, 100, 100);
    
    const canvas2 = document.getElementById('canvas2');
    const context2 = canvas2.getContext('2d');
    
    context2.fillStyle = "green";
    context2.fillRect(0, 0, 100, 100);
    
    const canvas3 = document.getElementById('canvas3');
    const context3 = canvas3.getContext('2d');
    
    context3.fillStyle = "blue";
    context3.fillRect(0, 0, 100, 100);
    
    let encoder = new GIFEncoder();
    encoder.setRepeat(0);                
    encoder.setDelay(500);
    encoder.start();
    
    encoder.addFrame(context1);
    encoder.addFrame(context2);
    encoder.addFrame(context3);
    
    encoder.finish();
    
    let binaryData = encoder.stream().getData();
    let dataUrl = 'data:image/gif;base64,'+encode64(binaryData);
    
    const image = document.createElement("img");
    
    image.src = dataUrl;
    document.getElementById('container').appendChild(image);
    ```

The full working code is in the [`canvas-to-gif.html`](canvas-to-gif.html) file. 

***

## Repo Resources

* [LZW Encoder](https://gist.github.com/revolunet/843889)
* [NewQuant](https://github.com/unindented/neuquant-js)
* [gifencoder](https://github.com/eugeneware/gifencoder)
* [base54.js](https://github.com/dankogai/js-base64)

<a href="https://codeadam.ca">
<img src="https://codeadam.ca/images/code-block.png" width="100">
</a>
