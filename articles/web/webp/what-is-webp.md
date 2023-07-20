WebP is a high-performance raster graphics file format developed by Google in 2010. It employs advanced compression techniques, including both lossless and lossy algorithms, to significantly reduce file sizes. This reduction in size leads to faster webpage load times, benefiting both users and website owners. Notably, WebP has gained widespread support across browsers, as confirmed by [Can I Use](https://caniuse.com/webp).

### Why you should use it

WebP aims to provide a more efficient solution compared to other raster graphics file formats such as JPEG, while maintaining the same quality. It offers both lossless and lossy compression options, where lossless retains all initial data, and lossy achieves higher compression ratios with some quality loss.

In many use cases, lossy WebP can be used without significant quality differences. In addition, WebP has an alpha channel, meaning it can be used for transparency, as well as support for animations making it an alternative to the widely recognized gif.

Using optimized media improves application performance by reducing page load times, resulting in a better overall user experience. The importance of a good user experience is universally recognized and is therefore one of many metrics used by search engines to index search results. In other words, using optimized formatted and sized media will have an impact on generating traffic to your site.

Developing accessible and performant web solutions is something developers should all strive for, and properly formatted media is one of several key components of that. Along with responsive design, efficient code, and semantic HTML to mention a few.

To provide a visual comparison, I have arranged three images with identical dimensions: ` .jpg (123 kb)`, `.webp (64 kb)`, and `.webp (16 kb)` using medium compression. I have chosen to use an image with sharp lines and strong contrast, as blurry lines are often one of the more obvious indications of compression and image quality loss.

![example-jpg](https://i.ibb.co/hLtHWBR/example.jpg)
![example-webp](https://i.ibb.co/xXX2JN7/example-webp.webp)
![example-lossy-webp](https://i.ibb.co/f4Y1dZW/exampleloss.webp)

The first two images should have no discernable differences between them but offer a significant difference in overall file size `(59kb)`. In the lossy example, you can spot some artifacts, but not to the extent where the image is unusable.

According to this source the average [download speed](https://www.europeandatajournalism.eu/internet-speed-in-europe/) is 103.3Mbps in Europe, making 59kb sound like such an arbitrary number. It would take roughly 1/100th of a second to load a file of 123kb so why should you make an effort to reduce the file size further?

In addition to the reasons explained above, with load times directly correlating with search engine indexing, media files are not the only assets being loaded by the client. JavaScript, CSS stylesheets, fonts, and CDN links also add to the overall footprint, which will all directly impact FCP (First Contentful Paint).

FCP refers to when the browser first renders a bit of content from the DOM to be consumed by the user and is one of several metrics used to measure the overall performance of a website.

It is also important to consider that not all corners of the world have access to high-speed connections, even in countries where the infrastructure is considered to be way above average. Some might be on limited data plans or live in remote locations.

Beyond considering the situations and locations from which your target demographic accesses your site, it is considered good internet etiquette to make your application as accessible as possible.

#### To Lossy or Not to Lossy

Using image compression will always result in a reduction in image quality, ranging from hardly noticeable to incredibly jarring. However, it shouldn't be applied without considering the following factors:

- Is it properly sized?
  It is quite common for images to have much larger dimensions than necessary. Therefore, optimizing media should begin by examining its dimensions. While responsive web design may require dynamic sizing, you should still determine the maximum acceptable size.

- What purpose does it serve?
  In situations where images complement the rest of the content, some loss in quality may be more acceptable. However, if an image is the primary focus, such as a promotional image for a new product, compromising quality might not an alternative.

  On the other hand, in an informative article, where media and images are usually complementary, compressing them to reduce load times becomes a more attractive option.

- How large is it?
  The larger an image, the more noticeable artifacts will be due to its size. Therefore, selective application of compression is recommended. It's worth noting that lossy WebP's compression algorithms aim to mask imperfections by removing unimportant data only,

#### In animations

Google reports that animated lossy WebP can result in as much as a 64% smaller file size. However, some accounts suggest that there might be a significant quality loss compared to other formats such as GIF.

It's important to consider that GIFs do not offer compression, making WebP a more attractive option in situations where performance is prioritized over quality. Another point to keep in mind is that although WebP is gaining popularity, it is not as widely recognized as GIF, which is almost universally accepted.

#### WebP in CMS

In general, Content Management Systems (CMS) typically do not provide native support for WebP images. However, there are usually extensions or plugins available that can automate the process of converting images to WebP format and deliver them to compatible browsers. Wordpress is one exception where support is native.

### Start using WebP

If you don’t have access to a premium application such as [Photoshop](https://www.adobe.com/products/photoshop.html) a popular image editing software, you can use [Advanced Batch Image Converter](https://sourceforge.net/projects/abic/) available on most operating systems, or [WebP Converter](https://apps.apple.com/us/app/webp-converter/id1522368690?mt=12) for MacOS.

As a free online solution, [XConvert](https://www.xconvert.com/compress-image) can convert your images in batches into WebP.

For those who are more tech-savvy or adventurous, converting images using the Command Line Interface is also an option. Here's how you can do it. First off, we need to install [cwebp](https://developers.google.com/speed/webp/docs/cwebp), a WebP Encoder tool.

To open your Terminal (MacOS) or Command Prompt (Windows) the easiest solution is to search for it within your operating system.

#### On Linux

```shell
sudo apt-get install webp
```

#### On MacOS (Using Homebrew)

To install Homebrew (if you haven't already) on your MacOS platform, start by running the following command:

```shell
// "install Homebrew if you haven't already"
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Once the installations is complete, run the following command and you'll be all set.

```shell
brew install webp
```

#### For Windows

To install WebP on windows, follow these steps:

1. Start by downloading the appropriate link from this [location](https://developers.google.com/speed/webp/docs/precompiled)
2. Since it is a zip file, you need to extract the `.exe` to a directory of your choice.
3. Navigate to that directory and copy `Ctrl + C` or cut `Ctrl + X` the directory file path.
4. Search for `Advanced System Settings` in your windows search bar.
5. Within the `Advanced` tab click on `Environmental Variables`
6. Scroll to find the `Path` variable under systems variable. Highlight it, and click `Edit`
7. Within the edit window select `New` and paste `Ctrl + V` as the new value.

Once you have restarted your Command Prompt, you should be able to run `cwebp` as an executable from within the CLI.

#### Converting a batch of images:

First, navigate to the folder of your images. Here’s an example of how the command might look in the terminal or command prompt:

```shell
cd documents/images/my-project
```

`CD` is the command for changing directory, and in this example the command specifies a folder with the name `documents`, which has a subfolder named `images`, which then again has a subfolder called `my-project`. Once you have located the folder you want to make changes to, you can run the following command to convert all images within.

On Windows:

```shell
for /R . %I in (*.jpg) do ( cwebp.exe %I -o %~fnI.webp )
```

On MacOS:

```shell
$ for F in *.jpg; do cwebp $F -o `basename ${F%.jpg}`.webp; done
```

To break this down, the command loops through all the files within the directory and subdirectories and converts all files ending with a `.jpg` file extension into webP. If for instance, your files have the `.PNG` file extension, you would simply replace `.jpg` with `.PNG`.

#### Convert a single image

To convert a single image you can run the command from its path directory:

```shell
cwebp example.jpg -o example.webp  && del example.jpg
```

This will look for an image named `example.jpg` and output a new web file with the name specified in the command. The second operation deletes the original file, but only if the first operation is successful.
In any instance, you can add the `-q` (quality) flag after the webp command word followed by the desired number between 1-100 for lossy compression on the conversion i.e `-q 80`.

For more extensive use you can visit the [cwebp documentation](https://developers.google.com/speed/webp/docs/cwebp)

### Conclusion

WebP is a highly effective option for optimizing web images, resulting in faster page load times and enhanced user experience. It also improves search engine indexing and helps generate more traffic to your website.

However, as technologies continue to evolve, file formats like avif and JPEG XL may eventually surpass WebP in terms of web optimization. Stay tuned for a future article where I will cover these formats in more detail.

The Markdown for this article as well as associated resources used can be located [here](https://github.com/Menubrea/menubrea-dev-articles/blob/main/articles/web/webp/what-is-webp.md).
