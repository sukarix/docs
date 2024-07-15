# File Upload

<!-- toc -->

## Introduction

The `Receiver` class in Sukarix is designed to handle file uploads efficiently. It provides methods for saving uploaded
files and preparing upload directories, ensuring that your application can manage file uploads seamlessly.

## Configuration

To use the `Receiver` class, you need to configure it in the `classes.ini` file:

```ini
receiver = \Helpers\Receiver
```

## Methods

### `saveUploadedFile`

This method saves the uploaded file to the specified destination. It checks the environment to decide whether to
use `rename` or `move_uploaded_file` for saving the file.

### `prepareUploadDirectory`

This method prepares the upload directory by creating it if it does not exist. It throws a `RuntimeException` if the
directory cannot be created.

## Example Usage

To use the `Receiver` class for handling file uploads, you can get an instance from the `Injector` and use
the `\Web::instance()->receive` method to process the uploaded files.

```php
/**
 * @var Receiver $receiver
 */
$receiver = Injector::instance()->get('receiver');

\Web::instance()->receive(static function(&$file, &$formFieldName) use (&$action, &$receiver) {
    if (0 === $file['size']) {
        return false;
    }
    
    $uploadDirectory = 'path/to/upload/directory';
    $receiver->prepareUploadDirectory($uploadDirectory);
    
    $destination = $uploadDirectory . '/' . $file['name'];
    return $receiver->saveUploadedFile($file, $destination);
});
```

The `Receiver` class ensures that file uploads are handled efficiently and securely, with proper directory preparation
and file movement based on the environment. This setup allows for easy management of uploaded files in your Sukarix
application.
