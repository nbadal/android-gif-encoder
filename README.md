android-gif-encoder
===================

An animated GIF encoder for Android, without any native code required. Based on the J2ME encoder posted here: http://www.jappit.com/blog/2008/12/04/j2me-animated-gif-encoder/, with the addition of dirty rectangle support.

See this solution.

https://github.com/nbadal/android-gif-encoder

It's an Android version of this post.

http://www.jappit.com/blog/2008/12/04/j2me-animated-gif-encoder/

To use this class, here is an example helper method to generate GIF byte array. Note here the getBitmapArray() function is a method to return all the Bitmap files in an image adapter at once. So the input is all the Bitmap files in one adapter, the output is a byte array which you can write to the file.

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
To use this function, do the following then you can save the file into SDcard.

FileOutputStream outStream = null;
        try{
            outStream = new FileOutputStream("/sdcard/generate_gif/test.gif");
            outStream.write(generateGIF());
            outStream.close();
        }catch(Exception e){
            e.printStackTrace();
        }
