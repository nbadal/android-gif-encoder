android-gif-encoder
===================

An animated GIF encoder for Android, without any native code required. Based on the J2ME encoder posted here: http://www.jappit.com/blog/2008/12/04/j2me-animated-gif-encoder/ with the addition of dirty rectangle support.

## Example usage:

```java
public byte[] generateGIF() {
    ArrayList<Bitmap> bitmaps = adapter.getBitmapArray();
    ByteArrayOutputStream bos = new ByteArrayOutputStream();
    AnimatedGifEncoder encoder = new AnimatedGifEncoder();
    encoder.start(bos);
    for (Bitmap bitmap : bitmaps) {
        encoder.addFrame(bitmap);
    }
    encoder.finish();
    return bos.toByteArray();
}

public void saveGif() {
    try {
        FileOutputStream outStream = new FileOutputStream("/sdcard/test.gif");
        outStream.write(generateGIF());
        outStream.close();
    } catch(Exception e) {
        e.printStackTrace();
    }
}
```
