Working through Sass via FreeCodeCamp resources and copying passed code to Git repo as I go through each task. Documenting below anything new I learn.

- Learned to create Sass variables in order to make CSS easily reusable and changable. Declared with '$', followed by variable name and value. Can then be called by passing variable name to an element. Example:
```
$main-pink:#FF008C;

header{
    background-color:$main-pink;
}

.btn{
    background-color:$main-pink;
}
```
Both items indicated above would have a background color of #FF008C. If this color needs to be changed, only the main color variable needs to be altered in the stylesheet.

- Learned to nest child elements within SCSS stylesheet in order to maintain cleaner code. Cleaner alternative to everything on one line. Example:

```
.text-box{
    background-color:green;
}

.text-box h3{
    font-size:1.4em;
    color:white;
}

.text-box p{
    color:yellow;
}
```

Would become:

```
.text-box{
    background-color:green;

    h3{
        font-size:1.4em;
        color:white;
    }

    p{
        color:yellow;
    }
}
```

- Learned to create mixins to make reusable blocks of CSS. Declared with @mixin then given a name, followed by the relevent CSS. Unlike variables, mixins can take parameters. Can then be called on an element with @include, followed by mixin name and any parameters, just like a JS function. Example:

```
@mixin box-shadow($x,$y,$blur,$c){
    -webkit-box-shadow: $x, $y, $blur, $c;
    -moz-box-shadow: $x, $y, $blur, $c;
    -ms-box-shadow: $x, $y, $blur, $c;
    box-shadow: $x, $y, $blur, $c;
}

.text-box{
    @include box-shadow(15px, 15px, 10px, red)
}

.feature-img{
    @include box-shadow(20px, 20px, 15px, blue)
}
```

Uses parameters in the same way as a JS function in order to avoid having to re-write same code in order to support multiple browsers.