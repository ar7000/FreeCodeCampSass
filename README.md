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

    - Can also be passed an if/else statment:

    ```
    <style type='text/sass'>

    @mixin border-stroke($val){
        @if $val == light{
        border:1px solid black;
        } @else if $val == medium{
        border:3px solid black;
        } @else if $val == heavy{
        border:6px solid black;
        } @else {
        border:none;
        }
    }

    #box {
        width: 150px;
        height: 150px;
        background-color: red;
        @include border-stroke(medium);
    }
    </style>

    <div id="box"></div>
    ```

    Would output a red box with a 3px solid black border.

- Learned to create a for loop using Sass, resulting in an automated output of a list of classes. Example:

    ```
    <style type='text/sass'>

    @for $j from 1 to 6{
        .text-#{$j} {font-size: $j * 10}
    }

    </style>

    <p class="text-1">Hello</p>
    <p class="text-2">Hello</p>
    <p class="text-3">Hello</p>
    <p class="text-4">Hello</p>
    <p class="text-5">Hello</p>
    ```

    Would increment each line's font size by 10px. Resulting CSS would look like:

    ```
    .text-1{
        font-size:10px;
    }

    .text-2{
        font-size:20px;
    }

    .text-3{
        font-size:30px;
    }

    .text-4{
        font-size:40px;
    }

    .text-5{
        font-size:50px;
    }

    .text-6{
        font-size:60px;
    }
    ```

- Learned how to map over each item in a list and create an output for each item. Example:

```
$colors: (1: black, 2: white, 3: yellow);

@each $key, $color in $colors{
    .#{$color}-text {color: $color}
}

```

Would output:

```
.black-text{
    color:black;
}

.gold-text{
    color:white;
}

.yellow-text{
    color:yellow;
}
```

- Learned to create a while loop. Working similarly to a JS while loop, this executes a function until a condition is met. Example:

```
$x: 1;
@while $x < 5{
    .width-#{$x} {width: $x * 10}
    $x: $x + 1;
}
```

Would output:

```
.width-1{
    width:10px;
}
.width-2{
    width:20px;
}
.width-3{
    width:30px;
}
.width-4{
    width:40px;
}
```

- Learned to copy an elements values to another element with @extend. Directly copies the values of the specified element then gives us to ability to build on them. Example:

```
.box{
    display:flex;
    justify-content:center;
    align-items:center;
    width:200px;
    height:200px;
}

.red-box{
    @extend .box;
    background-color:red;
}

.blue-box{
    @extend .box;
    background-color:blue;
}

.yellow-box{
    @extend .box;
    background-color:yellow;
}
```

Calling these classes on three divs would create three 200px boxes with their child elements horizontally and vertically centered. Each box's background color would vary as indicated on the individual classes.