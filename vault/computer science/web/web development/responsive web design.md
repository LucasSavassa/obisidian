q: what is resolution? how is it different from screen size?
q: what is viewport?
q: how zoom affects all?
q: how bandwidth would affect design choices?

```
first batch

- responsive web design is about looking well on different devices
- responsive web design is about good usability on different devices
- different devices include smartphone, table, laptop, wide screen, watch
- in the past, server-side sniffing was used to determine device capability
- for each device capability, a different site was served
- nowadays, mobile devices are much more capable
- therefore, old techniques became obsolete
- usability is still a concern
- bandwidth is still a concern
- life battery is still a concern
```

```
second batch

- the concept of breakpoint is related to media queries
- media queries are assertions about the screen media
- media query: @media screen and (width > 200px)
- media query: if the media is screen and is larger than 200px
- css rules inside media query is applied when the condition is met
- a set of width-related media queries are called breakpoints
- an interesting approach is to create mobile-first default css
- then use media-queries to adapt content to larger pages
- media-query: could only link stylesheets inside media queries
- media-query: could only set variables inside media queries
```

# images

``` css
img, picture, video { max-width: 100%; }
```

> [!info] best practice
> images will shrink, but never grow larger than original width

# font-size rem and em

- `rem` sets a font size relative to html font-size
- `em` sets a font size relative to parent font-size

# viewport
![[Pasted image 20260225120011.png]]