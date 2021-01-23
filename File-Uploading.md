## File Uploading

  Unic framework provide simplest way to upload files on the server.

### Get Files Information

  Uploaded files information stored in the `$request->files` object.

  - `$request->files->file_var['name']` : store the original name of uploaded files.
  - `$request->files->file_var['type']` : store mime type of the file, if the browser provided this information. An example would be `image/gif`.
  - `$request->files->file_var['size']` : store size, in bytes, of the uploaded file.
  - `$request->files->file_var['tmp_name']` : store the temporary filename of the file in which the uploaded file was stored on the server.
  - `$request->files->file_var['error']` : store the error code associated with this file upload.

### Example

  - Create a HTML form for file uploading.

```html
<form action="<?= url('/upload'); ?>" method="post" enctype="multipart/form-data">
  <input type="file" name="image">
  <input type="submit" value="Upload Image" name="submit">
</form>
```
  - Upload files on server.

```php
class view extends Views {
  function home(Request $req) {
    //File source path
    $source = $req->files->image['tmp_name'];

    //File destination path
    $destination = BASEPATH.'/application/app/static/img/'.$req->files->image['name'];

    //Upload files
    if($req->files->upload($source, $destination)) {
      return $this->response('File uploaded');
    } else {
      return $this->response('Error: File not uploaded');
    }
  }
}
```
