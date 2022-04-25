# What is the purpose of this ?
[react-slick](https://react-slick.neostack.com/) uses peer-dependency [slick-carousel](https://github.com/kenwheeler/slick) which uses custom font unfortunately not optimized. This is impacting a few of the performance of our main site **80ms**. Every thousand seconds contributes to the user experience.

![metrics](https://i.ibb.co/ZVLSf09/Screen-Shot-2022-04-24-at-8-21-23.png)

slick-carousel uses the following font format:
- .eot
- .ttf
- .woff

As you can see, they are formats that are not friendly.

## How can we solve this ?

The source was converted to an optimized `woff2` format, we deployed that asset independently. In the main site the slick-carousel styles are overwritten and so that the new font is consumed instead of the one that the package has integrated.

In the main site, a prefetch of the source is made to be able to eliminate that 80ms metric.