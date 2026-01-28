# ⚠️ ARCHIVED / UNMAINTANED
Archived / Unmaintained: This project was originally published in 2008 as a small Android-compatible adaptation of an existing Java GIF encoder, at a time when GitHub did not yet have features like Gist. As of 2026, it is roughly 18 years old, unmaintained, and has now been marked archived and read-only to preserve it as a historical reference. 

For a modern maintained library, check this out instead:
- https://github.com/square/gifencoder

---

# android-gif-encoder

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
