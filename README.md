# Basic Example of react Image upload

In this example we create a very simple form with one field for uploading an image (maybe for a profile picture?)

We then put it in a useState called filebase64 that you could use like any other input field 

there's nothing fancy about the form submit and nother fancy about the ```<input type="file">```

### But how to use it
To use it is simply. Save the value as if someone typed it. Then use it in the src of your image.
or else the source of your video or sound. 

See example on how to do all three.

### Where's the magic.

The magic is to have an input that looks like this:<br />
```  <input type="file" onChange={(e)=> convertFile(e.target.files)} />```


And then in your component add: 
```
  function convertFile(files: FileList|null) {
    if (files) {
      const fileRef = files[0] || ""
      const fileType: string= fileRef.type || ""
      console.log("This file upload is of type:",fileType)
      const reader = new FileReader()
      reader.readAsBinaryString(fileRef)
      reader.onload=(ev: any) => {
        // convert it to base64
        setFileBase64(`data:${fileType};base64,${btoa(ev.target.result)}`)
      }
    }
  }
  ```

  Which updates a setFileBase64 useState
